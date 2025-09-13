# AI-project
Artificial intelligence project


# Image Segmentation with UNet, AttentionUNet, and ResidualAttentionUNet

## 📌 Project Overview

This project was developed as **Phase 1 of the Artificial Intelligence course (Spring 2025, Sharif University of Technology, Computer Engineering Department)**.
It focuses on implementing **image segmentation** using the **Massachusetts Road Dataset**.

We explore and build from scratch the following architectures using **PyTorch**:

* **UNet**
* **Attention UNet**
* **Residual Attention UNet**

The models are trained with a **composite loss function**:

* **IoU Loss + Dice Loss + BCE Loss**

Optimization is performed with **AdamW** along with a **learning rate scheduler** to stabilize convergence.

---

## 👨‍💻 Authors

* Matin Bagheri
* Ali Hossein Khalaj
* Parsa NorouziManesh

---

## 📂 Dataset

We use the [Massachusetts Roads Dataset](https://www.kaggle.com/datasets/balraj98/massachusetts-roads-dataset), a benchmark dataset for **road extraction from aerial images**.

* **Input images**: 1500 aerial RGB images of size 1500×1500 pixels
* **Ground truth masks**: Binary masks indicating road vs. non-road pixels
* **Splits**: Training, Validation, and Test sets

In this project:

* Images are resized to **256×256** for training efficiency.
* Masks are normalized and thresholded for binary segmentation.

This dataset is widely used for evaluating deep learning methods in **semantic segmentation**.

---

## 🏗️ Implementation Details

The project consists of three main stages:

### 1. **Data Preparation**

* Loaded the dataset from Kaggle using `kagglehub`.
* Applied preprocessing: resizing, normalization, tensor conversion.
* Implemented a custom `RoadDataset` class for PyTorch.

### 2. **Model Architectures**

* **UNet**: Encoder-decoder with skip connections.
* **Attention UNet**: Adds attention gates to focus on relevant spatial features.
* **Residual Attention UNet**: Combines residual blocks with attention gates for deeper and more efficient learning.

### 3. **Training Setup**

* **Optimizer**: AdamW
* **Scheduler**: Learning rate scheduler for stable convergence
* **Loss Function**: IoU Loss + Dice Loss + BCE Loss
* **Metrics**: Accuracy, IoU Score, Dice Score

---

## 📊 Results

The models were trained and evaluated on the Massachusetts Roads dataset.

| Model                       | Best Epoch | Val Loss | IoU Score | Dice Score |
| --------------------------- | ---------: | -------: | --------: | ---------: |
| **UNet**                    |         32 |   0.3143 |    0.5441 |     0.6799 |
| **Attention UNet**          |         44 |   0.2615 |    0.6307 |     0.7587 |
| **Residual Attention UNet** |         30 |   0.2397 |    0.6640 |     0.7964 |

### Observations

* **UNet** serves as a solid baseline but struggles with fine road structures.
* **Attention UNet** improves segmentation by focusing on road regions.
* **Residual Attention UNet** achieves the **best overall performance**, thanks to residual connections + attention mechanisms.

---

## 📜 License

This project is for **educational purposes** as part of the AI course at Sharif University of Technology.

---
