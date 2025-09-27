# 📊 Task 4: Aggregate Functions and Grouping

## 🎯 Objective
Use **aggregate functions** and **grouping** to summarize Ecommerce data.  
This task demonstrates `SUM`, `COUNT`, `AVG`, `MAX`, `MIN`, `GROUP BY`, and `HAVING`.

---

## 🛠 Tools
-  MySQL Workbench
- Database: `EcommerceDB`

---

## 📑 Queries

### 1. Total Amount Spent by Each Customer
```sql
SELECT c.Name, SUM(oi.Quantity * p.Price) AS Total_Spent
FROM Customers c
JOIN Orders o ON c.CustomerID = o.CustomerID
JOIN Order_Items oi ON o.OrderID = oi.OrderID
JOIN Products p ON oi.ProductID = p.ProductID
GROUP BY c.Name;
```

### 2. Number of Orders per Customer
```sql
SELECT c.Name, COUNT(o.OrderID) AS Order_Count
FROM Customers c
LEFT JOIN Orders o ON c.CustomerID = o.CustomerID
GROUP BY c.Name;
```

### 3. Average Quantity Ordered per Product
```sql
SELECT p.ProductName, AVG(oi.Quantity) AS Avg_Quantity
FROM Products p
JOIN Order_Items oi ON p.ProductID = oi.ProductID
GROUP BY p.ProductName;
```

### 4. Customers Who Spent More Than ₹50,000
```sql
SELECT c.Name, SUM(oi.Quantity * p.Price) AS Total_Spent
FROM Customers c
JOIN Orders o ON c.CustomerID = o.CustomerID
JOIN Order_Items oi ON o.OrderID = oi.OrderID
JOIN Products p ON oi.ProductID = p.ProductID
GROUP BY c.Name
HAVING SUM(oi.Quantity * p.Price) > 50000;
```

### 5. Most and Least Quantity Ordered per Product
```sql
SELECT p.ProductName,
       MAX(oi.Quantity) AS Max_Ordered,
       MIN(oi.Quantity) AS Min_Ordered
FROM Products p
JOIN Order_Items oi ON p.ProductID = oi.ProductID
GROUP BY p.ProductName;
```

---
# 📂 Files in This Repository

1. **Schema.sql** → Database schema (tables creation)
2. **Insert_data.sql** → Insert sample data
3. **Task4.sql** → Aggregate functions and grouping queries
4. **README.md** → Documentation


