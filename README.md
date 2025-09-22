# 📊 Sales Transactions Dashboard  
[![Power BI](https://img.shields.io/badge/Tool-PowerBI-F2C811?logo=power-bi&logoColor=white)](https://powerbi.microsoft.com/) 
[![Python](https://img.shields.io/badge/Language-Python-3776AB?logo=python&logoColor=white)]()
[![EDA](https://img.shields.io/badge/Process-Exploratory%20Data%20Analysis-orange)]()
[![Data Analytics](https://img.shields.io/badge/Focus-Business%20Intelligence-blue)]()
[![Portfolio](https://img.shields.io/badge/Type-Data%20Analytics%20Portfolio-green)]()

---

## 📌 Project Overview  
This project demonstrates a **complete data analytics pipeline** that combines:  

1. **Python (pandas, numpy, matplotlib, seaborn):**  
   - Cleaning raw sales data  
   - Performing exploratory data analysis (EDA)  
   - Identifying trends, correlations, and outliers  

2. **Power BI:**  
   - Building relationships and DAX measures  
   - Creating interactive dashboards  
   - Enabling drillthrough functionality for product-level insights  

The solution consists of:  
- **Main Dashboard (Sales Transactions Performance):** High-level KPIs, product revenue, weekly and monthly sales trends.  
- **Drillthrough Dashboard (Home Appliances):** Focused deep dive into the performance of the Home Appliances category.  

---

## 🐍 Python – Data Cleaning & EDA  

### 🔹 Data Cleaning  
Steps taken before importing into Power BI:  
- Removed duplicates  
- Handled missing values (imputation using mean for unit prices)  
- Standardized column names  
- Exported a clean dataset for modeling  

```python
import pandas as pd  

# Load dataset  
df = pd.read_csv("sales.csv")  

# Drop duplicates  
df.drop_duplicates(inplace=True)  

# Handle missing values  
df.fillna({"UnitPrice": df["UnitPrice"].mean()}, inplace=True)  

# Standardize column names  
df.columns = df.columns.str.strip().str.lower().str.replace(" ", "_")  
df.head()  
```
[!Sales Dashboard](Sales%20python%20images/Sales%20dataset%20image(3).png)
🔹 Exploratory Data Analysis (EDA)

EDA was conducted to uncover early patterns before visualization in Power BI.
```
import matplotlib.pyplot as plt  
import seaborn as sns  

category_revenue = df.groupby("product_category")["revenue"].sum()  
sns.barplot(x=category_revenue.index, y=category_revenue.values)  
plt.title("Revenue by Product Category")  
plt.show()  
```
