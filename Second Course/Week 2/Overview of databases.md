### Sequential access
We used to have tapes storing records as databases before hard drives. They were read sequentially, so we needed to read one entry at a time and update it. 
### Random access
Nowadays we use random access. We can access each record individually and update it pretty fast. But that raises some concerns: 
- How can you lay out data to be most efficient?
	- Sorting may not be the best idea.

---
## *S*tructural *Q*uery *L*anguage
- Structured Query Language (SQL) came out of a government/industry partnership
- National Institute of Standards and Technology (NIST)
### What it is:
- SQL is the language we use to issue commands to the database
	- Create/insert data
	- Read/Select some data
	- Update data
	- Delete data
	 ![[Pasted image 20230903215147.png]]
#### Terminology
- Database - Contains one or more tables
- Relation (or table) - Contains tuples and attributes
- Tuple (or row) - A set of fields which generally represent an "object" like a person or music track
- Attribute (also column or field) - One of possibly many elements of data corresponding to the object represented by the row

---
## Common Database Systems
- Three major Database Management Systems in wide use
	- Oracle -Large, commercial, enterprise-style, very tweakable
	- MySQL - Simpler but very fast and scallable - commercial open source
	- SqlServer - Very nice - from Microsoft (also Access)
- Many other smaller projects, free and open source
	- HSQL, SQLite, PostgreSQL, ...