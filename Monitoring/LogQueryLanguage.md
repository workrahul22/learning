# There are two types of LogQL queries:

## Log queries : Return the contents of log lines.
## Metric queries: Extend log queries to calculate values based on query results.

## Binary Operators: +, -, *, /, %, ^
### Binary arithmetic operators are defined between two literals, a literals and a vector, and two vectors.

### Two Literals
```
    1 + 1
```

### Double the rate of a log stream's entries: A Literal and a vector
```
    sum(rate({app="foo"}[1m]))*2
```

### Get proportion of warning logs to error logs for the foor app
```
    sum(rate({app="foo", level="warn"}[1m])) / sum(rate({app="foo", level="error"}[1m]))
```



