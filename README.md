# 📊 Sales Transactions Dashboard  


##  Project Overview  
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

##  Python – Data Cleaning & EDA  

###  Data Cleaning  
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

##  Exploratory Data Analysis (EDA)

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

- Electronics and Home Appliances are top revenue contributors.

- Sales spike on Fridays, aligning with consumer shopping patterns.

- January revenue > February revenue, showing seasonality effects.

- Customer base includes a small set of high-value clients.

#  Dashboard Previews & Interpretations
![Sales Transactions Performance](Sales%20Dashboard%20new.png)

## Key Metrics:

- Total Customers: 475

- Total Sales: $110K

- Net Quantity: 1,936

- Average Unit Price: $97

## Business Insights:

- Products: Electronics (21.9%) and Home Appliances (20.8%) drive revenue.

- Revenue Concentration: 76% from loyal/repeat customers → retention is key.

- Weekly Trend: Fridays are the strongest sales day.

- Monthly Trend: Revenue dipped from Jan ($32.2K) → Feb ($28.5K).

![Sales Transactions Performance](images/Sales%20Dashboard.png)

#  Drillthrough Dashboard – Home Appliances

## Key Metrics:

- Total Customers: 168

- Total Sales: $35K

- Net Quantity: 669

- Average Unit Price: $99

##Business Insights:

- Weekly Trend: Fridays and Mondays generate >$4K each.

- Revenue Concentration: 77% reliance on one group → risk of over-dependence.

- Seasonality: Sales rose in February → growth potential despite overall slowdown.

- Customer Drillthrough: Identifies high-value clients for targeted campaigns.

  ![Sales Transactions Performance](images/Sales%20Dashboard%20Drillthrough.png)

 #   Tools & Technologies

- Python (pandas, numpy, matplotlib, seaborn): Data cleaning & exploratory analysis

- Power BI Desktop: Data modeling, DAX measures, drillthrough dashboards

- Excel / CSV: Input dataset

#  Business Objectives Achieved

-  Build a clean ETL pipeline with Python
-  Perform EDA to guide visualization design
-  Develop interactive dashboards with drillthrough
-  Provide business insights for sales optimization

 #  Future Improvements

- Automate dataset refresh using Python + Power BI Service

- Expand drillthrough for Electronics & Furniture

- Integrate forecasting models (ARIMA, Prophet) for revenue prediction

- Develop a customer churn prediction model and visualize results in Power BI

#   Business Value

- Saves time through automated cleaning + reporting

- Provides data-driven insights for executives

- Identifies high-value customers and revenue concentration risks

- Demonstrates end-to-end analytics workflow (Python → Power BI)


 # Author

 **Duru Chukwuma**

 chukwuduru588@gmail.com

🔗 [LinkedIn](https://linkedin.com/in/chukwuma-duru)  
🔗 [Portfolio](https://www.datascienceportfol.io/chukwuduru588)

