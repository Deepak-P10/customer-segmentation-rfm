# Customer Intelligence & Segmentation Using Machine Learning

## Overview
An end-to-end customer analytics project using transactional retail data to segment customers, analyze purchasing patterns, and generate data-driven marketing recommendations.

## Objectives
- Segment customers using Recency, Frequency, and Monetary (RFM) features.
- Apply K-Means clustering and compare clustering configurations.
- Evaluate cluster quality using inertia and silhouette scores.
- Analyze customer inactivity and product revenue patterns.
- Generate segment-specific marketing recommendations.

## Technologies
Python, Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, Jupyter Notebook.

## Dataset
UCI Machine Learning Repository — Online Retail.

Dataset: https://archive.ics.uci.edu/dataset/352/online+retail

## Methodology
1. Data cleaning and exploratory data analysis.
2. RFM feature engineering.
3. Log transformation and feature scaling.
4. K-Means clustering and model evaluation.
5. Customer profile analysis and business recommendations.

## Project Outputs
- Customer segment assignments.
- Cluster evaluation results.
- Customer profile summaries.
- Product revenue analysis.
- Visualizations and business insights.

## How to Run
1. Clone this repository.
2. Install dependencies using `pip install -r requirements.txt`.
3. Download the dataset from UCI and place it in the project directory.
4. Open `Customer_Segmentation_ML.ipynb` in Jupyter Notebook.
5. Run the notebook cells in order.

## Limitations
Customer inactivity is defined using a chosen threshold and is not a validated churn prediction. Clustering results depend on preprocessing and model parameters.

## Dataset Attribution
Online Retail dataset, UCI Machine Learning Repository. Dataset license: CC BY 4.0.

## Author
DEEPAK P
