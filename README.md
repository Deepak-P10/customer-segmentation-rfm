# Customer Segmentation Using RFM Analysis and K-Means

## Overview

This project segments customers from an online retail dataset using **RFM analysis** and **K-Means clustering**. It explores the transaction data, cleans records, calculates customer-level Recency, Frequency, and Monetary (RFM) features, scales the features, and groups customers into clusters.

## Objectives

- Inspect and clean online retail transaction data.
- Explore transaction counts by country and monthly revenue trends.
- Build customer-level RFM metrics.
- Use the Elbow Method and silhouette scores to help assess the number of clusters.
- Apply K-Means clustering to assign each customer to a segment.

## Dataset

The notebook expects an Excel file named **`Online Retail.xlsx`** in the same directory as the notebook.

The dataset should contain these columns:

- `CustomerID`
- `InvoiceNo`
- `InvoiceDate`
- `Quantity`
- `UnitPrice`
- `Country`

The notebook does not download the dataset automatically. Obtain the dataset separately and place it beside `Customer_Segmentation.ipynb` before running the notebook.

## Tools and Libraries

- Python
- Jupyter Notebook
- pandas
- NumPy
- Matplotlib
- Seaborn
- scikit-learn
- openpyxl

## Setup

1. Clone or download this project.
2. Place `Online Retail.xlsx` in the project directory.
3. Install the required packages:

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn openpyxl jupyter
   ```

4. Launch Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

5. Open `Customer_Segmentation.ipynb` and run the cells from top to bottom.

The notebook also includes package-installation commands near the beginning, which can be run inside Jupyter if needed.

## Project Workflow

### 1. Load and inspect the data

The notebook loads the Excel dataset with pandas and examines sample records, descriptive statistics, and missing values.

### 2. Clean the transactions

The cleaning steps:

- Remove rows with missing `CustomerID`.
- Convert `InvoiceNo` to a string.
- Exclude invoices whose identifiers start with `C` (cancellations/returns as represented by the notebook's rule).
- Keep only rows with positive `Quantity` and positive `UnitPrice`.
- Convert `CustomerID` to an integer.
- Calculate revenue for each row as `Quantity × UnitPrice`.

### 3. Explore the data

The notebook plots:
- The top 10 countries by transaction-record count.
- Monthly revenue over time.

### 4. Calculate RFM features

Customer-level metrics are calculated as follows:

| Feature | Meaning in this project |
|---|---|
| **Recency** | Number of days since the customer's most recent invoice, relative to one day after the latest invoice date in the cleaned data |
| **Frequency** | Number of distinct invoice numbers for the customer |
| **Monetary** | Sum of transaction revenue for the customer |

### 5. Prepare features

The RFM values are transformed using `log1p` and then standardized with `StandardScaler` before clustering.

### 6. Evaluate candidate cluster counts

- The **Elbow Method** plots K-Means inertia for cluster counts from 2 through 10.
- **Silhouette scores** are calculated for cluster counts from 2 through 7.

These plots and scores help assess clustering choices. The notebook's final model currently uses **4 clusters**.

### 7. Fit the final model

K-Means is fitted with `n_clusters=4`, `random_state=42`, and `n_init=10`. The resulting cluster label is added to the customer-level RFM table as `Cluster`.

## Output

After the notebook runs, the `rfm` DataFrame contains one row per customer and these columns:

- `Recency`
- `Frequency`
- `Monetary`
- `Cluster`

The notebook also displays exploratory charts and cluster-count evaluation results. It does not currently include a detailed interpretation or business label for each cluster.

## Notes and Limitations

- The input file must be available locally; it is not included automatically.
- The final number of clusters is hard-coded to 4. Review the Elbow Method and silhouette scores before changing or accepting this choice.
- Cluster labels such as `0`, `1`, `2`, and `3` are identifiers, not rankings.
- The notebook does not currently generate a cluster profile report or assign descriptive names such as “high-value” or “at-risk” customers.

## Repository Structure

```text
.
├── Customer_Segmentation.ipynb
├── Online Retail.xlsx       # Required input data; add separately
└── README.md
```

