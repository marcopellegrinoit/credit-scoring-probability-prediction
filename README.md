# **Credit Scoring Probability Prediction** 💳
Author: Marco Pellegrino<br>
Year: 2024

This project aims to build a simple model to predict the probability of loan default based on loan application data. This information helps assess business risk and improve loan approval decisions.

## Table of Contents

1.  [Description](#description)
2.  [Input Data](#input-data)
3.  [Install Required Libraries](#install-required-libraries)
4.  [Project Structure](#project-structure)
5.  [License](#license)

## Description
The main steps consist of processing the input data, training models, and evaluating their performance.

**1. Data Processing**

Raw input data is processed in the following steps:

- Data Inspection
- Domain-based Feature Selection
- Values Formatting
- Correlation Analysis
- Final Distribution Inspection

Note: raw data can be read from a local CSV file or from an AWS S3 bucket.

**2. Data Modeling**

Develop a machine learning model based on the provided data to predict the probability of loan default. The model should achieve good accuracy and be easily interpretable by business stakeholders.

Some missing values are initially removed, others are imputed during the training phase to avoid data leakage.

Different models are implemented:

*   Decision Tree
*   Random Forest
*   XGBoost

**3. Data Evaluation**

Model performance is evaluated using the following metrics:

*   Log Loss
*   AUC Score
*   F1 score (for class prediction)

Data visualizations are provided to compare the models on the above metrics.

## Input data

The dataset contains loan application data. Data cannot be attached to this repository. Each data point includes information relevant to assessing loan risk, such as financial ratios, company demographics, and loan terms. The following features are provided:

<table><tbody><tr><td><strong>Feature</strong></td><td><strong>Description</strong></td><td><strong>Type</strong></td><td><strong>Values</strong></td></tr><tr><td><code>r_application_id</code></td><td>Application ID</td><td>Integer</td><td>&nbsp;</td></tr><tr><td><code>applic_date</code></td><td>Application Date</td><td>Date</td><td>&nbsp;</td></tr><tr><td><code>company_type</code></td><td>Company Type</td><td>String</td><td>Fixed "AB"</td></tr><tr><td><code>company_rating</code></td><td>Company Rating</td><td>Float</td><td>Scale 0-100: 0=worst, 100=best</td></tr><tr><td><code>incorporation_date</code></td><td>Incorporation Date</td><td>Date</td><td>&nbsp;</td></tr><tr><td><code>net_turnover</code></td><td>Net Turnover</td><td>Float</td><td>&nbsp;</td></tr><tr><td><code>person_scoring</code></td><td>Person's Scoring</td><td>Float</td><td>Scale 0-100: 0=worst, 100=best</td></tr><tr><td><code>prev_contr_count</code></td><td>Number of Previous Loan Contracts</td><td>Integer</td><td>&nbsp;</td></tr><tr><td><code>max_late_1yr</code></td><td>Longest Payment Delay in Previous 12 Months</td><td>Float</td><td>&nbsp;</td></tr><tr><td><code>uc_risk_class</code></td><td>UC Risk Class</td><td>Integer</td><td>Scale 1-5: 1=worst, 5=best</td></tr><tr><td><code>default</code></td><td>Loan Default</td><td>Integer</td><td>Binary: 1 if loan defaulted (was sent to collection), 0 if no default</td></tr></tbody></table>

## Install Required Libraries

To install the required Python libraries:

```plaintext
pip install -r requirements.txt
```

Note: In some environments, use `pip3` instead of `pip`.

The code has been tested with Python 3.11.

## Project Structure
Note: paths of resources (data frames, plots, ...) are defined in `config.py`.

```plaintext
.
├── data/
    ├── raw/
        └── loan_application_data-raw.csv   # raw input dataset
    └── preprocessed/
        └── loan_application_data-preprocessed.csv # preprocessed data for training
    ├── evaluation
        ├── all/
            └── evaluation-*.csv   # AUC, Log Loss, F1 Scores
        ├── tpf/
            └── evaluation_tpr-*.csv   # True Positive Rates or ROC-AUC per model
        └── fpr/
            └── evaluation_fpr-*.csv # # False Positive Rates or ROC-AUC per model
├── plots/
    ├── raw_data/ # Plot of raw data
    ├── models/ # Plot of raw data
        ├── models_feature_importance/    # Plots of model feature importance
        ├── model_comparison/    # Plots to compare models
        ├── models_auc_roc_curve/    # Plots of ROC Curve during CV Validation
        └── rules_decision_tree.png  # Decision Rules of Decision Tree Model
├── 1_EDA-preprocessing.ipynb    # Process raw data for modeling
├── 2-training-*.ipynb    # Training and evaluation for different models
├── 3_compare_models.ipynb  # Compare model performance with visualizations
├── requirements.txt    # Required Python libraries
├── config.py    # Paths definition
└── README.md    # This description
```

## License

This repository is licensed under the GNU General Public License v3.0 (GPL-3.0). For more details, see the [LICENSE](LICENSE) file.