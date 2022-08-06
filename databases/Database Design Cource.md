## Relation

- Entity: what we store data about (Person)
- Attribute: what we store (usename, email, password, address, phone etc.)

Ex:
Person
name ====> Bohdan
username ====> bellon
password ====> 12345

Making a relation between Attributes and Entity

| name   | username | password |
| ------ | -------- | -------- |
| Bohdan | bellon   | 123456   |

Each row in db represents a tuple in math perspective

## Database management systems (DBMS) (RDBMS for Relational)

Examples:
- MySQL
- SQL
- PostgreSQL
- etc

**All the DBMS takes data from Disk and then puts them into presentable tables for managing them from admin side. **

View mechanism - allowas us to change the surface appearence of our data

Ex: 

| id  | name   | username | password |
| --- | ------ | -------- | -------- |
| 1   | Bohdan | bellon   | 123456   |

There're two users who want to get specific data for example Adam want to see all names and usernames nad Jane want to see all id and passwords. View mechanism allow you to check it in restricted way line:
for Jane
| id  | password |
| --- | -------- |
| 1   | 123456   |

and for Adam

 | name   | username |
 | ------ | -------- |
 | Bohdan | bellon   |

For security purposes not all users allowed to see all infromation that can be stored in db


## SQL (Structured Query Language)

**Sql help define database structures and manipulates data within it, using:**
- Data definition language (DDL)
- Data manipulation language (DML) 

When we talking about defineng or changing some Attirbites DDL stands for it, meanwile DML stands for manipulation of Attributes values.

Ex:
DDL => Define a new Person attribute mail or change naming of username attribute to nickname

| id  | name   | nickname | password | mail          |
| --- | ------ | -------- | -------- | ------------- |
| 1   | Bohdan | bellon   | 123456   | test@test.com |


DML => Rename a nickname or add new row

| id  | name   | nickname | password | mail           |
| --- | ------ | -------- | -------- | -------------- |
| 1   | Bohdan | bodo     | 123456   | test@test.com  |
| 2   | Elen   | ellie    | 123456   | test2@test.com |


### Naming convention

As an example from author of course he use lowercase or snake_case for db naming, snake_case for attributes naming and UPPERCASE for commands

## Database desing

What's database design all about:
- DB don't have data integrity issues (When two tables were linked, and after some time link was deleted and now data not used anywhere. All data should be up to date and used properly)
- DB don't have repeating data
- DB don't have old data that shouldn't be there (ex: you have a customer in db and his address and the address is out of date and doesn't update that's the problem)

### DB Design schemas:
- Conceptual schema
- Logical schema
- Physical schema

schema - is the was that data structured

On Conceptual level you define which entity you need and relation between them (user => sale)
On Logical level you define which attributes entities have, columns,  data types etc 

**user**
| user_id | name   | nickname | password | mail           |
| ------- | ------ | -------- | -------- | -------------- |
| 1       | Bohdan | bodo     | 123456   | test@test.com  |
| 2       | Elen   | ellie    | 123456   | test2@test.com |

**sale**
| sale_id | user_id |
| ------- | ------- |
| 1       | 1       |
| 2       | 1       |

On physical we define which DBMS or server we will use. How people will access it: through internet or computer programs

Example of bad data integrity design
You have such DB table
| user_id | name   | phone   | fav_color |
| ------- | ------ | ------- | --------- |
| 1       | Bohdan | 3809915 | red       |

then you decide to add new favor color in, because we already have red one, we need to create a new row for other
**congrats, we have duplicated data (name phone)**

| id  | user_id | name   | phone   | fav_color |
| --- | ------- | ------ | ------- | --------- |
| 1   | 7       | Bohdan | 3809915 | red       |
| 2   | 7       | Bohdan | 3809915 | blue      |

but then you decide to update phone number 
| user_id | name   | phone   | fav_color  |
| ------- | ------ | ------- | ---------- |
| 1       | Bohdan | 12345   | **yellow** |
| 2       | Bohdan | 3809915 | blue       |

**congrats, now we have data integrity issue, because we have new phone number that person use and old one which he don't use**

## Data integrity