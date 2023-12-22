# Get Started
> Rotates a table by turning the unique values from one column in the input expression into multiple columns and aggregating results where required on any remaining column values

# Database
## Snowflake
> PIVOT, SUM and FOR..IN
- It's the Syntactic sugar
```
SELECT * 
  FROM monthly_sales
    PIVOT(SUM(amount) FOR MONTH IN ('JAN', 'FEB', 'MAR', 'APR'))
      AS p (EMP_ID_renamed, JAN, FEB, MAR, APR)
  ORDER BY EMP_ID_renamed;
```
### Ref
- https://docs.snowflake.com/en/sql-reference/constructs/pivot
## PostgreSQL
> SUM, CASE WHEN..THEN..ELSE..END and GROUP BY
```
SELECT month,
SUM(CASE WHEN product = 'A' THEN sales ELSE 0 END) AS "A",
SUM(CASE WHEN product = 'B' THEN sales ELSE 0 END) AS "B"
FROM sales
GROUP BY month;
```
### Ref
- https://www.sql-easy.com/learn/how-to-pivot-in-postgresql/
## MySQL
> SUM, CASE WHEN..THEN..ELSE..END and GROUP BY
```
SELECT
product_name,
SUM(CASE
  WHEN store_location = 'North' THEN num_sales ELSE 0 END
) AS north
FROM product_sales
GROUP BY product_name;
```
### Ref
- https://www.databasestar.com/mysql-pivot/
