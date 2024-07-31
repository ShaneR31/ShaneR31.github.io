---
layout: page
title: Digital Marketing Analysis
description: Discover how data-driven marketing strategies can enhance customer conversion and engagement. Explore our comprehensive analysis, model predictions, and customer segmentation.
img: assets/img/marketing_analysis/title.jpg
importance: 6
category: 
---
<style>
    .header-image {
        max-width: 90%;
        margin: 0 auto;
        display: block;
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
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/marketing_analysis/title.jpg" title="Digital Marketing Campaign Analysis" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

## Intro

This project focuses on analyzing and optimizing digital marketing strategies using a comprehensive dataset that includes customer demographics, engagement metrics, and campaign interactions. The goal is to understand the key factors driving customer conversions, segment customers for targeted marketing, and evaluate the effectiveness of various marketing campaigns. The full notebook and analysis can be found [here](https://shanereichlin.com/digital-marketing-conversion/docs/digital_marketing_conversion.html){:target="_blank"}.

### Exploratory Data Analysis (EDA)
We started by performing exploratory data analysis to understand the distribution and relationships of the features in our dataset:
- **Numerical Features**: Key features such as Age, Income, AdSpend, ConversionRate, and WebsiteVisits were visualized to understand their distributions. Most features showed relatively uniform distributions, indicating a diverse customer base and varied marketing efforts.

<div class="row">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/marketing_analysis/numDists.png" title="Numerical Features Distribution" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

- **Categorical Features**: Features like Gender, CampaignChannel, and CampaignType were analyzed to understand the composition of the dataset. The analysis showed a balanced use of different marketing channels and campaign types.

<div class="row">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/marketing_analysis/catDists.png" title="Categorical Features Distribution" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

### Feature Engineering
We created new features to enhance the predictive power of our model and promote a deeper understanding of the data, these include:
- **EmailEngagement**: Combined email opens and clicks.
- **SiteEngagement**: Combined website visits, pages per visit, and time on site.
- **IncomePerClick**: Income divided by click-through rate.
- **AdSpendPerClick**: Ad spend divided by click-through rate.
- **ClickToConversionRate**: Conversion rate divided by click-through rate.
- **TotalInteractions**: Aggregated social shares, email opens, email clicks, and previous purchases.

### Correlation Analysis
A correlation matrix was created to identify relationships between features. The analysis revealed the following key insights related to conversion:
- **Positive Correlations**:
  - **EmailEngagement and Conversion**: Higher engagement with email campaigns is strongly associated with higher conversion rates.
  - **SiteEngagement and Conversion**: Increased interaction with the website correlates positively with conversion likelihood.
  - **PreviousPurchases and Conversion**: Customers with a history of previous purchases are more likely to convert again.

- **Negative Correlations**:
  - **AdSpendPerClick and Conversion**: Higher ad spend per click showed a weaker, negative correlation with conversion, indicating that simply increasing ad spend may not directly lead to higher conversions.

<div class="row">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/marketing_analysis/corrMatrix.png" title="Correlation Matrix" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

### Predicting Customer Conversion
#### Data Preprocessing
SMOTE was applied to handle class imbalance in the target variable (Conversion) so that the model may learn the attributes of both conversions and non-conversions. Feature scaling was also performed with MinMaxScaler to normalize values prior to model creation.

#### Model Training
The XGBoost classifier was trained and tuned using GridSearchCV. The best model demonstrated strong performance with high precision, recall, and F1 scores.

#### Model Evaluation

| Model   | Accuracy | Precision | Recall   | F1 Score | ROC AUC |
|---------|----------|-----------|----------|----------|---------|
| XGBoost | 0.927917 | 0.927402  | 0.995722 | 0.960348 | 0.803918|

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/marketing_analysis/confusionMatrix.png" title="Confusion Matrix" class="img-fluid rounded z-depth-1" %}
        <div class="caption"><strong>Confusion Matrix:</strong> High true positives and low false negatives indicated the model's effectiveness in predicting conversions.</div>
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/marketing_analysis/roc.png" title="ROC Curve" class="img-fluid rounded z-depth-1" %}
        <div class="caption"><strong>ROC Curve:</strong> The AUC value of 0.80 indicated good performance in distinguishing between converted and non-converted customers.</div>
    </div>
</div>

### Customer Segmentation
#### Clustering Analysis
K-Means clustering was used to segment customers based on engagement and demographic features. The clusters were visualized using PCA, and the analysis revealed distinct customer segments, allowing for tailored marketing strategies.

<div class="row">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/marketing_analysis/pca.png" title="PCA Clusters" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

#### Cluster Evaluation
- **Silhouette Score**: 0.19
- **Davies-Bouldin Score**: 1.73
- **Calinski-Harabasz Score**: 1725.85

The scores indicated reasonable cluster separation but also highlighted areas where clustering performance could be further enhanced, such as improving within-cluster cohesion and minimizing cluster overlap, suggesting that there is potential for more distinct and meaningful clusters through refined feature engineering, advanced clustering algorithms, and additional data enrichment.


### Campaign Effectiveness
- **Campaign Channels**: Email, PPC, and Social Media showed high conversion rates.
- **Campaign Types**: Conversion campaigns were the most effective, followed by Awareness and Retention campaigns.

### Future Work
Several areas for future exploration were identified:
- **Feature Engineering**: Additional interaction features and external data sources could further improve model performance and clustering results.
- **Advanced Clustering Techniques**: Techniques like DBSCAN or Gaussian Mixture Models may provide better cluster separation and interpretability.
- **A/B Testing**: Implementing A/B testing strategies can optimize marketing efforts in areas such as email campaigns, ad campaigns, website engagement, loyalty programs, conversion rate optimization, content marketing, and referral programs.

### Conclusion
This project provided valuable insights into customer behavior and marketing strategies. The predictive model, customer segmentation, and campaign effectiveness analysis offer a comprehensive approach to optimizing digital marketing efforts. Future work will focus on refining these strategies through advanced techniques and A/B testing to drive even greater marketing success.

### Links
- [Full Notebook and Analysis](https://shanereichlin.com/digital-marketing-conversion/docs/digital_marketing_conversion.html){:target="_blank"}
- [Project Repository](https://github.com/ShaneR31/digital-marketing-conversion){:target="_blank"}