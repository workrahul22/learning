```mysql
    create or replace view order_summary
    as
    select o.order_id, o.date, p.product_name, c.cust_name
        , (p.price * o.quantity) - ((p.price * o.quantity) * disc_percent::float/100) as cost
    from tb_customer_date c
    join tb_order_details o on o.cust_id = c.cust_id
    join tb_product_info p on p.prod_id = o.prod_id;

    select * from order_summary;
```

### We use views for 2 inportant reasons
- security
- to reference reusable queries inside complex queries

### Rules when using CREATE OR REPLACE
- Cannot change column name
- Cannot change column data type
- Cannot change order of the column (we can add column at the end)
- you cange anything in join column

### We can change the column using
```mysql
    alter view order_summary rename column date to order_date;
```

### Rename the view name
```mysql
    alter view order_summary rename to order_summary_2
```

### Drop view
```mysql
    drop view order_summary_2
```

```mysql
    create view expensive_products
    as
    select * from tb_product_info where price > 1000;

    select * from expenside_products
```

### if we add new column in the table it will not be added to the view
```mysql
    alter table tb_product_info add column prod_config varchar(100)

    select * from expensive_products;
```
### Updatable views
- views should be created using 1 table/view only
```mysql
    update expendive_products set prod_name = "Airpods Pro, brand = 'Apple'
    where prod_id = 'P10';
```
The underlying table will also be updated

```mysql
    update order_summary set cost = 10 where ord_id = 1
```
Update will not work as this views use join

- cannot have distinct clause
```mysql
     create or replace view expensive_products
     as
     select distinct * from tb_product_info where price > 1000;

     select * from expensive_products;

     update expensive_products
     set prod_name = "Airpods Pro 2', brand = 'Apple'
     where prod_id = 'P10';
```

- if query contains GROUP BY the can not update such views.
```mysql
    create view order_count
    as
    select date, count(1) as no_of_order
    from tb_order_details
    group by date;

    select * from order_count;

    update order_count
    set no_of_order = 0
    where date = '2020-06-01';
``` 

- if query contains with clause then cannot update such views.
- If query contains window functions then cannot update such views.

### With check option
```mysql
    create or replace view apple_products
    as
    select * from tb_product_info where brand 'Apple'
    with check option;

    insert into apple_products
    values ('P20','Note 20', 'Samsung', 2500, null);

    select * from apple_products;
    select * from tb_product_info;
```