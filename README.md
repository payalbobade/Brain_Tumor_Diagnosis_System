<div align="center">

# 🩺 Medical Image Analysis for Brain Tumor Diagnosis
### CNN + VGG16 + ResNet50 transfer learning with Grad-CAM explainability

![Python](https://img.shields.io/badge/Python-3.10-blue?style=flat-square&logo=python)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat-square&logo=tensorflow&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-success?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)

[Overview](#-overview) • [Approach](#-approach) • [Installation](#️-installation--how-to-run) • [Results](#-results) • [Contact](#-contact)

</div>

---

## 📌 Overview

A CNN + VGG16 + ResNet50 (transfer learning) pipeline that classifies brain MRI scans into **glioma, meningioma, pituitary tumor, or no tumor**, with a Grad-CAM explainability add-on so predictions are visually interpretable.

Early, accurate brain tumor diagnosis directly impacts treatment outcomes, but manual MRI review is slow and subject to human error. This project builds and compares three deep learning approaches for automated classification, then adds Grad-CAM visualizations so a clinician could see *why* the model made each prediction — not just the label.

## 🎯 Problem Statement

Manual review of MRI scans for tumor diagnosis is time-consuming and depends on radiologist experience, which can delay treatment decisions in high-volume clinical settings.

## 💼 Business Objective

Provide a fast, consistent, explainable first-pass screening tool that classifies tumor type and shows *where* in the scan the model is basing its decision — critical for clinical trust and adoption.

## 🧠 Approach

- **Data preprocessing**: resizing to 224×224, normalization, and augmentation (rotation, shift, zoom, flip, brightness) to improve generalization on a limited medical imaging dataset.
- **Model 1 — Custom CNN**: a 4-block Conv→BatchNorm→ReLU→MaxPool architecture trained from scratch as a baseline.
- **Model 2 — VGG16 (transfer learning)**: ImageNet-pretrained VGG16 with the last few convolutional blocks fine-tuned on MRI data.
- **Model 3 — ResNet50 (transfer learning)**: ImageNet-pretrained ResNet50, fine-tuned, to test whether a deeper residual architecture improves classification.
- **Explainability add-on**: Grad-CAM heatmaps overlay the regions of the MRI scan the model focused on, addressing the "black box" concern in clinical AI adoption.

Full detail in [`docs/Model.md`](docs/Model.md) and [`docs/Workflow.md`](docs/Workflow.md).

## 📂 Dataset

[Brain Tumor MRI Dataset (Kaggle)](https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset) — ~7,000 MRI images across 4 classes (glioma, meningioma, pituitary, no tumor).

Smaller 2-class alternative: [Brain MRI Images for Brain Tumor Detection](https://www.kaggle.com/datasets/navoneel/brain-mri-images-for-brain-tumor-detection)

See [`docs/Dataset.md`](docs/Dataset.md) for preprocessing and split details.

## 🗂️ Project Structure

```text
brain-tumor-diagnosis-cnn/
│
├── Brain_Tumor_Detection_CNN_VGG16_ResNet50.ipynb   # Full self-contained pipeline
├── docs/
│   ├── Architecture.md
│   ├── Dataset.md
│   ├── Workflow.md
│   └── Model.md
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
└── .gitignore
```

## ⚙️ Installation & How to Run

```bash
git clone https://github.com/payalbobade/brain-tumor-diagnosis-cnn.git
cd brain-tumor-diagnosis-cnn
```

1. Open `Brain_Tumor_Detection_CNN_VGG16_ResNet50.ipynb` in **Google Colab** or **Kaggle Notebooks** (GPU recommended).
2. The notebook is fully self-contained — it handles dataset download, training, evaluation, Grad-CAM generation, and model saving.
3. Run all cells top to bottom.

## ✨ Features

- ✅ Three-way model comparison: custom CNN vs VGG16 vs ResNet50
- ✅ Data augmentation pipeline for limited medical imaging data
- ✅ Grad-CAM visual explainability overlays
- ✅ Auto-generated comparison table (accuracy, precision, recall, F1, confusion matrices)

## 📏 Results

| Model | Accuracy | 
|---|--- |
| Custom CNN | 89.6% – 97.55%|
| VGG16 (transfer learning) | 94.1% – 98.5% |
| ResNet50 (transfer learning) | 45.1% – 98.4% |

## 🧭 Key Learnings

- Transfer learning (VGG16/ResNet50) typically outperforms a from-scratch CNN on limited medical imaging data, since ImageNet features transfer well to texture/edge-heavy scans.
- Explainability tools like Grad-CAM are essential for any medical AI system to build clinical trust.
- Class imbalance and image quality variability are the main real-world challenges for this task.

## 🚀 Future Improvements

- [ ] Add tumor **segmentation** (U-Net) in addition to classification, to localize tumor boundaries
- [ ] Deploy as a Flask/Streamlit web app for real-time predictions
- [ ] Test with multi-modal input (MRI + CT) for higher diagnostic confidence

## 🛠️ Technologies Used

`Python` `TensorFlow/Keras` `OpenCV` `NumPy` `Pandas` `Matplotlib` `Seaborn` `Scikit-learn`

## 📄 License

MIT — see [LICENSE](LICENSE)

## 🤝 Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) and our [Code of Conduct](CODE_OF_CONDUCT.md).

## 📬 Contact

**Payal Prabhakar Bobade** — [LinkedIn](https://www.linkedin.com/in/payal-bobade-0b7725309) • [Email](mailto:bpayal477@gmail.com) • [GitHub](https://github.com/payalbobade)

---
<div align="center">⭐ Part of my <a href="https://github.com/payalbobade/payalbobade">GitHub profile portfolio</a> — feel free to star if you find it useful!</div>
