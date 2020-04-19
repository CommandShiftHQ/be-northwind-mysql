# Create Exercises

These exercises require you to create a table in the database, and insert records into it.

If at any point you need to reset the database, you can do so by finding the northwind container with `docker container ls`. 

You can then stop the container with `docker stop CONTIANER_ID`. 

Once the container is stopped you can remove it with `docker container rm CONTAINER_ID`. After this you can simply re-run the run script: `sh ./run.sh`. 

You may need to restart `mysql-workbench`.

1. Write a statement to drate a simple table called `countries`. It shoud include the columns `country_id`, `country_name` and `region_id`

    ```
    CREATE TABLE countries (
        country_id VARCHAR(2),
        country_name VARCHAR(40),
        region_id DECIMAL(10,0)
    );
    ```

1. Write a statement to insert a record into your country table. Confirm that the record exists with `SELECT * FROM countries`.

    ```
    INSERT INTO countries (
        country_id,
        country_name,
        region_id
    ) 
    VALUES (
        'en',
        'england',
        1
    );
    ```

1. Remove the `countries` table with `DROP TABLE countries`. Now write a statement to create the same table again, none of the fields should be able to be null. Confirm that this is the case by attempting to insert a record with null values.

    ```
    CREATE TABLE countries (
        country_id VARCHAR(2) NOT NULL,
        country_name VARCHAR(40) NOT NULL,
        region_id DECIMAL(10 , 0 ) NOT NULL
    );
    ```

1. Remove the `countries` table and create it again. This time make sure that only the countries `Italy`, `India` and `China` are valid entries.

    ```
    CREATE TABLE countries (
        country_id VARCHAR(2) NOT NULL,
        country_name VARCHAR(40) CHECK (country_name IN ('Italy' , 'India', 'China')),
        region_id DECIMAL(10 , 0 ) NOT NULL
    );
    ```

1. Delete and recreate this table. This time make sure that no duplicate data against column country_id will be allowed at the time of insertion.

    ```
    CREATE TABLE countries (
        country_id VARCHAR(2) NOT NULL,
        country_name VARCHAR(40) CHECK (country_name IN ('Italy' , 'India', 'China')),
        region_id DECIMAL(10 , 0 ) NOT NULL,
        UNIQUE (country_id)
    );
    ```

1. Now recreate the table, but this time make the country a `key` field. This can also be used to prevent duplicate data.

    ```
    CREATE TABLE countries (
        country_id VARCHAR(2) NOT NULL,
        country_name VARCHAR(40) CHECK (country_name IN ('Italy' , 'India', 'China')),
        region_id DECIMAL(10 , 0 ) KEY
    );
    ```

1. Finally, recreate the table with the `country_id` as a `primary key` with auto increment. Insert a few records into the table to confirm that it is auto-incrementing this column.

    ```
    CREATE TABLE countries (
    country_id INTEGER NOT NULL UNIQUE AUTO_INCREMENT PRIMARY KEY,
    country_name VARCHAR(40) CHECK (country_name IN ('Italy' , 'India', 'China')),
    region_id DECIMAL(10 , 0 )
);
    ```

1. Write a statement to create a table named `jobs`. It should have the columns `job_id`, `job_title`, `min_salery`, `max_salery`. You should make sure that salery cannot exceed 25000.

1. Write a SQL statement to create a table named job_histry including columns employee_id, start_date, end_date, job_id and department_id and make sure that the value against column end_date will be entered at the time of insertion to the format like '--/--/----'.

1. Write a SQL statement to create a table job_history including columns employee_id, start_date, end_date, job_id and department_id and make sure that, the employee_id column does not contain any duplicate value at the time of insertion and the foreign key column job_id contain only those values which are exists in the jobs table.

Here is the structure of the table jobs;

```
+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | varchar(10)  | NO   | PRI |         |       |
| JOB_TITLE  | varchar(35)  | NO   |     | NULL    |       |
| MIN_SALARY | decimal(6,0) | YES  |     | NULL    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
```

# Insert Exercises

Create the following table in your database:

```
+--------------+---------------+------+-----+---------+-------+
| Field        | Type          | Null | Key | Default | Extra |
+--------------+---------------+------+-----+---------+-------+
| COUNTRY_ID   | varchar(2)    | YES  |     | NULL    |       |
| COUNTRY_NAME | varchar(40)   | YES  |     | NULL    |       |
| REGION_ID    | decimal(10,0) | YES  |     | NULL    |       |
+--------------+---------------+------+-----+---------+-------+
```

1. Write a SQL statement to insert a record with your own value into the table countries against each column.

2. Write a SQL statement to insert 3 rows by a single insert statement.

