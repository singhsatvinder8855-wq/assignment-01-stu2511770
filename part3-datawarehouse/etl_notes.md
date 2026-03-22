## ETL Decisions

### Decision 1 — Standardizing Date Formats
Problem: The raw transactional data contained inconsistent date formats across rows (e.g., mixing '29/08/2023', '12-12-2023', and '2023-02-05').
Resolution: I implemented a transformation step in the ETL pipeline to parse all incoming date strings and standardize them into a uniform `YYYY-MM-DD` ISO format before loading them into the `dim_date` and `fact_sales` tables.

### Decision 2 — Handling NULL Values
Problem: Several records had `NULL` or entirely blank values for the `store_city` field in the store data (19 missing values in total).
Resolution: To maintain referential integrity and ensure the dimension table does not contain blank fields that could break business intelligence reporting roll-ups, I replaced all `NULL` location values with the string 'Unknown'.

### Decision 3 — Unifying Category Casing
Problem: The `category` column suffered from inconsistent casing due to manual data entry errors (e.g., 'electronics', 'Electronics', 'Grocery', and 'Groceries' were treated as different categories).
Resolution: I applied a string formatting transformation (Title Case) and category mapping during the cleaning phase to standardize all category names to 'Electronics', 'Clothing', and 'Groceries'. This ensures that analytical queries grouping by category sum the revenues correctly.
