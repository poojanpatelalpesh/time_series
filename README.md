##  A. Techniques, Tools, and Reasoning

###  Techniques Used

#### 1. Exploratory Data Analysis (EDA)
- Visualized **daily, monthly, and yearly** sales trends.
- <img width="561" height="567" alt="Screenshot 2025-11-02 at 12 15 51 AM" src="https://github.com/user-attachments/assets/187c344e-1aab-4f00-a172-bf08f4d8a8bb" />
- Examined store-level and product-level performance.
- <img width="455" height="390" alt="Screenshot 2025-11-02 at 12 16 49 AM" src="https://github.com/user-attachments/assets/c7cf8edb-be90-4e1c-98d5-ce6a80e8d890" />
<img width="570" height="331" alt="Screenshot 2025-11-02 at 12 17 11 AM" src="https://github.com/user-attachments/assets/b11c10cc-def8-4a5c-b627-f802d6b4dd96" />

- Used **STL decomposition** to separate trend, seasonality, and residuals.
- <img width="566" height="352" alt="Screenshot 2025-11-02 at 12 18 26 AM" src="https://github.com/user-attachments/assets/3dc9be50-9ad9-41a1-9559-bf89215f63da" />
- Used **Autocorrelation and stationarity**
- <img width="547" height="386" alt="Screenshot 2025-11-02 at 12 24 31 AM" src="https://github.com/user-attachments/assets/f84dad19-76e5-4660-94a2-2bac65b46ae9" />


#### 2. Statistical Approach – Z-Score Method
- Calculated **rolling mean** and **rolling standard deviation**.
- Flagged anomalies when sales deviated beyond **±2σ**.
- Simple yet effective for interpretable anomaly detection.

- <img width="531" height="238" alt="Screenshot 2025-11-02 at 12 19 47 AM" src="https://github.com/user-attachments/assets/98b9b5c0-62c9-4b18-958b-30c53a3ec35c" />




#### 3. Machine Learning Approach – Isolation Forest
- Identified anomalies through random partitioning of data.
- Handles **non-linear relationships** and **irregular patterns** effectively.

<img width="533" height="233" alt="Screenshot 2025-11-02 at 12 20 37 AM" src="https://github.com/user-attachments/assets/2bd70c1c-2d80-4edc-b94b-8d322f9f679f" />

#### 4. Hybrid Approach - combine Z-score and Isolation Forest anomalies
<img width="526" height="236" alt="Screenshot 2025-11-02 at 12 22 05 AM" src="https://github.com/user-attachments/assets/3f3dbb7e-b578-4714-8786-ae8ac44bf302" />


#### 5. Ensemble Approach
Combined multiple ML models to make anomaly detection more stable:
-  **Isolation Forest**  
-  **One-Class SVM**  
-  **Local Outlier Factor**  
-  **Elliptic Envelope**  
A data point is marked anomalous if **2 or more models** agree — reducing false positives.

<img width="530" height="270" alt="Screenshot 2025-11-02 at 12 22 23 AM" src="https://github.com/user-attachments/assets/d856b262-7941-435d-8c5d-467653ede5d7" />


#### 6. Visualization and Trend Analysis
- Used **STL Decomposition**, **Rolling Statistics**, and **ACF/PACF** plots.
- Overlaid anomalies on time-series graphs for clear interpretation.

- <img width="536" height="237" alt="Screenshot 2025-11-02 at 12 22 42 AM" src="https://github.com/user-attachments/assets/b5a60434-8ea4-41fc-9073-d65b2fe4ef9c" />


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
