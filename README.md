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
**The Scenario:** A stakeholder wanted a deep dive into the performance and behavior of our different selling platforms.

### Stakeholder Question:
"I want insights on channel behavior. Specifically, I need to know what each channel is like in terms of customer loyalty. Are we actually building a base in our physical stores, or are they just one-time walk-ins?"

### My Data-Driven Answer:
Based on the dashboard analysis, we can see that our physical stores are actually powerhouses for loyalty. Here is the breakdown:

Retail Customer Base: In our Retail channel, we have 6.5k New Customers and 6.4k Returning Customers. This nearly 1:1 ratio is incredible—it proves that for almost every person who walks in for the first time, another is coming back for a second visit.

Profitability: We are generating $6.65M in Total Net Profit, and while Retail is excellent for loyalty, the Online channel is where we see our highest profit efficiency.

Volume: We have successfully moved 26k units, with a total Retention Rate of 50% across the board.

**My Recommendation:** Since we have such a strong balance in Retail (6.5k vs 6.4k), we should launch a 'Returning Customer' discount in Retail to push that 6.4k higher, while continuing to use the Online channel as our primary profit driver.

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