## Change Primary Key name
```sql
-- Firstly, remove PRIMARY KEY attribute of former PRIMARY KEY
ALTER TABLE <table_name> DROP CONSTRAINT <table_name>_pkey;
-- Then change column name of  your PRIMARY KEY and PRIMARY KEY candidates properly.
ALTER TABLE <table_name> RENAME COLUMN <primary_key_candidate> TO id;
-- Lastly set your new PRIMARY KEY
ALTER TABLE <table_name> ADD PRIMARY KEY (id);
```

```sql
SELECT
    pc."usedAt" AT TIME ZONE 'UTC' AT TIME ZONE 'JST' AS used_at_jst,
    pc.code,
    pc."promotionId" AS promotion_id,
    p."promotionOwnerId" AS promotion_owner_id,
    p.title AS promotion_title,
    p."couponId" AS coupon_id,
    po.name AS promotion_owner_name,
    c.name AS coupon_name,
    CASE WHEN pc."usedAt" IS NOT NULL THEN TRUE ELSE FALSE END AS is_used
FROM
    "PromotionCode" pc
    LEFT JOIN "Promotion" p ON p.id = pc."promotionId"
    LEFT JOIN "PromotionOwner" po on p."promotionOwnerId" = po.id
    LEFT JOIN "Coupon" c ON p."couponId" = c.id
    WHERE pc."usedAt" IS NOT NULL
```
