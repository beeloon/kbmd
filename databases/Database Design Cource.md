## [Course LINK](https://www.youtube.com/watch?v=ztHopE5Wnpc)


## Relation

Relation now comes from world relationship. It comes from mathematical term **relation** (conection of sets)

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

Data integrety is just having correct data in your database

Data integrity solving such kind of problems:
- repeatina values
- incorrect values
- broken relationship

Three main type of data integriry:
- Entity integrity
- Referential integrity
- Domain integrity

**Entity integrity** - when we mention this type, we basically mean **unique entities**. For entity uniqueness we use **unique id**

**Ex:**
If we have two users two users in DB that have the same info, but actually they're two different people we need to set uniqueness for such table so every user in DB have unique id

FROM:
| name   | phone   |
| ------ | ------- |
| Bohdan | 3809915 |
| Bohdan | 3809915 |

TO:
| id  | name   | phone   |
| --- | ------ | ------- |
| 1   | Bohdan | 3809915 |
| 2   | Bohdan | 3809915 |

**Referential integrity** - is when we reference an id of one table to another table.

**Ex:**
We have users and comments table, and defining a user_id in comments table we specify referantial integtity between these two tables. If in some case user who wrote the comment will be deleted and comments still exists, then we will have referential integrity problems, because we cannot have comments independant from user

**users**
| user_id | name   | phone   |
| ------- | ------ | ------- |
| 777     | Bohdan | 3809915 |
| 12      | Ann    | 123     |

**comments**
| comment_id | user_id | text         |
| ---------- | ------- | ------------ |
| 1          | 12      | awesome      |
| 2          | 777     | test comment |


**Domain integrity** - is basically acceptale values for a column.

**Ex:**
For example we have phone numbers and we know that all phone numbers should be numbers and have a country prefix, like for Ukraine (+38). And then user decided to add text like "Some jubbrish" to the phone table, with data integrity you'll not have such problems,because it's not in number format and have not prefix

| phone         | id  | note            |
| ------------- | --- | --------------- |
| 380777777777  | 1   | ok              |
| 380666676666  | 2   | ok              |
| Some jubbrish | 3   | what the heck?! |

## Data Types

We can put limits on data type (eg. `char(20)`)


## Database Terms

Data - anything that we store in DB
Database - what we store out data in
Relational DB - it stire things in tables
DBMS - how we control and manage Database
RDBMS - how we control and manage Database between a values and tables
Null - when someone did not integrated value withing a table column
DB Anomalies - errors withing data integrity (something goes away from what we expect or from the normal)
DB Integrity - protect from DB anomalies

Entity - anything we store data user about
Attributes - things that we store about the entity
Relation - put it simply it's just a table and connection between them (in math connection between two data sets)
Tuple - all of the attributes about specific entity (row)
Table (File) - physical representation of relation
Row (Record or Entry) - specific individual entry within a table
Column(Field) - specific attribute of entity
Value - information that we put in a specific column
DB Design - the process of designing your table to remove anomalies and have data integrity
Schema - draw of desing structure 
Normalization - bunch of steps that we need to follow for better database design
Naming conventions - rules that help make things consistent
Keys - make something unique withing a table

SQL - domain specific programming lang designed for managing data in RDBMS
DDL (part of SQL) - definethe structure of database
DML (part of SQL) - insert, update, delete, search values in DB
SQL keywords - reserved words that (not supposed to use for your user defined data)

## Atomic values

Atomic value - means that value stores one thing

**Ex**: we have attriute `name`, but in common perspective this column can be generated like 'Caleb Daniel Curry', it's not necessary atomic because we store three names ('Caleb', 'Daniel', 'Curry') in one column.
If we wanna to make this field atomic, the best wasy to do it by DB design is to split this by first_name, middle_name, last_name

FROM:
| user_id | name               | phone   |
| ------- | ------------------ | ------- |
| 1       | Caleb Daniel Curry | 3809915 |

TO:
| user_id | first_name | middle_name | last_name | phone   |
| ------- | ---------- | ----------- | --------- | ------- |
| 1       | Caleb      | Daniel      | Curry     | 3809915 |

Also when we talk about atomic values, it means that we not want to store multiple thing withing a column like

| favourite_movies                | id  |
| ------------------------------- | --- |
| Pirates of Caribes, World War Z | 1   |

Split it properly
| favourite_movie    | id  |
| ------------------ | --- |
| Pirates of Caribes | 1   |
| World War Z        | 2   |

## Relationship

Relationship in DB perspective it's a connection between two or more entities

Types of relationship:
- One to one
- One to many
- Many to many

### One to one (1:1)

One Entity has a reletion with only one another Entity

**Ex:** Social securitry numbers. Person can have only one ssn, and a ssn can have only one person

person
| name    | person_id |
| ------- | --------- |
| Stephen | 1         |
| Hugh    | 2         |

ssn
| number    | ssn_id | person_id |
| --------- | ------ | --------- |
| 492345934 | 1      | 2         |
| 534586796 | 2      | 1         |

#### Designing one to one

**Cardholder and Card**. Cardholder can have only one related card(restriction from business rules).
Storing all information about user and card in one table can lead to bad desing.
 
***Why: We need to follow the rule of one, when table should describe only one entity and each row should be about one entity***

A one-to-one relationship between two tables can be established via a **UNIQUE** foreign key constraint.

cardholder
| name    | surname  | password     | card_id |
| ------- | -------- | ------------ | ------- |
| Stephen | Spilberg | great_pass43 | 111     |

card
| id  | issue_date | fee_rate |
| --- | ---------- | -------- |
| 111 | 2020-01-01 | 10       |



### One to many (1:N)

One Entity can have a relation ship with multipe other Entities

**Ex:** On youtube one person can create many comments, but one specific comment can be linked to one specific person

person
| name   | person_id |
| ------ | --------- |
| Bohdan | 1         |

comments
| text            | comment_id | person_id |
| --------------- | ---------- | --------- |
| awesome         | 1          | 1         |
| greate          | 2          | 1         |
| too much for me | 2          | 1         |

### Many to many (M:N)

Multipe Entities can have a relation ship with multipe other Entities

**Ex:** Polyamorous Marriage. Many husbands can be married to many wifes

#### Designing many to many

We have classes and students.
We need to split it to 1:M and M:1 (for two one to many relation) and add intermidiary table

**class ==> student_class <== student (1 : M | M : 1)**

class
| id  | subject   |
| --- | --------- |
| c5  | math      |
| c6  | phisics   |
| c7  | chemestry |

student
| name    | surname  | id  |
| ------- | -------- | --- |
| Stephen | Spilberg | s1  |
| Roman   | Moshak   | s2  |
| Anthony | Pollin   | s3  |

student_class
| id    | student_id | class_id |
| ----- | ---------- | -------- |
| sc11  | s1         | c5       |
| sc23  | s2         | c5       |
| sc64  | s3         | c5       |
| sc21  | s2         | c7       |
| sc88  | s3         | c7       |
| sc914 | s1         | c6       |


### Parent and child relationship

Parent have a PK(Primary key) <== Child have a FK(Foreign key)

Children inherit value from a parent, such as FK = 47, that tells us that his Parent is entry with Id = 47.
Foreign key always points back to Primary key. Child table FK(user_id) points to Parent table PK(user_id).

## Introduction to Keys

Properties of Keys:  
- Unique
- Never NULL
- Never changing

Benefits of DB Keys:
- Integrity (protect from duplication and old values)
- Unique ()
- Improves functionality of DB (speed of requests)
- Less work (we don't need to change data in many places, only in one)
- Allows for adding more complexity

Type of Keys:
- superkey (SK)
- candidate key (CK)

superkey - any number of colemns that forces every row to be unique, they have no practical usage and used only for designing DB. Defines:
- can each row be unique?
- can every row be unique?

candidate - combinations of columns that can be a key (first_name_middle_name_last_name)
Defines:
- how many CK do i have?
- how many columns are unique?

### Primary and Alternate keys
PRIMARY KEY - uniquely identifies each record in the table
ALTERNATE KEY - the keys that contain all the properties needed to become a Candidate Key 

Some important points about Alternate Keys are as follows :
- A Primary Key can’t be an Alternate Key. For a table with a single Candidate Key which has to be the Primary Key will not contain any Alternate Key.
- A Foreign Key can’t be an Alternate Key as it is only used to reference another table.
- The alternate Key should be unique.
- An Alternate Key can be a set of a single attribute or multiple attributes.
- It can be NULL as well.

### Surrogate and Natural keys

Surrogate and Natural key is categories of Primary keys. It's more for DB design, for know different types of keys

Natural key - some key that you would naturally store. 
**Ex:** Users table will naturally store username 

Natural is something that already in DB, when surrogate - is something that we just add.

**Ex of surrogate key:** We have tables like users, sales etc. surrogate keys will be user_id, sales_id etc

Surrogate key is private to DB, because of that we don't try to show them anywhere and the can be used only by DB admin. Also they're autoincremented (AI) everytime with big numbers or uuid.

#### PROS and CONS

Natural PROS
- you don't  need to defind any new data, natural keys already there
- keep your DB more minimalize 

Natural CONS
- sometimes it's hard to define natural keys (look Properties of KEYS above)
- natural key have real world connection, so it might happen that something will change in realworld value, and because of that it can break NOT CHANGING key rule

Surrogate PROS
- numbers that we set for surrogate key are easy to works with

Surrogate CONS
- you have to add new column to your table which can require to store more data 


### Foreign key

**Ex:** We have a class table

class
| class_id | instructor_id | building_id | name    |
| -------- | ------------- | ----------- | ------- |
| 7        | 45            | 14          | math    |
| 5        | 38            | 11          | phisics |

In the table we have class_id, which is   for the table.
When instructor_id and building_id are **Foreign key**, which point out to other table and form a relation

#### NOT NULL Foreign key

NOT NULL - it's a  constraint that specify that each row in column should have some value, in case of keys it determinate that each of relation required

**Ex:** We have a user and cars. User can have some ralation with cars in our table, but he can also not have any car, in other option ha can change one car to another, it will update Foreign key

### Foreign key CONSTRAINTS

Refers to the parent:
- ON DELETE - when we delete the parent, we want children to do smth
- ON UPDATE - when we update the parent, we want children to do smth

Refers what happend to the child:
- RESTRICT (NO ACTION)  - cannot delete or update before not change child
- CASCADE - delete or update value after parent changes
- SET NULL - will set value on null


### Simple key, Composite key, Compound key

These terms more for desing purposes

Simple key - compose from one column (surrogate key or natural) (user_id, username)
Composite key - compose from 2+ columns (natural key) (first_name + last_name + email)
Compound key - compose from 2+ columns from different tables (in intermidiatery table)

**Ex (compound key):**

- Student table (student_id)
- Class table (class_id)
- Student classes table (student_id_class_id)