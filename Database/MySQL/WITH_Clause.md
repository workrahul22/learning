It is also called CTE : Common Table Expression
It is also called sub query factory

Fetch employees who earn more than average salary of all employees
```sql
    select *
    from employee e
    where e.salary > <<average_salary>>
```

```sql
    with average_salary (avg_sal) as 
        (select cast(avg(salary) as int) from employee)
    select *
    from employee e, average_salary av
    where e.salary > av.avg_sal;
```

Find stores who's sales where better than average sales across all stores
1. Total sales per each store -- Total Sales
```sql
    select s.store_id, sum(cost) as total_sales_per_store
    from sales s
    group by s.store_id
```
2. Find the average sales with respect all the stores -- Avg_Sales
```sql
    select cast(avg(x.total_sales_per_store) as int) avg_sales_for_all_store
    from (select s.store_id, sum(cost) as total_sales_per_store
    from sales s
    group by s.store_id) x
```

3. Find the stores where Total_sales > Avg_Sales of all stores.
```sql
    select * 
    from (select s.store_id, sum(cost) as total_sales_per_store
    from sales s
    group by s.store_id) total_sales
    join (select cast(avg(x.total_sales_per_store) as int) avg_sales_for_all_store
    from (select s.store_id, sum(cost) as total_sales_per_store
    from sales s
    group by s.store_id) x) avg_sales
    on total_sales.total_sales_per_store > avg_sales_for_all_stores;
```

```sql
    with 
        Total_Sales (store_id, total_sales_per_store) as
            (select s.store_id, sum(cost) as total_sales_per_store
            from sales s
            group by s.store_id)
        avg_sales (avg_sales_for_all_store) as 
            (select cast(avg(total_sales_per_store) as int) as avg_sales_for_all_stores from Total_Sales)
    select
    from Total_Sales ts
    join avg_sales av
    on ts.total_sales_per_store > av.avg_sales_for_all_stores 
```