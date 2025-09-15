# Customer Segmentation using RFM Analysis

This project applies **RFM (Recency, Frequency, Monetary) analysis** to an online retail dataset to segment customers based on purchasing behavior.  
The insights help businesses design **targeted marketing strategies** for different customer groups.

---

## What is RFM?
RFM is a marketing analysis technique that measures three key metrics:

- **Recency (R):** How recently a customer made a purchase.  
- **Frequency (F):** How often a customer makes a purchase.  
- **Monetary (M):** How much money a customer spends.  

By scoring customers on these dimensions, businesses can group them into segments such as **Champions, New Customers, At-Risk**, and more.

---

## Files in this Repository
- `rfm_analysis.ipynb` → Jupyter Notebook with full workflow (data cleaning, RFM calculation, scoring, segmentation, visualization).  
- `Online_retail.csv` → Raw dataset used for analysis.  
- `rfm_analysis_data.csv` → Processed file with final RFM scores and customer segments.
- `Dashboard.pdf` → The Dashboard created in Tableau for the RFM analysis performed.  

---

## Key Steps in the Notebook

### 1. Data Loading & Exploration
- Load dataset into Pandas.  
- Check structure (`head()`, `info()`, `describe()`).  

### 2. Data Cleaning & Preprocessing
- Remove missing `CustomerID`.  
- Drop duplicates.  
- Convert `InvoiceDate` to datetime.  
- Remove negative quantities (returns/cancellations).  
- Create `TotalPrice = Quantity × UnitPrice`.  

### 3. Calculating RFM Metrics
- Define **snapshot date** (1 day after last transaction).  
- Compute per customer:  
  - `Recency` = Days since last purchase.  
  - `Frequency` = Number of unique invoices.  
  - `Monetary` = Total spend.  

### 4. RFM Scoring
- Quartile-based scoring (`pd.qcut`).  
- **Recency:** lower = better → scored 4 → 1.  
- **Frequency & Monetary:** higher = better → scored 1 → 4.  
- Combine into `RFM_Score` (e.g., `444`).  

### 5. Customer Segmentation
- **Champions:** [3-4][3-4][3-4] → Recent, frequent, high spenders.  
- **Potential Loyalists:** [2-4][1-2][3-4].  
- **New Customers:** [3-4][1-2][1-2].  
- **Needs Attention:** [2-3][2-3][2-3].  
- **At-Risk:** starts with 2, then [3-4][3-4].  
- **Hibernating:** starts with 1, then [2-4][2-4].  
- **Lost Customers:** 11[1-4].  
- Others categorized as **“Other”**.  

---

## Results & Visualizations
The notebook generates:
- **Customer Segments by Size** → bar chart.  
- **Average R/F/M values by Segment** → comparison charts.  
- **Exported dataset** → `rfm_analysis_data.csv`.  

These outputs provide actionable insights for **customer retention & targeted campaigns**.  

---

## Tech Stack
- Python (Pandas, NumPy, Matplotlib, Seaborn)  
- Jupyter Notebook  
- CSV data processing
- Tableau

---

## Example Use Cases
- Identify best customers to reward (Champions).  
- Detect churn signals (At-Risk, Hibernating).  
- Personalize offers for **New Customers**.  
- Optimize loyalty programs.  
