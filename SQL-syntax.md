# SQL 

SQL allows interactions with data stored in a database.
SQL code is used to send requests to a database. These requests are known as queries. 
- Rows are records, columns are fields. 
- Data that can be stored in tables is called structured.
- Key words in SQL: E.g. SELECT, ALTER, FROM, CREATE etc. 
  - These words can't be used tp name variables or objects or databases. 

- E.g. if there's a table called `movies`: 
```
SELECT title 
FROM movies
```

- This selects only the `title` column from the table called `movies`. 

## SQL SYNTAX

1. DDL - Data Definition Language (creation of data)
2. DML - Data Manipulation Language (manipulation of data)
3. DCL - Data Control Language (assignment andd removal of permissions to use this data)
4. TCL - Transaction Control Language (saving and restoring changes to a database)


## Data manipulation language - 

- `INSERT` - Used to insert data into tables.
- `INSERT INTO sales (purchase_number, date_of_purchase)` - 2 new sections. 
- Delete statement- can specifiy precisely which records you want to delete. Similar to truncate - Allows us to remove all the records in a table. 
- E.g.:
```
DELETE FROM sales
WHERE
  purchase_number = 1;
```
- This deletes a specific record. 
- `TRUNCATE` - Data Definition Language (DDL) used to quickly remove all records from the table. - not data manipulation language

## Data Control Language 

- Grant and revoke statements - allow us to manage the rights users have in a database. E.g. complete or partial access. 
- E.g. `GRANT type_of_permission ON database_name.table_name TO 'username@localhost'`
- These rights will be assigned to a person who has a username registered at the local server. 
- Big companies don't use this method. 

### Creating a user
- `CREATE USER 'frank@localhost' IDENTIFIED BY 'pass'`
- Creates a user with the password 'pass'.

### Granting permissions to frank
- `GRANT SELECT ON sales.customers TO 'frank' @'localhost';`  - Allows frank to apply only the select statement to the customers. 
- `GRANT ALL ON sales." to 'frank'@'localhost';` - Allows frank to have access to all the table (*). 

### Revoke
- `REVOKE` - used to revoke permissions and privileges of database users. 
- `REVOKE SELECT ON sales.customers FROM 'frank'@'localhost';`.


## Transaction Control Language (TCL)

- not every change you make to a database is saved automatically. 
- Commit statement- saves the changes youve made and will let others access the modified version of the database. 
- E.g. 

```
UPDATE customers
SET last_name = 'Johnson'
WHERE customer_id = 4
COMMIT;
```

- This saves the change made. 

### Rollback clause 
- The clause that will allowe you to make a step back. Allows you to undo any changes you've made but don't want to be saved permenantly. 
- Just add `ROLLBACK;` at the end. 
- The last change will not count. 
- Reverts to the last non-committed state. 

