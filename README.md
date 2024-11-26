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

**2. Orders with Shippers**
Retrieve orders along with the name of the shipping company:
```SELECT o.OrderID, shp.ShipperName
FROM orders o
JOIN shippers shp
ON o.ShipperID = shp.ShipperID;

**3. Customer-Specific Orders**

```SELECT c.CustomerID, c.CustomerName, o.OrderID
FROM customers c
JOIN orders o
ON c.CustomerID = o.CustomerID
WHERE c.CustomerID > 50;

