# 🛡️ Intelligent Credit Card Fraud Detection System

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![XGBoost](https://img.shields.io/badge/Model-XGBoost-orange)
![Status](https://img.shields.io/badge/Status-Deployment%20Ready-green)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

> **A Cost-Sensitive AI Approach to Minimizing Financial Risk.**

## 📖 Executive Summary
In financial fraud detection, standard accuracy is an insufficient metric due to the high cost of false negatives. A model can achieve 99% accuracy by simply predicting the majority class, yet fail to mitigate any financial loss.

This Capstone Project establishes a **Cost-Sensitive Learning** framework. By analyzing the asymmetric costs of fraud (avg. **$122** per incident) versus prevention (approx. **$2** per alert), we engineered a model optimized for **Return on Investment (ROI)** rather than raw classification metrics.

**Key Outcome:** The final model achieves a **Net Savings of ~$9,717** per test batch, yielding a projected **ROI of >3,000%**.

---

## 📉 The Problem Statement
Credit card fraud is a "Needle in a Haystack" problem (Imbalanced Classification):
* **The Data:** 284,807 transactions, but only **492 (0.17%)** are fraudulent.
* **The Risk:**
    * **False Negative (Missed Fraud):** The bank loses the full transaction value (~$122).
    * **False Positive (False Alarm):** The bank pays a small administrative fee (~$2) and risks annoying the customer.
* **The Goal:** Deploy a model that maximizes **Net Savings** (Money Recovered - Operational Costs).

---

## 📊 Model Selection & Comparative Analysis
We established a rigorous evaluation framework to identify the optimal algorithm. The analysis assessed candidate models across three dimensions: **Predictive Performance (AUPRC)**, **Stability**, and **Training Latency**.

| Model | Architecture | AUPRC | Latency | Verdict |
| :--- | :--- | :---: | :---: | :--- |
| **Logistic Regression** | Linear Baseline | 0.69 | 2.77s | Baseline Benchmark |
| **Neural Network (MLP)** | Feedforward ANN (+SMOTE) | 0.75 | 35.48s | High Latency |
| **Random Forest** | Bagging Ensemble | 0.76 | 8.97s | Competitive |
| **XGBoost** | **Gradient Boosting** | **0.84** | **0.91s** | **Selected** |

---

## 💰 Business Impact Analysis
We translated the model's performance into concrete financial metrics using a custom simulation.

![Business Impact](images/business_impact_custom.png)

* **Red Bar:** Financial loss from fraud.
* **Gray Bar:** Operational cost of the AI system.
* **Green Bar:** The **Value Saved** by the model.

**Final ROI:** For every $1 spent on monitoring, the system saves approximately **$31.96**.

---

## 📂 Dataset Details
The project utilizes the **European Credit Card Fraud** dataset (Sept 2013).
* **Source:** **OpenML Repository (ID: 43627)**.
* **Smart Loading:** The notebook includes an auto-fetch mechanism. If `creditcard_raw.csv` is not found locally, it automatically connects to the OpenML API to fetch the live dataset.
* **Privacy:** Features `V1`...`V28` are PCA-transformed to protect user confidentiality. Only `Amount` is an original feature.

---

## ⚙️ Installation & Usage

### 1. Clone the Repository
```bash
git clone [https://github.com/ecbaldono/Credit-Card-Fraud-Detection.git](https://github.com/ecbaldono/Credit-Card-Fraud-Detection.git)
cd Credit-Card-Fraud-Detection
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the Analysis
**Note on Data:** You do **not** need to manually download the dataset. The code will fetch it automatically on the first run.
```bash
jupyter notebook notebooks/ernesto_baldono_jr_capstone.ipynb
```
*(Alternatively, you can open the notebook in VS Code and click "Run All".)*

---

## 📂 Repository Structure
* `notebooks/`: Contains the main analysis file (`.ipynb`).
* `models/`: Serialized model artifacts (`.pkl`) including the scaler and threshold metadata.
* `images/`: Generated visualizations for the executive report.

---

## 👤 Author
**Ernesto Baldono Jr.**
* [LinkedIn](https://www.linkedin.com/in/ecbaldono)
* [Email](mailto:ebaldonojr@gmail.com)

---
*Developed as the final capstone project for the Postgraduate Diploma in AI & Machine Learning at the Asian Institute of Management.*


