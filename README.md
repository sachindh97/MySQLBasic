
# MySQL Basic

A brief description of what this project does and who it's for

# 1.DATABASE 
Databases are a structure that can hold multiple tables, indexes, procedures, and help define a scope for privileges, customizations, and more.

# # Create database 
Create new database.
```
CREATE DATABASE <database_name>
```
for example
```
CREATE DATABASE companyDB
```
# # Drop Database
drop exiting database.
```
DROP DATABASE <database_name>
```
for example
```
DROP DATABASE companyDB
```

# # Show Database 
Get the list of database.
``` 
SHOW DATABASES
```

# # Use Database
```
use <database_name> 
```
for example
```
use companyDB
```
After selecting the database, we can perform various operations on it such as creating tables, inserting data, updating data, and deleting data.

# 2.Table
Tables store data within predefined schemas of columns and data types

# # Create new table 
creating new table 
```
CREATE TABLE table_name (
  column_name datatype constraints,
  column_name datatype constraints,
);
```
for example:
```
CREATE TABLE employee (
  emp_id int auto_increment(),
  first_name varchar(100) not null,
  last_name  varchar(100) not null,
  email varchar(100) not null
);
```
```
CREATE TABLE designation (
  designation_id int auto_increment,
  name varchar(100)
)
```
# # Delete exiting table 

```
DROP TABLE <table_name>

```
for example
```
DROP TABLE employee;
```

# 3. Alter columns and constraints.
add,delete or modifiy column and constraints in table.

# # 3.1 Add new column in exiting table.

```
ALTER TABLE <table_name>
ADD COLUMN <column_name> <data_type> <constraints> AFTER | BEFORE <exiting_column_name>;
```

for example :

```
ALTER TABLE employee
ADD COLUMN designation_id int not null after email;
``` 

# # 3.2 Drop column in exiting table.
```
ALTER TABLE <table_name>
DROP COLUMN <column_name>;
```

for example : 
```
ALTER TABLE <table_name>
DROP COLUMN designation_id;
```

# # 3.3 Modifiy column in exiting table.
```
ALTER TABLE <table_name>
MODIFIY COLUMN <column_name> <column_definition>;
```

for example:
```
ALTER TABLE employee
MODIFIY COLUMN last_name varchar(50) null ;
```

# # 3.5 Add constraints in exiting column.
```
ALTER TABLE <table_name>
ADD CONSTRAINTS <constraints_name> PRIMARY KEY (col_name1,col_name2),
ADD CONSTRAINTS <constraints_name> FOREGIN KEY <column_name> REFERENCES second_table(primary_column);
```

for example:

```
ALTER TABLE employee
ADD CONSTRAINTS empid_key PRIMARY KEY (emp_id),
ADD CONSTRAINTS desgID_fk FOREGIN KEY (designation_id) REFERENCES designation (designation_id);

```

# # 3.6 Drop constraints.
```
ALTER TABLE <table_name>
DROP CONSTRAINTS <constraints_name>
```

for example:
```
ALTER TABLE employee
DROP CONSTRAINTS empid_key;
```

# 4. Insert , update, delete data. 

# 4.1 Insert 

```
INSERT INTO <table_name>(colName1,colName1,..)
VALUES('data1','data2',...);
```

for example
```
INSERT INTO employee(first_name,last_name,email)
VALUES('Raj','Sharma','test@gmail.com')
```

-multiple insert.

```
INSERT INTO employee(first_name,last_name,email)
VALUES('Raj','Sharma','test@gmail.com'),
('Vijay','Json','json@gmail.com');
```

# # 4.2 Update 
```
UPDATE <table_name> 
SET <colName1> = <value1>, <colName2> = <value2>
where <colName> = <value>
```

for example
```
UPDATE employee
SET first_name='jay',last_name='Sharma'
where id=1;
```
# #4.3 Delete 

```
DELETE FROM <table_name>
where <colName> = <value>
```

for example :
```
DELETE FROM employee
where id=1;
```

# 5. Join 
# # 5.1 Inner Join 

```
SELECT * FROM <table_name1> as T1
INNER JOIN <table_name2> as T2
ON T1.<colName> = T2.<colName>;
```

for example:

```
SELECT * FROM employee as emp 
INNER JOIN designation as desg
ON emp.designation_id = desg.designation_id; 
```

# # 5.2 Left Join 
```
SELECT * FROM <table_name1> as T1
LEFT JOIN <table_name2> as T2
ON T1.<colName> = T2.<colName>;
```

for example:

```
SELECT * FROM employee as emp 
LEFT JOIN designation as desg
ON emp.designation_id = desg.designation_id; 
```

# # 5.3 Right Join 
```
SELECT * FROM <table_name1> as T1
RIGHT JOIN <table_name2> as T2
ON T1.<colName> = T2.<colName>;
```

for example:

```
SELECT * FROM employee as emp 
RIGHT JOIN designation as desg
ON emp.designation_id = desg.designation_id; 
```

# # 5.4 Full Join 
```
SELECT * FROM <table_name1> as T1
FULL JOIN <table_name2> as T2
ON T1.<colName> = T2.<colName>;
```

for example:

```
SELECT * FROM employee as emp 
FULL JOIN designation as desg
ON emp.designation_id = desg.designation_id; 
```

# 6 Update,delete data with join

# # 6.1 Update with join
```
UPDATE <table_1> as t1 
INNER JOIN <table_2> as t2
ON t1.id = t2.id
SET t1.<colName> = t2.<colName>
WHERE t1.<colName> = <value>; 
```
for example:

```
UPDATE employee as emp 
INNER JOIN designation desg 
ON emp.designation_id = desg.designation_id
SET emp.desgination_name = desg.name;
where emp.emp_id = 1;
```

# # 6.2 Delete with join
```
DELETE FROM <table_1> as t1 
INNER JOIN <table_2> as t2 
on t1.<colName> = t2.<colName>
where t2.<colName>=<value>;
```

for example:
```
DELETE FROM employee as emp 
INNER JOIN designation as desg
on emp.designation_id = desg.designation_id
where desg.name = 'QA';
```

# # 6.3 Insert with join 

```
INSERT INTO <table_3>
SELECT <colName1>,<colName2>,... FROM <table_1> 
INNER JOIN <table_2> 
ON table_1.<colName> = table_2.<colName>;
```

for example:

```
INSERT INTO emp_logs 
SELECT emp.first_name,emp.last_name,desg.name 
FROM employee as emp 
INNER JOIN designation as desg
ON emp.designation_id = desg.designation_id;
```

# 7. Operators

# # 7.1 AND 
```
SELECT * FROM <table_1> WHERE <colName1> = <value>
AND <colName2> = <value>
```

for example :
```
SELECT * FROM employee where first_name = 'sachin' and last_name = 'rao';
```

# # 7.2 OR 
```
SELECT * FROM <table_1> WHERE <colName1> = <value>
OR <colName2> = <value>
```

for example :
```
SELECT * FROM employee where first_name = 'sachin' or first_name = 'Vijay';
```

# # 7.3 NOT 
```
SELECT * FROM <table_1> WHERE NOT <colName1> = <value>
```

for example :
```
SELECT * FROM employee WHERE NOT first_name = 'sachin'
```

# # 7.4 IN
```
SELECT * FROM <table_1> WHERE <colName1> IN (<val1>,<val2>,...)
```

for example :
```
SELECT * FROM employee WHERE first_name in ('sachin','Vijay','rahul');
```

# # 7.4 BETWEEN
```
SELECT * FROM <table_1> WHERE <colName> BETWEEN <val1> AND <val2>
```

for example :
```
SELECT * FROM employee WHERE salary BETWEEN 
20000 AND 30000;
```


# 8.Comparison Operators
# # 8.1 = equal 
```
SELECT * FROM employee WHERE first_name = 'sachin';
```
# # 8.2 > greater than or >= greater than equal to 
```
SELECT * FROM employee WHERE salary > 30000;
SELECT * FROM employee WHERE salary >= 30000;
```

# # 8.3 < less than  or <= less than equal to 
```
SELECT * FROM employee WHERE salary < 30000;
SELECT * FROM employee WHERE salary <= 30000;
```

# # 8.4 <> Not equal to 
```
SELECT * FROM employee WHERE salary <> 30000;
```

# 9 Limit 
```
SELECT * FROM employee limit 2;
```

# 10 Order By 
```
SELECT * FROM <table_name> ORDER BY <colName> ASC | DESC 
```
for example:
```
SELECT * FROM employee Order By first_name asc;

SELECT * FROM employee Order By first_name asc,last_name desc
```

# 11 Group By 

```
SELECT * FROM <table_name> 
GROUP BY <colName>;
```
for example :
```
SELECT count(emp_id) FROM employee
GROUP BY first_name;
```

# 12 Having 
```
SELECT * FROM <table_name>
GROUP BY <colName>
HAVING <condition>
```

```
SELECT COUNT(emp_id) FROM employee
GROUP BY first_name
HAVING COUNT(emp_id) > 4;
```
# 13 Functions

# # 1.1 Count()

```
SELECT COUNT(emp_id) FROM employee;
```

# # 1.2 SUM()

```
SELECT SUM(salary) FROM employee;
```

# # 1.3 Min()

```
SELECT Min(salary) FROM employee;
```

# # 1.4 Max()

```
SELECT Max(salary) FROM employee;
```

# # 1.5 Avg() 

```
SELECT Avg(salary) FROM employee;
```

# 14 Store Procedure 
# # 14.1 without parameter
```
DELIMITER //
CREATE PROCEDURE <procedure_name>()
BEGIN 
  <WRITE SQL STATEMENT AND LOGIC>
END //  
DELIMITER ;
```
call the procedures
```
CALL <procedures_name>()
```
```
DELIMITER // 
CREATE PROCEDURE employee()
BEGIN 
    SELECT * FROM employee emp 
    INNER JOIN designation desg
    ON emp.designation_id = desg.designation_id;
END //
DELIMITER ;    
```


```
call employee();
```

# 14.2 with parameter (IN,OUT)
```
DELIMITER //
CREATE PROCEDURE <procedures_name>(
  IN <parameter_name> <data_type>,
  IN <parameter_name> <data_type>,
  OUT <parameter_name>
)
BEGIN
  <write SQL statement and logic>
END //
DELIMITER ;  
```
```
CALL <procedures_name>(<param1>,<param2>);
```

```
DELIMITER //
CREATE PROCEDURE employee(
  IN param_name varchar(100),
  IN param_salaryP int,
  OUT totalCount
)
BEGIN
  SELECT COUNT(emp_id) INTO totalCount FROM employee
  where first_name = param_name and salary =      param_salary
```

```
CALL employee('sachin',80000,@totalCount);
select @totalCount;
```

- show procedures
```
SHOW PROCEDURES STATUS
```

# 15.View 

```
CREATE VIEW <VIEW_NAME> AS SELECT * FROM <table_name>;
```

```
CREATE VIEW developer_employees AS 
SELECT emp.first_name,emp.last_name,desg.name 
FROM employee emp INNER JOIN designation desg 
ON emp.designation_id = desg.designation_id
where desg.name = 'developer';
```

# 16.indexes 
- create indexes
```
CREATE INDEX <index_name> ON <table_name> (colName1,colName2);
```

```
CREATE INDEX emp_index on employee (first_name,email);
```

- drop indexs 
```
ALTER TABLE <table_name>
DROP INDEX <index_name>
```

```
ALTER TABLE employee
DROP INDEX emp_index
```

# 17 Triggers

- Create Triggers

```
DELIMITER // 
CREATE TRIGGER <trigger_name>
{BEFORE|AFTER} {INSERT|UPDATE|DELETE}
ON <table_name>
FOR EACH ROW 
  <write query>
DELIMITER ;  
```

```
DELIMITER //
CREATE TRIGGER empUpdateLogs
AFTER UPDATE 
FOR EACH ROW 
  INSERT INTO emp_logs(status) 
  VALUES('UPDATE');
DELIMITER ;  
```

- Drop Triggers
```
DROP TRIGGER <trigger_name>;
```
```
DROP TRIGGER empUpdateLogs;
```

# 18 Transaction

```
START TRANSACTION 
query statement 1;
query statement 2;
ROLLBACK;
query statement 3;
SAVEPOINT <savepoint_name>
query statement 4;
ROLLBACK <savepoint_name>;
COMMIT;
```
