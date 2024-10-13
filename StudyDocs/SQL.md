### Types of SQL Commands (Subsets)
1. **DDL (Data Definition Language)**: Defines and modifies database structures.
   - Examples: `CREATE`, `ALTER`, `DROP`, `TRUNCATE`
   
2. **DML (Data Manipulation Language)**: Handles data within tables.
   - Examples: `INSERT`, `UPDATE`, `DELETE`
   
3. **DQL (Data Query Language)**: Retrieves data from the database.
   - Example: `SELECT`
   
4. **DCL (Data Control Language)**: Manages access and permissions.
   - Examples: `GRANT`, `REVOKE`
   
5. **TCL (Transaction Control Language)**: Manages database transactions.
   - Examples: `COMMIT`, `ROLLBACK`, `SAVEPOINT`

### Subqueries
A **subquery** is a query nested inside another SQL query. It is used to filter data and perform operations in a stepwise manner.

- **Types of Subqueries**:
  - **Single-row subqueries**: Returns a single row.
  - **Multi-row subqueries**: Returns multiple rows.
  - **Correlated subqueries**: Subquery references columns from the outer query.
  - **Nested subqueries**: Subqueries within subqueries.

### Constraints
Constraints enforce rules on data in a table to maintain data integrity.

- **Common Constraints**:
  - `NOT NULL`: Ensures that a column cannot have a NULL value.
  - `UNIQUE`: Ensures all values in a column are unique.
  - `PRIMARY KEY`: Combines `NOT NULL` and `UNIQUE` to uniquely identify each row.
  - `FOREIGN KEY`: Links two tables by enforcing referential integrity.
  - `CHECK`: Ensures that all values in a column meet a specified condition.
  - `DEFAULT`: Assigns a default value if none is provided.

### Joins
A **JOIN** is used to combine rows from two or more tables based on a related column.

- **Types of Joins**:
  - **INNER JOIN**: Returns only matching rows.
  - **LEFT JOIN**: Returns all rows from the left table and matched rows from the right table.
  - **RIGHT JOIN**: Returns all rows from the right table and matched rows from the left table.
  - **FULL OUTER JOIN**: Returns all matching and non-matching rows from both tables.
  - **CROSS JOIN**: Returns the Cartesian product of two tables.
  - **SELF JOIN**: Joins a table to itself.

### Key Types
1. **Primary Key**: Uniquely identifies each record in a table. Cannot be `NULL`.
2. **Unique Key**: Ensures that all values in a column are unique, but can have a single `NULL` value.
3. **Foreign Key**: A field that links one table to the primary key of another table.

### Indexes
An **index** is used to speed up the retrieval of rows from a table.

- **Types of Indexes**:
  - **Clustered Index**: Determines the physical order of data in the table. Only one per table.
  - **Non-Clustered Index**: Does not alter the physical order but creates a separate structure for quick lookups.
  - **Unique Index**: Ensures the uniqueness of values.

### Schema
A **schema** is a collection of database objects (tables, views, procedures) belonging to a single user.

### SQL Comment
SQL comments help annotate code for readability.

- **Single-line Comment**: `--`
- **Multi-line Comment**: `/* comment */`

### Common SQL Commands
- **Create a Table**:
  ```sql
  CREATE TABLE Employee (
      ID INT PRIMARY KEY,
      Name VARCHAR(50),
      Age INT,
      Department VARCHAR(50)
  );
  ```

- **Update a Table**:
  ```sql
  UPDATE Employee SET Age = 30 WHERE ID = 1;
  ```

- **Sort Records**:
  ```sql
  SELECT * FROM Employee ORDER BY Age DESC;
  ```

- **Select Common Records from Two Tables**:
  ```sql
  SELECT Employee.Name FROM Employee
  INTERSECT
  SELECT Department.Name FROM Department;
  ```

### Entities and Relationships
- **Entities**: Real-world objects (e.g., Employee, Department).
- **Relationships**: Connections between entities (e.g., One-to-Many, Many-to-Many).

### NULL Value
A **NULL** value indicates missing or unknown data. It’s different from zero or a blank space, as it represents the absence of a value.

### ORDER BY Default Data Ordering
The default order is **ascending (ASC)**. Use `DESC` for descending order.

### Difference Between Primary Key and Unique Key
- **Primary Key**: Only one per table, cannot have `NULL`.
- **Unique Key**: Can have multiple, allows a single `NULL` value.

### Order of Appearance in `SELECT` Query
1. `SELECT`
2. `FROM`
3. `WHERE`
4. `GROUP BY`
5. `HAVING`
6. `ORDER BY`

### Execution Order of `SELECT` Query
1. `FROM`
2. `WHERE`
3. `GROUP BY`
4. `HAVING`
5. `SELECT`
6. `ORDER BY`

### DELETE vs. TRUNCATE
- **DELETE**: Removes rows one by one and logs each deletion. Can use `WHERE`.
- **TRUNCATE**: Removes all rows quickly, without logging each row.

### `CASE` Function
Used for conditional logic in SQL.

```sql
SELECT Name, 
CASE 
  WHEN Age < 18 THEN 'Minor' 
  ELSE 'Adult' 
END AS AgeGroup 
FROM Employee;
```

### Clustered vs. Non-Clustered Indexes
- **Clustered Index**: Sorts data rows in the table based on the key.
- **Non-Clustered Index**: Creates a separate object that points to the data rows.

### Nested vs. Correlated Subqueries
- **Nested Subqueries**: Executed once for the parent query.
- **Correlated Subqueries**: Uses values from the outer query and executes for each row.

### Select Even or Odd Records
- **Even Records**:
  ```sql
  SELECT * FROM Employee WHERE ID % 2 = 0;
  ```
- **Odd Records**:
  ```sql
  SELECT * FROM Employee WHERE ID % 2 <> 0;
  ```

### Prevent Duplicate Records
Use `DISTINCT`:

```sql
SELECT DISTINCT Name FROM Employee;
```

### Insert Many Rows
```sql
INSERT INTO Employee (ID, Name, Age) VALUES (1, 'John', 30), (2, 'Jane', 25);
```

### Find Nth Highest Value
```sql
SELECT DISTINCT Salary 
FROM Employee 
ORDER BY Salary DESC 
LIMIT 1 OFFSET N-1;
```

### Find Values Starting with a Letter
```sql
SELECT * FROM Employee WHERE Name LIKE 'A%';
```

### Find Last ID in a Table
```sql
SELECT MAX(ID) FROM Employee;
```

### Select Random Rows
```sql
SELECT * FROM Employee ORDER BY RAND() LIMIT 1;
```


Sure! Here are some advanced SQL questions that dive deeper into complex queries, performance optimization, and database management:

### Advanced SQL Questions

1. **How would you optimize a query that involves multiple `JOIN` operations on large tables?**
   - Discuss strategies like using appropriate indexes, avoiding Cartesian joins, using `EXPLAIN` to understand execution plans, and breaking down complex joins into subqueries.

2. **What is the difference between `HAVING` and `WHERE` clauses? When should each be used?**
   - Explain how `HAVING` is used to filter aggregated results, while `WHERE` is used to filter rows before aggregation.

3. **Explain what a Common Table Expression (CTE) is and how it is different from subqueries.**
   - Discuss how CTEs use the `WITH` keyword to simplify complex queries and provide readability, especially for recursive queries.

4. **Write a query to find employees who have the second-highest salary in each department.**
   - Use window functions like `ROW_NUMBER()` or `DENSE_RANK()` partitioned by department.

   ```sql
   SELECT Department, Name, Salary
   FROM (
       SELECT Department, Name, Salary, 
              DENSE_RANK() OVER (PARTITION BY Department ORDER BY Salary DESC) AS Rank
       FROM Employee
   ) AS RankedEmployees
   WHERE Rank = 2;
   ```

5. **How would you implement a full outer join using `UNION` in databases that don’t support it natively?**
   - Use `LEFT JOIN` and `RIGHT JOIN` combined with `UNION`.

   ```sql
   SELECT * FROM TableA
   LEFT JOIN TableB ON TableA.ID = TableB.ID
   UNION
   SELECT * FROM TableA
   RIGHT JOIN TableB ON TableA.ID = TableB.ID;
   ```

6. **Explain what a materialized view is and how it differs from a regular view.**
   - Discuss how a materialized view stores query results physically, improving read performance at the cost of space and maintenance, whereas a regular view is a virtual table that doesn’t store data.

7. **What are window functions, and how would you use them to calculate a running total of sales?**
   - Introduce `SUM() OVER` and other window functions.

   ```sql
   SELECT OrderID, CustomerID, OrderAmount,
          SUM(OrderAmount) OVER (ORDER BY OrderDate) AS RunningTotal
   FROM Orders
   ORDER BY OrderDate;
   ```


**8. How would you identify and delete duplicate records from a table without using a temporary table?**
To delete duplicate records from a table without using a temporary table, you can use the `ROW_NUMBER()` window function to assign unique row numbers to duplicates and then delete based on these numbers.

#### Example:
```sql
WITH RankedEmployees AS (
    SELECT ID, 
           ROW_NUMBER() OVER (PARTITION BY Name, Department, Age ORDER BY ID) AS row_num
    FROM Employee
)
DELETE FROM Employee
WHERE ID IN (SELECT ID FROM RankedEmployees WHERE row_num > 1);
```

- **Explanation**:
  - `ROW_NUMBER()` assigns a unique rank (`row_num`) to each duplicate record based on `Name`, `Department`, and `Age`.
  - The `PARTITION BY` clause groups the records, and `ORDER BY ID` ensures consistent ordering.
  - The query deletes rows where `row_num` is greater than 1, keeping only the first occurrence.

**Explain indexing in detail. What factors should be considered when creating indexes?**
Indexes speed up data retrieval in a database by providing a quick lookup mechanism. However, they also increase storage size and can slow down insert and update operations. When creating indexes, consider:

- **Types of Indexes**:
  - **Single Column Index**: Indexes based on a single column.
  - **Composite Index**: Indexes based on multiple columns.
  - **Clustered Index**: Determines the physical order of data in the table. Only one clustered index per table.
  - **Non-Clustered Index**: Creates a separate structure for quick lookups. Multiple non-clustered indexes can exist per table.
  - **Covering Index**: An index that includes all columns needed for a query, avoiding the need to access the table.
  
- **Factors to Consider**:
  - **Selectivity**: High selectivity (many unique values) leads to more efficient indexes.
  - **Column Order**: For composite indexes, place the most selective columns first.
  - **Read vs. Write Trade-off**: Indexes speed up reads but slow down writes.
  - **Index Maintenance**: Regular updates and inserts require index re-balancing.

 **What are some pitfalls of using the `NOT IN` clause in subqueries, and how can you replace it with `NOT EXISTS` for better performance?**
- **Problem with `NOT IN`**:
  - `NOT IN` does not handle `NULL` values correctly. If the subquery contains even a single `NULL`, the entire `NOT IN` condition will return `false`.
  
- **Solution: Use `NOT EXISTS`**:
  - `NOT EXISTS` works better because it checks for the absence of rows without being affected by `NULL` values.

#### Example:
```sql
-- Using NOT IN (may cause issues if `ID` contains NULLs)
SELECT * FROM Employee WHERE ID NOT IN (SELECT ManagerID FROM Employee);

-- Replace with NOT EXISTS
SELECT * FROM Employee e WHERE NOT EXISTS (
    SELECT 1 FROM Employee m WHERE m.ManagerID = e.ID
);
```

**How would you design a database schema for handling hierarchical data (e.g., organizational charts)?**
- **Two Common Models**:
  1. **Adjacency List Model**: Each node has a `parent_id` field pointing to its parent.
  
     ```sql
     CREATE TABLE Employee (
         ID INT PRIMARY KEY,
         Name VARCHAR(100),
         ParentID INT,  -- References the manager or parent employee
         FOREIGN KEY (ParentID) REFERENCES Employee(ID)
     );
     ```
  
  2. **Nested Set Model**: Each node has `left` and `right` values defining its hierarchy.

     ```sql
     CREATE TABLE Employee (
         ID INT PRIMARY KEY,
         Name VARCHAR(100),
         Left INT,
         Right INT
     );
     ```
  
- **Query Example with Recursive CTE**:
   ```sql
   WITH RECURSIVE Subordinates AS (
       SELECT ID, Name, ParentID
       FROM Employee
       WHERE ParentID IS NULL
       UNION ALL
       SELECT e.ID, e.Name, e.ParentID
       FROM Employee e
       INNER JOIN Subordinates s ON e.ParentID = s.ID
   )
   SELECT * FROM Subordinates;
   ```

**What are `triggers` in SQL, and how would you use them to automatically update a log table whenever a record is inserted into a specific table?**
- **Trigger**: A database trigger is a special stored procedure that is automatically executed in response to certain events on a particular table (e.g., `INSERT`, `UPDATE`, `DELETE`).

#### Example of a Trigger:
```sql
CREATE TRIGGER LogInsertion
AFTER INSERT ON Employee
FOR EACH ROW
BEGIN
    INSERT INTO EmployeeLog (ID, Action, Timestamp)
    VALUES (NEW.ID, 'INSERTED', NOW());
END;
```

- **Explanation**:
  - `AFTER INSERT ON Employee`: Trigger activates after a new row is inserted into the `Employee` table.
  - `FOR EACH ROW`: Executes for each inserted row.
  - `NEW.ID`: Refers to the new row being inserted.

**How would you pivot a table in SQL to convert rows into columns?**
- Use the `PIVOT` clause (for databases like SQL Server) or `CASE` statements (for most SQL dialects).

#### Example Using `CASE`:
```sql
SELECT Department,
       SUM(CASE WHEN Gender = 'Male' THEN 1 ELSE 0 END) AS MaleCount,
       SUM(CASE WHEN Gender = 'Female' THEN 1 ELSE 0 END) AS FemaleCount
FROM Employee
GROUP BY Department;
```

**What is sharding, and how does it differ from partitioning? When would you use each technique?**
- **Sharding**: Splits data across multiple databases (horizontal scaling). Typically used for large-scale applications.
- **Partitioning**: Splits data within a single database (horizontal partitioning). Used to improve query performance by dividing tables into smaller pieces.

**Write a query to find gaps in a sequence of numbers in a table.**
- Use `LEAD()` or `LAG()` window functions to detect gaps.

```sql
SELECT ID + 1 AS MissingID
FROM Employee e
WHERE NOT EXISTS (
    SELECT 1 FROM Employee WHERE ID = e.ID + 1
);
```

**Difference Between OLTP and OLAP**
- **OLTP (Online Transaction Processing)**:
  - Used for transactional systems.
  - Schema is normalized for write efficiency.
  
- **OLAP (Online Analytical Processing)**:
  - Used for analytical systems (data warehouses).
  - Schema is denormalized for read efficiency.

**Create a Recursive CTE for Traversing a Hierarchy**
Use the `WITH RECURSIVE` clause:

```sql
WITH RECURSIVE Subordinates AS (
    SELECT EmployeeID, ManagerID, Name
    FROM Employee
    WHERE ManagerID IS NULL
    UNION ALL
    SELECT e.EmployeeID, e.ManagerID, e.Name
    FROM Employee e
    INNER JOIN Subordinates s ON e.ManagerID = s.EmployeeID
)
SELECT * FROM Subordinates;
```

**ACID Properties in SQL**
1. **Atomicity**: Ensures all parts of a transaction are completed successfully.
2. **Consistency**: Maintains database integrity before and after a transaction.
3. **Isolation**: Transactions do not interfere with each other.
4. **Durability**: Once committed, changes are permanent.

**How would you perform a cross-database query, and what are the challenges involved?**

- **Syntax**: Use fully qualified table names (`db1.schema1.Table`).
- **Example**:
  ```sql
  SELECT db1.dbo.TableA.col, db2.dbo.TableB.col
  FROM db1.dbo.TableA
  INNER JOIN db2.dbo.TableB ON db1.dbo.TableA.ID = db2.dbo.TableB.ID;
  ```

- **Challenges**:
  1. **Permissions**: Ensure appropriate access across databases.
  2. **Performance**: Cross-database joins can cause latency.
  3. **Schema Inconsistencies**: Handle mismatched data types.
  4. **Transaction Management**: Distributed transactions are complex.
  5. **Syntax Variations**: SQL syntax may differ across platforms.

**How would you handle schema changes in a production environment without downtime?**

- **Use Strategies**:
  1. **Backward-Compatible Changes**: Add new columns as `NULL` or `DEFAULT`.
  2. **Online Schema Change Tools**: Use `gh-ost`, `pt-online-schema-change`, or `pg_repack`.
  3. **Rolling Schema Updates**: Update schema in phases—Add, Migrate, Update Code, Remove.
  4. **Double-Writing**: Temporarily write to both old and new schema until stable.
  5. **Feature Flags**: Control new schema usage via flags.
  
- **Example**: For adding a new column:
  1. **Phase 1**: `ALTER TABLE Employee ADD COLUMN Department VARCHAR(100) NULL;`
  2. **Phase 2**: Migrate data and update app to use new column.
  3. **Phase 3**: Remove old column after verification.


