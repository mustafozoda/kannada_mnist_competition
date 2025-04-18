# 🏁 ML/DL Competition 3 – Final Report

**Participant**: Sharifbek  
**Submissions**:

- 📦 `mldl_competition3_sharifbek_submission1.csv` (Category 1: Boosting Models)
- 📦 `mldl_competition3_sharifbek_submission2.csv` (Category 2: Freestyle CNN)
- 📒 Notebooks: `.ipynb` `.html` (Reproducible)

---

## 📂 Category 1: Boosting Models

### 🔧 Overview

- **Model Type**: LightGBM
- **Input**: Flattened pixel values (784 features), scaled to `[0, 1]` using `pixel / 255.0`
- **Preprocessing**: ❌ No PCA, no augmentation
- **Cross-validation**: Stratified 5-Fold
- **Evaluation**: Accuracy on validation and Dig-MNIST

### 🧪 Model Comparison

| Model Name     | Val Accuracy | Dig-MNIST Accuracy |
| -------------- | ------------ | ------------------ |
| LGBM_base      | 0.9858       | 0.6751             |
| LGBM_deep_wide | 0.9845       | 0.6579             |
| ✅ LGBM_fast   | **0.9863**   | **0.6822**         |

### ✅ Final Model: `LGBM_fast`

- Best generalization and fastest training
- Tuned hyperparameters:
  - `n_estimators=500`
  - `learning_rate=0.1`
  - `num_leaves=31`
  - `max_depth=7`

📁 **Submission File**: `mldl_competition3_sharifbek_submission1.csv`

---

## 📂 Category 2: Freestyle – Deep Learning (CNN)

### 🧠 Overview

- **Framework**: PyTorch
- **Model**: Custom CNN with 3 convolutional blocks
- **Input shape**: `(1, 28, 28)` grayscale image
- **Preprocessing**: Only pixel normalization (`/255.0`), no augmentation
- **CV**: 5-Fold Stratified
- **Training**:
  - Optimizer: Adam
  - Loss: CrossEntropyLoss
  - Epochs: 15
  - Batch size: 128 (train), 256 (val/test)

### 📊 Cross-Validation Performance

| Fold   | Val Accuracy | Dig-MNIST Accuracy |
| ------ | ------------ | ------------------ |
| 1      | 0.9969       | 0.8012             |
| 2      | 0.9958       | 0.7839             |
| 3      | 0.9962       | 0.7887             |
| 4      | 0.9956       | 0.7774             |
| 5      | 0.9960       | 0.7880             |
|        |              |                    |
| ✅ Avg | **0.9961**   | **0.7878**         |

📁 **Submission File**: `mldl_competition3_sharifbek_submission2.csv`
