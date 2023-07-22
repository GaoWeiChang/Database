# SQL

## Basic command
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
