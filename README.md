# 🌳 Imbalanced-Classification-Decision-Tree

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white)

[![Status](https://img.shields.io/badge/Status-Optimized-success)](#)

## 📌 Project Overview
This project addresses a classic Machine Learning challenge: **Class Imbalance.** Using a dataset where the minority class ("True") represents only 15% of the data, I optimized a Decision Tree to move from a biased 0.00 F1-score to a robust **0.65 F1-score.**



## 🧠 The Problem: "The Accuracy Trap"
Initially, the model achieved **85% accuracy** but was effectively useless because it predicted "False" for 100% of cases. 

### Performance Evolution:
| Version | Strategy | Accuracy | Minority F1-Score |
| :--- | :--- | :--- | :--- |
| **v1.0** | Default (Baseline) | 85% | 0.00 |
| **v2.0** | Balanced Weights Only | 15% | 0.27 |
| **v3.0** | Unconstrained Tree | 86% | 0.51 |
| **v4.0** | **Tuned & Pruned (Final)** | **87%** | **0.65** |

---

## 🛠️ Optimization Techniques Used

### 1. Cost Complexity Pruning (CCP)
I utilized the `ccp_alpha` parameter to find the "Sweet Spot" between an oversimplified model and an overfitted one. This removed noisy branches that didn't contribute to generalizable patterns.



### 2. Class Weight Balancing
By applying `class_weight='balanced'`, I penalized the model for misclassifying the minority class, forcing the decision boundaries to shift in favor of the "True" cases.

### 3. Hyperparameter Constraints
* **Max Depth (6):** Limited tree growth to ensure the model captures the "signal" rather than "noise."
* **Min Samples Split (12):** Prevented the creation of nodes based on very small, non-representative samples.

---

## 📊 Final Evaluation
The final model identifies **78% of all positive cases (Recall)** while maintaining high precision for the majority class.

### Confusion Matrix Insights


### Final Classification Report
```text
              precision    recall  f1-score   support

       False       0.96      0.89      0.92      2084
        True       0.55      0.78      0.65       382

    accuracy                           0.87      2466
