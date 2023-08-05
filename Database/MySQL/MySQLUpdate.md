MySQL UPDATE JOIN

In MySQL, you can use the JOIN clauses in the UPDATE statement to perform the cross-table update.

The syntext of MYSQL UPDATE JOIN is as follows:
```sql
    UPDATE T1, T2,
    [INNER JOIN | LEFT JOIN] T1 ON T1.C1 = T2.C1
    SET T1.C2 = T2.C2,
        T2.C3 = expr
    WHERE condition
```

Let's examine the MySQL UPDATE JOIN syntax in greater details:
    1. First, specify the main table (T1) and the table that you want the main to join to (T2) after the UPDATE clause. Notice that you must pecify at least on table after the UPDATE clause. The data in the table that is not specified after the UPDATE clause will not be updated.
    2. Next, specify a kind of join you want to use, either INNER JOIN or LEFT JOIN and a join predicate. The JOIN clause must appear right after the UPDATE clause.
    3. Then, assign new values to the columns in T1 and/or T2 tables that you want to update.
    4. After that, specify a condition in the WHERE clause to limit rows to rows for updating.
