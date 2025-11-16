# Water Quality Sustainability Prediction

## 🚀 Project Overview

This repository contains the complete codebase and documentation for our **Water Quality Prediction** project. The primary goal is to leverage advanced machine learning models to accurately predict the sustainability of freshwater samples based on a wide range of chemical and physical parameters.

---

## 🎯 The Challenge: Ensuring Freshwater Quality

Freshwater is a finite and critical resource, essential for human health, agriculture, and ecosystem stability. This project addresses the challenge of ensuring water safety by developing a robust predictive model to determine the sustainability of water samples for consumption.

---

## 🛠️ Dependencies & Setup

This project relies on several Python libraries. Ensure you have them installed to run the code.

* `Python 3.x`
* `intel-extension-for-pytorch==2.0.100`
* `matplotlib==3.7.1`
* `numpy==1.23.5`
* `pandas==2.0.1`
* `pytorch-tabnet==4.1.0`
* `scikit-learn==1.2.2`
* `scikit-learn-intelex==2023.2.1`
* `scipy==1.10.1`
* `seaborn==0.12.2`
* `torch==2.0.0+cpu`
* `xgboost==1.7.6`

---

## 💻 How to Use

Follow these steps to get the project running on your local machine.

1.  **Clone the Repository**:
    ```bash
    git clone https://github.com/IzhaanK/WQI-Modeling
    
    ```
2.  **Install Required Dependencies**:
    ```bash
    pip install -r requirements.txt
    ```
3.  **Execute the Main Script**:
    ```bash
    python3 main.py
    ```

---

## 📊 About the Dataset

This rich dataset originates from an authoritative source: the **Central Pollution Control Board (CPCB) — National Water Quality Monitoring Programme (NWMP)** of India. This ensures the data is credible and reflects a comprehensive, real-world scenario of water quality across the nation.

### Geographic and Organizational Source
* As of 2024, this network comprises **2,108 monitoring stations** distributed across all **28 states and 8 Union Territories** of India.
* Monitored water bodies include **rivers, lakes, canals, coastal zones, tanks, and groundwater wells**.

### Data Collection and Parameters
Each monitoring station is identified by a unique code, latitude-longitude coordinates, and follows a monthly or quarterly sampling frequency. The parameters measured are identical to those in the Kaggle dataset and include:
* Physical properties like **pH, temperature, conductivity, and total dissolved solids**.
* Chemical properties like **dissolved oxygen (DO), biochemical oxygen demand (BOD), and nitrate levels**.
* Biological indicators like **fecal and total coliforms**.

### Data Challenges and Preprocessing
The raw dataset was massive, containing over **5.9 million data points** with 22 features. Challenges faced:
* **Imbalanced Data**: A significant class imbalance was observed, with **69.69%** of samples labeled as non-sustainable (Target: 0) and only **30.31%** as sustainable (Target: 1).
* **Missing Values**: Nearly **2 million rows** had missing data, requiring a robust imputation strategy. We filled missing values using the feature column's mean, guided by concentration graph analysis.
* **High Dimensionality**: The large feature set increased computational overhead. 

After preprocessing, the dataset was refined to approximately **5.1 million clean data points**, framed as a binary classification problem.

---

## 🤖 Methodology and Technology

### Model Development Workflow
Our approach involved a systematic progression from simpler to more complex models to establish a strong performance baseline.
* **Baseline Models**: started with **Logistic Regression** and **Decision Trees**.
* **Advanced Models**: then implemented more powerful models, including **XGBoost**, a **Multilayer Perceptron (MLP)**, and finally **TabNet**.

The dataset was split into **70% for training, 10% for validation, and 20% for testing**. Given the class imbalance, the **F1 Score** was chosen as the primary evaluation metric.

### Final Model: TabNet
The best-performing model was **TabNet**, a deep learning architecture from Google designed specifically for tabular data. We chose it for its:
* **Sequential Attention Mechanism**: Allows the model to focus on the most relevant features for each prediction.
* **High Performance & Interpretability**: Delivers state-of-the-art accuracy while providing insights into its decision-making process.
* **Robustness**: Handles noisy data effectively.

To further boost performance, we created an **ensemble of multiple TabNet models**, which achieved a final **accuracy of 87.39%** and an **F1 Score of 0.81786**.

### Final Results
| Model | Accuracy (Test Set) | F1 Score (Test Set) |
| :--- | :--- | :--- |
| Logistic Regression | 79.02% | 0.5931 |
| Decision Tree | 83.03% | 0.7179 |
| XGBoost | 86.37% | 0.7961 |
| MLP | 83.94% | 0.7581 |
| **TabNet (Ensemble)** | **87.39%** | **0.81786** |

---

