- Create Database:
```SQL
CREATE DATABASE People DEFAULT CHARACTER SET utf8;
```
- Create table:
```SQL
CREATE TABLE Users(
	name VARCHAR(128),
	email VARCHAR(128)
);
```
- Describe table:
```SQL
DESCRIBE Users;
```
![[Pasted image 20230903221210.png|center]]
- Insert data:
	- The INSERT statement inserts a row into a table
```SQL
INSERT INTO Users (name, email) VALUES ('Chuck', 'csev@umich.edu');
INSERT INTO Users (name, email) VALUES ('Somesh', 'somesh@umich.edu');
INSERT INTO Users (name, email) VALUES ('Caitlin', 'cait@umich.edu');
INSERT INTO Users (name, email) VALUES ('Ted', 'ted@umich.edu');
INSERT INTO Users (name, email) VALUES ('Sally', 'sally@umich.edu');
```
- DELETE
	- Deletes a row in a table based on selection criteria
```SQL
DELETE FROM Users WHERE email='ted@umich.edu'
```
The WHERE above does a comparison. 
- UPDATE
	- Allows updating of a field with a WHERE clause
```SQL
UPDATE Users SET name='Charles' WHERE email='csev@umich.edu'
```
- SELECT
	- Retrieves a group of records - you can either retrieve all the records or a subset of the records with a WHERE clause
```SQL
SELECT * FROM Users;
SELECT * FROM Users WHERE email='csev@umich.edu';
```
- Sorting with ORDER BY
	- You can add an ORDER BY clause to SELECT statements to get the results sorted in ascending or descending order
```SQL
SELECT * FROM Users ORDER BY email
```
- LIKE
	- We can do wildcard matching in a WHERE clause using the LIKE operator
```SQL
SELECT * FROM Users WHERE name LIKE '%e%'
```
![[Pasted image 20230903222818.png| center]]
- Counting Rows with SELECT
	- You can request to receive the COUNT of the rows that would be retrieved instead of the rows
```SQL
SELECT COUNT(*) FROM Users;
SELECT COUNT(*) FROM Users WHERE email='csev@umich.edu'
```
- LIMIT
	- Limit specifies the number of rows in a query