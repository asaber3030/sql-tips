# SQL Tips & Information

## 1. Use the `CHECK` constraint on columns on creating a new table:
[1-1] The following SQL creates a CHECK constraint on the "Age" column when the "Persons" table is created. The CHECK constraint ensures that the age of a person must be 18, or older:
```sql
CREATE TABLE users(
  id int(11) PRIMARY KEY NOT NULL AUTO_INCREMENT,
  age int(11) NOT NULL,
  name varchar(255) NOT NULL,
  CHECK (age >= 18)
);
```
[2-1] Here's another example to add multiple ***CHECK***
```sql
CREATE TABLE users (
  id int NOT NULL,
  lastName varchar(255) NOT NULL,
  firstName varchar(255),
  age int,
  city varchar(255),
  CONSTRAINT CHK_Person CHECK (age >= 18 AND city = 'Aswan')
);
```
[3-1] Using `ALTER` to add `CHECK` constraint
```sql
ALTER TABLE users ADD CHECK (age >= 18);
--- OR ---
ALTER TABLE users ADD CONSTRAINT CHK_PersonAge CHECK (age >= 18 AND city = 'Cairo');
```
[4-1] Drop `CHECK` constraint
```sql
ALTER TABLE users DROP CHECK CHK_PersonAge;
--- OR ---
ALTER TABLE users DROP CONSTRAINT CHK_PersonAge;
```
## 2. How to use SQL Views
What's the meaning of `SQL Views`?
---> It's a virtual stored data you make on your own way
[1-2] How to create SQL View
```sql
CREATE VIEW view_name AS SELECT name, age, email from users;
--- OR ---
CREATE OR REPLACE VIEW view_name AS
SELECT name, age, email
FROM users
WHERE age >= 25;
```
[2-2] How to restore data from created view?
```sql
SELECT * FROM view_name
```
[3-2] Drop created view
```sql
DROP VIEW view_name
```
## 3. What's `UNION` and how to use?
Union is a way to combine multiple `SELECT` statements
1. `UNION` only select distinct values
2. `UNION ALL` select all values even the duplicated ones
[1-3] How to use UNION
```sql
SELECT city from users
UNION
SELECT city from payments
```


