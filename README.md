##  A. Techniques, Tools, and Reasoning

###  Techniques Used

#### 1. Exploratory Data Analysis (EDA)
- Visualized **daily, monthly, and yearly** sales trends.
- Examined store-level and product-level performance.
- Used **STL decomposition** to separate trend, seasonality, and residuals.

#### 2. Statistical Approach – Z-Score Method
- Calculated **rolling mean** and **rolling standard deviation**.
- Flagged anomalies when sales deviated beyond **±2σ**.
- Simple yet effective for interpretable anomaly detection.

#### 3. Machine Learning Approach – Isolation Forest
- Identified anomalies through random partitioning of data.
- Handles **non-linear relationships** and **irregular patterns** effectively.

#### 4. Ensemble Approach
Combined multiple ML models to make anomaly detection more stable:
-  **Isolation Forest**  
-  **One-Class SVM**  
-  **Local Outlier Factor**  
-  **Elliptic Envelope**  
A data point is marked anomalous if **2 or more models** agree — reducing false positives.

#### 5. Visualization and Trend Analysis
- Used **STL Decomposition**, **Rolling Statistics**, and **ACF/PACF** plots.
- Overlaid anomalies on time-series graphs for clear interpretation.

---

### Tools and Libraries

| Category | Tools Used |
|-----------|-------------|
| **Data Processing** | `pandas`, `numpy` |
| **Visualization** | `matplotlib`, `seaborn`, `statsmodels` |
| **Machine Learning** | `scikit-learn` |
| **Time-Series Analysis** | `STL`, `adfuller` (for stationarity test) |

---

###  Reasoning Behind the Approach

- **Why Ensemble?**  
  Individual models may overfit or miss anomalies. Combining them ensures **robust and consistent results**.

- **Why Monthly Aggregation?**  
  Aggregating to monthly level smooths out random daily fluctuations and reveals **meaningful business trends**.

  ---

  ## Data Description

The dataset contains **daily sales data from 2010 to 2019** for **7 stores** and **10 products**.  
It includes the following columns:
- **Date:** Transaction date  
- **store:** Store ID (1–7)  
- **product:** Product ID (1–10)  
- **number_sold:** Number of items sold on that day  


##  B. Key Observations & Results

1. **Sales Seasonality**
   - Strong seasonal peaks in **Jan, Aug, Oct–Dec** (likely due to holidays or promotions).  
   - Consistent dips in **Feb** and **June**.

2. **Trend Behavior**
   - Sales were steady from **2010–2014**, followed by a **clear upward growth trend post-2015**.  
   - Likely due to product or marketing expansion.

3. **Store & Product Insights**
   - **Store 4** had the highest total sales; **Store 3** had the lowest.  
   - **Product 7** was the top seller, while **Product 8** sold the least.

4. **Detected Anomalies**
   - Anomalies around **2012** and **2016** detected by both statistical and ML models.  
   - Ensemble approach produced **the most reliable results**, minimizing false positives.

---
