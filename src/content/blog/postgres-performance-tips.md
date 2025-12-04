---
title: 'PostgreSQL Performance Tips'
description: 'Simple optimizations that can dramatically speed up your database queries'
pubDate: 2024-10-22
tags: ['postgres', 'databases']
---

A few tweaks can make a huge difference in PostgreSQL performance.

## Use EXPLAIN ANALYZE

Always start by understanding your query plan:

```sql
EXPLAIN ANALYZE SELECT * FROM users WHERE email = 'test@example.com';
```

## Index your foreign keys

This is often overlooked but crucial for JOIN performance.

## Connection pooling

Use PgBouncer or similar to manage connections efficiently.
