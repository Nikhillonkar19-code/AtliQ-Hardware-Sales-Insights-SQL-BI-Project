
# 📊 AtliQ Hardware Sales Insights — Power BI + MySQL

[![Live Dashboard](https://img.shields.io/badge/View-Live%20Dashboard-blue?style=for-the-badge&logo=powerbi)](https://app.powerbi.com/view?r=eyJrIjoiYWIxODg5YjMtZDUwNS00OGI5LTljMzgtMjE3NjZjNzdjNWNlIiwidCI6IjNiYTNhODMxLTFkMzItNDA4My1hMzBjLWQ0YTk0NGYzNWI3ZSJ9)

An **end-to-end data analytics project** delivering actionable sales insights for **AtliQ Hardware**, a leading Indian hardware supplier.  
This project leverages **MySQL** for data storage, **Power BI** for visualization, and **DAX** for KPI calculations.

---

## 📝 Project Overview
**AtliQ Hardware** supplies computer hardware & peripherals to major retail chains across India.  
The sales director faced challenges:
- Sales performance updates were **verbal** and **inconsistent**.
- No **centralized dashboard** to track performance by region/product/customer.
- **Declining sales** in a competitive market.

**Goal:**  
Build an **interactive Power BI dashboard** connected to MySQL to provide **real-time, data-driven insights**.

---

## 🎯 Business Problem
The Sales Director needed:
- A **clear view** of sales trends vs. last year.
- Market, product, and customer **performance breakdown**.
- Eliminate **manual reporting** and delays.
- Support **faster decision-making** with factual data.

---

## 🛠 Process & Methodology

### 1️⃣ Data Discovery & Planning — **AIMS Grid**
| **Element**       | **Details** |
|-------------------|-------------|
| **Purpose**       | Unlock hidden sales insights and automate reporting. |
| **Stakeholders**  | Sales Director, Marketing, Customer Service, Analytics, IT. |
| **End Result**    | Automated, real-time dashboard for strategic decision-making. |
| **Success Criteria** | 10% cost savings, 20% time saved in reporting. |

---

### 2️⃣ Data Extraction (MySQL)
- Imported **`db_dump.sql`** into **MySQL Workbench**.
- Tables analyzed: `customers`, `transactions`, `markets`, `products`, `date`.
- Example Query:
```sql
-- Total revenue for 2020
SELECT SUM(sales_amount)
FROM sales.transactions
JOIN sales.date 
ON transactions.order_date = date.date
WHERE year = 2020;
````

---

### 3️⃣ Data Cleaning (Power Query)

* Removed **null** and **duplicate** entries in `markets` table.
* Filtered **negative & zero** sales values.
* Converted **USD to INR**:

```m
if [currency] = "USD" then [sales_amount] * 75 else [sales_amount]
```

---

### 4️⃣ Data Modeling (Star Schema)

**Fact Table:**

* `transactions` — transaction\_id, sales\_amount, sales\_qty, market\_code, product\_code

**Dimension Tables:**

* `date` — date, month, year
* `customers` — customer\_code, customer\_name, region
* `products` — product\_code, product\_name, category
* `markets` — market\_code, market\_name, zone

---

### 5️⃣ Data Analysis (DAX Measures)

```DAX
Revenue = SUM('sales transactions'[sales_amount])
Revenue LY = CALCULATE([Revenue], SAMEPERIODLASTYEAR('sales date'[date]))
Profit Margin % = DIVIDE([Total Profit Margin], [Revenue], 0)
Sales Quantity = SUM('sales transactions'[sales_qty])
```

---

### 6️⃣ Dashboard Features

* **Revenue Trend Analysis** (YoY comparison)
* **Top Performing Products**
* **Market & Region Insights**
* **Customer Contribution Analysis**
* **Profit Margin Tracking**

---

## 📷 Dashboard Preview

### 📌 Key Insights
![Key Insights](https://github.com/Nikhillonkar19-code/AtliQ-Hardware-Sales-Insights-SQL-BI-Project/blob/main/Atliq%20Hardware_page-Key%20Insights.jpg)

### 📌 Performance Insights
![Performance Insights](https://github.com/Nikhillonkar19-code/AtliQ-Hardware-Sales-Insights-SQL-BI-Project/blob/main/Atliq%20Hardware_page-Performance%20insights.jpg)

### 📌 Profit Analysis
![Profit Analysis](https://github.com/Nikhillonkar19-code/AtliQ-Hardware-Sales-Insights-SQL-BI-Project/blob/main/Atliq%20Hardware_page-Profit%20Analysis.jpg)


---

## 🔗 Live Dashboard Link

[**Click Here to View Dashboard**](https://app.powerbi.com/view?r=eyJrIjoiYWIxODg5YjMtZDUwNS00OGI5LTljMzgtMjE3NjZjNzdjNWNlIiwidCI6IjNiYTNhODMxLTFkMzItNDA4My1hMzBjLWQ0YTk0NGYzNWI3ZSJ9)

---

## 🛠 Tools & Technologies Used

* **MySQL** — Data Storage & Extraction
* **Power BI** — Data Visualization
* **Power Query** — Data Cleaning & ETL
* **DAX** — Measures & Calculations

---

## 👨‍💻 Author

**Nikhil Lonkar**
📌 [LinkedIn](https://linkedin.com/in/nikhil-lonkar-0436a1338)
📌 [GitHub](https://github.com/Nikhillonkar19-code)




