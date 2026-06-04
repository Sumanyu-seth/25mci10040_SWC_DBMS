## Finding User Purchases
```sql
WITH first_purchase AS (
    SELECT
        user_id,
        MIN(created_at) AS first_purchase_date
    FROM amazon_transactions
    GROUP BY user_id
)

SELECT DISTINCT t.user_id
FROM amazon_transactions AS t
INNER JOIN first_purchase AS f
    ON t.user_id = f.user_id
WHERE
    t.created_at > f.first_purchase_date
    AND t.created_at <= f.first_purchase_date + INTERVAL '7 days';

```
<img width="1632" height="711" alt="Screenshot 2026-06-04 155222" src="https://github.com/user-attachments/assets/c33de9c1-fbfa-4653-ade9-62690855418d" />
