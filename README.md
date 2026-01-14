## 📌 Project Objective

The objective of this project is to replicate real-world data analysis tasks performed in the e-commerce domain using SQL. It focuses on transforming raw inventory data into meaningful business insights by applying structured querying and analytical thinking.

Through this project, SQL is used to:
- Create and manage an e-commerce inventory database
- Perform Exploratory Data Analysis (EDA) to understand product distribution, pricing, and stock status
- Clean and standardize raw data by handling missing values, invalid entries, and unit inconsistencies
- Generate business-oriented insights related to inventory management, discounts, pricing strategies, and revenue estimation

---

## 📁 Dataset Description

The dataset used in this project is sourced from Kaggle and was originally scraped from Zepto’s product listings. It closely reflects real-world e-commerce catalog data.

Each row represents a unique Stock Keeping Unit (SKU). Duplicate product names may appear due to differences in packaging, weight, pricing, discounts, or category placement, which is common in large-scale e-commerce systems.

### Dataset Columns
- **sku_id** – Unique identifier for each SKU (primary key)
- **name** – Product name as listed on the platform
- **category** – Product category
- **mrp** – Maximum Retail Price (converted to ₹)
- **discountPercent** – Discount percentage applied on MRP
- **discountedSellingPrice** – Final selling price after discount (₹)
- **availableQuantity** – Quantity available in inventory
- **weightInGms** – Product weight in grams
- **outOfStock** – Boolean indicator of stock availability
- **quantity** – Units per package or grams (for loose items)

---

## 🔧 Project Workflow

### 1️⃣ Database & Table Creation

```sql
CREATE TABLE zepto (
  sku_id SERIAL PRIMARY KEY,
  category VARCHAR(120),
  name VARCHAR(150) NOT NULL,
  mrp NUMERIC(8,2),
  discountPercent NUMERIC(5,2),
  availableQuantity INTEGER,
  discountedSellingPrice NUMERIC(8,2),
  weightInGms INTEGER,
  outOfStock BOOLEAN,
  quantity INTEGER
);
### 3️⃣ Exploratory Data Analysis (EDA)

Initial exploration was performed to understand the structure and quality of the dataset:

1.Total record count
2.Sample data inspection
3.Null value analysis across columns
4.Identification of unique product categories
5.Comparison of in-stock vs out-of-stock items
6.Detection of products appearing under multiple SKUs

### 4️⃣ Data Cleaning

1.To ensure accurate analysis, the following cleaning steps were applied:
2.Removal of records with zero MRP or zero selling price
3.Conversion of price-related columns from paise to rupees

### 5️⃣ Business Insights

1.SQL queries were written to answer key business questions, including:
2.dentification of top products based on discount percentage
3.High-MRP products that are currently out of stock
4.Estimated revenue contribution by product category
5.Premium products (MRP > ₹500) with minimal discounts
6.Categories offering the highest average discounts
7.Price-per-gram analysis to determine value-for-money products
8.Product segmentation based on weight (Low, Medium, Bulk)
9.Total inventory weight by category
