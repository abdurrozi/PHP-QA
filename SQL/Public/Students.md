Given the following data definition, write a query that returns the number of students whose first name is `John`.

``` sql
TABLE students
   id INTEGER PRIMARY KEY,
   firstName VARCHAR(30) NOT NULL,
   lastName VARCHAR(30) NOT NULL
```

<details><summary>Answer</summary>

``` sql
SELECT COUNT(*) FROM students
WHERE firstName = "John"
```

</details>
