# 🧠 EEG Brain Signal Preprocessing (MindBigData)

## 📌 Objectives
- Download and load the **MindBigData EEG dataset**.  
- Parse raw EEG signals into structured arrays.  
- Apply **signal preprocessing**:
  - DC offset removal  
  - Band-pass filtering (0.5–40 Hz)  
  - Notch filtering (50 Hz powerline noise)  
- Normalize signals using **Z-score standardization**.  
- Store processed signals and labels for later feature extraction and classification.  
- Visualize raw vs. processed EEG signals.

---

## 📂 Workflow Overview

### 1. Dataset Handling
- Download dataset from Kaggle using `kagglehub`.  
- Explore dataset structure (`IN.txt`, `MW.txt`, `EP.txt`, `MU.txt`).  
- Load EEG data into a **pandas DataFrame** with columns:  
  `id`, `event`, `device`, `channel`, `code`, `size`, `data`.

### 2. Signal Preprocessing
- **Band-pass filter**: 4th-order Butterworth, 0.5–40 Hz.  
- **Notch filter**: 50 Hz with Q=30 to remove powerline interference.  
- **DC removal**: subtract mean from each signal.  
- **Normalization**: Z-score per trial (mean=0, std=1).  

### 3. Implementation
- Functions:
  - `bandpass_filter(signal, fs, lowcut, highcut)`  
  - `notch_filter(signal, fs, notch_freq, Q)`  
  - `clean_signal(signal, fs, lowcut, highcut, notch_freq, Q)`  
  - `normalize(signal)`  
- Loop through first 1000 rows of the dataset:  
  - Convert `data` column to NumPy array.  
  - Apply cleaning and normalization.  
  - Append processed signals and labels.  

### 4. Visualization
- Plot raw vs. processed EEG signals for comparison.  
- Time vector created using sampling frequency (`fs=128 Hz`).  
- Demonstrates the effect of filtering and normalization.

### 5. Object-Oriented Pipeline
- `EEGPreprocessor` class encapsulates the pipeline:  
  - Precomputes filter coefficients.  
  - Provides `_clean_signal` and `_normalize` methods.  
  - `transform(df)` processes a DataFrame and returns `(signals, labels)`.

Thank You!