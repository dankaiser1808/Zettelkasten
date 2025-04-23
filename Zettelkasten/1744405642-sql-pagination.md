---
id: 1744405642-sql-pagination
aliases:
  - SQL Pagination
tags: []
---

# SQL Pagination

A common way to use pagination is to use SQL OFFSET based pagination. This will tell the database to skip a specified amount of rows. The problem with OFFSET is that SQL still has to read the skipped rows. It's like flipping thousands of pages of a book before reading the page you are looking for.

bad:
```SQL
SELECT * FROM products
ORDER BY created_at DESC
LIMIT 10 OFFSET 20;
```

better:
```SQL
SELECT * FROM products
WHERE created_at < '2024-04-1 12:00:00'
ORDER BY created_at DESC
LIMIT 10;
```

