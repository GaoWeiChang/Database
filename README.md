# SQL basic command
### select columns from the table
```
SELECT column_name
FROM table_name

/*----------------------------------*/

SELECT TOP(100) -- select top 100 rows
	first_name as [First Name] -- If column name include space we need to put inside bracket
	,last_name as [Last Name]
	,phone	as Phone
	,email
FROM sales.customers
```

### create Table
```
CREATE TABLE table_name (
   column_1 data_type, 
   column_2 data_type, 
   column_3 data_type
);
```
```
USE database_name

CREATE TABLE table_name(
	id INT IDENTITY (1,1) PRIMARY KEY,
	name VARCHAR (255) not null
);
```

### create FOREIGN key in the TABLE
```
CREATE TABLE production.senior(
	id INT IDENTITY(1,1) PRIMARY KEY,
	employee_id INT NOT NULL,
	FOREIGN KEY (employee_id)
		REFERENCES production.employee (id)
		ON DELETE CASCADE ON UPDATE CASCADE
);
```

### insert data in table
```
INSERT INTO celebs (id, name, age) 
VALUES (1, 'Justin Bieber', 22);
```

```
INSERT INTO production.employee (name, phone, email)
VALUES ('Mark', '888-8888', 'Mark@gmail.com')
```


### update data in table
```
UPDATE production.employee
SET name = 'Tom', phone = '333-2222'
WHERE id = 2
```

### delete row from table 
> The DELETE FROM statement deletes one or more rows from a table. You can use the statement when you want to delete existing records. The statement below deletes all records in the celebs table with no twitter_handle:
```
DELETE FROM celebs 
WHERE twitter_handle IS NULL;
```

### add new column to table
> The ALTER TABLE statement adds a new column to a table. You can use this command when you want to add columns to a table. The statement below adds a new column twitter_handle to the celebs table.
```
ALTER TABLE celebs 
ADD COLUMN twitter_handle TEXT;
```

### filter the data
```
SELECT TOP (1000) [customer_id]
      ,[first_name]
      ,[last_name]
      ,[phone]
      ,[email]
      ,[street]
      ,[city]
      ,[state]
      ,[zip_code]
  FROM [BikeStores].[sales].[customers]
  WHERE customer_id <> 1 AND phone is not null -- filter data
```
* If we cannot find the specific value inside the column, we can use ***LIKE*** to find relate value
```
WHERE  phone LIKE '%246-8322%' -- find the phone number that similar as 246-8322
WHERE  first_name LIKE 'W%' -- find the word start with letter W
```

### Sort the data
* ASC = ascending order
* DESC = descending order
```
 SELECT TOP (1000) [product_id]
      ,[product_name]
      ,[brand_id]
      ,[category_id]
      ,[model_year]
      ,[list_price]
  FROM [BikeStores].[production].[products]
  ORDER BY model_year desc
```
* Sort multiple column
```
 SELECT TOP (1000) [product_id]
      ,[product_name]
      ,[brand_id]
      ,[category_id]
      ,[model_year]
      ,[list_price]
  FROM [BikeStores].[production].[products]
  ORDER BY model_year, list_price ASC 
```

### Constraits
> Constraints that add information about how a column can be used are invoked after specifying the data type for a column.
```
CREATE TABLE celebs (
   id INTEGER PRIMARY KEY, 
   name TEXT UNIQUE,
   date_of_birth TEXT NOT NULL,
   date_of_death TEXT DEFAULT 'Not Applicable'
);
```
1. PRIMARY KEY columns can be used to uniquely identify the row. Attempts to insert a row with an identical value to a row already in the table will result in a constraint violation which will not allow you to insert the new row.

2. UNIQUE columns have a different value for every row. This is similar to PRIMARY KEY except a table can have many different UNIQUE columns.

3. NOT NULL columns must have a value. Attempts to insert a row without a value for a NOT NULL column will result in a constraint violation and the new row will not be inserted.

4. DEFAULT columns take an additional argument that will be the assumed value for an inserted row if the new row does not specify a value for that column.

# Database relations
![image](https://github.com/GaoWeiChang/Database/assets/128176822/86e4fbc3-1245-4843-b7a7-13c3f444224f)
* *One to One* => Both are has only 1 relation to each other ex. one employee contact has one exployee accounts
* *Many to Many* => Both are have many relation to each other ex. many writer write many books
* *One to Many* => (Most popular) One side connect to many of the another side ex. customer can have many order
