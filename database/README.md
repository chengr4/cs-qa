# Database

## Q: What is **"transaction"**?

A SQL transaction is a grouping of one or more SQL statements that interact with a database.

## Q: When to Use Index?

取決於使用者的使用情況。觀察哪種 queries 最頻繁最吃 resource ，再考慮值不值得創建索引

## Q: What is a Database Driver?

A database driver is a software component that enables a software application to communicate with DBMS and perform database operations. A database driver acts as an intermediary between the application and the DBMS, translating the API calls made by the application into a format that the DBMS can understand and execute.

Eg. Oracle JDBC driver for Java, pq for Golang

## What is `for share`?

`FOR SHARE` is used to lock a table for reading. It allows other transactions to read the rows but not to modify them until the current transaction is committed.

## Q: When will dead lock happen?

### Case 1:

- ENV: PostgreSQL (Read Committed)
- Condition: A table and B table has foreign key to A table
- Keyword: `UPDATE`/`INSERT` + `SELECT ... FOR UPDATE`

if B table is updated (X lock) in TX B, and A table is selcted for update (X Lock) in TX A and, then B table is selected for update (X Lock) in TX B, then dead lock will happen. (TX A wait for TX B and TX B wait for TX A)

- Solution:

```sql
    SELECT * FROM account
    WHERE id = $1
    LIMIT 1
    FOR NO KEY UPDATE; <!-- Not update the key or ID of the column => Not affect on other table -->
```

## Q: How to avoid dead lock?

1. Be care for when you update or insert table in a transaction
2. `FOR NO KEY UPDATE;`
    ```sql
    SELECT * FROM account
    WHERE id = $1
    LIMIT 1
    FOR NO KEY UPDATE; <!-- Not update the key or ID of the column => Not affect on other table -->
    ```
3. Always update data in a consistant order (eg small ID first)