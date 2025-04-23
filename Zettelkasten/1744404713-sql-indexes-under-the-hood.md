---
id: 1744404713-sql-indexes-under-the-hood
aliases:
  - SQL Indexes under the hood
tags: []
---

# SQL Indexes under the hood

Indexes create a sorted data structure for the specified column and a pointer to the actual table row. The pointer lives in memory, which enables us to quickly access the table row the indexed value belongs to.

This makes it possible to query an indexed value, and access the table rows through the pointer reference.
