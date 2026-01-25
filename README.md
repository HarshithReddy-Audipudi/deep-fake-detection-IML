# 🧠 Deepfake Detection for Electoral Integrity

A **multi‑model computer vision system** designed to detect synthetic media in election‑related content using CNN and transformer‑based architectures. This project combines deep learning, explainable AI (Grad‑CAM), and real‑world security applications.

---

## 📌 Project Overview

As synthetic media becomes increasingly sophisticated and politically weaponized, this project provides a **comparative framework** for detecting deepfake images using state‑of‑the‑art models. The system evaluates traditional CNNs (ResNet‑50, XceptionNet) alongside modern hybrid architectures (MobileViT) on a curated dataset of real and fake facial images.

**Core objectives:**
- Detect deepfake images with high accuracy
- Compare CNN‑based and transformer‑based models
- Interpret model decisions using Grad‑CAM attention visualization
- Provide actionable insights for election‑security applications

---

## 🏗️ Architecture

| Model | Type | Key Features | Best Accuracy |
|-------|------|--------------|---------------|
| **ResNet‑50** | CNN | Residual learning, skip connections | **91%** |
| **XceptionNet** | CNN | Depthwise separable convolutions | 88% |
| **MobileViT** | CNN‑Transformer Hybrid | Mobile‑optimized, global attention | 86% |
| **LRNet (Lightweight)** | Custom CNN | Fast inference, low params | 59% |

---

## 📊 Results

### Performance Metrics
| Model | Accuracy | Precision (Fake) | Recall (Fake) |
|-------|----------|------------------|---------------|
| ResNet‑50 | **91%** | 88% | 97% |
| XceptionNet | 88% | **92%** | 93% |
| MobileViT | 86% | 90% | 95% |
| LRNet | 59% | 59% | 73% |

### Key Findings
1. **ResNet‑50** consistently delivered the highest accuracy and recall
2. **XceptionNet** showed the best precision (lowest false positives)
3. **MobileViT** balanced accuracy with modern architecture benefits
4. **LRNet**, while fastest, struggled with generalization

---

## 🔍 Model Interpretability with Grad‑CAM

Grad‑CAM visualizations reveal where each model "looks" when classifying images:

- **ResNet‑50**: Focuses on facial outlines and edge artifacts
- **XceptionNet**: Sharply highlights eyes, mouth, and eyebrow regions
- **MobileViT**: Captures detailed facial structures (nose, mouth contours)
- **LRNet**: Shows inconsistent, scattered attention patterns

These visualizations help **explain model decisions** and identify manipulated regions.

---

## 🗂️ Dataset

- **Source**: Custom‑collected real and synthetic face images
- **Size**: ~2,000 images (balanced real/fake)
- **Preprocessing**:
  - Resize: 224×224 (ResNet, MobileViT), 299×299 (Xception)
  - Normalization: ImageNet mean/std or [‑1, 1] scaling
  - Augmentation: Random flip, rotation, brightness adjustment
- **Split**: 80% training, 20% testing (stratified)

---

## 🚀 Getting Started

### Prerequisites
```bash
Python 3.8+
PyTorch 1.12+
torchvision
OpenCV
matplotlib
numpy

# Clone the repository
git clone https://github.com/yourusername/deepfake-election-detection.git
cd deepfake-election-detection

# Install dependencies
pip install -r requirements.txt


# Load trained model
from inference import DeepfakeDetector
detector = DeepfakeDetector(model_type='resnet50', weights_path='weights/resnet50_best.pth')

# Predict on single image
prediction, confidence = detector.predict('path/to/image.jpg')

# Generate Grad-CAM visualization
detector.visualize_attention('path/to/image.jpg', output_path='heatmap.png')


deepfake-election-detection/
├── data/
│   ├── processed/          # Preprocessed datasets
│   └── raw/               # Original images
├── models/
│   ├── resnet_model.py
│   ├── xception_model.py
│   ├── mobilevit_model.py
│   └── lrnet_model.py
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_model_training.ipynb
│   └── 03_visualization.ipynb
├── utils/
│   ├── dataset.py
│   ├── visualization.py
│   └── metrics.py
├── weights/               # Trained model checkpoints
├── train.py
├── inference.py
├── requirements.txt
└── README.md
