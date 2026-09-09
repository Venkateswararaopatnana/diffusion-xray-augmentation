# Diffusion-Enhanced X-ray Image Augmentation for Improved Disease Classification

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)

A comprehensive framework for generating synthetic X-ray images using diffusion models to augment medical imaging datasets and improve disease classification accuracy.

## 🎯 Project Overview

This project leverages **diffusion models** (specifically Denoising Diffusion Probabilistic Models - DDPMs) to generate high-quality synthetic X-ray images. These synthetic images are used to:

- **Balance imbalanced datasets** for underrepresented diseases
- **Augment training data** for improved model robustness
- **Enhance disease classification** performance (pneumonia, COVID-19, TB, fractures, etc.)
- **Reduce data collection burden** in medical imaging

## 🚀 Key Features

✅ **Diffusion Model Training**: Train custom diffusion models on X-ray datasets
✅ **Synthetic Image Generation**: Generate realistic synthetic X-rays from noise
✅ **Data Augmentation Pipeline**: Automatically augment datasets with synthetic images
✅ **Disease Classifier**: CNN-based classifier (ResNet, DenseNet) for disease prediction
✅ **Evaluation Metrics**: Compare performance with/without augmentation
✅ **Visualization Tools**: Inspect generated images and training progress

## 📋 Requirements

- Python 3.8+
- PyTorch 1.12+
- CUDA 11.6+ (for GPU acceleration)
- See `requirements.txt` for detailed dependencies

## 🔧 Installation

1. Clone the repository:
```bash
git clone https://github.com/Venkateswararaopatnana/diffusion-xray-augmentation.git
cd diffusion-xray-augmentation
```

2. Create a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

## 📂 Project Structure

```
diffusion-xray-augmentation/
├── data/
│   ├── raw/                 # Original X-ray datasets
│   ├── processed/           # Preprocessed images
│   └── synthetic/           # Generated synthetic X-rays
├── models/
│   ├── diffusion_model.py   # DDPM implementation
│   ├── classifier.py        # Disease classification model
│   └── checkpoints/         # Saved model weights
├── src/
│   ├── augmentation.py      # Data augmentation pipeline
│   ├── train_diffusion.py   # Training script for diffusion model
│   ├── train_classifier.py  # Training script for classifier
│   ├── generate_images.py   # Image generation script
│   └── evaluate.py          # Evaluation metrics
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_train_diffusion.ipynb
│   ├── 03_generate_augmented_data.ipynb
│   └── 04_train_classifier.ipynb
├── configs/
│   ├── diffusion_config.yaml
│   ├── classifier_config.yaml
│   └── augmentation_config.yaml
├── tests/
│   ├── test_diffusion.py
│   ├── test_classifier.py
│   └── test_augmentation.py
├── requirements.txt
├── setup.py
└── README.md
```

## 🚀 Quick Start

### 1. Prepare Your Data

Place your X-ray images in `data/raw/` organized by disease class:
```
data/raw/
├── normal/
│   ├── img_001.jpg
│   └── ...
├── pneumonia/
│   ├── img_101.jpg
│   └── ...
└── covid/
    ├── img_201.jpg
    └── ...
```

### 2. Train Diffusion Model

```bash
python src/train_diffusion.py --config configs/diffusion_config.yaml
```

### 3. Generate Synthetic X-rays

```bash
python src/generate_images.py --model checkpoints/diffusion_model.pt --num_samples 1000
```

### 4. Train Disease Classifier

```bash
python src/train_classifier.py --config configs/classifier_config.yaml --augmented
```

### 5. Evaluate Performance

```bash
python src/evaluate.py --model checkpoints/classifier_model.pt --test_data data/processed/test
```

## 📊 Model Architecture

### Diffusion Model (DDPM)
- **Type**: Denoising Diffusion Probabilistic Model
- **Architecture**: U-Net with attention mechanisms
- **Training Objective**: Predict noise in diffusion process
- **Inference**: Reverse diffusion from pure noise to realistic X-rays

### Classifier
- **Backbone**: ResNet-50 / DenseNet-121
- **Input**: 224×224 grayscale X-ray images
- **Output**: Disease class probabilities
- **Loss**: Cross-entropy with class weighting

## 📈 Results

Expected improvements with diffusion-augmented data:
- **Accuracy**: +5-15% improvement
- **Sensitivity**: +10-20% for minority classes
- **Robustness**: Better generalization on new data

## 🔍 Evaluation Metrics

- Accuracy, Precision, Recall, F1-Score
- ROC-AUC curves
- Confusion matrices
- Computational cost (FLOPs, memory usage)

## 📚 References

1. Ho et al. (2020) - "Denoising Diffusion Probabilistic Models" - https://arxiv.org/abs/2006.11239
2. Rombach et al. (2022) - "High-Resolution Image Synthesis with Latent Diffusion Models"
3. Tian et al. (2023) - "Diffusion Models for Medical Image Analysis"
4. Zeng et al. (2023) - "Synthesizing chest X-rays with diffusion models for COVID-19 diagnosis"

## 💡 Future Work

- [ ] Support for 3D CT scans
- [ ] Conditional generation (control disease type)
- [ ] Uncertainty quantification
- [ ] Integration with federated learning
- [ ] Web-based inference API
- [ ] Multi-modal fusion (combine X-ray + clinical data)

## 🤝 Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Submit a pull request

## 📄 License

This project is licensed under the Apache License 2.0 - see the LICENSE file for details.

## ✉️ Contact

For questions or collaborations, please contact: [your-email]

---

**Disclaimer**: This is a research project. Always validate results with medical professionals before clinical application.
