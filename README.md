# Smart Voyage: Travel Desirability Analysis

Popular travel destinations change over time due to shifts in tourism demand and climate, and these changes are often reflected in both visitor volume and tourism revenue (Zhou, 2024). The goal of this project is to build a data driven travel analytics system that combines tourism statistics and climate data to identify long term patterns in destination popularity and spending. Specifically, we aim to:

* Analyze long-term trends in tourism popularity (international arrivals), tourism spending intensity (receipts per arrival), and climate (yearly aggregated temperature).
* Classify destinations as increasing, stable, or decreasing in travel desirability based on their historical tourism trends.
* Cluster countries into groups with similar patterns and project future desirability.

We expect to find interpretable relationships between tourism demand, spending intensity, and climate trends. Our classification models should predict whether a destination is becoming more or less desirable, and clustering should reveal clear groups of countries with similar travel evolution profiles.

## Description

We formulated this project as a multivariate country year data mining problem, where each observation represents a single country in a specific year with associated tourism and climate columns. The final dataset spans 145 countries from 2000 to 2020, resulting in a structured panel dataset suitable for both predictive modeling and pattern analyzing.

Each data point includes both raw features and our engineered variables. Core input features consist of tourism variables such as arrivals, tourism receipts, and GDP, along with climate variables such as average yearly temperature. To enhance predictive performance, we constructed additional features including tourism and receipts growth rates, receipts per arrival (RPA), temperature change, and 5 year trend slopes. A key derived variable in this project is the trend_score, which combines tourism demand growth and spending quality into a single metric. This score serves as the foundation for multiple downstream tasks, including classification, forecasting, and ranking.

The unit of analysis is therefore a (country, year) pair, and overall the objective is to extract meaningful insights about how tourism desirability changes over time and across different countries using a combination of supervised and unsupervised learning methods and variation algorithms.

## Dataset
We combined two datasets:
* Tourism Data: International arrivals, tourism receipts, GDP -> https://www.kaggle.com/datasets/bushraqurban/tourism-and-economic-impact 
* Climate Data: Yearly temperature measurements -> https://www.kaggle.com/datasets/berkeleyearth/climate-change-earth-surface-temperature-data 

### Preprocessing Steps: 
* Removed missing values
* standardized country names
* Filtered years (1999+)
* Removed regional aggregates (e.g., 'World')
* Merged datasets on (country, year)

Final Dataset consisted of: 
* ~ 2,395 rows
* 145 countries

## Algorithms and Evaluation Metrics

### Classification: 
Used to label each country-year as increasing, stable, or decreasing
* Gradient Boosted Trees (GBT)
* Decision Tree
* Multilayer Perceptron (MLP)
* Linear SVM
Evaluated using Accuracy, Weighted F1 Scores, Precision/Recall

### Clustering (K-Means): 
Grouped countries based on tourism and climate patterns
Evaluated using Silhouette Score and PCA cluster plots

### Time Series Analysis:
Analyzed trends over time using linear regression
Evaluated using RMSE, Actual vs Predicted Plots, and Forecast Trend Lines

### Ranking System (Desirability Score): 
Ranked countries based on tourism performance and climate

## Conclusion
This project demonstrates that: 
* Combining tourism + climate data provides deeper insights
* Different algorithms reveal different perspectives
* Simple models work well for stable patterns, but struggle with volatile trends
Using multiple approaches allowed us to better understand global travel trends and destination desirability. 

## Executing program
### Requirements
- Python 3.x
- pandas
- numpy
- matplotlib
- scikit-learn
- pyspark

Install Dependencies: 
```
pip install pandas numpy matplotlib scikit-learn pyspark
```
Run Notebook Script
* Data preprocessing
* Feature engineering
* Model training
* Evaluation

## Authors
* Muhammed Arabi
* Shuroq Hussein
* Sarah Syeda
