============================================================
COMPREHENSIVE TEST DURATION ANALYSIS
============================================================

File size analysis (proxy for duration):
  Total files: 3020
  Size range: 261.0 KB - 1317.0 KB
  Mean size: 1234.0 KB
  Std size: 162.5 KB

Estimated duration distribution:
  Min: 6.06s
  Max: 30.58s
  Mean: 28.65s
  Median: 29.95s

============================================================
VERIFYING DURATION ESTIMATES (sampling 50 files)
============================================================
Loading samples: 100%|██████████| 50/50 [00:01<00:00, 46.03it/s]


Verification - Actual vs Estimated:
  Correlation: 1.0000
  Actual range: 15.56s - 30.24s

<img width="1392" height="376" alt="image" src="https://github.com/user-attachments/assets/328c3fa6-5230-4f0d-94f5-ef25ab93abea" />

Duration category breakdown:
<15s        67
15-20s      85
20-25s     145
25-30s    1375
30s+      1348
Name: count, dtype: int64

============================================================
GENRE-SPECIFIC FEATURE PROFILING
============================================================

Extracting genre features (3 songs per genre)...
Processing genres: 100%|██████████| 10/10 [00:40<00:00,  4.08s/it]

Genre feature DataFrame shape: (30, 53)

<img width="1363" height="695" alt="image" src="https://github.com/user-attachments/assets/0314c9de-7b68-4412-a370-75d4a86e59de" />

============================================================
KEY DISTINGUISHING FEATURES BY GENRE
============================================================

Mean values by genre:
                          tempo  spectral_centroid  zcr_mean  mfcc_1_mean
genre                                                                    
blues      [117.51516241776316]            1622.19      0.07   128.679993
classical  [102.47809538740245]            1451.68      0.09   136.809998
country     [99.56212197580646]            2617.56      0.10    73.320000
disco      [109.06427556818183]            2941.54      0.14    70.239998
hiphop     [103.04100196678321]            2317.37      0.10    89.080002
jazz       [137.01504450464395]            1256.78      0.07   154.250000
metal       [95.45094285243742]            2768.16      0.15    77.629997
pop         [93.37441992839267]            3219.19      0.12    57.310001
reggae     [126.13511029411764]            1856.30      0.08   114.400002
rock       [127.57065716911764]            1799.44      0.07   120.339996

============================================================
TEMPO ANALYSIS (Critical for Mashup Understanding)
============================================================
                           mean   std                  min                   max
genre                                                                           
blues      [117.51516241776316]  47.0  [67.99958881578948]      [161.4990234375]
classical  [102.47809538740245]   8.7          [95.703125]  [112.34714673913044]
country     [99.56212197580646]  25.7  [83.35433467741936]        [129.19921875]
disco      [109.06427556818183]  14.5        [92.28515625]  [117.45383522727273]
hiphop     [103.04100196678321]  13.0        [92.28515625]  [117.45383522727273]
jazz       [137.01504450464395]  14.5         [123.046875]  [151.99908088235293]
metal       [95.45094285243742]  17.0  [78.30255681818181]  [112.34714673913044]
pop         [93.37441992839267]  12.7  [83.35433467741936]       [107.666015625]
reggae     [126.13511029411764]  24.5         [103.359375]  [151.99908088235293]
rock       [127.57065716911764]  22.5      [107.666015625]  [151.99908088235293]

✅ Genre analysis complete!

<img width="733" height="625" alt="image" src="https://github.com/user-attachments/assets/99acbd99-2932-4bbb-aad7-629d3045de39" />


