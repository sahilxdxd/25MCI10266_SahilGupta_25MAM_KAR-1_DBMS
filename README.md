# 25MCI10266_SahilGupta_25MAM_KAR-1_DBMS



```sql
CREATE TABLE Employees (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(50),
    manager_id INT,
    department VARCHAR(50),
    salary INT
);
```

### Insert Sample Values

```sql
INSERT INTO Employees VALUES
(1, 'Amit', NULL, 'Management', 120000),
(2, 'Ravi', 1, 'Engineering', 80000),
(3, 'Neha', 1, 'Engineering', 82000),
(4, 'Karan', 2, 'Engineering', 60000),
(5, 'Simran', 2, 'Engineering', 62000),
(6, 'Pooja', 3, 'Engineering', 61000),
(7, 'Rahul', 3, 'Engineering', 64000),
(8, 'Arjun', 1, 'HR', 70000);
```


## Question 1 Answer :

```sql
SELECT 
    e1.manager_id,
    e1.emp_name AS employee_1,
    e2.emp_name AS employee_2
FROM Employees e1
JOIN Employees e2
    ON e1.manager_id = e2.manager_id
    AND e1.emp_id < e2.emp_id
WHERE e1.manager_id IS NOT NULL;
```

### Output
![](images/1.png)

---

## Question 2 answer 

```sql
SELECT emp_name, salary
FROM Employees
WHERE salary = (
    SELECT MAX(salary)
    FROM Employees
    WHERE salary < (SELECT MAX(salary) FROM Employees)
);
```

