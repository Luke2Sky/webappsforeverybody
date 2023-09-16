![[Relational Database Design#For each "piece of info"]]
![[Pasted image 20230905230245.png]]
### Creating our Music Database
```sql
CREATE DATABASE Music
	DEFAULT CHARACTER SET UTF8
USE Music;
CREATE TABLE Artist (
	artist_id INTEGER NOT NULL AUTO_INCREMENT,
	name VARCHAR(255),
	PRIMARY KEY(artist_id)
) ENGINE = InnoDB;
CREATE TABLE Album (
	album_id INTEGER NOT NULL AUTO_INCREMENT,
	title VARCHAR(255),
	PRIMARY KEY(album_id)
	INDEX USING BTREE (title),

	CONSTRAINT FOREIGN KEY (artist_id)
		REFERENCES Artist (artist_id)
		ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE = InnoDB;
CREATE TABLE Genre (
	genre_id INTEGER NOT NULL AUTO_INCREMENT,
	name VARCHAR(255),
	PRIMARY KEY(genre_id),
	INDEX USING BTREE (name)
) ENGINE = InnoDB;
CREATE TABLE Track (
	track_id INTEGER NOT NULL AUTO_INCREMENT,
	title VARCHAR(255),
	len INTEGER,
	rating INTEGER,
	count INTEGER,
	album_id INTEGER,
	genre_id INTEGER,
	PRIMARY KEY(track_id),
	INDEX USING BTREE (title),

	CONSTRAINT FOREIGN KEY (album_id)
		REFERENCES Album (album_id)
		ON DELETE CASCADE ON UPDATE CASCADE
	CONSTRAINT FOREIGN KEY (genre_id)
		REFERENCES Genre (genre_id)
		ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE = InnoDB;
```
### Now we have relationships!
![[Pasted image 20230905232610.png]]

