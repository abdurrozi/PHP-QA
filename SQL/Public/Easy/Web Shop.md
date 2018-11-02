Each item in a web shop belongs to a seller. To ensure service quality, each seller has a rating.

The data are kept in the following two tables:

``` sql
TABLE sellers
  id INTEGER PRIMARY KEY,
  name VARCHAR(30) NOT NULL,
  rating INTEGER NOT NULL
``` 

``` sql
TABLE items
  id INTEGER PRIMARY KEY,
  name VARCHAR(30) NOT NULL,
  sellerId INTEGER REFERENCES sellers(id)
``` 

Write a query that selects the item name and the name of its seller for each item that belongs to a seller with a rating greater than `4`.

<details><summary>Answer</summary>

``` sql
SELECT 
    items.name as Item,
    sellers.name as Seller
FROM items
LEFT OUTER JOIN sellers
ON items.sellerId = sellers.id
WHERE sellers.rating > 4
```

</details>
