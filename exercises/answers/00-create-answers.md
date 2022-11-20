# Create Exercises

These exercises require you to create a table in the database, and insert records into it.

If at any point you need to reset the database, you can do so by finding the northwind container with `docker container ls`. 

You can then stop the container with `docker stop CONTIANER_ID`. 

Once the container is stopped you can remove it with `docker container rm CONTAINER_ID`. After this you can simply re-run the run script: `sh ./run.sh`. 

You may need to restart `mysql-workbench`.

1. Write a statement to create a simple table called `countries`. It shoud include the columns `country_id`, `country_name` and `region_id`

    ```
    CREATE TABLE countries (
        country_id INTEGER,
        country_name VARCHAR(40),
        country_code VARCHAR(2)
    );
    ```

1. Write a statement to insert a record into your country table. Confirm that the record exists with `SELECT * FROM countries`.

    ```
    INSERT INTO countries (
        country_id,
        country_name,
        country_code
    ) 
    VALUES (
        '1',
        'England',
        'en'
    );
    ```

1. Remove the `countries` table with `DROP TABLE countries`. Now write a statement to create the same table again, none of the fields should be able to be null. Confirm that this is the case by attempting to insert a record with null values.

    ```
    CREATE TABLE countries (
        country_id INTEGER NOT NULL,
        country_name VARCHAR(40) NOT NULL,
        country_code VARCHAR(2) NOT NULL
    );
    ```

1. Remove the `countries` table and create it again. This time make sure that only the countries `Italy`, `India` and `China` are valid entries.

    ```
    CREATE TABLE countries (
        country_id INTEGER  NOT NULL,
        country_name VARCHAR(40) CHECK (country_name IN ('Italy' , 'India', 'China')),
        country_code VARCHAR(2) NOT NULL
    );
    ```

1. Delete and recreate this table. This time make sure that no duplicate data against column country_id will be allowed at the time of insertion.

    ```
    CREATE TABLE countries (
        country_id INTEGER NOT NULL,
        country_name VARCHAR(40) CHECK (country_name IN ('Italy' , 'India', 'China')),
        country_code VARCHAR(2) NOT NULL, 
        UNIQUE (country_id)
    );
    ```

1. Now recreate the table, but this time make the country_code a `unique` field. This can be used to prevent duplicate data.

    ```
    CREATE TABLE countries (
        country_id INTEGER NOT NULL,
        country_name VARCHAR(40) CHECK (country_name IN ('Italy' , 'India', 'China')),
        country_code VARCHAR(2) UNIQUE
    );
    ```

1. Finally, recreate the table with the `country_id` as a `primary key` with auto increment. Insert a few records into the table to confirm that it is auto-incrementing this column.

    ```
    CREATE TABLE countries (
        country_id INTEGER NOT NULL UNIQUE AUTO_INCREMENT PRIMARY KEY,
        country_name VARCHAR(40) CHECK (country_name IN ('Italy' , 'India', 'China')),
        country_code VARCHAR(2)
    );
    ```

1. Write a statement to create a table named `jobs`. It should have the columns `job_id`, `job_title`, `min_salary`, `max_salary`. You should make sure that salary cannot exceed 25000.

    ```
    CREATE TABLE jobs ( 
        job_id varchar(10) NOT NULL , 
        job_title varchar(35) NOT NULL, 
        min_salary decimal(6,0), 
        max_salary decimal(6,0) CHECK(max_salary <= 25000)
    );
    ```

1. Write a SQL statement to create a table named `job_history` including columns `employee_id`, `start_date`, `end_date`, `job_id` and `department_id` and make sure that the value against column `end_date` will be entered at the time of insertion to the format like '--/--/----'.

    ```
    CREATE TABLE IF NOT EXISTS job_history ( 
        employee_id decimal(6,0) NOT NULL, 
        start_date date NOT NULL, 
        end_date date NOT NULL CHECK (END_DATE LIKE '--/--/----'), 
        job_id varchar(10) NOT NULL, 
        department_id decimal(4,0) NOT NULL 
    );
    ```

# Insert Exercises

Create the following table in your database:

    ```
    +--------------+---------------+------+--------------+---------------+
    | Field        | Type          | Null | Key          | Extra         |
    +--------------+---------------+------+--------------+---------------+
    | COUNTRY_ID   | integer       | NO   | PRIMARY KEY  | AUTO_INCREMENT|
    | COUNTRY_NAME | varchar(40)   | NO   |              |               |
    | COUNTRY_CODE | varchar(2)    | NO   |              | UNIQUE        |
    +--------------+---------------+------+--------------+---------------+
    ```
    
    ```
    CREATE TABLE countries (
        country_id INTEGER NOT NULL PRIMARY KEY AUTO_INCREMENT,
        country_name VARCHAR(40) NOT NULL,
        country_code VARCHAR(2) NOT NULL UNIQUE
    );
    ```

1. Write a SQL statement to insert a record with your own value into the table countries against each column.


    ```
    INSERT INTO countries (
        country_id,
        country_name,
        country_code
    ) 
    VALUES (
        1,
        'Italy',
        'it'
    );
    ```

2. Write a SQL statement to insert 3 rows by a single insert statement.

    ```
    INSERT INTO countries (
        country_id,
        country_name,
        country_code
    ) 
    VALUES 
    (
        1,
        'Italy',
        'it'
    ),
    (
        2,
        'China',
        'ch'
    ),
    (
        3,
        'India',
        'in'
    );
    ```

