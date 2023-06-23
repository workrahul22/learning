### FIRST_VALUE
- Write query to display the most expensive product under each category (corresponding to each record)
```sql
    select *,
    first_value(product_name) over (partition by product_category order by price desc) as most_exp_product
    from product
```

### LAST_VALUE
- Write query to display the least expensive product under each category (corresponding to each recor)
```sql
    select *,
    first_value(product_name) over (partition by product_category order by price desc) as most_exp_product
    last_value(product_name) over (partition by product_category order by price desc range between unbounded preceding and unbounded following) as least_exp_product
```




