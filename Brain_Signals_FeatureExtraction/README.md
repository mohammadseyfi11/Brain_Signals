# 🧠 EEG Brain Signal Preprocessing and Feature Extraction

## 📌 Objectives
- Download and load the **MindBigData EEG dataset**.  
- Parse raw EEG signals into structured arrays.  
- Apply **signal preprocessing**:
  - DC offset removal  
  - Band-pass filtering (0.5–40 Hz)  
  - Notch filtering (50 Hz powerline noise)  
- Normalize signals using **Z-score standardization**.  
- Extract **time-domain and frequency-domain features**:
  - Statistical features (mean, variance, skewness, kurtosis, peak-to-peak)  
  - Hjorth parameters (activity, mobility, complexity)  
  - Band powers (Delta, Theta, Alpha, Beta, Gamma)  
  - Spectral entropy  
- Save extracted features into a **CSV file** for further analysis or classification.

---

## 📂 Workflow Overview

### 1. Dataset Handling
- Download dataset from Kaggle using `kagglehub`.  
- Explore dataset structure (`IN.txt`, `MW.txt`, `EP.txt`, `MU.txt`).  
- Load EEG data into a **pandas DataFrame** with columns:  
  `id`, `event`, `device`, `channel`, `code`, `size`, `data`.

### 2. Preprocessing
- **EEGPreprocessor Class**:
  - Initializes with sampling rate and filter parameters.  
  - `_bandpass_filter`: 4th-order Butterworth filter (0.5–40 Hz).  
  - `_notch_filter`: 50 Hz notch filter with Q=30.  
  - `_clean_signal`: removes DC offset, applies band-pass and notch filters.  
  - `_normalize`: Z-score normalization (mean=0, std=1).  
  - `transform`: processes all rows in a DataFrame and returns `(signals, labels)`.

### 3. Feature Extraction
- **EEGFeatureExtractor Class**:
  - `_time_features`: mean, variance, skewness, kurtosis, peak-to-peak, Hjorth parameters.  
  - `_freq_features`:  
    - Power Spectral Density (Welch’s method).  
    - Band powers (Delta, Theta, Alpha, Beta, Gamma).  
    - Normalized band powers.  
    - Spectral entropy.  
  - `extract_features`: combines time and frequency features into a single dictionary.

### 4. Integrated Pipeline
- Loop through all rows of the DataFrame.  
- Convert raw signal strings into NumPy arrays.  
- Apply preprocessing (`EEGPreprocessor`).  
- Extract features (`EEGFeatureExtractor`).  
- Add metadata (`digit` and `channel`).  
- Append results to `feature_list`.

### 5. Save Features
- Convert `feature_list` into a **pandas DataFrame**.  
- Save as `features_preprocessed_full.csv`.  
- Print shape and preview of the resulting DataFrame.  

Thank You!
