# SQL Queries: Practice Your SQL Knowledge!

## Project Description

This project provides a comprehensive set of SQL queries designed to improve your skills across various levels of expertise, ranging from advanced to expert. Using a relational schema with tables such as `Customers`, `Orders`, `Products`, and more, these queries explore data manipulation, joins, aggregations, subqueries, window functions, and beyond. The dataset is inspired by a sample e-commerce database that includes customer orders, employee assignments, shipping details, and product information.

---

## Schema Overview

The database schema includes the following tables:
- **Customers:** Details of customers (e.g., `CustomerID`, `CustomerName`, `Country`).
- **Orders:** Information about customer orders (e.g., `OrderID`, `OrderDate`, `CustomerID`).
- **Products:** Product catalog with pricing details (e.g., `ProductID`, `ProductName`, `Price`).
- **Employees:** Employee information (e.g., `EmployeeID`, `LastName`, `FirstName`).
- **OrderDetails:** Details of products in each order (e.g., `OrderID`, `ProductID`, `Quantity`).
- **Shippers:** Shipping companies handling orders (e.g., `ShipperID`, `ShipperName`).

To set up the schema, use the **w3schools-database**:  
[Database Schema on GitHub](https://github.com/AndrejPHP/w3schools-database)

---

## Query Highlights

### **Advanced Level**
1. **Customer Orders:** Fetch all customer names alongside their respective orders.
   ```sql
   SELECT CustomerName, OrderID
   FROM customers c
   JOIN orders o
   ON c.CustomerID = o.CustomerID;

---
### **2. Orders with Shippers**
Retrieve orders along with the name of the shipping company:
```SELECT o.OrderID, shp.ShipperName
FROM orders o
JOIN shippers shp
ON o.ShipperID = shp.ShipperID;

---
### **3. Customer-Specific Orders**
```SELECT c.CustomerID, c.CustomerName, o.OrderID

FROM customers c
JOIN orders o
ON c.CustomerID = o.CustomerID
WHERE c.CustomerID > 50;

---
### **4. Employees with Large Orders**
```SELECT o.OrderID, e.EmployeeID, e.FirstName, e.LastName
FROM orders o
JOIN employees e
ON o.EmployeeID = e.EmployeeID
WHERE o.OrderID > 10400;

---
### Expert Level Queries
### **1. Most Expensive Product**

```SELECT ProductID, ProductName, Price
FROM products
ORDER BY Price DESC
LIMIT 1;

---
### **2. Second Most Expensive Product**
Retrieve the second most expensive product:
```SELECT ProductID, ProductName, Price
FROM products
ORDER BY Price DESC
LIMIT 1 OFFSET 1;

---
### **3. Customer Spending**
Find the customer who spent the most:
```SELECT c.CustomerID, c.CustomerName, SUM(od.Quantity * p.Price) AS TotalSpending
FROM orders o
JOIN customers c ON o.CustomerID = c.CustomerID
JOIN order_details od ON o.OrderID = od.OrderID
JOIN products p ON p.ProductID = od.ProductID
GROUP BY c.CustomerID
ORDER BY TotalSpending DESC
LIMIT 1;

---
### **4. Customer Spending in Canada**
Find the top spender in Canada:
```SELECT c.CustomerID, c.CustomerName, SUM(od.Quantity * p.Price) AS TotalSpending, c.Country
FROM orders o
JOIN customers c ON o.CustomerID = c.CustomerID
JOIN order_details od ON o.OrderID = od.OrderID
JOIN products p ON p.ProductID = od.ProductID
WHERE c.Country LIKE 'Canada'
GROUP BY c.CustomerID
ORDER BY TotalSpending DESC
LIMIT 1;

---
### **5. Total Value of Shipper Orders**
Calculate the total value of orders handled by each shipping company:
```SELECT o.ShipperID, shp.ShipperName, SUM(od.Quantity * p.Price) AS TotalValueOfOrder
FROM orders o
JOIN order_details od ON o.OrderID = od.OrderID
JOIN products p ON p.ProductID = od.ProductID
JOIN shippers shp ON shp.ShipperID = o.ShipperID
GROUP BY shp.ShipperID
ORDER BY TotalValueOfOrder DESC;

