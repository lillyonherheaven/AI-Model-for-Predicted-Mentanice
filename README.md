# AI Model for Predictive Maintenance

An end-to-end machine learning project that predicts machine failures before they happen, using sensor data from industrial equipment. Built on the **AI4I 2020 Predictive Maintenance Dataset**.

## 📌 Project Overview

Unplanned equipment downtime is costly. This project uses machine sensor readings — temperature, rotational speed, torque, and tool wear — to classify whether a machine is likely to fail, enabling proactive maintenance instead of reactive repairs.

The workflow covers:
- Data cleaning and exploration (EDA)
- Outlier and correlation analysis
- Training and comparing classification models (Decision Tree vs. Random Forest)
- Evaluating model performance with confusion matrices

## 📊 Dataset

**Source:** [AI4I 2020 Predictive Maintenance Dataset](https://archive.ics.uci.edu/dataset/601/ai4i+2020+predictive+maintenance+dataset)

The dataset contains **10,000 records** with the following features:

| Column | Description |
|---|---|
| UDI | Unique record ID |
| Product ID | Product identifier |
| Type | Product quality variant (L, M, H) |
| Air temperature [K] | Ambient air temperature |
| Process temperature [K] | Process temperature |
| Rotational speed [rpm] | Machine rotational speed |
| Torque [Nm] | Torque applied |
| Tool wear [min] | Tool wear in minutes |
| Machine failure | Target label (0 = no failure, 1 = failure) |
| TWF, HDF, PWF, OSF, RNF | Individual failure mode flags |

## 🔍 Exploratory Data Analysis

### Distribution & Outliers
Boxplots were used to inspect the spread and outliers of each numerical feature.

![Boxplots of numerical features](images/boxplots.jpg)

### Correlation Analysis
A correlation heatmap was generated to understand relationships between features and the target variable.

![Correlation heatmap](images/correlation_heatmap.jpg)

### Rotational Speed vs Torque
A scatter plot highlights how failures cluster at the extremes of rotational speed and torque.

![Rotational speed vs torque scatter plot](images/scatter_plot.jpg)

## 🤖 Modeling

Two classification models were trained and compared:
- **Decision Tree Classifier**
- **Random Forest Classifier**

### Results — Confusion Matrices

![Confusion matrices for Decision Tree and Random Forest](images/confusion_matrices.jpg)

| Model | True Negatives | False Positives | False Negatives | True Positives |
|---|---|---|---|---|
| Decision Tree | 1795 | 137 | 8 | 60 |
| Random Forest | 1793 | 139 | 7 | 61 |

Both models perform similarly on this dataset, with Random Forest showing a marginal edge in correctly identifying failures (true positives).

## 🛠️ Tech Stack

- **Python**
- **Pandas** – data manipulation
- **Matplotlib / Seaborn** – visualization
- **Scikit-learn** – Decision Tree & Random Forest models

## 📁 Project Structure

```
├── ai4i2020.csv                 # Dataset
├── notebook.ipynb                # Analysis & modeling notebook
├── images/                       # Visualization exports
│   ├── boxplots.jpg
│   ├── correlation_heatmap.jpg
│   ├── scatter_plot.jpg
│   └── confusion_matrices.jpg
└── README.md
```

## 🚀 How to Run

1. Clone this repository
2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn
   ```
3. Open the notebook and run all cells:
   ```bash
   jupyter notebook notebook.ipynb
   ```

## 📈 Future Improvements

- Address class imbalance (failures are rare in the dataset)
- Try additional models (XGBoost, Gradient Boosting)
- Hyperparameter tuning
- Feature importance analysis for interpretability
- Deploy as a real-time prediction API

## Author

Developed as part of a graduation capstone project at the National Telecommunication Institute (NTI).
 ## License & Attribution

This project, including the code and the dataset, is licensed under the **Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)** License.

* **Dataset Source:** [Kaggle](https://www.kaggle.com/datasets/stephanmatzka/predictive-maintenance-dataset-ai4i-2020) 
* **Dataset Creator:** Prof. Dr. Stephan Matzka (HTW Berlin)

You are free to share and adapt this material, provided that you give appropriate credit, do not use it for commercial purposes, and distribute your contributions under the same license.
