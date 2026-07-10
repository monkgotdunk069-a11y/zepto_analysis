<img width="1129" height="849" alt="Screenshot 2026-07-11 010746" src="https://github.com/user-attachments/assets/e88d83b7-2934-4a70-8de3-63dcc354de98" />

# Zepto Product Analytics Dashboard

> A comprehensive data analytics project analyzing Zepto's product catalog - covering pricing, discounts, stock availability, and category performance using Python (EDA) and Power BI (Dashboard).

---

## Table of Contents

- [Project Overview](#project-overview)
- [Dataset Description](#dataset-description)
- [Tech Stack](#tech-stack)
- [Dashboard Preview](#dashboard-preview)
- [KPI Summary Cards](#kpi-summary-cards)
- [Business Questions Answered](#business-questions-answered)
  - [Q1: Products by Category](#q1-how-many-products-does-each-category-have)
  - [Q2: Category Distribution](#q2-how-are-products-distributed-across-categories)
  - [Q3: MRP vs Selling Price](#q3-what-is-the-relationship-between-mrp-and-selling-price)
  - [Q4: Average Discount by Category](#q4-which-category-offers-the-highest-average-discount)
  - [Q5: Top 10 Highest MRP Products](#q5-which-are-the-top-10-highest-mrp-products)
  - [Q6: Stock Status by Category](#q6-what-is-the-stock-status-across-each-category)
  - [Q7: Product Detail Table](#q7-what-does-the-full-product-detail-table-look-like)
- [Data Preprocessing and EDA (Python)](#data-preprocessing-and-eda-python)
- [Files in This Repository](#files-in-this-repository)
- [How to Run](#how-to-run)

---

## Project Overview

This project performs an end-to-end analysis of Zepto's product data. The goal is to derive meaningful business insights related to product categorization, pricing strategy, discount patterns, stock availability, and overall catalog health.

**Key Objectives:**
- Understand the distribution of products across 5 major categories
- Identify pricing patterns and discount strategies
- Monitor stock availability to flag out-of-stock products
- Highlight high-value products by MRP
- Provide an interactive, filterable Power BI dashboard for business stakeholders

---

## Dataset Description

| Column | Description |
|---|---|
| 
ame | Product name |
| mrp | Maximum Retail Price (in paise) |
| discountPercent | Discount percentage offered |
| vailableQuantity | Current stock quantity |
| discountedSellingPrice | Actual selling price after discount (in paise) |
| weightInGms | Product weight in grams |
| outOfStock | Boolean flag - True if out of stock |
| quantity | Packaged quantity unit |
| category | (Engineered Feature) Product category via keyword mapping |
| mrp_ruppees | MRP converted to Rupees (divided by 100) |
| discount_selling_price_ruppees | Selling price in Rupees (divided by 100) |

**Dataset Size:** 93 rows x 8 original columns (+ 3 engineered features)

**No missing values found in the dataset.**

**Categories (5 total):**

| Category | Count | Percentage |
|---|---|---|
| Vegetables | 34 | 36.56% |
| Fruits | 27 | 29.03% |
| Other | 21 | 22.58% |
| Leafy Greens | 9 | 9.68% |
| Frozen | 2 | 2.15% |

---

## Tech Stack

| Tool | Purpose |
|---|---|
| **Python** | Data Cleaning, Feature Engineering, EDA |
| **Pandas** | Data manipulation and analysis |
| **NumPy** | Numerical computations |
| **Matplotlib / Seaborn** | Exploratory visualizations |
| **Power BI** | Interactive dashboard creation |
| **Excel (.xlsx)** | Raw data source |

---

## Dashboard Preview

The dashboard was built in Power BI Desktop and includes:
- 8 KPI summary cards at the top
- 6 interactive visualizations
- 1 product detail data table
- Category slicer for filtering all visuals simultaneously

![Dashboard](https://raw.githubusercontent.com/your-username/zepto/main/assets/dashboard_preview.png)

> To view the dashboard interactively, open zepto_dashboard.pbix in Power BI Desktop.

---

## KPI Summary Cards

The top row of the dashboard shows 8 key metrics at a glance:

| KPI | Value | Description |
|---|---|---|
| **Total Products** | 93 | Total number of unique products in the catalog |
| **Total Categories** | 5 | Number of distinct product categories |
| **Avg Selling Price** | Rs. 39.84 | Average discounted selling price |
| **Avg MRP** | Rs. 47.01 | Average maximum retail price |
| **In Stocks** | 87 | Products currently available |
| **Avg Discount** | 15.46% | Average discount percentage across all products |
| **Out of Stocks** | 6 | Products currently unavailable |
| **Avg Avl Qty** | 2.96 | Average available quantity per product |

---

## Business Questions Answered

### Q1: How many products does each category have?

**Visual Type:** Horizontal Bar Chart
**Chart Title:** Products by Category

**Results:**

| Category | Product Count |
|---|---|
| Vegetables | 34 |
| Fruits | 27 |
| Other | 21 |
| Leafy Greens | 9 |
| Frozen | 2 |

**Insights:**
- Vegetables dominate the catalog with the most SKUs (34), making it Zepto's largest category.
- Frozen products are the most niche segment with only 2 products (Safal Frozen - Mixed Vegetables and Safal Frozen - Sweet Corn).
- The catalog is heavily skewed toward fresh produce — Vegetables and Fruits together account for 65.59% of all products.
- Leafy Greens and Frozen categories represent growth opportunities where Zepto can expand its product range.

---

### Q2: How are products distributed across categories?

**Visual Type:** Donut Chart
**Chart Title:** Category Distribution

**Results:**

| Category | Share |
|---|---|
| Vegetables | 36.56% |
| Fruits | 29.03% |
| Other | 22.58% |
| Leafy Greens | 9.68% |
| Frozen | 2.15% |

**Insights:**
- Over 65% of all products fall under Vegetables and Fruits — confirming Zepto's core focus on fresh produce.
- The "Other" category (22.58%) represents products that didn't fit neatly into the main 4 categories; this may include specialty or miscellaneous items.
- Leafy Greens and Frozen are underrepresented compared to their potential demand.
- This distribution suggests Zepto should consider expanding frozen and leafy green offerings.

---

### Q3: What is the relationship between MRP and Selling Price?

**Visual Type:** Scatter Plot
**Chart Title:** MRP VS Selling by Product
**Color Encoding:** By category (Frozen, Fruits, Leafy Greens, Other, Vegetables)

**Insights:**
- There is a strong positive linear correlation between MRP and selling price — higher MRP products maintain proportionally higher selling prices even after discounts.
- Fruits contain the most premium-priced products (upper-right quadrant), particularly varieties like Apple Royal Gala (MRP ~Rs.189), Apple Washington (~Rs.177), and Avocado Indian Premium (~Rs.177).
- Vegetables cluster in the mid-to-low price range (mostly below Rs.50 MRP).
- The consistent linear trend across all categories suggests a uniform discount policy (approximately 15-16%) is applied rather than selective deep discounting.
- A few Frozen products appear at elevated MRP points, indicating premium positioning for branded frozen goods.

---

### Q4: Which category offers the highest average discount?

**Visual Type:** Bar Chart
**Chart Title:** Average discount by Category

**Results:**

| Category | Average Discount % |
|---|---|
| Vegetables | ~16% |
| Leafy Greens | ~16% |
| Other | ~15% |
| Fruits | ~15% |
| Frozen | ~4% |

**Insights:**
- Vegetables and Leafy Greens receive the highest average discounts (~16%), likely to drive volume for perishable items that have a short shelf life.
- Frozen products have the lowest discount (~4%) — possibly because Safal-branded frozen products operate with a fixed/premium pricing model and do not need deep discounts to move inventory.
- Discount rates are remarkably consistent across fresh categories (Vegetables, Leafy Greens, Other, Fruits), all hovering around 15-16%, suggesting a centralized pricing policy.
- The large gap between Frozen (~4%) and all other categories (~15-16%) is a notable pricing anomaly worth investigating.

---

### Q5: Which are the Top 10 highest MRP products?

**Visual Type:** Horizontal Bar Chart
**Chart Title:** Top 10 Height MRP
**Metric:** Sum of mrp_ruppees

**Results:**

| Rank | Product | Approx MRP (Rs.) |
|---|---|---|
| 1 | Apple Royal Gala | ~189 |
| 2 | Apple Washington | ~177 |
| 3 | Avocado Indian Premium | ~177 |
| 4 | Safal Frozen - Sweet Corn | ~160 |
| 5 | Apple Kinnaur | ~142 |
| 6 | Apple Shimla | ~142 |
| 7 | Potato | ~35 |
| 8 | Bell Peppers Red and Yellow | ~35 |
| 9 | Safal Frozen - Mixed Vegetables | ~35 |
| 10 | (Others) | ~35 |

**Insights:**
- Premium apple varieties (Royal Gala, Washington, Kinnaur, Shimla) dominate the high-MRP segment — these are imported or premium quality variants.
- Avocado Indian Premium ranks among the most expensive products, reflecting its "farm-to-table" premium positioning as a domestic substitute for imported avocados.
- Safal Frozen Sweet Corn appears in the top 5 at ~Rs.160, showing that branded frozen products command high prices.
- The top 6 products (all above Rs.100) are well-separated from the remaining products, which cluster around Rs.35.
- These premium SKUs could be targeted for promotional campaigns to attract high-spending, health-conscious consumers.

---

### Q6: What is the stock status across each category?

**Visual Type:** Stacked Bar Chart
**Chart Title:** Stock Status By Category
**Color Encoding:** False = In Stock (dark teal), True = Out of Stock (beige/light)

**Results:**

| Category | In Stock | Out of Stock |
|---|---|---|
| Vegetables | ~32 | ~2 |
| Fruits | ~24 | ~3 |
| Other | ~20 | ~1 |
| Leafy Greens | ~9 | ~0 |
| Frozen | ~2 | ~0 |

**Overall: 87 in stock / 6 out of stock**

**Insights:**
- Overall stock health is strong — 87 out of 93 products (93.5%) are currently in stock.
- Fruits have the highest proportion of out-of-stock items (~3 products), which could signal demand exceeding supply for popular premium fruit varieties.
- Vegetables also have ~2 out-of-stock products, likely seasonal produce that experiences demand spikes.
- Leafy Greens and Frozen categories have 100% availability, suggesting reliable supply chains for these segments.
- Out-of-stock products should be escalated to the procurement team for immediate restocking review.
- Persistent out-of-stock in premium fruits could lead to customer churn to competitor apps.

---

### Q7: What does the full product detail table look like?

**Visual Type:** Data Table
**Chart Title:** Product details

**Columns displayed:**
- 
ame - Product name
- category - Product category
- mrp_ruppees - MRP in Rs.
- discountedSellingPrice - Selling price (in paise)
- discountPercent - Discount percentage
- vailableQuantity - Current stock

**Sample Data (first 9 rows, alphabetical by name):**

| Name | Category | MRP (Rs.) | Selling Price (Rs.) | Discount % | Qty |
|---|---|---|---|---|---|
| Amla | Other | 32 | 27 | 15 | 3 |
| Apple Kinnaur | Fruits | 142 | 119 | 16 | 6 |
| Apple Royal Gala | Fruits | 189 | 159 | 15 | 3 |
| Apple Shimla | Fruits | 142 | 119 | 16 | 3 |
| Apple Washington | Fruits | 177 | 149 | 15 | 3 |
| Avocado Indian Premium | Fruits | 177 | 149 | 15 | 3 |
| Baby Corn Peeled | Vegetables | 35 | 29 | 17 | 3 |
| Baby Potato | Vegetables | 19 | 16 | 15 | 3 |
| Banana Elaichi | Fruits | 58 | 49 | 15 | 3 |

**Insights:**
- The table allows detailed drill-down per product and works with the category slicer filter.
- Most products maintain an available quantity of 3 — suggesting a standard restocking threshold.
- Apple Kinnaur is notable for having quantity 6 (double the typical), which may indicate bulk supply availability.
- This table is most useful for procurement and operations teams for day-to-day inventory management.

---

## Data Preprocessing and EDA (Python)

The complete Python analysis is in 
otebook.ipynb. Here is a summary of the steps:

### Step 1: Import Libraries
`python
import pandas as pd
import numpy as np
import os
import matplotlib.pyplot as plt
import seaborn as sns
`

### Step 2: Load Data
`python
df = pd.read_excel(r'Zepto.xlsx')
df.head(10)
`

### Step 3: Basic Exploration
`python
print(df.shape)    # (93, 8)
print(df.info())   # Column types and null check
print(df.describe())  # Statistical summary
`

**Key Findings:**
- 93 products, 8 columns
- No missing values in any column
- MRP ranges from Rs.11 to Rs.189
- Discount ranges from 4% to 23%
- 6 products are out of stock (outOfStock = True)
- 87 products are in stock (outOfStock = False)

### Step 4: Unique Product Names
`python
df['name'].unique()  # 93 unique product names found
`

### Step 5: Feature Engineering - Category Column
`python
def categorize_product(name):
    name_lower = name.lower()
    if any(word in name_lower for word in ['onion', 'tomato', 'potato', 'carrot', 
           'beetroot', 'capsicum', 'broccoli', 'cauliflower', 'garlic', 'ginger', 
           'corn', 'bean', 'gourd']):
        return 'Vegetables'
    elif any(word in name_lower for word in ['coriander', 'mint', 'lettuce', 
             'curry', 'spinach', 'methi', 'basil', 'leaves']):
        return 'Leafy Greens'
    elif any(word in name_lower for word in ['banana', 'apple', 'orange', 'watermelon',
             'lemon', 'mango', 'papaya', 'pineapple', 'guava', 'pomegranate', 
             'avocado', 'coconut', 'dragon fruit']):
        return 'Fruits'
    elif any(word in name_lower for word in ['frozen', 'safal', 'zama']):
        return 'Frozen'
    else:
        return 'Other'

df['category'] = df['name'].apply(categorize_product)
print(df['category'].value_counts())
`

**Category Distribution:**
`
Vegetables      34
Fruits          27
Other           21
Leafy Greens     9
Frozen           2
`

### Step 6: Price Conversion (Paise to Rupees)
`python
df['mrp_ruppees'] = df['mrp'] / 100
df['discount_selling_price_ruppees'] = df['discountedSellingPrice'] / 100
`

### Step 7: EDA Visualizations

**7a. Category Distribution Bar Chart:**
`python
sns.countplot(x='category', data=df)
plt.title('Category Distribution')
plt.show()
`

**7b. Out of Stock Distribution:**
`python
df['outOfStock'].value_counts().plot(kind='bar')
plt.title('Out of Stock Distribution')
plt.show()
# Result: 87 in stock, 6 out of stock
`

**7c. Selling Price by Category (Box Plot):**
`python
# Shows price spread and outliers within each category
# Fruits has the highest price outliers
`

**7d. Discount Percentage Distribution (Histogram):**
`python
plt.hist(df['discountPercent'], bins=20, edgecolor='k')
plt.title('Distribution of Discount Percentage')
plt.show()
# Most products cluster around 15-16% discount
`

**7e. Selling Price Distribution (Box Plot):**
`python
sns.boxplot(x='discount_selling_price_ruppees', data=df)
# Outliers present - premium products pull the distribution right
`

**7f. Available Quantity Distribution:**
`python
# Most products have quantity = 3 (standard restocking level)
`

### Step 8: Export Cleaned Data
`python
df.to_excel('Zepto_cleaned.xlsx', index=False)
`

---

## Files in This Repository

`
zepto/
|
|-- README.md                  <- Project documentation (this file)
|-- Zepto.xlsx                 <- Raw dataset (93 products, 8 columns)
|-- Zepto_cleaned.xlsx         <- Cleaned & feature-engineered dataset (Power BI source)
|-- notebook.ipynb             <- Python EDA notebook (Jupyter)
|-- zepto_dashboard.pbix       <- Power BI Dashboard file
`

---

## How to Run

### Python EDA Notebook

1. Install required packages:
`ash
pip install pandas numpy matplotlib seaborn openpyxl jupyter
`

2. Launch Jupyter Notebook:
`ash
jupyter notebook
`

3. Open 
otebook.ipynb and run all cells sequentially (Cell > Run All)

### Power BI Dashboard

1. Download and install **Power BI Desktop** (free from Microsoft)
2. Open zepto_dashboard.pbix in Power BI Desktop
3. Use the **Category slicer** panel on the left to filter all visuals by category
4. Hover over any chart element for detailed tooltips
5. Click on chart bars/segments to cross-filter other visuals

---

## Author

**Nishant**
- Python EDA and Feature Engineering
- Power BI Dashboard Design and Development

---

## License

This project is created for educational and portfolio purposes.
