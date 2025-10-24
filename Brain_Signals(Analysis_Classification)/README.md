# 🧠 EEG Brain Signal Analysis and Classification

This repository contains a complete workflow for **EEG signal analysis and digit classification** using the [MindBigData](https://www.mindbigdata.com/opendb/) dataset.  
The project demonstrates how to preprocess raw EEG signals, extract meaningful features in both time and frequency domains, and train machine learning models for classification.

---

## 📌 Objectives
- Load and preprocess large-scale EEG datasets.  
- Visualize raw and averaged EEG signals across multiple channels.  
- Perform **frequency-domain analysis** (PSD, spectrograms, band powers).  
- Extract **band power features** (Delta, Theta, Alpha, Beta, Gamma).  
- Normalize and prepare features for machine learning.  
- Train and evaluate classifiers (SVM) for digit recognition.  
- Provide interpretable results with confusion matrices and performance metrics.  

---

## 📂 Project Workflow

### 1. Dataset Handling
- Download EEG datasets from Kaggle via `kagglehub`.  
- Explore dataset structure and load `.txt` files into a **pandas DataFrame**.  
- Columns include: `id`, `event`, `device`, `channel`, `code`, `size`, `data`.  
- Convert the `data` column (comma-separated string) into numeric arrays.  

### 2. Signal Visualization
- Plot raw EEG signals for:
  - A random event across all channels.  
  - A specific digit (e.g., digit = 1 or 3).  
- Compute **average waveforms** per channel by aligning signals to the most common length.  

### 3. Frequency Analysis
- **Power Spectral Density (PSD):**  
  - Use Welch’s method to estimate power distribution across frequencies.  
  - Focus on the 0–60 Hz range (Delta–Gamma bands).  
- **Spectrograms:**  
  - Compute time–frequency representations of EEG signals.  
  - Visualize how power changes across time and frequency.  

### 4. Band Power Extraction
- Define EEG bands:  
  - Delta (0.5–4 Hz)  
  - Theta (4–8 Hz)  
  - Alpha (8–13 Hz)  
  - Beta (13–30 Hz)  
  - Gamma (30–60 Hz)  
- Integrate PSD values within each band to compute **band powers**.  
- Aggregate average band powers per channel and digit.  
- Visualize results with bar plots.  

### 5. Feature Engineering
- Construct a **feature matrix** with band powers as features.  
- Normalize features using **StandardScaler**.  
- Handle missing values (if any).  
- Optionally apply **PCA** for dimensionality reduction and visualization.  

### 6. Classification
- Train a **Support Vector Machine (SVM)** classifier with:  
  - `kernel='rbf'`  
  - `class_weight='balanced'` (to handle class imbalance).  
- Evaluate with:
  - **5-fold cross-validation** (balanced accuracy).  
  - **Classification report** (precision, recall, F1-score).  
  - **Confusion matrix** for detailed error analysis.  

Thank You!
