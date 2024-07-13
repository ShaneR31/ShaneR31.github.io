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
    }

    .caption {
        text-align: left;
        font-size: 14px;
        margin-top: 5px;
    }
</style>

## Summary

In this project, we developed a robust fraud detection model to identify fraudulent transactions within a highly imbalanced dataset. The primary goal was to enhance security and reliability for financial transactions by accurately distinguishing between genuine and fraudulent activities. This summary provides an overview of the project's key features, methodologies, and practical implications. The full notebook and analysis is available [here](assets/pdf/creditCardFraud.pdf).


<div class="row">
    <div class="col-sm-8 mt-3 mt-md-0 header-image">
        {% include figure.liquid loading="eager" path="assets/img/fraud_detection/atm.jpg" title="ATM" class="img-fluid rounded z-depth-1" %}
        <div class="caption"><strong>ATM used for Credit Card Fraud Detection Project:</strong> Highlights the use of ATMs in the fraud detection project.</div>
    </div>
</div>

### Key Features

- **Data Preprocessing**:
  - Applied log transformation to the `Amount` feature to reduce skewness.
  - Standardized features using `RobustScaler` for consistent scaling.
  - Addressed class imbalance with SMOTE (Synthetic Minority Over-sampling Technique).

- **Exploratory Data Analysis (EDA)**:
  - Used visualizations like histograms, pairplots, and heatmaps to understand feature distributions and relationships.
  - Identified key patterns differentiating fraudulent from non-fraudulent transactions.

- **Model Selection and Hyperparameter Tuning**:
  - Evaluated Logistic Regression, Random Forest, Gradient Boosting, and XGBoost models.
  - Performed hyperparameter tuning with GridSearchCV, optimizing for the ROC AUC score.

- **Model Performance Evaluation**:
  - Compared models using metrics such as ROC AUC, precision-recall curves, and F1-score.
  - Selected **Random Forest** as the final model due to its superior balance of precision and recall, achieving an excellent AUC of 0.98 and the best F1 score. This choice ensures the model's high accuracy and reliability in detecting fraudulent transactions.

### Practical Implications

- **High Accuracy and Reliability**: The Random Forest model is highly effective in detecting fraudulent transactions, ensuring genuine transactions are processed smoothly.
- **Customer Confidence**: Provides a reliable system, minimizing interruptions to legitimate transactions.
- **Continuous Improvement**: Emphasizes ongoing monitoring and enhancement to adapt to new fraud patterns.

### Visual Highlights

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/fraud_detection/classDistribution.png" title="Class Distribution" class="img-fluid rounded z-depth-1" %}
        <div class="caption"><strong>Class Distribution:</strong> Highlights the severe class imbalance with fraudulent transactions being a very small fraction of the total transactions, underscoring the need for techniques like SMOTE.</div>
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/fraud_detection/timeDistribution.png" title="Time Feature Distribution" class="img-fluid rounded z-depth-1" %}
        <div class="caption"><strong>Time Feature Distribution:</strong> Shows the distribution of the `Time` feature, with a bimodal distribution indicating peak volumes during the day.</div>
    </div>
</div>

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="../assets/img/fraud_detection/logamountDistribution.png" title="LogAmount Distribution" class="img-fluid rounded z-depth-1" %}
        <div class="caption"><strong>LogAmount Distribution:</strong> Distribution of log-transformed transaction amounts.</div>
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="../assets/img/fraud_detection/pairplot.png" title="Pairplot" class="img-fluid rounded z-depth-1" %}
        <div class="caption"><strong>Pairplot:</strong> Visualizes relationships between selected features and highlights distinct clusters for fraudulent transactions.</div>
    </div>
</div>

### Model Performance

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="../assets/img/fraud_detection/precisionRecall.png" title="Precision-Recall Curves" class="img-fluid rounded z-depth-1" %}
        <div class="caption"><strong>Precision-Recall Curves:</strong> Demonstrates the model's ability to balance precision and recall, with Random Forest and XGBoost narrowly performing the best after tuning.</div>
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="../assets/img/fraud_detection/roc.png" title="ROC Curves" class="img-fluid rounded z-depth-1" %}
        <div class="caption"><strong>ROC Curves:</strong> Shows the model's performance in distinguishing between fraudulent and non-fraudulent transactions, with Random Forest and XGBoost achieving the highest AUC.</div>
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
            <th>Precision</th>
            <th>Recall</th>
            <th>F1-score</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Logistic Regression</td>
            <td>3.49</td>
            <td>0.97</td>
            <td>0.72</td>
            <td>0.06</td>
            <td>0.92</td>
            <td>0.11</td>
        </tr>
        <tr>
            <td>Random Forest</td>
            <td>225.78</td>
            <td>0.98</td>
            <td>0.87</td>
            <td>0.87</td>
            <td>0.84</td>
            <td>0.85</td>
        </tr>
        <tr>
            <td>Gradient Boosting</td>
            <td>414.15</td>
            <td>0.96</td>
            <td>0.77</td>
            <td>0.10</td>
            <td>0.91</td>
            <td>0.18</td>
        </tr>
        <tr>
            <td>XGBoost</td>
            <td>1.99</td>
            <td>0.98</td>
            <td>0.84</td>
            <td>0.69</td>
            <td>0.88</td>
            <td>0.77</td>
        </tr>
    </tbody>
</table>

### Final Model: Random Forest

Random Forest was chosen as the final model due to its superior performance across multiple evaluation metrics. It achieved the highest balance of precision and recall, with an excellent AUC of 0.98, indicating its strong ability to distinguish between fraudulent and non-fraudulent transactions. Additionally, the Random Forest model had the best F1 score, reflecting its effectiveness in correctly identifying both fraudulent transactions (high recall) and minimizing false positives (high precision).

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="../assets/img/fraud_detection/featureImportance.png" title="Feature Importance" class="img-fluid rounded z-depth-1" %}
        <div class="caption"><strong>Feature Importance:</strong> Shows the most important features used by the Random Forest model.</div>
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="../assets/img/fraud_detection/confusionMatrix.png" title="Random Forest Confusion Matrix" class="img-fluid rounded z-depth-1" %}
        <div class="caption"><strong>Confusion Matrix:</strong> The Random Forest model effectively minimizes false positives and false negatives while capturing many fraudulent transactions.</div>
    </div>
</div>

### Future Work

- **Model Enhancement**: Further tuning and adding additional features to improve performance.
- **Ensemble Methods**: Exploring combinations of multiple models for better results.

### Links

- [Full Notebook and Analysis](https://shanereichlin.com/fraud-detection/full-notebook)
- [GitHub Repository](https://github.com/ShaneR31/credit-card-fraud-detection)

