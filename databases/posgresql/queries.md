[SELECT](https://www.postgresql.org/docs/current/sql-select.html)
SELECT retrieves rows from zero or more tables. The general processing of SELECT is as follows:
```sql
-- get all rows where createdAt is greather or equal 2021-10-29 
select * from "Purchase" where "createdAt" >= '2021-10-29';

-- get all rows from Benefit table and show only their "benefitId", "couponId", "name"
select "benefitId", "couponId", "name" from "Benefit";
```

[DELETE](https://www.postgresql.org/docs/10/sql-delete.html)
DELETE deletes rows that satisfy the WHERE clause from the specified table. If the WHERE clause is absent, the effect is to delete all rows in the table. The result is a valid, but empty table.
```sql
-- delete all rows in the table
delete from "Purchase"

-- delete rows from Purchase which createdAt is greather or equal 2021-10-29 
delete from "Purchase" where "createdAt" >= '2021-10-29';
```
[TRUNCATE](https://www.postgresql.org/docs/current/sql-truncate.html)
TRUNCATE quickly removes all rows from a set of tables. It has the same effect as an unqualified DELETE on each table, but since it does not actually scan the tables it is faster. Furthermore, it reclaims disk space immediately, rather than requiring a subsequent VACUUM operation. This is most useful on large tables.
```sql
-- removes all rows from PromotionCode table 
truncate table "PromotionCode";

-- removes all rows from customers, orders tables 
truncate table customers, orders;
```

[UPDATE](https://www.postgresql.org/docs/current/sql-update.html)
UPDATE changes the values of the specified columns in all rows that satisfy the condition. Only the columns to be modified need be mentioned in the SET clause; columns not explicitly modified retain their previous values.
```sql
-- set usedAt to null for PromotionCode with code 7736CN3T3CWZ34
update "PromotionCode" set "usedAt"=null, "usedBy"=null where "code"='7736CN3T3CWZ34';

-- set usedAt, usedBy to null for all PromotionCodes where usedAt  null
update "PromotionCode" set "usedAt"=null, "usedBy"=null where "usedAt" is not null;
```

[Pattern Matching](https://www.postgresql.org/docs/current/functions-matching.html)
[LIKE](https://www.postgresql.org/docs/current/functions-matching.html#FUNCTIONS-LIKE)
The LIKE expression returns true if the string matches the supplied pattern. (As expected, the NOT LIKE expression returns false if LIKE returns true, and vice versa. An equivalent expression is NOT (string LIKE pattern).)
```sql
select "benefitId", "couponId", "name" from "Benefit" where "couponId" like 'd7cff%' order by "couponId" asc;

```