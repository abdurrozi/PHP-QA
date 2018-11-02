The following data definition defines an organization's employee hierarchy.

An employee is a manager if any other employee has their managerId set to the first employees id. An employee who is a manager may or may not also have a manager.

``` sql
TABLE employees
  id INTEGER NOT NULL PRIMARY KEY
  managerId INTEGER REFERENCES employees(id)
  name VARCHAR(30) NOT NULL
```

Write a query that selects the names of employees who are not managers.

<details><summary>Answer</summary>

``` sql
SELECT name FROM employees 
WHERE id NOT IN (SELECT managerId FROM employees WHERE managerid IS NOT NULL);
```

</details>
