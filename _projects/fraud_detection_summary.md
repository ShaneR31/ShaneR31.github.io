---
layout: page
title: Credit Card Fraud Detection
description: Curious about the technology behind fraud prevention? Uncover the machine learning algorithms that can help protect your financial data.
img: assets/img/fraud_detection/atm.jpg
importance: 5
category: 
---
<style>
    .header-image {
        max-width: 90%;
        align: center;
    }

    .caption {
        text-align: left;
        font-size: 14px;
        margin-top: 5px;
    }

    table {
        width: 100%;
        border-collapse: collapse;
        margin-bottom: 20px;
    }

    th, td {
        border: 1px solid var(--global-divider-color);
        text-align: left;
        padding: 8px;
    }

    th {
        background-color: var(--global-theme-color);
        color: var(--global-hover-text-color);
    }

    tr:nth-child(even) {
        background-color: var(--global-card-bg-color);
    }

    tr:nth-child(odd) {
        background-color: var(--global-bg-color);
    }

    td {
        color: var(--global-text-color);
    }
</style>

<div class="row">
    <div class="col-sm-8 mt-3 mt-md-0 header-image">
        {% include figure.liquid loading="eager" path="assets/img/fraud_detection/atm.jpg" title="ATM" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

## Summary

In this project, we developed a robust fraud detection model to identify fraudulent transactions within a highly imbalanced dataset. The primary goal was to enhance security and reliability for financial transactions by accurately distinguishing between genuine and fraudulent activities. This summary provides an overview of the project's key features, methodologies, and practical implications. The full notebook and analysis with larger visualizations is available [here](https://shaner31.github.io/credit-card-fraud-detection/Docs/fraud-detection.html).

### Key Features

- **Data Preprocessing**:
  - Applied log transformation to the `Amount` feature to reduce skewness.
  - Standardized features using `RobustScaler` for consistent scaling.
  - Addressed class imbalance with SMOTE (Synthetic Minority Over-sampling Technique).

- **Exploratory Data Analysis (EDA)**:
  - Used visualizations like histograms, pairplots, and heatmaps to understand feature distributions and relationships.
  - Identified key patterns differentiating fraudulent from non-fraudulent transactions.

- **Model Selection and Hyperparameter Tuning**:
  - Evaluated basic Logistic Regression, Random Forest, Gradient Boosting, and XGBoost models.
  - Performed hyperparameter tuning with GridSearchCV on Random Forest and XGBoost models, optimizing for average precision.

- **Model Performance Evaluation**:
  - Compared models using metrics such as Precision-Recall AUC, ROC AUC, and F1-score.
  - Selected **XGBoost** as the final model due to its superior balance of precision and recall, achieving a Precision-Recall AUC of 0.89 and the best F1 score among tuned models. This choice ensures the model's high accuracy and reliability in detecting fraudulent transactions.

### Practical Implications

- **High Accuracy and Reliability**: The XGBoost classifier is highly effective in detecting fraudulent transactions, ensuring genuine transactions are processed smoothly.
- **Customer Confidence**: Provides a reliable system, minimizing interruptions to legitimate transactions.
- **Continuous Improvement**: Emphasizes ongoing monitoring and enhancement to adapt to new fraud patterns.

### Visual Highlights

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/fraud_detection/classDistribution.png" title="Class Distribution" class="img-fluid rounded z-depth-1" %}
        <div class="caption"><strong>Class Distribution:</strong> Highlights the severe class imbalance with fraudulent transactions being a very small fraction of the total transactions, underscoring the need for rebalancing techniques like SMOTE.</div>
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/fraud_detection/timeDistribution.png" title="Time Feature Distribution" class="img-fluid rounded z-depth-1" %}
        <div class="caption"><strong>Time Feature Distribution:</strong> Shows the distribution of the `Time` feature, with a bimodal distribution indicating peak volumes during the day.</div>
    </div>
</div>

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="../assets/img/fraud_detection/logamountDistribution.png" title="LogAmount Distribution" class="img-fluid rounded z-depth-1" %}
        <div class="caption"><strong>LogAmount Distribution:</strong> Distribution of log-transformed transaction amounts. A minority of extremely high value transactions contributed to a significant skew in the untransformed data.</div>
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="../assets/img/fraud_detection/pairplot.png" title="Pairplot" class="img-fluid rounded z-depth-1" %}
        <div class="caption"><strong>Pairplot:</strong> Visualizes relationships between selected features and highlights distinct clusters for fraudulent transactions.</div>
    </div>
</div>

### Tuned Model Performance

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="../assets/img/fraud_detection/precisionRecall.png" title="Precision-Recall Curves" class="img-fluid rounded z-depth-1" %}
        <div class="caption"><strong>Precision-Recall Curves:</strong> Demonstrates the model's ability to balance precision and recall, with XGBoost performing the best after tuning.</div>
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="../assets/img/fraud_detection/roc.png" title="ROC Curves" class="img-fluid rounded z-depth-1" %}
        <div class="caption"><strong>ROC Curves:</strong> Shows the performance of each model in distinguishing between fraudulent and non-fraudulent transactions, with XGBoost achieving the highest AUC.</div>
    </div>
</div>

### Tuned Model Results

<table>
    <thead>
        <tr>
            <th>Model</th>
            <th>Training Time (s)</th>
            <th>ROC AUC</th>
            <th>Average Precision</th>
            <th>PRC AUC</th>
            <th>Precision</th>
            <th>Recall</th>
            <th>F1-score</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Random Forest</td>
            <td>488.24</td>
            <td>0.97</td>
            <td>0.86</td>
            <td>0.86</td>
            <td>0.73</td>
            <td>0.85</td>
            <td>0.79</td>
        </tr>
        <tr>
            <td>XGBoost</td>
            <td>3.72</td>
            <td>0.98</td>
            <td>0.89</td>
            <td>0.89</td>
            <td>0.78</td>
            <td>0.88</td>
            <td>0.83</td>
        </tr>
    </tbody>
</table>

### Final Model: XGBoost

XGBoost was chosen as the final model due to its outstanding performance across all evaluation metrics. It achieved the highest balance of precision and recall, evidenced by an excellent Precision-Recall AUC of 0.89, which indicates its strong capability to differentiate between fraudulent and non-fraudulent transactions. Additionally, the XGBoost model achieved the best F1 score, demonstrating its effectiveness in accurately identifying fraudulent transactions (high recall) while minimizing false positives (high precision). Furthermore, XGBoost had a significantly shorter training time compared to other models, making it not only effective but also efficient and practical for real-world applications.

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="../assets/img/fraud_detection/confusionMatrix.png" title="Random Forest Confusion Matrix" class="img-fluid rounded z-depth-1" %}
        <div class="caption"><strong>Confusion Matrix:</strong> The Random Forest model effectively minimizes false positives and false negatives while capturing many fraudulent transactions.</div>
    </div>
        <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="../assets/img/fraud_detection/featureImportance" title="Feature Importance" class="img-fluid rounded z-depth-1" %}
        <div class="caption"><strong>Feature Importance:</strong> Shows the most important features used by the XGBoost model to make predictions.</div>
    </div>
</div>

### Future Work

- **Model Enhancement**: Further tuning and adding additional features to improve performance.
- **Ensemble Methods**: Exploring combinations of multiple models for better results.

### Links

- [Full Notebook and Analysis](https://shaner31.github.io/credit-card-fraud-detection/Docs/fraud-detection.html)
- [GitHub Repository](https://github.com/ShaneR31/credit-card-fraud-detection)

