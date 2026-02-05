# 📊 Sales Performance & Channel Behavior Analysis
Hello! In this project, I demonstrate an end-to-end Business Intelligence workflow. We transition from a raw, disorganized dataset to a professional Power BI dashboard, utilizing Excel Power Query for the ETL process and Power BI for advanced modeling and visualization.

## 🖼️ Dashboard Preview
![dashboard](/Images/final.png)

## 🔍 Data Exploration: Identifying the "Mess"
The initial dataset was highly unstructured and unreliable for direct reporting. Upon exploring the data, I identified several critical issues that required deep cleaning:

- Duplicates: Multiple identical entries recorded during data entry.

- Missing Data: null values, empty strings, and "n/a" entries in Sales_Rep, Region, and Sales_Amount.

- Whitespace & Casing: Leading/trailing spaces in Product_Category and inconsistent casing (UPPER/lower) in Sales_Channel.

- Data Type Errors: Numeric columns contained text strings like "ERROR_99".

- Invalid Values: Negative numbers in the Quantity_Sold column.

- Date Standardization: Mixed date formats (e.g., YYYY-MM-DD, M/D/YYYY, YYYY.MM.DD, and Mon-YY).

- Column Splitting: The Region_and_Sales_Rep column used inconsistent delimiters (- and |).

![image](/Images/1.png)

## ⚙️ ETL Pipeline: Data Cleaning via Power Query
I built a robust data-cleaning pipeline using Excel Power Query to create a clean fact_table, ensuring the original dataset remained untouched for audit purposes.

![image](/Images/2.png)

### 🔹 Step 1: Import and Initial Cleanup
Remove Duplicates: Selected all columns and used Remove Rows > Remove Duplicates.

Handle "n/a" Values: Replaced n/a in the Region column with blank values (null).

### 🔹 Step 2: Text Formatting
Trim Whitespace: Applied Format > Trim to Product_Category and Sales_Rep.

Fix Casing: Standardized the Sales_Channel column using Format > Capitalize Each Word.

### 🔹 Step 3: Fixing Numeric Data & Structural Cleanup
Addressing Sales Inconsistency: Upon audit, the original Sales_Amount column was found to be mathematically inconsistent with Unit Price and Quantity. To maintain data integrity and prevent misleading reports, I removed the original Sales column and shifted the focus to Net Profit and Volume metrics.

Handle Errors: Replaced "ERROR_99" results with null.

Correct Negatives: Used a Conditional Column for Quantity_Sold: If value < 0, then 0, else use original column value.

### 🔹 Step 4: Standardizing Dates
Date Conversion: Converted Sale_Date to Date type. Used Locale settings to correctly parse mixed international date formats.

### 🔹 Step 5: Structural Fixes & Normalization
Split Combined Column: Split Region_and_Sales_Rep twice using both - and | as delimiters.

Merge & Cleanup: Merged the resulting split columns for Sales_Rep_Clean to eliminate nulls.

**Final Table Structure:** Removed the original redundant Region and Sales_Rep columns, using the new cleaned versions for a leaner model.

![image](/Images/3.png)

## 📅 Time Intelligence: Date Dimension Table
To unlock advanced time-based filtering (Months, Quarters, Weeks), I created a dedicated Date Dimensional Table.

![image](/Images/4.png)

## 🧬 Data Modeling
Once the cleaning was finished in Power Query, I moved to Power BI to establish the analytical relationships.

Connection: Established a relationship between date_dim_table[Sale_Date] and fact_table[Sale_Date].

![image](/Images/5.png)

## ❓ Stakeholder Question & Answer
### 🧠 Stakeholder Context

The operations and sales leadership wanted to better understand channel behavior, not just raw sales numbers. Specifically, they were concerned about whether each channel was building long-term customer value or simply relying on one-time transactions.

### 📣 Stakeholder Question

**Are we more dependent on new customers in Online or Retail?
And which channel is actually driving sustainable profitability?**

### 📊 Data-Driven Findings

Using the finalized Power BI dashboard, several key insights emerged:

- Customer Retention:
The overall retention rate sits at 50%, indicating a balanced mix of new and returning customers across the business.

- Retail Channel Behavior:
Retail shows an almost 1:1 ratio of New (≈6.5K) to Returning Customers (≈6.4K).
This suggests that physical stores are successfully driving repeat purchases, not just walk-in traffic.

- Online Channel Behavior:
Online attracts slightly more new customers, but has a lower proportion of returning customers compared to Retail.
This indicates stronger acquisition performance, but weaker long-term loyalty.

- Profitability Comparison:

> Online generates higher total sales (~30.1M) and higher net profit (~3.27M)

> Retail follows closely with ~29.4M in sales and ~3.21M in net profit

> While both channels are profitable, Online is the more efficient profit driver, whereas Retail excels in customer retention.

### 📌 Recommendation to Stakeholders

- Introduce returning-customer incentives in Retail to further strengthen loyalty.

- Continue leveraging Online for high-margin sales and customer acquisition.

- Treat the two channels as complementary, not competing—each serves a distinct business goal.

## 🌟 Skills Showcased
- ETL (Extract, Transform, Load): Mastering Power Query to automate the cleaning of highly inconsistent data.

- Data Integrity Auditing: Identifying and removing corrupt metrics (Sales column) to ensure report accuracy.

- Data Modeling: Designing a Star Schema for efficient calculation and filtering.



- Business Storytelling: Framing data to answer high-level stakeholder strategic questions.

## 🛠️ Tools Used
- Microsoft Excel: Data exploration and source file management.

- Excel Power Query (ETL): Building a repeatable cleaning pipeline and data transformation.

- Power BI Desktop: Data modeling, DAX measure creation, and interactive report design.

- VS Code: Project documentation and Markdown management.

## 🏁 Conclusion
This project proves that the value of Business Intelligence lies in the quality of the data, not just the visuals. By identifying and removing corrupted metrics and cleaning complex structural errors in Power Query, I created a dashboard that stakeholders can actually trust.

We moved from a "broken" spreadsheet to a strategic tool that measures Profit, Quantity, and Customer Loyalty with 100% accuracy.