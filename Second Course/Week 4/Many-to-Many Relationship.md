### Many to Many
- Sometimes we need to model a relationship that is many to many.
- We need to add a "connection" table with two foreign keys.
- There is usually no separate primary key.
```mermaid
flowchart LR
	Books <--> Authors

```
```mermaid
flowchart LR 
	autBooks["Authors
	Books"]
    Books <--> autBooks 
    autBooks <--> Authors   
```
#### Example:
![[Pasted image 20230906213451.png]]
The member table does not have a primary key in this case
### Start with a Fresh Database
```SQL
CREATE TABLE Account (
	account_id INTEGER NOT NULL AUTO_INCREMENT,
	email VARCHAR(128) UNIQUE,
	name  VARCHAR(128),
	PRIMARY KEY(account_id)
)ENGINE=InnoDB CHARACTER SET=utf8
```
A UNIQUE value makes sure that each value in a column is distinct.
```SQL
CREATE TABLE Course (
	course_id INTEGER NOT NULL AUTO_INCREMENT,
	title VARCHAR(128) UNIQUE,
	PRIMARY KEY(course_id)
)ENGINE=InnoDB CHARACTER SET=utf8
```
```SQL
CREATE TABLE Member(
	account_id INTEGER,
	course_id  INTEGER,
	role       INTEGER,
	CONSTRAINT FOREIGN KEY (account_id) REFERENCES Account (account_id)
		ON DELETE CASCADE ON UPDATE CASCADE,
	CONSTRAINT FOREIGN KEY (course_id) REFERENCES Course (course_id)
		ON DELETE CASCADE ON UPDATE CASCADE,
	PRIMARY KEY(account_id, course_id)
)ENGINE=InnoDB CHARACTER SET=utf8
```
### Insert Accounts and Courses
```SQL
INSERT INTO Account (name, email) VALUES ('Jane', 'jane@tsugi.org');
INSERT INTO Account (name, email) VALUES ('Ed', 'ed@tsugi.org');
INSERT INTO Account (name, email) VALUES ('Sue', 'Sue@tsugi.org');
```
```SQL
INSERT INTO Course (title) VALUES ('Python');
INSERT INTO Course (title) VALUES ('SQL');
INSERT INTO Course (title) VALUES ('PHP');
```
### Insert Memberships
| account_id | email                     | name |
| ---------- | ------------------------- | ---- |
| 1          | $\mathrm{jane@tsugi.org}$ | Jane |
| 2          | $\mathrm{ed@tsugi.org}$   | Ed   |
| 3          | $\mathrm{sue@tsugi.org}$  | Sue  |

| course_id | title  |
| --------- | ------ |
| 1         | Python |
| 2         | SQL    |
| 3         | PHP    |
```SQL
INSERT INTO Member (account_id, course_id, role) VALUES (1, 1, 1);
INSERT INTO Member (account_id, course_id, role) VALUES (2, 1, 0);
INSERT INTO Member (account_id, course_id, role) VALUES (3, 1, 0);

INSERT INTO Member (account_id, course_id, role) VALUES (1, 2, 0);
INSERT INTO Member (account_id, course_id, role) VALUES (2, 2, 1);

INSERT INTO Member (account_id, course_id, role) VALUES (2, 3, 1);
INSERT INTO Member (account_id, course_id, role) VALUES (3, 3, 0);
```
![[Pasted image 20230906221615.png]]
```SQL
SELECT Account.name, Member.role, Course.title
FROM Account JOIN Member JOIN Course
ON Member.account_id = Account.account_id AND 
Member.course_id = Course.course_id
ORDER BY Course.title, Member.role DESC, Account.name
```
### Complexity Enables Speed
- Complexity makes speed possible and allows you to get very fast results as the data size grows.
- By <span style="color: #42ff14">normalising the data and linking it with integer keys</span>, the overall <span style="color: #42ff14">amount of data</span> which the relational database must <span style="color: #42ff14">scan</span> is far lower than if the data were simply flattened out.
- It might seem like a <span style="color: #e500f0">tradeoff</span> - spend some time designing your database so it continues to be fast when your application is a success.
### Summary
- Relational databases allow us to <span style="color: #42ff14">scale</span> to very large amounts of data.
- The key is to have <span style="color: #e500f0">one copy of any data element</span> and use relations and joins to link the data to multiple places.
- This greatly <span style="color: orange">reduces the amount of data that must be scanned</span> when doing complex operations across large amounts of data.
