### Relational Power
- By removing the replicated data and replacing it with references to a single copy of each bit of data, we built a "<span style="color: #e500f0">web</span>" of information that the relational database can read trough very quickly - even for very large amounts of data
- Often when you want some data it comes from a number of tables linked by these <span style="color: #e500f0">foreign keys</span>. 
### The JOIN operation
- The JOIN operation <span style="color: #e500f0">links across several tables</span> as part of a SELECT operation.
- You must tell JOIN <span style="color: #42ff14">how to use the keys</span> that make the connection between the tables using an <span style="color: #42ff14">ON clause</span>.
#### Example
![[Pasted image 20230905233518.png]]
![[Pasted image 20230905233725.png]]
![[Pasted image 20230906203825.png]]
It is possible to see that you should specify which column corresponds to which id and therefore should be joined. Now the data looks as followed but without being inefficient. It is just a "front-end" change:

| title         | name  |
| ------------- | ----- |
| Black Dog     | Rock  |
| About to Rock | Metal |
| Who Made Who  | Metal |
```SQL
SELECT Track.title, Genre.name FROM Track JOIN Genre 
	ON Track.genre_id=Genre.genre_id
```
### It can get complex...
```SQL
SELECT Track.title, Artist.name, Album.title, Genre.name
FROM Track JOIN Genre JOIN Album JOIN Artist ON 
Track.genre_id = Genre.genre_id AND Track.album_id=Album.album_id AND Album.artist_id = Artist.artist_id 
```

| title         | name        | title        | name  |
| ------------- | ----------- | ------------ | ----- |
| About to Rock | AC/DC       | Who Made Who | Metal |
| Who Made Who  | AC/DC       | Who Made Who | Metal |
| Black Dog     | Led Zepplin | IV           | Rock  |
| Stairway      | Led Zepplin | IV           | Rock  |
The tables are linked, and we see it.
### ON DELETE CASCADE
This statement basically cleans up broken references:
![[Pasted image 20230906205252.png]]
```SQL
DELETE FROM Genre WHERE name='Metal'
```
### ON DELETE Choices
- Default/`{SQL}RESTRICT` - Don't allow changes that break the constraint
- `{SQL}CASCADE` - Adjust child rows by removing or updating to maintain consistency
- `{SQL}SET NULL` - Set the foreign key columns in the child rows to null
