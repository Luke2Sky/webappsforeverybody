### Database Normalization (3NF)
- Do not replicate data. Instead, reference data. Point at data.
- Use integers for keys and for references.
- Add a special "key" column to each table, which you will make references to.
### Integer Reference Pattern
![[Pasted image 20230905215214.png|center]]
- Do not replicate data. Instead, reference data. Point at data.
- Use integers for keys and for references.
- Add a special "key" column to each table, which you will make references to.
![[Pasted image 20230905222001.png|300]] 
- <span style="color: orange">Primary key</span> - generally an integer auto-increment field
- <span style="color: #42ff14">Logical key</span> - what the outside world uses for lookup 
- <span style="color: #e500f0">Foreign key</span> - generally an integer key pointing to a row in another table
### Primary Key Rules
Best practices
- Never use your <span style="color: #42ff14">Logical key</span> the <span style="color: orange">primary key</span> 
- <span style="color: #42ff14">Logical keys</span> can and do change, albeit slower.
- <span style="color: #e500f0">Relationships</span> that are based on matching string fields is less efficient than integers
### Foreign Keys
![[Pasted image 20230905224955.png]]
- A <span style="color: #e500f0">foreign key</span> is when a table has a column containing a key that points to the <span style="color: orange">primary key</span> of another  table.
- When all primary keys are integers, then all foreign keys are integers. This is very good.
