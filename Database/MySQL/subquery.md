Find the employees who's salary is more than the average salary earned by all employees.

1. Find the average salary
```sql
    select avg(salary) from employee
```
2. Filtered the employee based on the above result.

```sql
    select * from employee
    where salary > (select avg(salary) from employee)
```

Types of subquery

scalar subquery: it always returns one row and one column
```sql
    select * from employee
    where salary > (select avg(salary) from employee)
```

```sql
    select *
    from employee e
    join (select avg(salary) sal from employee) avg_sal
    on e.salary > avg_sal.sal;
```

Multiple row subquery
    1. subquery which returns multiple column and multiple rows.
    2. subquery which returns only 1 column and multiple rows.

Find the employees who earn the highest salary in each department.
```sql
    select dept_name, max(salary)
    from employee e
    group by dept_name
```

```sql
    select * 
    from employee
    where (dept_name, salary) in (select dept_name , max(salary) from employee group by dept_name)
```

Find department who do not have any employees
```sql
    select *
    from department
    where dept_name not in (select distinct dep_name from employee)
```

correlated subquery: a subquery which is related to the outer query

find the employee in each department who earn more than the average salary in the department.
```sql
    select avg(salary) from empoyee where dept_name = <<specific_dept>>
```

```sql
    select * 
    from employee e1
    where salary > (
        select avg(salary) from employee e2
        where e2.dep_name = e1.dept_name
    )
```

Find department who do not have any employees

```sql
    select *
    from department d
    where not exists (
        select * from employee e
        e.dept_name = d.dept_name
        )
```

Nested Subquery

Find stores who's sales where better than the average sales across all stores
    1. find the total sales for each store
    2. find avg sales for all the stores
    3. compare 1 & 2

```sql
    select store_name, sum(price) as total_sales
    from sales
    group by store_name
```

```sql
    select avg(total_sales)
    from (
        select store_name, sum(price) as total_sales
        from sales
        group by store_name
    )
```

```sql
    select *
    from (
        select store_name, sum(price) as total_sales
        from sales
        group by store_name
    ) sales
    join (
        select avg(total_sales) as sales
        from (
            select store_name, sum(price) as total_sales
            from sales
            group by store_name
        )
    ) avg_sales
    on sales.total_sales > avg_sales.sales;
```

if your query got multiple similar subquery then use with clause

```sql
    with sales as (
        select store_name, sum(price) as total_sales
        from sales
        group by store_name
    )
    select *
    from sales
    join (
        select avg(total_sales) as sales 
        from sales
    ) avg_sales
    on sales.total_sales > avg_sales.sales;
```

Clauses in SQL where we can use subquer
1. select
2. from
3. where
4. having

subquery in SELECT clause
Fetch all employee details and add remarks to those employees who earn more than the average pay.

```sql
    select *, (
        case when salary > (select avg(salary) from employee)
            then 'Higher than average'
            else null
        end
    ) as remarks
    from employee
```

Always avoid using subquery in select

```sql
    select *, (
        case when salary > avg_sal.sal
            then 'Higher than average'
            else null
        end
    ) as remarks
    from employee
    cross join (select avg(salary) sal from employee) avg_sal
```

subquery with having clause

Find the stores who have sold more units than the average units sold by all stores.

```sql
    select store_name, sum(quantity)
    from sales
    group by store_name
    having sum(quantity) > (select avg(quantity) from sales);
```

Sql commands where we can use subquery

1. SQL Query
2. Insert
3. Update
4. Delete

1. Insert
Insert data to employee history table. Make sure not insert duplicate records.
```sql
    insert into employee_history
    select e.emp_id, e.emp_name, d._dept_name, e.salary, d.location
    from employee e
    join department d on d.dep_name = e.dept_name
    where not exists (select 1 from employee_history eh where eh.emp_id = ememp_id)
```

2. Update

Give 10% increment to all employees in Bangalore location based on the maximum salary earned by an emp in each dept. Only consider employees in employee_history table

```sql
    update employee e
    set salary = (
        select max(salary) + max(salary) * 0.1
        from employee_hostory eh
        where eh.dept_name = e.dept_name
    )
    where e.dept_name in (select dept_name from department where location='Bangalore')
    and e.empt_id in (select empt_id from employee_history);
```

3. delete

Delete all departments who do not have any employees.

```sql
    delete from department
    where dept_name in (
        select dept_name
        from department d
        where not exists (
            select 1 from employee e
            where e.dept_name = d.dept_name
        )
    )
```

