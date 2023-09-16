### AUTO_INCREMENT
Often as we make multiple tables and we need to JOIN them together we need an integer primary key for each row so we can efficiently add a reference to a row in some other table as a foreign key.
```SQL
DROP TABLE Users;

CREATE TABLE Users (
	user_id INT UNSIGNED NOT NULL AUTO_INCREMENT,
	name VARCHAR(128),
	email VARCHAR(128),
	PRIMARY KEY(user_id),
	INDEX(email)
)
```
- `{SQL}UNSIGNED` means it is only positive
- `{SQL} NOT NULL` means it is required 
- `{SQL}AUTO_INCREMENT` means it will increment by 1 with each insertion
- `{SQL}PRIMARY KEY(user_id)` it means that we are going to look up by ids primarily 
- `{SQL}INDEX(email)` It will be looked up with [[Basic SQL Operations|WHERE]] a lot
### MySQL Functions
Many operations in MySQL need to use the built-in functions (like [[Data Types in SQL#Dates|NOW()]] for dates)
- Look it up.
### Indexes
- As a table gets large (they always do), scanning all the data to find a single row becomes very costly
- When drchuck@gmail.com logs into Facebook, they must find the password amongst 500 million users
- There are techniques to greatly shorten the scan as long as you create data structures and maintain those structures - like shortcuts
- Hashes or Trees
#### MySQL index types
- `{SQL} PRIMARY KEY`  - Very little space, exact match, requires no duplicates, extremely fast for integer fields
- `{SQL}INDEX` - Good for individual row lookup and sorting / grouping results - works best with exact matches or prefix lookups - can suggest HASH or BTREE
###  B-trees
A B-tree is a tree data structure that keeps data sorted and allows searches, sequential access, insertions, and deletions in logarithmic amortized time. The B-tree is optimized for systems that read and write large blocks of data. It is commonly used in databases and file systems.
![[Pasted image 20230904224843.png]]
### Hashes
A hash function is any algorithm or subroutine that maps large data sets to smaller data sets, called keys. For example, a single integer can serve as an index to an array (cf. aasociative array). The values returned by a hash function are called hash values, hash codes, hash sums, chacksums, or simply hashes. Hash functions are mostly used to accelerate table lookup or data comparison tasks such as finding items in a database...
![[Pasted image 20230904231423.png|450|center]]
### Specifying Indexes
[[Databases Keys and Indexes#Hashes|Hashes]] and [[Databases Keys and Indexes#B-trees|B-trees]] are two different kinds of indexes. We can indicate directly what we want to use. We can also alter databases for them to use those data types. Suppose that you want the index email of the table created in the [[Databases Keys and Indexes#AUTO_INCREMENT|AUTO_INCREMENT]] section to use  [[Databases Keys and Indexes#B-trees|B-trees]]:  
```SQL
ALTER TABLE Users ADD INDEX ( email ) USING BTREE
```