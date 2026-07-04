# Zepto E-commerce SQL Data Analysis

A comprehensive SQL data analysis project on e-commerce inventory management. This project demonstrates exploratory data analysis, data cleaning, and business intelligence workflows using real-world e-commerce data.

## Project Overview

This project analyzes a Zepto e-commerce inventory dataset to extract meaningful insights about product pricing, inventory management, and revenue optimization. The analysis covers:

- **Database Design & Setup**: Creating normalized schemas for e-commerce inventory data
- **Exploratory Data Analysis (EDA)**: Understanding data structure, distributions, and anomalies
- **Data Cleaning & Validation**: Handling missing values, inconsistent pricing, and data quality issues
- **Business Analytics**: Deriving actionable insights on pricing strategy, stock management, and category performance

## Dataset

The dataset contains Zepto e-commerce inventory information with the following fields:

| Column | Description |
|--------|-------------|
| sku_id | Unique product identifier |
| name | Product name |
| category | Product category (Fruits, Snacks, Beverages, etc.) |
| mrp | Maximum Retail Price in rupees |
| discountPercent | Applied discount percentage |
| discountedSellingPrice | Final selling price after discount |
| availableQuantity | Current stock quantity |
| weightInGms | Product weight in grams |
| outOfStock | Stock availability flag |
| quantity | Units per package |

**Data Source**: [Kaggle - Zepto Inventory Dataset](https://www.kaggle.com/datasets/palvinder2006/zepto-inventory-dataset/)

## Project Structure

```
├── Zepto_SQL_data_analysis.sql    Main SQL analysis queries
├── zepto_v2.csv                   Dataset CSV file
├── LICENSE                        MIT License
└── README.md                      This file
```

## Getting Started

### Prerequisites
- PostgreSQL 12+
- pgAdmin or any PostgreSQL client
- CSV data file (zepto_v2.csv)

### Setup Instructions

1. **Create Database & Table**
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
   ```

2. **Import Data**
   ```sql
   \copy zepto(category,name,mrp,discountPercent,availableQuantity,
            discountedSellingPrice,weightInGms,outOfStock,quantity)
   FROM 'zepto_v2.csv' WITH (FORMAT csv, HEADER true, DELIMITER ',', QUOTE '"', ENCODING 'UTF8');
   ```

3. **Run Analysis**
   - Execute queries from `Zepto_SQL_data_analysis.sql`
   - Explore and modify queries as needed

## Key Analysis Areas

### 1. Data Quality Assessment
- Null value detection and handling
- Duplicate record identification
- Data type validation

### 2. Pricing Analysis
- Best-value products by discount
- Price per gram calculations
- Category-wise pricing trends
- MRP vs selling price inconsistencies

### 3. Inventory Management
- Stock availability distribution
- Category-wise inventory levels
- Weight-based product grouping
- Out-of-stock product identification

### 4. Revenue Insights
- Estimated revenue by category
- Product performance ranking
- Discount impact analysis
- High-value product identification

## Usage

Open `Zepto_SQL_data_analysis.sql` in your PostgreSQL client and run the queries section by section to understand the data and extract insights.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

You are free to use, modify, and distribute this project for personal or commercial purposes.

## Notes

- Product names may appear multiple times representing different SKUs (different sizes, weights, or packages)
- Original pricing data in paise has been converted to rupees
- Some products may have pricing inconsistencies that are flagged during cleaning
- Analysis assumes data freshness relative to Zepto's actual current inventory
