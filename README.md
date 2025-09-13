# Phase 1: Image Segmentation with UNet, AttentionUNet, and ResidualAttentionUNet

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
* Ali HosseinKhalaj
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
* **Metrics**: Validation loss, IoU Score, Dice Score

---

## 📊 Results

The models were trained and evaluated on the Massachusetts Roads dataset.

| Model                       | Num Epochs | Val Loss | IoU Score | Dice Score |
| --------------------------- | ---------: | -------: | --------: | ---------: |
| **UNet**                    |         15 |   0.59 |    0.69 |     0.81 |
| **Attention UNet**          |         15 |   0.61 |    0.67 |     0.80 |
| **Residual Attention UNet** |         15 |   0.59 |    0.68 |     0.81 |

### Observations

* **UNet** achieved the **highest IoU (0.69)** and Dice (0.81), serving as a strong baseline.
* **Attention UNet** slightly underperformed compared to vanilla UNet, suggesting that the attention mechanism did not yield significant benefits within the given training setup and dataset size.
* **Residual Attention UNet** performed similarly to UNet, showing stable Dice scores but no substantial improvement in IoU or loss reduction.

👉 Overall, all three models converge to **very close performance**, with **UNet providing the best balance** under the current configuration.

---

## 📜 License

This project is for **educational purposes** as part of the AI course at Sharif University of Technology.

---


#Phase 2:
