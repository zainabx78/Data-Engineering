# SQL

## Creating a database

- `CREATE DATABASE [IF NOT EXISTS] database_name;`
- SQL code is not case sensitive.
- To use the database/ be ready to run SQL commands on it: `USE database_name;`.


## Creating a table

```
CREATE DATABASE [IF NOT EXISTS] sales;
CREATE TABLE table_name ();
```

- Auto_increment = frees you from having to insert all the purchase numbers manually through the `INSERT` command at a later stage.

```
CREATE TABLE sales
(
    purchase_number INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    date_of_purchase DATE NOT NULL,
    customer_id INT,
    item_code VARCHAR(10) NOT NULL
);
```

### Create the “customers” table in the “sales” database. Let it contain the following 5 columns: customer_id, first_name, last_name, email_address, and number_of_complaints. Let the data types of customer_id and number_of_complaints be integer, while the data types of all other columns be VARCHAR of 255.

```
CREATE TABLE customers                                                 

(

    customer_id INT,

    first_name varchar(255),

    last_name varchar(255),

    email_address varchar(255),

    number_of_complaints int

);

```