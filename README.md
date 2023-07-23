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
INSERT INTO production.employee (name, phone, email)
VALUES ('Mark', '888-8888', 'Mark@gmail.com')
```


### update data in table
```
UPDATE production.employee
SET name = 'Tom', phone = '333-2222'
WHERE id = 2
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
