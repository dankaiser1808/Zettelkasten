---
id: 1744402142-sql-query-optimization
aliases:
  - SQL Query Optimization
tags: []
---

# SQL Query Optimization

- Filter early to minimize the number of rows processed
- Limit result size using Limits and ordering for proper results
- Indexing on filter queries or joins for often used columns
  - SQL can jump straight to the record like a pk.
  - Especially for joins we can use indexes to faster match both tables.
- Avoid functions on indexed columns
  - The problem here is that some functions transform the passed property, so SQL can't use the original passed value.
- Use Explain function to diagnose query function
- Denormalization can be useful. Instead of having multiple tables that we join, we can add some redundancy with another table that holds all the needed information, effectively skipping a join.


Also, Avoid N+1 Problems where we loop through a query, resulting in multiple queries. If possible, we can Joins or IN clauses to batch the multiple queries into one.
