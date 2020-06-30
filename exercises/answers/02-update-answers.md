# Update Exercises

These exercises require you to update existing records in Northwind company database. You will need to use [`UPDATE`](https://www.w3schools.com/sql/sql_update.asp) statment. This makes use of the `UPDATE`, `SET` and `WHERE` keywords.


Remember:
 If you make a mistake you can always remove the container and start a new one.

 1. Write a statement to change the `email` of every employee to `'not available'`

1. Write a statement to change the `email` of every employee to `'classified'` and set everybody's `first_name` to `Dave`

1. Write a statement to change `email` to `'super top secret'` and `last_name` to `McSalesman` for employees who's `job_title` is `Sales Representative`

1. Write a statement to change the `webpage` of all the employees in Seattle to the wikipedia page for Seattle. 

Now that we've rendered the `employees` table, let's look at the `customers`:

1. Elizabeth Anderson recently Married Roland Wacker. They have requested that you update the customer table to reflect the fact that Roland has taken Elizabeth's last name. 

1. The also request that you change the `ship_name` and `ship_address` on any orders that have not yet shipped to Roland. The ship name should reflect Roland's new `last_name`. The new address should match Elizabeth's. You should check the `order_details_status` table to see which codes correspond to being shipped. Extra points if you complete this one using a `JOIN` statment.


```
UPDATE orders
        LEFT JOIN
    orders_status ON orders.status_id = orders_status.id
SET 
    orders.ship_name = 'Roland Andersen',
    orders.ship_address = '123 8th Street',
    orders.ship_city = 'Portland',
    orders.ship_state_province = 'OR'
WHERE
    customer_id = 10
        AND orders_status.status_name != 'Shipped';
```
