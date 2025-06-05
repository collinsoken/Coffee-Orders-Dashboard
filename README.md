# Coffee-Orders-Dashboard

This read-me provides a comprehensive overview of the **Coffee Orders Excel Dashboard** project. It outlines the transformation of the raw data (`coffeeordersrawdata.xlsx`) into a dynamic and insightful dashboard (`coffeeordersproject.xlsx`). The document covers the steps taken for data cleaning, transformation, formula application, visualization, and a breakdown of the dashboard’s structure and features.

---

### **Project Description**

The **Coffee Orders Excel Dashboard** project analyzes coffee sales data to uncover trends, identify top customers, and visualize sales distribution by country and coffee type. The project transforms raw transactional data into a visually engaging, interactive dashboard that provides quick insights into sales performance and customer behavior.

![Screenshot 2025-06-05 154344](https://github.com/user-attachments/assets/d13a2892-dac8-44b3-986d-5b1f9b34ac92)

---

## **1. Data Transformation**

**Raw Data Overview:**

- The raw dataset contains detailed coffee order transactions, spread across three worksheets: `orders`, `customers`, and `products`.  
- The `orders` worksheet includes fields such as: Order ID, Order Date, Customer ID, Product ID, Quantity, and several initially empty columns like Customer Name, Email, Country, Coffee Type, Roast Type, Size, Unit Price, and Sales.  
- The `customers` worksheet includes: Customer ID, Customer Name, Email, Phone Number, Address Line 1, City, Country, Postcode, and Loyalty Card.  
- The `products` worksheet includes: Product ID, Coffee Type, Roast Type, Size, Unit Price, Price per 100g, and Profit.

**Columns Filled and Added to the `orders` Table:**

- **Filled Missing Column Data:** Used `INDEX` and `MATCH` functions nested in `IF` statements to extract missing data from the `customers` and `products` worksheets.  
- **Added Loyalty Card:** Populated the `Loyalty Card` column in `orders` by extracting it from the `customers` worksheet using `INDEX` and `MATCH`.  
- **Added Readable Names:** Created `Coffee Type Name` and `Roast Type Name` columns using `IF` statements to convert short codes (e.g., “Rob”) into full names (e.g., “Robusta”) for clearer reporting.  
- **Calculated Sales Field:** Computed the `Sales` value per order by multiplying `Quantity` by `Unit Price`.

---

## **2. Data Preparation and Cleaning**

**Data Cleaning Steps:**

- **Checking Duplicates:** Verified uniqueness of transactions by using Excel’s **Remove Duplicates** feature.  
- **Standardized Data Formats:**  
    - Converted `Order Date` into a standardized date format.  
    - Formatted `Size` entries into clearer units (e.g., "0.2" to "0.2kg").  
    - Applied currency formatting to `Unit Price`.

**Formulas and Functions Used:**

| Column/Field | Formula/Function Used | Purpose |
| :-- | :-- | :-- |
| Coffee Type Name | `=IF([@Coffee Type]="Rob","Robusta",IF([@Coffee Type]="Lib","Liberica",...))` | Map codes to full names |
| Roast Type Name | `=IF([@Roast Type]="M","Medium",IF([@Roast Type]="D","Dark",...))` | Map codes to full names |
| Sales | `=[@Quantity]*[@Unit Price]` | Calculate total sales per order |
| Customer Name to Loyalty Card | `=IF(INDEX(customers!$A$1:$I$1001,MATCH(orders!$C2,customers!$A$1:$A$1001,0),MATCH(orders!F$1,customers!$A$1:$I$1,0))=0,"",INDEX(customers!$A$1:$I$1001,MATCH(orders!$C2,customers!$A$1:$A$1001,0),MATCH(orders!F$1,customers!$A$1:$I$1,0)))` | Retrieve customer-related data from the `customers` worksheet |
| Coffee Type to Unit Price | `=IF(INDEX(products!$A$1:$G$49,MATCH(orders!$D2,products!$A$1:$A$49,0),MATCH(orders!J$1,products!$A$1:$G$1,0))=0,"",INDEX(products!$A$1:$G$49,MATCH(orders!$D2,products!$A$1:$A$49,0),MATCH(orders!J$1,products!$A$1:$G$1,0)))` | Retrieve product-related data from the `products` worksheet |

**Pivot Tables Created:**

- **Total Sales by Coffee Type and Month/Year:** Summarizes monthly and yearly sales by coffee type.  
- **Sales by Country:** Aggregates total sales per country.  
- **Top 5 Customers:** Identifies customers with the highest total sales.

---

## **3. Dashboard Creation**

**Charts and Visual Elements:**

- **Total Sales Chart:** Displays monthly sales trends by coffee type using a line or clustered column chart for easy comparison.  
- **Country Sales Chart:** Visualizes total sales per country, illustrating geographic distribution.  
- **Top 5 Customers Table:** Highlights the top five customers by total purchases, supporting targeted marketing or loyalty efforts.  
- **Timeline:** Allows users to filter the dashboard by date range interactively.  
- **Slicers:** Enables dynamic filtering based on Roast Type Name, Size, and Loyalty Card.

---

## **4. Summary of Key Steps**

- Cleaned and standardized raw data to ensure accuracy and consistency.  
- Added derived columns for better readability and analysis (e.g., full names and sales).  
- Used Excel functions (`IF`, `INDEX`, `MATCH`, multiplication) to automate value derivation and enable dynamic analysis.  
- Built pivot tables to summarize and group sales data across different dimensions.  
- Created interactive visual elements to highlight trends and key insights.  
- Applied formatting enhancements for a polished and professional dashboard presentation.

---

## **5. Files Included**

- **coffeeordersrawdata.xlsx:** Contains the original, unprocessed transactional data.  
- **coffeeordersproject.xlsx:** Includes the completed dashboard with cleaned data, added fields, pivot tables, and visualizations.

---
