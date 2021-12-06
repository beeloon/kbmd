## Change Primary Key name
```sql
-- Firstly, remove PRIMARY KEY attribute of former PRIMARY KEY
ALTER TABLE <table_name> DROP CONSTRAINT <table_name>_pkey;
-- Then change column name of  your PRIMARY KEY and PRIMARY KEY candidates properly.
ALTER TABLE <table_name> RENAME COLUMN <primary_key_candidate> TO id;
-- Lastly set your new PRIMARY KEY
ALTER TABLE <table_name> ADD PRIMARY KEY (id);
```