============================================================
DIRECTORY STRUCTURE EXPLORATION
============================================================

📂 Main Directory Structure:
📁 ESC-50-master/
  📄 LICENSE (277.9 KB)
  📄 README.md (29.8 KB)
  📁 audio/
    📄 1-100032-A-0.wav (430.7 KB)
    📄 1-100038-A-14.wav (430.7 KB)
    📄 1-100210-A-36.wav (430.7 KB)
    📄 1-100210-B-36.wav (430.7 KB)
    📄 1-101296-A-19.wav (430.7 KB)
    📄 1-101296-B-19.wav (430.7 KB)
    📄 1-101336-A-30.wav (430.7 KB)
    📄 1-101404-A-34.wav (430.7 KB)
    📄 1-103298-A-9.wav (430.7 KB)
    📄 1-103995-A-30.wav (430.7 KB)
    ... and 1990 more items
  📁 meta/
    📄 esc50-human.xlsx (533.7 KB)
    📄 esc50.csv (91.5 KB)
📁 genres_stems/
  📁 blues/
    📁 blues.00000/
    📁 blues.00001/
    📁 blues.00002/
    📁 blues.00003/
    📁 blues.00004/
    📁 blues.00005/
    📁 blues.00006/
    📁 blues.00007/
    📁 blues.00008/
    📁 blues.00009/
    ... and 90 more items
  📁 classical/
    📁 classical.00000/
    📁 classical.00001/
    📁 classical.00002/
    📁 classical.00003/
    📁 classical.00004/
    📁 classical.00005/
    📁 classical.00006/
    📁 classical.00007/
    📁 classical.00008/
    📁 classical.00009/
    ... and 90 more items
  📁 country/
    📁 country.00000/
    📁 country.00001/
    📁 country.00002/
    📁 country.00003/
    📁 country.00004/
    📁 country.00005/
    📁 country.00006/
    📁 country.00007/
    📁 country.00008/
    📁 country.00009/
    ... and 90 more items
  📁 disco/
    📁 disco.00000/
    📁 disco.00001/
    📁 disco.00002/
    📁 disco.00003/
    📁 disco.00004/
    📁 disco.00005/
    📁 disco.00006/
    📁 disco.00007/
    📁 disco.00008/
    📁 disco.00009/
    ... and 90 more items
  📁 hiphop/
    📁 hiphop.00000/
    📁 hiphop.00001/
    📁 hiphop.00002/
    📁 hiphop.00003/
    📁 hiphop.00004/
    📁 hiphop.00005/
    📁 hiphop.00006/
    📁 hiphop.00007/
    📁 hiphop.00008/
    📁 hiphop.00009/
    ... and 90 more items
  📁 jazz/
    📁 jazz.00000/
    📁 jazz.00001/
    📁 jazz.00002/
    📁 jazz.00003/
    📁 jazz.00004/
    📁 jazz.00005/
    📁 jazz.00006/
    📁 jazz.00007/
    📁 jazz.00008/
    📁 jazz.00009/
    ... and 90 more items
  📁 metal/
    📁 metal.00000/
    📁 metal.00001/
    📁 metal.00002/
    📁 metal.00003/
    📁 metal.00004/
    📁 metal.00005/
    📁 metal.00006/
    📁 metal.00007/
    📁 metal.00008/
    📁 metal.00009/
    ... and 90 more items
  📁 pop/
    📁 pop.00000/
    📁 pop.00001/
    📁 pop.00002/
    📁 pop.00003/
    📁 pop.00004/
    📁 pop.00005/
    📁 pop.00006/
    📁 pop.00007/
    📁 pop.00008/
    📁 pop.00009/
    ... and 90 more items
  📁 reggae/
    📁 reggae.00000/
    📁 reggae.00001/
    📁 reggae.00002/
    📁 reggae.00003/
    📁 reggae.00004/
    📁 reggae.00005/
    📁 reggae.00006/
    📁 reggae.00007/
    📁 reggae.00008/
    📁 reggae.00009/
    ... and 90 more items
  📁 rock/
    📁 rock.00000/
    📁 rock.00001/
    📁 rock.00002/
    📁 rock.00003/
    📁 rock.00004/
    📁 rock.00005/
    📁 rock.00006/
    📁 rock.00007/
    📁 rock.00008/
    📁 rock.00009/
    ... and 90 more items
📁 mashups/
  📄 song0001.wav (1292.0 KB)
  📄 song0002.wav (962.0 KB)
  📄 song0003.wav (1288.0 KB)
  📄 song0004.wav (1292.0 KB)
  📄 song0005.wav (1292.0 KB)
  📄 song0006.wav (1292.0 KB)
  📄 song0007.wav (1292.6 KB)
  📄 song0008.wav (1287.0 KB)
  📄 song0009.wav (1292.0 KB)
  📄 song0010.wav (1281.0 KB)
  ... and 3010 more items
📄 sample_submission.csv (33.6 KB)
📄 test.csv (76.7 KB)

============================================================
CSV FILES EXPLORATION
============================================================

📄 test.csv:
   Shape: (3020, 2)
   Columns: ['id', 'filename']

   First 5 rows:
   id              filename
0   1  mashups/song0001.wav
1   2  mashups/song0002.wav
2   3  mashups/song0003.wav
3   4  mashups/song0004.wav
4   5  mashups/song0005.wav

   Data types:
id           int64
filename    object
dtype: object

📄 sample_submission.csv:
   Shape: (3020, 2)
   Columns: ['id', 'genre']

   First 5 rows:
   id      genre
0   1       jazz
1   2      blues
2   3  classical
3   4        pop
4   5      disco

   Unique genres in sample: ['jazz' 'blues' 'classical' 'pop' 'disco' 'rock' 'hiphop' 'country'
 'metal' 'reggae']

============================================================
FILE COUNTS
============================================================

📁 genres_stems/:
   Genres found: ['blues', 'classical', 'country', 'disco', 'hiphop', 'jazz', 'metal', 'pop', 'reggae', 'rock']
   blues: 100 songs
      └── Sample stems: ['drums.wav', 'vocals.wav', 'bass.wav', 'other.wav']
   classical: 100 songs
      └── Sample stems: ['drums.wav', 'vocals.wav', 'bass.wav', 'other.wav']
   country: 100 songs
      └── Sample stems: ['drums.wav', 'vocals.wav', 'bass.wav', 'other.wav']
   disco: 100 songs
      └── Sample stems: ['drums.wav', 'vocals.wav', 'bass.wav', 'other.wav']
   hiphop: 100 songs
      └── Sample stems: ['drums.wav', 'vocals.wav', 'bass.wav', 'other.wav']
   jazz: 100 songs
      └── Sample stems: ['drums.wav', 'vocals.wav', 'bass.wav', 'other.wav']
   metal: 100 songs
      └── Sample stems: ['drums.wav', 'vocals.wav', 'bass.wav', 'other.wav']
   pop: 100 songs
      └── Sample stems: ['drums.wav', 'vocals.wav', 'bass.wav', 'other.wav']
   reggae: 100 songs
      └── Sample stems: ['drums.wav', 'vocals.wav', 'bass.wav', 'other.wav']
   rock: 100 songs
      └── Sample stems: ['drums.wav', 'vocals.wav', 'bass.wav', 'other.wav']

📁 mashups/: 3020 files
   Sample files: ['song0001.wav', 'song0002.wav', 'song0003.wav', 'song0004.wav', 'song0005.wav']

📁 ESC-50-master/:
   📁 meta/: 2 files
   📄 LICENSE
   📄 README.md
   📁 audio/: 2000 files

============================================================
EXPLORATION COMPLETE
============================================================
