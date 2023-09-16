### Text Fields
- Have a character set - paragraphs or HTML pages
	- `{SQL} TINYTEXT`  up to 255 characters
	- `{SQL} TEXT`  up to 65k characters
	- `{SQL} MEDIUMTEXT`  up to 16M characters
	- `{SQL} LONGTEXT`  up to 4G characters
- Generally not using with indexing or sorting - and only then limited to a prefix
### Binary Types (rarely used)
- Character = 8 - 32 bits of information depending on character set
- Byte = 8 bits of information
	- `{SQL}BYTE(n)` up to 255 bytes
	- `{SQL}VARBINARY(n)` up to 65K bytes
- Small Images - data
- Not indexed or sorted
### Binary Large Object (BLOB)
- Large raw data, files, images, word documents. PDFs, movies, etc
- No translation, indexing, or character set
- `{SQL} TINYBLOB(n)` - up to 255
- `{SQL} BLOB(n)` - up to 65K
- `{SQL} MEDIUMBLOB(n)` - up to 16M
- `{SQL} LONGBLOB(n)` - up to 4G
### Integer Numbers
Integer numbers are very efficient, take little storage, and are easy to process because CPUs can often compare them with a single instruction.
- `{SQL} TINYINT` (-128, 128)
- `{SQL} SMALLINT` (-32768, 32768)
- `{SQL} INT` or INTEGER (2 Billion)
- `{SQL} BIGINT` ($10^{18}$ ish)
### Floating Point Numbers
Floating point numbers can represent a wide range of values, but accuracy is limited.
- `{SQL} FLOAT` (32-bit) $10^{38}$ with 7 digits accuracy
- `{SQL} DOUBLE` (64-bit) $10^{308}$ with 14 digits accuracy
### Dates
- `{SQL} TIMESTAMP` - 'YYY-MM-DD HH:MM:SS' (1970, 2037)
- `{SQL} DATETIME` - 'YYY-MM-DD HH:MM:SS' 
- `{SQL} DATE` - 'YYY-MM-DD'
- `{SQL} TIME` - 'HH:MM:SS'
- Built-in MYSQL function `NOW()`, gives the current timw