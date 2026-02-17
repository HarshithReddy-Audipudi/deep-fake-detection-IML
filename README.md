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


## 2️⃣ Explainability Layer (GradCAM)

To increase transparency and trust in model predictions, the system integrates **GradCAM (Gradient-weighted Class Activation Mapping)** to visualize the regions influencing classification decisions.

### Why GradCAM?

Deepfake detection models can behave like black boxes. GradCAM helps:

- Highlight manipulated regions (face blending edges, texture artifacts)
- Reveal model attention patterns
- Diagnose false positives and false negatives
- Improve interpretability for forensic analysis

### Observations Across Models

- **ResNet-50** → Focuses on facial outlines and boundary blending artifacts  
- **XceptionNet** → Strong attention around eyes, mouth, and eyebrow regions  
- **MobileViT** → Captures global structural inconsistencies  
- **LRNet** → Shows scattered and less stable attention patterns  

These visualizations are later fused into the forensic reporting pipeline.

---

## 3️⃣ RAG-Enhanced Forensic Attribution Pipeline

Beyond classification, this system introduces a lightweight **Retrieval-Augmented Generation (RAG)** workflow to enhance interpretability.

Instead of outputting only:
> "Fake (Confidence: 0.92)"

The system generates a structured forensic report.

### 🔹 Step 1: Evidence Extraction

- Model prediction score
- GradCAM attention heatmaps
- Detected artifact regions (boundary inconsistencies, unnatural textures)

### 🔹 Step 2: Threat Intelligence Retrieval

A curated knowledge base contains manipulation signatures such as:

- Face-swap blending artifacts  
- GAN texture fingerprints  
- Lighting inconsistencies  
- Facial asymmetry distortions  

The system retrieves relevant artifact patterns based on extracted visual evidence.

### 🔹 Step 3: Structured Report Generation

The final output includes:

- Classification result  
- Confidence score  
- Highlighted manipulated regions  
- Likely artifact category  
- Automated citation references to retrieved patterns  

This bridges deep learning outputs with explainable forensic reasoning.

---

## 4️⃣ Experimental Results

The system benchmarks multiple architectures for detecting manipulated political media.

### 📊 Model Performance

| Model        | Accuracy | Precision (Fake) | Recall (Fake) |
|--------------|----------|------------------|---------------|
| ResNet-50   | **91%**  | 88%              | 97%           |
| XceptionNet | 88%      | **92%**          | 93%           |
| MobileViT   | 86%      | 90%              | 95%           |
| LRNet       | 59%      | 59%              | 73%           |

### 🔎 Key Findings

- **ResNet-50** achieved the highest overall accuracy  
- **XceptionNet** achieved the highest precision (lowest false positives)  
- **MobileViT** balanced performance with modern hybrid architecture  
- Precision improved by **14%** compared to baseline configuration  

### 🧠 Insights

- CNN architectures remain strong for curated deepfake datasets  
- Transformer hybrids help capture global structural inconsistencies  
- GradCAM significantly improves interpretability and trust  
- RAG-enhanced attribution provides explainability beyond raw probabilities  
