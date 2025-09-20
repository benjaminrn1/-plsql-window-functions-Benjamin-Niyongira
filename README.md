# 📘 README – Database Development with PL/SQL

## 👥 BENJAMIN NIYONGIRA

---

## 📌 Project Overview

This project demonstrates advanced analytical capabilities in Oracle **PL/SQL** using window functions to solve complex business problems related to coffee sales data analysis. The implementation focuses on deriving actionable insights from transactional data using five key analytical techniques

Our main tasks were:

1. Create tables with constraints.
2. Insert sample data.
3. Finding Top 5 products per region/quarter using RANK
4. Showing Running monthly sales totals using SUM() and  OVER()
5. Finding Month-over-month growth using LAG()/LEAD()
6. Customer quartiles → NTILE(4)
7.  3-month moving averages → AVG() OVER()

---

## 🗄 Database Design

We created four tables:

1. **Customers** – stores customers information
2. **Products** – stores products detail
3. **Transaction** – stores transaction made


### Constraints applied:

* **PRIMARY KEY**: `customer_id`, `product_id`, `transaction_id`
* **FOREIGN KEY**: links  Transaction to customers & product
* **NOT NULL**: mandatory fields like `customer_id`, `product_id`

![Inserting Data](relationship.PNG)

---

## 🔍 Queries

### ✔ Table Creation

Implemented using **CREATE TABLE** with constraints.
Example:

```sql
CREATE TABLE products (
    product_id NUMBER PRIMARY KEY,
    name VARCHAR2(100),
    category VARCHAR2(50),
    price_per_kg NUMBER
);
```
creation of all tables 
![Inserting Data](creating%20tables.PNG)

### ✔ Sample Data Insertion

Data was added for testing using **INSERT INTO**.

![Inserting Data](inserting%20data.PNG)

**Product table**
![Inserting Data](product%20table.PNG)

**Customer table**
![Inserting Data](customer%20table.PNG)

**Transaction table**
![Inserting Data](transaction%20table.PNG)

### ✔ task we did

We tested:

* **RANK()** → Assigns ranks within each partition (region/quarter).
  
This SQL query analyzes sales performance to identify the top 5 best-selling products in each region for each quarter

![Inserting Data](Top%205%20Products%20per%20Region.PNG)
  
* **LEFT JOIN** → shows all employees, even without projects.
* **RIGHT JOIN** → shows all projects, even without employees.
* **FULL JOIN** → shows all employees & projects with or without assignments.

### ✔ Index

Example:

```sql
CREATE INDEX idx_emp_email ON Employees(email);
```

### ✔ View

Example:

```sql
CREATE VIEW EmployeeProjectDetails AS
SELECT e.first_name, e.last_name, p.project_name, a.role
FROM Employees e
INNER JOIN Assignments a ON e.emp_id = a.emp_id
INNER JOIN Projects p ON a.project_id = p.project_id;
```

---

## 📊 Results

* The database schema is **normalized** and supports many-to-many employee-project relationships.
* **Joins** allow flexible data queries across multiple tables.
* **Indexes** improve performance for searches (e.g., by email).
* **Views** simplify repeated queries by providing a logical “shortcut” to complex joins.

---

## ✅ How to Run

1. Copy all `CREATE TABLE` queries into your SQL environment.
2. Insert the sample data.
3. Run the join queries to test relationships.
4. Create the index and view as shown.
5. Use the view (`SELECT * FROM EmployeeProjectDetails;`) to see summarized results.

---

