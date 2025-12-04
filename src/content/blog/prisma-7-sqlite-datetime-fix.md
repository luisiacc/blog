---
title: "Fixing Prisma 7 DateTime Comparisons with SQLite"
description: "How to fix broken datetime queries after upgrading to Prisma 7 with an existing SQLite database"
pubDate: 2025-12-03
tags: ["prisma", "sqlite", "typescript"]
---

After upgrading to Prisma 7, you might find that datetime comparisons like `gt` or `gte` no longer work correctly with your existing SQLite database.

## The Problem

Prisma 7 changed how it handles datetime storage in SQLite. If you have an existing database with datetime values, queries like this will fail:

```typescript
await prisma.post.findMany({
  where: {
    createdAt: { gte: new Date() },
  },
});
```

They won't actually fail in the sense that it will explode, but they will return no results.

The issue is that the default behaviour of the prisma adaptar that is used, compares strings by default for dates, instead of the internal timestamps already stored in your database.

## The Solution

When creating the Prisma adapter, specify the `timestampFormat` option:

```typescript
const adapter = new PrismaBetterSqlite3(
  { url: process.env.DATABASE_URL!, timeout: 10_000 },
  { timestampFormat: "unixepoch-ms" },
);

const prisma = new PrismaClient({ adapter });
```

This tells Prisma to use Unix epoch milliseconds for timestamp comparisons, matching the format of your existing data.
