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
![Sales Dashboard](Sales%20python%20images/Sales%20dataset%20image(3).png)

## 🔹 Exploratory Data Analysis (EDA)

### EDA was conducted to uncover early patterns before visualization in Power BI.

```
# Cell 14 - plots (matplotlib)
plt.rcParams.update({'figure.max_open_warning': 0})

#  Bar: revenue by category
plt.figure(figsize=(10,5))
cats = category_summary['Product_Category']
vals = category_summary['total_revenue']
plt.bar(cats, vals)
plt.xticks(rotation=30, ha='right')
plt.title('Total Revenue by Product Category')
plt.ylabel('Total Revenue ($)')
plt.tight_layout()
plt.savefig('revenue_by_category.png')
plt.show()
```
![Sales Dashboard](Sales%20python%20images/Sales%20dataset%20image(2).png)

```
#  Histogram: unit price distribution
plt.figure(figsize=(7,4))
plt.hist(df['Unit_Price'].dropna(), bins=30)
plt.title('Unit Price Distribution')
plt.xlabel('Unit Price ($)')
plt.tight_layout()
plt.savefig('unit_price_hist.png')
plt.show()
```
![Sales Dashboard](Sales%20python%20images/Sales%20dataset%20image(1).png)
## EDA Insights:

**-Electronics and Home Appliances are top revenue contributors.**

**-Sales spike on Fridays, aligning with consumer shopping patterns.**

* January revenue > February revenue, showing seasonality effects.

* Customer base includes a small set of high-value clients.

**Dashboard Preview**
![Sales Transactions Performance](Sales%20Dashboard%20new.png)
