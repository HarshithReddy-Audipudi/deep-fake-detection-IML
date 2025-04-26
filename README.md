# 🧠 Deepfake Detection using ResNet, XceptionNet, LRNet, and MobileViT

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![PyTorch](https://img.shields.io/badge/PyTorch-1.9+-red.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

---

## 📚 Project Overview

This project focuses on the **detection of deepfake images** using multiple deep learning architectures.  
The models used are **ResNet50**, **XceptionNet**, **LRNet** (a lightweight CNN), and **MobileViT** (a hybrid CNN+Transformer model).

We also employ **GradCAM visualizations** to **interpret model decisions**, offering insights into which image regions the models focus on when classifying an image as real or fake.

This project is a complete academic-style study:
- Model training and evaluation
- Attention visualization (GradCAM)
- Result comparison
- Conclusions and recommendations

---

## 🎯 Objectives

- Detect deepfake images with high accuracy.
- Compare traditional CNNs and Transformer-based models.
- Visualize attention areas using GradCAM.
- Analyze model performance (Accuracy, Precision, Recall).
- Recommend the best architecture for real-world deployment.

---

## 🏗️ Models Used

| Model | Description |
|------|-------------|
| **ResNet50** | Residual learning CNN with skip connections (strong baseline) |
| **XceptionNet** | Extreme Inception architecture with depthwise separable convolutions |
| **LRNet** | Custom lightweight CNN (fast and simple) |
| **MobileViT** | Hybrid CNN-Transformer architecture optimized for mobile devices |

---

## 📂 Dataset

- **Custom Rebuilt Dataset**: 
  - Collected **Real** and **Fake** face images.
  - Approximately **2000 images** sampled for efficient training.
  - Balanced classes (Real = Fake).
  - Preprocessing:
    - Resize to 224x224 (CNNs) or 256x256 (MobileViT) or 299x299 (Xception).
    - Normalization between [-1, 1].
- **Train/Test Split**:
  - 80% for training
  - 20% for testing
  - Stratified split based on labels

---

## 📊 Results Summary

| Model         | Accuracy | Precision (Fake) | Recall (Fake) |
|---------------|----------|------------------|---------------|
| ResNet50      | 91%      | 88%               | 97%           |
| XceptionNet   | 88%      | 92%               | 93%           |
| LRNet         | 59%      | 59%               | 73%           |
| MobileViT     | 86%      | 90%               | 95%           |

✅ **ResNet and MobileViT** gave consistently high results.  
✅ **XceptionNet** showed strong precision.  
✅ **LRNet**, though faster, struggled with generalization.

---

## 🎨 GradCAM Visualizations

GradCAM was applied on each model to visualize **attention heatmaps**:

- 🔵 **ResNet50**: Focused on facial outlines and artifacts.
- 🔵 **XceptionNet**: Sharply highlighted eye and mouth regions.
- 🔵 **LRNet**: Focused inconsistently — less reliable.
- 🔵 **MobileViT**: Captured detailed features like nose and mouth structures.

These visualizations helped interpret **how models detect fake regions** inside faces.

Example Visualization:
- Red → High attention
- Blue → Low attention

---

## 📋 Project Folder Structure
