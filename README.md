> **Early prototype (2024-25) on a self-built 81-recording dataset. Not the code or results of the manuscript.**

# Parkinson's Disease Detection from Voice Data

## Overview
This project involves detecting Parkinson's disease using voice recordings. By extracting key voice features from audio data, machine learning models were trained to predict the likelihood of Parkinson's disease. The final solution includes a user-friendly **Streamlit web application** for real-time analysis.

## SMOTE leakage
In `Model_selection_for_Parkinson's_Disease_Detection(with created_dataset).ipynb`, SMOTE is fit on the full feature matrix **before** the train/test split. Synthetic samples can therefore appear in both the training and test sets. This is a known leakage issue, so the metrics reported in that notebook are optimistic. The notebook was not re-run for this note; the 81 source recordings are not committed in this repository.

---

## Data Source
The dataset used for this project was created from the following source:
[Voice Samples for Patients with Parkinson's Disease and Healthy Controls](https://figshare.com/articles/dataset/Voice_Samples_for_Patients_with_Parkinson_s_Disease_and_Healthy_Controls/23849127).

### Features Extracted
The audio data was processed to extract the following features for analysis:

| Column Name         | Description                                 | Data Type |
|---------------------|---------------------------------------------|-----------|
| `MDVP:Fo(Hz)`       | Average fundamental frequency              | `float64` |
| `MDVP:Fhi(Hz)`      | Maximum fundamental frequency              | `float64` |
| `MDVP:Flo(Hz)`      | Minimum fundamental frequency              | `float64` |
| `MDVP:Jitter(%)`    | Percentage of Jitter                       | `float64` |
| `MDVP:Jitter(Abs)`  | Absolute Jitter                            | `float64` |
| `MDVP:RAP`          | Relative Amplitude Perturbation            | `float64` |
| `MDVP:PPQ`          | Pitch Period Perturbation Quotient         | `float64` |
| `Jitter:DDP`        | Difference of Difference of Jitter         | `float64` |
| `MDVP:Shimmer`      | Shimmer (dB)                               | `float64` |
| `MDVP:Shimmer(dB)`  | Shimmer (logarithmic scale)                | `float64` |
| `Shimmer:APQ3`      | Amplitude Perturbation Quotient (3 cycles) | `float64` |
| `Shimmer:APQ5`      | Amplitude Perturbation Quotient (5 cycles) | `float64` |
| `MDVP:APQ`          | Average Amplitude Perturbation             | `float64` |
| `Shimmer:DDA`       | Difference of Difference of Amplitude      | `float64` |
| `NHR`               | Noise-to-Harmonics Ratio                   | `float64` |
| `HNR`               | Harmonics-to-Noise Ratio                   | `float64` |
| `RPDE`              | Recurrence Period Density Entropy          | `float64` |
| `DFA`               | Detrended Fluctuation Analysis             | `float64` |
| `spread1`           | First spread measure                       | `float64` |
| `spread2`           | Second spread measure                      | `float64` |
| `D2`                | Nonlinear dynamical complexity             | `float64` |
| `PPE`               | Pitch Period Entropy                       | `float64` |
| `status`            | Disease status (1 = Parkinson's, 0 = Healthy) | `uint8` |

---

## Machine Learning Models Trained
The following machine learning models were trained on the dataset:

1. **Decision Tree Classifier**
2. **Random Forest Classifier**
3. **Logistic Regression**
4. **Support Vector Machine (SVM)**
5. **Naive Bayes**
6. **K-Nearest Neighbors (KNN) Classifier**
7. **XGBoost Classifier**

### Model Selection
After training and evaluating all models, the **XGBoost Classifier** was chosen due to its superior accuracy and ability to handle imbalanced datasets.

---

## Application Development
A **Streamlit** app was created to make the solution accessible and interactive. Users can:

1. **Upload an audio file** or **record their voice** directly.
2. Extract features from the provided audio data.
3. Use the trained model to predict the likelihood of Parkinson's disease.

### Features of the App
- Real-time audio recording and analysis.
- Display of extracted features for user insight.
- Intuitive interface for medical professionals and general users.
- Secure and efficient model prediction.

---

## How to Run the App
1. Clone this repository:
   ```bash
   git clone https://github.com/your-repo/parkinsons-detection-app.git
   cd parkinsons-detection-app
   ```
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the Streamlit app:
   ```bash
   streamlit run parkinsons_app.py
   ```

---

## Note
This application is for educational and demonstration purposes only. It should not replace professional medical diagnosis. Always consult a healthcare provider for medical advice.