# 🧠 Brain Signal Analysis and Exploration

## 📌 Project Overview
The main objectives of this project are:
- Inspect the dataset structure and load EEG signals into a structured DataFrame.
- Perform **time-domain analysis** of EEG signals.
- Apply **Fast Fourier Transform (FFT)** to explore frequency-domain characteristics.
- Compare signals across different digits and channels.
- Compute and visualize **channel correlations** using a correlation matrix and heatmap.
- Highlight **brainwave frequency bands** (Delta, Theta, Alpha, Beta, Gamma).
- Explore statistical summaries such as mean signal values across events.

---

## 📂 Dataset
The dataset is downloaded from Kaggle via `kagglehub`:
- **Files included**: `IN.txt`, `MW.txt`, `EP1.01.txt`, `MU.txt`
- Each row contains:
  - `id` – record identifier  
  - `event` – event code  
  - `device` – device type  
  - `channel` – EEG channel (e.g., AF3, AF4, T7, T8, PZ)  
  - `code` – digit label  
  - `size` – signal length  
  - `data` – comma-separated EEG values  

---

## ⚙️ Methods and Analysis
- **Signal Parsing**: Convert raw string data into NumPy arrays.  
- **Visualization**:
  - Time-domain plots of EEG signals.
  - Frequency spectra (linear and dB scale).
  - Distribution of signal lengths.
  - Boxplots of mean signal values by event.
- **Correlation Analysis**:
  - Truncate signals to equal lengths.
  - Compute Pearson correlation coefficients between channels.
  - Visualize results with a heatmap.
- **Brainwave Bands**:
  - Highlight Delta (0.5–4 Hz), Theta (4–8 Hz), Alpha (8–13 Hz), Beta (13–30 Hz), Gamma (30–50 Hz).

---

## 📊 Key Findings
- **Strong correlation** between left and right frontal channels (AF3 & AF4).  
- **Moderate correlations** between frontal and parietal regions.  
- **Weak correlations** between temporal channels (T7 & T8) and other regions.  
- Frequency analysis reveals activity across standard EEG bands, with distinguishable patterns per digit/channel.