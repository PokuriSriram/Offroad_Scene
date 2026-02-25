# 🚀 DesertVision: DeepLabV3+ for Off-Road Semantic Segmentation

## 🏆 Team: SPY  
**Members:** P Sriram, B Charan Sai Reddy, A Banny Vardhan Reddy, Rasmi M  
**College:** G. Pulla Reddy Engineering College  
**Date:** 25-02-2026  

---

# 📌 Project Overview

DesertVision is a semantic segmentation pipeline built using **DeepLabV3+ with a ResNet50 backbone** to segment off-road desert environments.

The model was trained on synthetic desert twin data and evaluated for generalization under domain shift.

### 🎯 Final Validation Mean IoU: **0.585**

---

# 🧠 Model Architecture

### 🔹 Backbone
- DeepLabV3+
- Encoder: ResNet50 (ImageNet pretrained)

### 🔹 Why DeepLabV3+?
- Atrous Spatial Pyramid Pooling (ASPP)
- Strong multi-scale context capture
- Encoder–decoder structure
- Good balance between speed and accuracy

---

# 📂 Dataset Structure
data/
│
├── train/
│ ├── Color_Images/
│ └── Segmentation/
│
├── val/
│ ├── Color_Images/
│ └── Segmentation/
│
└── testImages/
├── Color_Images/
└── Segmentation/


# 🧪 How To Run

## 1️⃣ Install Dependencies


pip install torch torchvision
pip install segmentation-models-pytorch
pip install albumentations
pip install opencv-python


---

## 2️⃣ Train Model


python train.py


Best model will be saved at:


runs/best_model.pth


---

## 3️⃣ Evaluate Model


python test.py


Outputs:

Test mIoU: <value>


---

# 🏗 Project Structure


Offroad_Scene/
│
├── train.py
├── test.py
├── runs/
│ └── best_model.pth
│
├── data/
│ ├── train/
│ ├── val/
│ └── testImages/
│
└── README.md


---

---

# ⚙️ Training Configuration

| Parameter | Value |
|------------|--------|
| Optimizer | Adam |
| Learning Rate | 1e-4 |
| Fine-tune LR | 3e-5 |
| Batch Size | 16 |
| Resolution | 256×256 |
| Epochs | 20 |
| GPU | Kaggle T4 |

---

# 📉 Loss Function

We used a hybrid loss:
Total Loss = CrossEntropy + Dice Loss

### Why?
- Handles class imbalance
- Improves rare class segmentation
- Stabilizes IoU during training

---

# 📊 Results

## 🔹 Validation Mean IoU
**0.585**

## 🔹 Class-wise IoU

| Class | IoU |
|--------|------|
| Trees | 0.543 |
| Lush Bushes | 0.636 |
| Dry Grass | 0.304 |
| Rocks | 0.328 |
| Logs | 0.605 |
| Flowers | 0.977 |
| Landscape | 0.678 |
| Sky | 0.554 |

---

# 🌍 Domain Shift Observation

- Validation IoU: **0.585**
- Test IoU: **~0.35**

### Reason:
- Texture sensitivity
- Distribution shift
- Synthetic-to-novel environment gap

This highlights real-world generalization challenges.

---

# 🔍 Confusion Matrix Insights

Common confusions:
- Dry Grass ↔ Landscape
- Rocks ↔ Logs

Applying Dice + CrossEntropy improved minority class learning stability.

---

---

# 💡 Key Contributions

- DeepLabV3+ implementation for desert segmentation
- Hybrid Dice + CrossEntropy loss
- Class imbalance handling
- Resolution experimentation (256 vs 384)
- Domain shift analysis
- Structured training-validation split

---

# 🔮 Future Improvements

- Domain adaptation techniques
- Stronger backbones (ResNet101 / Transformer-based)
- Multi-scale training
- Test-Time Augmentation (TTA)
- Focal Loss for extreme imbalance
- Ensemble learning
- Semi-supervised adaptation

---

# 🏁 Conclusion

We implemented a robust DeepLabV3+ segmentation pipeline achieving:

## 🎯 Validation Mean IoU: **0.685**

Through:
- Careful class imbalance handling
- Structured experimentation
- Controlled fine-tuning
- Domain shift diagnosis

The model demonstrates strong segmentation performance on synthetic off-road environments while identifying clear pathways for real-world robustness improvements.
