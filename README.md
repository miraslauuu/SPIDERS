# Stress Level Detection Based on Biosignals

This project focuses on processing and analyzing biosignals (ECG, GSR, and Respiration) collected from individuals with spider phobia during exposure to spider videos. The final goal was to extract features from these signals and train a machine learning model to classify emotional states.

## Dataset

The data was sourced from the PhysioNet repository:  
🔗 [ECG, GSR, and Respiration from Spider-Fearful Individuals](https://physionet.org/content/ecg-spider-clip/1.0.0/)

Reference paper:  
📝 [On-line anxiety level detection from biosignals](https://pmc.ncbi.nlm.nih.gov/articles/PMC7310735/)

## Project Structure

- **Loading signals**: ECG, GSR, and Respiration signals were loaded for multiple subjects.
- **Filtering**:
  - ECG: 5–12 Hz bandpass filter (4th-order Butterworth).
  - GSR: 1 Hz low-pass filter (4th-order Butterworth).
  - Respiration: 0.1–0.5 Hz bandpass filter (2nd-order Butterworth).
- **Segmentation**:
  - Signals were segmented based on timestamps provided in `Triggers.txt` for each subject.
- **Feature Extraction**:
  - **ECG**: HRV metrics (mean RR interval, SDNN, RMSSD, pNN50).
  - **GSR**: Statistical features (mean, std, range, peaks).
  - **Respiration**: Breathing rate, mean, std, number of peaks.
- **Classification**:
  - Random Forest Classifier to distinguish between "rest" and "stress" (video clips).
  - Cross-validation and leave-one-subject-out (LOSO) validation were performed.
  - Feature importance was analyzed and top features were selected for refinement.

## Results

- Achieved **very high accuracy** (close to 100%) using both full feature sets and reduced feature sets (top 4 features).
- LOSO cross-validation confirmed strong generalization across different subjects.

## Requirements

- Python 3.10+
- Libraries:
  - `numpy`
  - `pandas`
  - `scipy`
  - `matplotlib`
  - `scikit-learn`
  - `seaborn`
  - `jupyter`
  - `nbconvert` (optional, for exporting notebooks)

Install dependencies using:

```bash
pip install numpy pandas scipy matplotlib scikit-learn seaborn jupyter
```

## Notes

- Signal processing steps (especially ECG filtering and Pan-Tompkins peak detection) were manually implemented for better understanding.
- ChatGPT was used as a coding assistant for code optimization and explanation.
- The project is a learning exercise in both biomedical signal processing and machine learning.

## License

- **Dataset License**: [Open Database License (ODbL)](https://physionet.org/about/licenses/odbl/)
- **Project License**: MIT License
