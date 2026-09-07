# 🚗 Driver Drowsiness Detection

## 📌 Overview

Driver fatigue can reduce alertness, reaction time, and decision-making ability, increasing the risk of road accidents.

This project develops a deep learning-based Driver Drowsiness Detection system using facial images. The system analyzes eye closure and yawning behavior to identify the driver's state and estimate the level of fatigue.

Two deep learning approaches are developed and compared:

- Custom CNN
- MobileNetV2 Transfer Learning

The best-performing model is integrated into a Streamlit web application for interactive image-based prediction.

---

## 🎯 Objectives

- Detect driver eye and yawning states from facial images.
- Classify images into four categories: Closed, Open, no_yawn, and yawn.
- Develop and evaluate a Custom CNN model.
- Apply Transfer Learning using MobileNetV2.
- Compare the performance of both models.
- Convert the four-class prediction into three fatigue levels.
- Analyze fatigue progression over time.
- Deploy the final model through a Streamlit application.

---

## 📂 Dataset

The dataset contains facial images representing four classes:

| Class | Description |
|---|---|
| Closed | Eyes are closed |
| Open | Eyes are open |
| no_yawn | No yawning detected |
| yawn | Yawning detected |

The dataset is organized into training, validation, and test sets.

### Preprocessing

- Images are resized to **224 × 224 pixels**.
- Pixel values are normalized to the **0–1 range**.
- Data augmentation is applied during model training.
- Exploratory Data Analysis (EDA) is performed to understand the dataset and class distribution.

---

## 🧠 Model Development

### 1. Custom CNN

A lightweight Custom Convolutional Neural Network was developed to learn visual features directly from the dataset.

The architecture includes:

- Convolutional layers
- Separable Convolutional layers
- Max Pooling
- Global Average Pooling
- Dense classification layer
- Softmax output layer

### Custom CNN Performance

| Metric | Score |
|---|---:|
| Accuracy | **72.87%** |
| Precision | **73.00%** |
| Recall | **72.87%** |
| F1-Score | **72.85%** |

---

### 2. MobileNetV2 Transfer Learning

MobileNetV2 was used as a Transfer Learning model with pretrained ImageNet features.

The model was fine-tuned for the four driver-state classes:

- Closed
- Open
- no_yawn
- yawn

### MobileNetV2 Performance

| Metric | Score |
|---|---:|
| Accuracy | **97.70%** |
| Precision | **97.83%** |
| Recall | **97.70%** |
| F1-Score | **97.70%** |

**Test Set Size:** 435 images

MobileNetV2 achieved the best overall performance and was selected as the final model for the Streamlit application.

---

## 📊 Model Comparison

| Model | Accuracy | Precision | Recall | F1-Score |
|---|---:|---:|---:|---:|
| Custom CNN | 72.87% | 73.00% | 72.87% | 72.85% |
| MobileNetV2 | **97.70%** | **97.83%** | **97.70%** | **97.70%** |

The comparison shows that MobileNetV2 performed significantly better than the Custom CNN on the evaluated test dataset.

---

## 🔍 Model Evaluation

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-Score
- Confusion Matrix
- Training and validation performance

### MobileNetV2 Confusion Matrix

| Actual / Predicted | Closed | Open | no_yawn | yawn |
|---|---:|---:|---:|---:|
| Closed | 109 | 0 | 0 | 0 |
| Open | 0 | 109 | 0 | 0 |
| no_yawn | 0 | 0 | 107 | 1 |
| yawn | 0 | 0 | 9 | 100 |

The model correctly classified all test samples in the **Closed** and **Open** classes. Most classification errors occurred between the **no_yawn** and **yawn** classes.

---

## 😴 Fatigue Classification

The four model predictions are converted into three fatigue levels using rule-based decision logic:

| Model Prediction | Fatigue Level |
|---|---|
| Open | Alert |
| no_yawn | Alert |
| yawn | Mild Fatigue |
| Closed | Severe Fatigue |

This makes the model output easier to interpret as a driver's fatigue condition.

---

## 📈 Fatigue Progression Analysis

The system can process sequential image predictions from a simulated driving session.

Each prediction is converted into one of the three fatigue levels:

**Alert → Mild Fatigue → Severe Fatigue**

The predictions can then be grouped into time intervals to generate a fatigue progression curve and observe how the estimated fatigue level changes over time.

---

## 💻 Streamlit Application

The trained MobileNetV2 model is integrated into an interactive Streamlit web application.

### Application Features

- Upload a driver image
- Select sample images
- Predict the driver state
- Display prediction confidence
- Display the corresponding fatigue level
- View dataset and EDA information
- View model comparison
- View performance metrics
- View fatigue analysis
- View model information

---
## 🛠️ Tech Stack

- **Programming Language:** Python
- **Deep Learning:** TensorFlow, Keras
- **Computer Vision:** OpenCV
- **Data Processing:** NumPy, Pandas
- **Machine Learning:** Scikit-learn
- **Data Visualization:** Matplotlib, Plotly
- **Web Application:** Streamlit
- **Model:** Custom CNN, MobileNetV2 (Transfer Learning)
- **Development:** Jupyter Notebook, VS Code
- **Version Control:** Git, GitHub

## 🚀 Live Demo

The trained MobileNetV2 model is deployed as a Streamlit web application.

👉 **Live Demo:** https://driver-drowsiness-detection-gxvm7v7xckeuk4yatyptcb.streamlit.app/

The application allows users to upload an image or select a sample image and receive a drowsiness prediction based on the trained MobileNetV2 model.

## 🔄 Project Workflow

```text
Dataset
   ↓
Data Preprocessing
   ↓
Exploratory Data Analysis
   ↓
Custom CNN
   ↓
Model Tuning & Evaluation
   ↓
MobileNetV2 Transfer Learning
   ↓
Model Evaluation
   ↓
Model Comparison
   ↓
Select Best Model
   ↓
Fatigue Decision Logic
   ↓
Streamlit Application
