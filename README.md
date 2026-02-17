# 🧠 Fake Detection for American Electoral Integrity

A **multi-model deep learning system** to detect manipulated political media using CNN and hybrid transformer-based architectures. This project combines **deepfake classification**, **GradCAM explainability**, and a **RAG-enhanced forensic reporting pipeline** that enriches predictions with retrieved threat intelligence and automated citations.

---

## 📌 Project Overview

Synthetic and manipulated media is increasingly used to mislead audiences at scale. This project builds a practical detection and attribution workflow that:

- Detects manipulated facial media (real vs fake)
- Compares CNN-based and hybrid transformer architectures
- Explains model decisions using **GradCAM**
- Generates **forensic attribution reports** by retrieving known manipulation patterns (RAG-enhanced)

**Resume-aligned highlights**
- Built a deepfake detection system combining **ResNet-50, XceptionNet, and MobileViT** to identify manipulated political media, improving **precision by 14%**
- Developed a **RAG-enhanced pipeline** that fuses **GradCAM** visual evidence with retrieved threat intelligence (face-swap artifacts, GAN fingerprints) to produce reports with **automated citations**

---

## 🏗️ Architecture

### 1) Detection Models (Multi-Model Benchmark)
The system trains and evaluates multiple architectures to detect manipulated media:

- **ResNet-50** (CNN, strong baseline)
- **XceptionNet** (CNN with depthwise separable convs)
- **MobileViT** (CNN-Transformer hybrid for global attention)
- *(Optional)* LRNet (lightweight baseline)

### 2) Explainability (GradCAM)
GradCAM heatmaps help interpret *why* a model predicted “fake” by highlighting facial regions associated with artifacts such as:
- blending edges (face swap)
- texture inconsistencies (GAN fingerprints)
- unnatural contours / boundary artifacts

### 3) RAG-Enhanced Forensic Reporting
A lightweight retrieval + generation layer enriches raw predictions:

1. **Extract evidence** from model output + GradCAM heatmap signals  
2. **Retrieve relevant manipulation patterns** (threat intelligence KB), such as:
   - face-swap edge artifacts
   - GAN texture fingerprints
   - inconsistencies around eyes/mouth/skin boundaries
3. **Generate a structured attribution report** with **citations** pointing to retrieved patterns

This bridges black-box classification with interpretable, actionable reporting.

---

## 📊 Results

- Precision improvement: **+14%** (relative improvement vs baseline configuration)
- Models compared: **ResNet-50**, **XceptionNet**, **MobileViT** *(and LRNet optional)*

> Tip: If you have a table of metrics per model, place it here (Accuracy / Precision / Recall / F1).

---

## 🗂️ Dataset

- **Source:** Custom-collected real and synthetic face images (balanced real/fake)
- **Size:** ~2,000 images *(update if your dataset differs)*
- **Split:** 80% train / 20% test (stratified)

**Preprocessing**
- Resize: `224×224` (ResNet, MobileViT), `299×299` (Xception)
- Normalization: ImageNet mean/std (or [-1, 1] scaling where applicable)
- Augmentation: random flip, rotation, brightness adjustments

---

## ⚙️ Tech Stack

- **PyTorch**, torchvision
- **OpenCV**, NumPy
- **GradCAM** visualizations
- (Optional) lightweight retrieval store for threat intelligence
- Matplotlib for plots

---

## 🚀 Getting Started

### 1) Install
```bash
git clone https://github.com/yourusername/deepfake-election-detection.git
cd deepfake-election-detection
pip install -r requirements.txt
