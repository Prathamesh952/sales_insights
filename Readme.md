# 📊 Sales Analysis & SQL Dashboard

## 🔍 Reasons for Decline in Sales
In several regions, sales are dropping. Possible reasons:
1. Product Quality issues
2. Discounts not competitive
3. Weak Promotion / Advertising
4. Poor Product Attraction or Packaging

👉 Action: Identify low‑sales areas, check these points, and connect with the team for fixes.

---

## 📈 Dashboard Metrics
The dashboard should show:
- Total Revenue
- Total Sales Quantity
- Top 5 Products
- Top 5 Customers
- Revenue by Markets
- Sales Quantity by Markets

---

## 🗄️ SQL Queries for Analysis

### Customers

-- Show all customer records
SELECT * FROM customers;

-- Show total number of customers
SELECT COUNT(*) FROM customers;

-- Show transactions for Chennai market (Mark001)
SELECT * FROM transactions WHERE market_code = 'Mark001';

-- Show distinct product codes sold in Chennai
SELECT DISTINCT product_code FROM transactions WHERE market_code = 'Mark001';

-- Show transactions where currency is US dollars
SELECT * FROM transactions WHERE currency = 'USD';

-- Show transactions in 2020 (join with date table)
SELECT t.*, d.* 
FROM transactions t
INNER JOIN date d ON t.order_date = d.date
WHERE d.year = 2020;

-- Show total revenue in year 2020
SELECT SUM(t.sales_amount) 
FROM transactions t
INNER JOIN date d ON t.order_date = d.date
WHERE d.year = 2020 
AND (t.currency = 'INR' OR t.currency = 'USD');

-- Show total revenue in January 2020
SELECT SUM(t.sales_amount) 
FROM transactions t
INNER JOIN date d ON t.order_date = d.date
WHERE d.year = 2020 
AND d.month_name = 'January'
AND (t.currency = 'INR' OR t.currency = 'USD');

-- Show total revenue in 2020 for Chennai
SELECT SUM(t.sales_amount) 
FROM transactions t
INNER JOIN date d ON t.order_date = d.date
WHERE d.year = 2020 
AND t.market_code = 'Mark001';
