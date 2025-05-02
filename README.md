# 🏁 ML/DL Competition 3 – Final Report

**Participant**: Sharifbek  
**Submissions**:

- 📦 `mldl_competition3_sharifbek_submission1.csv` (Category 1: Boosting Models)
- 📦 `mldl_competition3_sharifbek_submission2.csv` (Category 2: Freestyle CNN)
- 📒 Notebooks: `.ipynb` + `.html` (Reproducible and Converted)

---

## 📂 Category 1: Boosting Models (LightGBM)

### 🔧 Overview

- **Model Type**: LightGBM (multiple configurations)
- **Input**: Flattened 28×28 grayscale pixels → 784 features, normalized using `pixel / 255.0`
- **Preprocessing**:
  - ❌ No PCA
  - ❌ No data augmentation
- **Cross-validation**: Stratified 5-Fold
- **Evaluation Metrics**:
  - Validation Accuracy (from CV)
  - Dig-MNIST Accuracy (out-of-distribution)

### 🧪 Model Comparison

| Model Name     | Val Accuracy | Dig-MNIST Accuracy |
| -------------- | ------------ | ------------------ |
| LGBM_base      | 0.9858       | 0.6751             |
| LGBM_deep_wide | 0.9845       | 0.6579             |
| LGBM_fast      | **0.9863**   | **0.6822**         |
| LGBM_very_deep | 0.9840       | 0.6538             |
| LGBM_compact   | 0.9860       | 0.6884             |

> _Note_: `LGBM_fast` achieved the highest **Val Accuracy**, while `LGBM_compact` had the best **Dig-MNIST Accuracy**. We prioritized validation accuracy.

### ✅ Final Model: `LGBM_fast`

- **Selected for best balance of speed and accuracy**
- **Hyperparameters**:
  - `n_estimators = 500`
  - `learning_rate = 0.1`
  - `num_leaves = 31`
  - `max_depth = 7`
  - `subsample = 0.8`
  - `colsample_bytree = 0.8`

📁 **Submission File**: `mldl_competition3_sharifbek_submission1.csv`

---

## 📂 Category 2: Freestyle Deep Learning (CNN)

### 🧠 Overview

- **Framework**: PyTorch
- **Model**: Custom Convolutional Neural Network (3 conv blocks)
- **Input**: Grayscale image with shape `(1, 28, 28)`
- **Preprocessing**:
  - ✅ Normalized pixels (`/ 255.0`)
  - ❌ No augmentation

### ⚙️ Training Setup

- **Cross-Validation**: Stratified 5-Fold
- **Loss**: `CrossEntropyLoss`
- **Optimizer**: Adam
- **Scheduler**: StepLR
- **Epochs**: 15
- **Batch Size**:
  - Training: 128
  - Validation/Test: 256

### 📊 Cross-Validation Results

| Fold   | Val Accuracy | Dig-MNIST Accuracy |
| ------ | ------------ | ------------------ |
| 1      | 0.9969       | 0.8012             |
| 2      | 0.9958       | 0.7839             |
| 3      | 0.9962       | 0.7887             |
| 4      | 0.9956       | 0.7774             |
| 5      | 0.9960       | 0.7880             |
|        |              |                    |
| ✅ Avg | **0.9961**   | **0.7878**         |

> _The CNN model clearly generalized better on Dig-MNIST and achieved superior overall accuracy compared to all LightGBM variants._

📁 **Submission File**: `mldl_competition3_sharifbek_submission2.csv`
