# PROJECT SUMMARY: Messy Mashup Music Genre Classification

## Competition Overview
- **Platform**: Kaggle
- **Task**: Classify music genre from noisy mashup audio files
- **Metric**: Macro F1 Score
- **Classes**: 10 genres - blues, classical, country, disco, hiphop, jazz, metal, pop, reggae, rock
- **Test samples**: 3,020 mashups

---

## Dataset Structure
```
messy_mashup/
├── genres_stems/          # Training data: 10 genres × 100 songs × 4 stems
│   └── {genre}/{song}/    # drums.wav, vocals.wav, bass.wav, other.wav
├── mashups/               # Test data: 3,020 noisy mashup files
├── ESC-50-master/audio/   # 2,000 noise files for augmentation
├── test.csv               # id, filename mapping
└── sample_submission.csv  # id, genre format
```

---

## Critical Domain Shift Analysis

| Property | Training Stems | Test Mashups |
|----------|---------------|--------------|
| Sample Rate | 44100 Hz | **22050 Hz** |
| Channels | Stereo (2) | **Mono (1)** |
| Duration | ~30s fixed | **15.84s - 30.01s variable** |
| ZCR | 0.0831 | 0.1340 (+61%) |
| Spectral Centroid | 1784 | 2933 (+64%) |
| Spectral Flatness | 0.0036 | 0.0530 (+1381%) |

**Key insight**: Test data is MUCH noisier than clean stems. Aggressive noise augmentation essential.

---

## Solution Architecture

### Data Pipeline
1. **Load stems** at 22050 Hz, mono
2. **Create synthetic mashups**: Mix stems from different songs of same genre
3. **Add noise**: 1-3 ESC-50 samples at 0.05-0.35 intensity
4. **Convert to Mel spectrogram**: 128 mels, 2048 FFT, 512 hop
5. **Normalize**: Min-max to [0,1]
6. **Output shape**: (1, 128, 1292)

### Model: Custom CNN with SE Blocks
```
- Conv1: 1→64 channels, 7×7, stride 2 + MaxPool
- Layer1: 2× ResBlock(64→64) with SE
- Layer2: 2× ResBlock(64→128) with SE, stride 2
- Layer3: 2× ResBlock(128→256) with SE, stride 2  
- Layer4: 2× ResBlock(256→512) with SE, stride 2
- AdaptiveAvgPool → Dropout(0.5) → FC(512→10)
- Total params: ~11.2M
```

### Training Config
```python
CONFIG = {
    'sr': 22050,
    'duration': 30,
    'n_mels': 128,
    'n_fft': 2048,
    'hop_length': 512,
    'fmin': 20,
    'fmax': 8000,
    'noise_intensity_range': (0.05, 0.35),
    'num_noise_samples': (1, 4),
    'volume_range': (0.4, 1.0),
    'batch_size': 16,
    'num_epochs': 30,
    'learning_rate': 1e-3,
    'weight_decay': 1e-4,
    'num_mashups_per_song': 5,
    'val_split': 0.15,
    'num_classes': 10,
}
```

---

## Notebook Structure (6 Cells)

### Cell 1-4: Data Exploration (CPU, optional for final run)
- Directory structure analysis
- Audio properties (sample rate, duration, channels)
- Spectrogram visualization
- Feature comparison (training vs test distribution)
- Synthetic mashup generation testing

### Cell 5: Not used in final version

### Cell 6: Model & Dataset Setup (GPU)
- Imports and configuration
- `MusicGenreDataset` class with on-the-fly augmentation
- `MusicGenreCNN` model with SE blocks
- Train/val split (85/15)
- DataLoader creation

### Cell 6.5: Pre-compute Spectrograms (GPU) ⚠️ CRITICAL
```python
# Must include this import!
from torch.utils.data import TensorDataset, DataLoader
```
- Pre-computes ALL spectrograms into memory
- Converts to TensorDataset for fast training
- Takes ~30-40 minutes but makes training ~10-15 minutes
- Frees memory after conversion

### Cell 7: Training + Inference + Submission (GPU)
**Features:**
- Multi-GPU support: `nn.DataParallel`
- Mixed precision: `GradScaler`, `autocast`
- Mixup augmentation
- OneCycleLR scheduler
- Label smoothing (0.1)
- Early stopping (patience=7)
- Test Time Augmentation (3 passes)
- Confidence score reporting
- Submission file creation

---

## Key Fixes Applied
1. **TensorDataset import** was missing in Cell 6.5
2. **Multi-GPU support** added for Kaggle's 2×T4 setup
3. **Pre-computation approach** to avoid Kaggle timeout (was ~11 hours, now ~60 min total)

---

## Expected Performance
| Validation F1 | Expected LB Range |
|---------------|-------------------|
| 60% | 50-58% |
| 70% | 58-65% |
| 80% | 65-75% |

---

## Runtime Estimates
| Phase | Time |
|-------|------|
| Cell 6 (setup) | ~2 min |
| Cell 6.5 (pre-compute) | ~30-40 min |
| Cell 7 (train 30 epochs) | ~10-15 min |
| Cell 7 (test inference) | ~10 min |
| **Total** | **~55-70 min** |

---

## Submission Format
```csv
id,genre
1,blues
2,classical
...
```

---

## Files Created
- `best_model.pth` - Trained model weights
- `submission.csv` - Final submission
- `training_history.png` - Loss/accuracy curves
- `confusion_matrix.png` - Validation confusion matrix
- `prediction_distribution.png` - Test prediction distribution

---

## Important Notes
1. **Kaggle timeout**: ~1-2 hours for GPU sessions. Pre-computation is essential.
2. **"Save Version" runs all cells fresh** - no previous outputs carry over
3. **Checkpointing won't help** - Kaggle wipes /kaggle/working/ on restart
4. **Domain gap is significant** - noise augmentation is critical for generalization
5. **Validation F1 will likely be 5-15% higher than LB** due to distribution differences

---

## To Resume in New Chat
Provide this summary and state:
- Current cell being worked on
- Any errors encountered
- Current validation F1 achieved (if training completed)
- Any modifications made to the code
