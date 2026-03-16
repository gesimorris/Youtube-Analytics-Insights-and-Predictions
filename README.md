# YouTube Analytics: Insights and Predictions

A machine learning project analyzing YouTube video performance data to uncover patterns in audience engagement, monetization, and ad revenue prediction.

## Overview

This project explores a YouTube channel analytics dataset to answer two questions:

1. Can views, watch time, impressions, and premium revenue predict ad revenue?
2. Do these metrics vary by day of the week a video is published?

## Dataset

- **Source:** [Kaggle — YouTube Channel Performance Analytics](https://www.kaggle.com/datasets/positivealexey/youtube-channel-performance-analytics)
- **Size:** 362 rows, ~137KB, CSV format
- **Usability score:** 10/10
- **Metrics include:** views, watch time, impressions, CTR, likes, comments, revenue, YouTube Premium revenue, subscribers, and more

## Methods

### Exploratory Data Analysis
- Scatterplots for views vs watch time, impressions vs CTR, and revenue vs impressions
- Stacked bar charts comparing AdSense vs YouTube Premium revenue
- PCA using sklearn to reduce dimensionality — 5 components explain 96% of variance

### Models Used
| Model | Task | R² / Accuracy |
|---|---|---|
| Decision Tree Regressor | Ad revenue prediction | Baseline |
| Random Forest Regressor | Ad revenue prediction | 0.9288 |
| Gradient Boost Regressor | Ad revenue prediction | 0.928 (best) |
| MLP Regressor | Ad revenue prediction | ~0.13 (after standardization) |
| Random Forest Classifier | Day of week prediction | Low |
| Gradient Boost Classifier | Day of week prediction | Low |
| MLP Classifier | Day of week prediction | 0.26 (best) |

### Tuning
- Grid search for hyperparameter optimization on all models
- Standardization applied to improve MLP performance
- Cross validation for generalization testing

## Results

**Regression:** The Gradient Boost Regressor was the best model with an R² of 0.928, MAE of 3.47, and MSE of 74.63. Views, watch time, impressions, and YouTube Premium revenue are strong predictors of ad revenue.

**Classification:** All models struggled to predict day of upload. The MLP Classifier achieved the best accuracy of 0.26, with Wednesday performing best likely due to having the most samples. These metrics do not vary meaningfully by day of the week.

## Key Findings

- Higher views, watch time, and impressions are positively correlated with ad revenue
- YouTube Premium revenue is the strongest individual predictor in the decision tree
- CTR is key to converting impressions into views and revenue
- Day of upload cannot be reliably predicted from performance metrics alone
- Tree-based models outperform neural networks on this dataset

## Technologies

- Python
- scikit-learn
- pandas
- matplotlib
- Google Colab

## Notebook

[View on Google Colab](https://colab.research.google.com/drive/1QYalgjnimiRrYweLoTgFtZjeY_uDcQ90)
