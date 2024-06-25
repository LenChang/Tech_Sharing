# Overview
> Window functions are like precision instruments in the hands of a data explorer
```
SELECT employee_id, employee_name,quarter,year,sales_amount,
  SUM(sales_amount) OVER (PARTITION by employee_id
 ORDER BY sales_amount
 ROWS BETWEEN 1 PRECEDING AND 1 FOLLOWING) as BeforeandAfter
FROM employeeperformance
ORDER BY employee_id;
```

## Window Functions vs. Group By
> It lies in **data reduction**
- GROUP BY
  - Reduces the dataset by grouping -> Applys aggregate func.
- Window Functions
  - Maintain the integrity of rows while performing calculations
## Reference
- https://medium.com/@santosh_beora/window-functions-vs-group-by-unleashing-data-insights-1611218158fe

# Frame Specification
> Essentially, it tells PostgreSQL not just to look at all rows in the partition but to focus on a specific range of rows around the current row, based on the defined criteria.
## ROWS vs. RANGE
- ROWS: When you specify **ROWS**, you're telling PostgreSQL to count the exact number of rows from the current row to determine the frame. 
- RANGE: It groups rows that **have the same values as the current row** in the ordering column(s), effectively treating rows with identical values as a single entity in the calculation.
## Reference
- https://medium.com/@anusoosanbaby/understanding-frame-specification-in-postgresql-window-functions-b93e0bba9a80
