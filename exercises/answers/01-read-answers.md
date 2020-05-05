# Read Exercises

These exercises all require you to read data from the `products` table.

1. Write a query to get Product name and quantity per unit

  ```
  SELECT 
    product_name, quantity_per_unit
  FROM
    products;
  ```

1. Write a query to get a list of current products (id and name)

  ```
  SELECT 
    product_name, quantity_per_unit
FROM
    products
WHERE
	discontinued = 0;
  ```

1. Write a query to get a list of discontinued products (id and name)

  ```
  SELECT 
    product_name, quantity_per_unit
FROM
    products
WHERE
	discontinued = 1;
  ```

1. Write a query to get the name and price of the most expensive product

  ```
  SELECT 
	product_name,
    list_price
FROM
    products
WHERE
	list_price = (SELECT MAX(list_price) from products);
  ```

1. Write a query to get the name and price of the least expensive product

SELECT 
	product_name,
    list_price
FROM
    products
WHERE
	list_price = (SELECT MIN(list_price) from products);

1. Write a query to get a list of products that cost less than $20

```
SELECT 
	product_name,
    list_price
FROM
    products
WHERE
	list_price < 20;

```

1. Write a query to get a list of products that cost between $15 and $25

```
SELECT 
	product_name,
    list_price
FROM
    products
WHERE
	list_price < 25 AND list_price > 15;
```

1. Write a query to get a list of the ten most expensive products.

```
SELECT 
	product_name, 
	list_price
FROM
    products
ORDER BY
	list_price DESC
LIMIT 10;
```

1. Write a query to get the count current and discontinued products

```
SELECT Count(product_name)
FROM products
GROUP BY discontinued;
```