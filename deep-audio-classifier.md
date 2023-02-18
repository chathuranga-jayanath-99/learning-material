src - https://www.youtube.com/watch?v=ZLIPkmmDJAc

done by - Nicholas Renotte

technologies - TensorFlow, Python

task - going to find a cappucino bird in a full audio clip. full clip is divided into 3 mins. then they are choped into 3s. first check for 3s intervals and aggregate at end. 

data available at - https://www.kaggle.com/kenjee/z-by-hp-unlocked-challenge-3-signal-processing 

data contain 3 folders. 
  1. forest souds 
  2. cappucino sounds 
  3. false cappucino sounds 

download the data. 

# 1. Import and Install Dependencies
## 1.1 Install Dependencies
`!pip install tensorflow==2.4.1 tensorflow-gpu==2.4.1 tensorflow-io matplotlib`
## 1.2 Load Dependencies
```python3
import os
from matplotlib import pyplot as plt
import tensorflow as tf 
import tensorflow_io as tfio
```
# 2. Build Data Loading Function
## 2.1 Define Paths to Files
```python3
CAPUCHIN_FILE = os.path.join('data', 'Parsed_Capuchinbird_Clips', 'XC3776-3.wav')
NOT_CAPUCHIN_FILE = os.path.join('data', 'Parsed_Not_Capuchinbird_Clips', 'afternoon-birds-song-in-forest-0.wav')
```
## 2.2 Build Dataloading Function

```python3
def load_wav_16k_mono(filename):
    # Load encoded wav file
    file_contents = tf.io.read_file(filename)
    # Decode wav (tensors by channels) 
    wav, sample_rate = tf.audio.decode_wav(file_contents, desired_channels=1)
    # Removes trailing axis
    wav = tf.squeeze(wav, axis=-1)
    sample_rate = tf.cast(sample_rate, dtype=tf.int64)
    # Goes from 44100Hz to 16000hz - amplitude of the audio signal
    wav = tfio.audio.resample(wav, rate_in=sample_rate, rate_out=16000)
    return wav
```

## 2.3 Plot Wave
```python3
wave = load_wav_16k_mono(CAPUCHIN_FILE)
nwave = load_wav_16k_mono(NOT_CAPUCHIN_FILE)
```

```python3
plt.plot(wave)
plt.plot(nwave)
plt.show()
```
