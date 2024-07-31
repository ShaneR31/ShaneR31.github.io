---
layout: page
title: Customer Segmentation
description: Learn how data-driven segmentation can identify key customer groups, optimize marketing strategies, and improve overall business performance through tailored campaigns.
img: assets/img/customer_segmentation/title.jpg
importance: 4
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

# Customer Segmentation Analysis

<div class="row">
    <div class="col-sm-12 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/customer_segmentation/title.jpg" title="Customer Segmentation Analysis" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

## Project Overview

This project aimed to perform customer segmentation using clustering techniques to identify distinct customer groups based on purchasing behaviors and demographics. The analysis provided insights into different customer segments, helping businesses tailor their marketing strategies and improve customer engagement.

## Key Objectives

1. **Identify Distinct Customer Segments**: Used clustering algorithms to group customers based on purchasing patterns and demographic data.
2. **Profile Each Segment**: Developed detailed profiles for each segment, highlighting spending habits, demographic characteristics, and marketing responsiveness.
3. **Visualize Segments**: Created visualizations to illustrate the unique characteristics and behaviors of each segment, facilitating strategic decision-making.

## Data Sources

The dataset, available [here](https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis/data), includes:
- **Demographic Information**: Age, income, marital status, education level, and household size.
- **Purchasing Behaviors**: Spending amounts on various product categories including wines, fruits, meat products, fish products, sweets, and gold.
- **Marketing Interaction**: Counts of web, catalog, and store purchases, and responses to marketing campaigns.
- **Additional Features**: Usage of discounts and complaint frequency.

## Methodology

1. **Data Preprocessing**: Cleaned the dataset, managed missing values, and standardized numerical features.
2. **Clustering**: Applied K-means clustering to uncover customer segments, choosing the optimal number of clusters using the elbow method and silhouette analysis.
3. **Segmentation and Profiling**: Analyzed each cluster to create comprehensive profiles based on demographic and behavioral data.
4. **Visualization**: Used radar charts, KDE plots, and bar charts to depict the characteristics of each segment.

## Segment Profiles

1. **Working Class**:
   The Working Class segment consists of middle-aged individuals with moderate incomes. They focus on balanced spending across necessities, with occasional luxury purchases. This group often includes married individuals and families. Their purchasing decisions are influenced by budget considerations, and they respond well to campaigns emphasizing value and affordability.

2. **Emerging Professionals**:
   Emerging Professionals are younger adults at the beginning of their careers, with lower to moderate incomes. They prioritize essential items and are highly responsive to discounts and promotions. This group is typically single or in small households and is influenced by digital marketing that offers value and career-related products.

3. **Value-Oriented Professionals**:
   Value-Oriented Professionals are higher-income individuals who focus on budgeting and getting the best value. Well-educated and often with advanced degrees, they have a balanced spending approach and prioritize quality. They respond to marketing that emphasizes product quality and value, and they often have families.

4. **High-Income Luxury Seekers**:
   High-Income Luxury Seekers are older, affluent individuals who prefer luxury items and experiences. They have significant spending power and a strong preference for high-quality, exclusive products. This group values premium branding and personalized services, responding well to luxury marketing that emphasizes exclusivity and prestige.


## Visual Highlights

### Customer Segmentation
<div class="row justify-content-center">
    <div class="col-sm-12 mt-3 mt-md-0" style="max-width: 85%;">
        {% include figure.liquid loading="eager" path="assets/img/customer_segmentation/fourClusterScatter.png" title="Customer Segmentation Scatter Plot" class="img-fluid rounded z-depth-1" style="max-width: 85%;" %}
    </div>
</div>

### Purchasing Behavior
<div class="row justify-content-center">
    <div class="col-sm-12 mt-3 mt-md-0" style="max-width: 85%;">
        {% include figure.liquid loading="eager" path="assets/img/customer_segmentation/clusterRadar.png" title="Radar Chart of Purchasing Behavior" class="img-fluid rounded z-depth-1" style="max-width: 85%;" %}
    </div>
</div>

### Age, Income, and Total Spending Distribution
<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/customer_segmentation/clusterAgeDist.png" title="Age Distribution by Cluster" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/customer_segmentation/clusterIncomeDist.png" title="Income Distribution by Cluster" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/customer_segmentation/clusterTotalSpendingDist.png" title="Total Spending Distribution by Cluster" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/customer_segmentation/clusterSpending.png" title="Total Spending Breakdown by Category" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

### Campaign Performance
<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/customer_segmentation/clusterCampaignAcceptance.png" title="Subcluster Campaign Acceptance Rates" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/customer_segmentation/campaignAcceptanceHeatmap.png" title="Heatmap of Campaign Acceptance" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

## Future Improvements

- **Enhance Data Features**: Integrate geographic data, customer feedback, and brand preferences for deeper insights.
- **Develop Predictive Models**: Create models to predict future customer behaviors based on historical data.
- **Explore Advanced Segmentation**: Utilize advanced clustering techniques for more refined customer segments.

## Conclusion

This customer segmentation analysis offers significant potential for businesses to enhance their marketing effectiveness. By understanding the distinct characteristics and behaviors of each customer segment, companies can tailor their strategies to improve key metrics such as campaign acceptance rates and targeted advertisement effectiveness. This targeted approach can lead to increased customer satisfaction, optimized resource allocation, and ultimately, higher conversion rates. By leveraging these insights, businesses can refine their marketing efforts, ensuring they reach the right audience with the right message, thereby maximizing their return on investment and fostering sustainable growth.

[Full Notebook](https://shanereichlin.com/customer-personality-analysis/notebooks/customer_personality_analysis.html)

[Repository](https://github.com/ShaneR31/customer-personality-analysis).

