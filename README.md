# Project-Panopticon-Intelligent-Proctoring

📌 Project Overview

Project Panopticon is an AI-powered intelligent proctoring system designed to monitor and enhance the integrity of online examinations.

The project uses machine learning techniques to analyze examination telemetry and identify suspicious behavior or potential instances of malpractice.

## 🎯 Objective

The primary objective is to develop a machine learning-based system that can identify potentially suspicious examination behavior while minimizing false accusations against innocent students.

## 📊 Data Used

The project uses two telemetry datasets:

- `video_telemetry.csv` – contains video-related examination signals such as eye-gaze information and audio levels.
- `system_events.csv` – contains system-level examination events such as tab switching and cheating labels.

The datasets are aligned using timestamp-based asynchronous merging.

## ⚙️ Methodology

The project follows these main steps:

1. Load and preprocess the telemetry datasets.
2. Convert timestamp values and sort the datasets chronologically.
3. Perform asynchronous timestamp-based data alignment.
4. Handle missing values using forward filling, interpolation, and zero filling.
5. Create rolling-window features for gaze and audio signals.
6. Prepare features and the target variable.
7. Split the dataset into training and testing sets.
8. Train a class-balanced Random Forest classifier.
9. Generate cheating probabilities.
10. Compare standard and strict decision thresholds.
11. Evaluate the model using precision, recall, and confusion matrices.
12. Analyze feature importance.

## 🤖 Machine Learning Model

**Model:** Random Forest Classifier

The model uses class balancing to address the difference between normal and cheating cases.

### Main Features

- Eye gaze angle
- Audio level
- Tab switches
- 10-second rolling gaze mean
- 10-second rolling audio maximum

## 🎯 Decision Threshold

A strict decision threshold of **0.90** was selected to prioritize precision and reduce false accusations.

At this threshold, a student is flagged only when the predicted probability of cheating is at least 90%.

## 📈 Final Results

| Metric | Result |
|---|---:|
| Decision Threshold | 0.90 |
| Precision | 100% |
| Recall | 58.69% |
| True Negatives | 1361 |
| False Positives | 0 |
| False Negatives | 264 |
| True Positives | 375 |
| Flagged Cases | 375 / 2000 |

The selected threshold achieved the project's precision requirement of at least 90% while producing **zero false positives** on the test set.

## 🔍 Feature Importance

The most influential features identified by the Random Forest model were:

1. Tab switches
2. 10-second rolling gaze feature
3. 10-second rolling audio feature
4. Eye gaze angle
5. Audio level

## 📁 Project Structure

```text
Project-Panopticon-Intelligent-Proctoring/
│
├── Project_Panopticon_Internship_Final.ipynb
├── video_telemetry.csv
├── system_events.csv
├── README.md
└── .gitignore
