# Others

## When should I use a unique constraint instead of a unique index

Under the hood a unique constraint is implemented the same way as a unique index - an index is needed to efficiently fulfil the requirement to enforce the constraint. Even if the index is created as a result of a UNIQUE constraint, the query planner can use it like any other index if it sees it as the best way to approach a given query.

So for a database that supports both features the choice of which to use will often come down to preferred style and consistency.

If you are planning to use the index as an index (i.e. your code may rely on searching/sorting/filtering on that field to be quick) I would explicitly use a unique index (and comment the source) rather than a constraint to make that clear - this way if the uniqueness requirement is changed in a later revision of the application you (or some other coder) will know to make sure a non-unique index is put in place of the unique one (just removing a unique constraint would remove the index completely). Also a specific index can be named in an index hint (i.e. WITH(INDEX(ix_index_name)), which I don't think is the case for the index created behind the scenes for managing uniqueness as you are unlikely to know its name.

Likewise if you are only needing to enforce uniqueness as a business rule rather than the field needing to be searched or used for sorting then I'd use the constraint, again to make the intended use more obvious when someone else looks at your table definition.

Note that if you use both a unique constraint and a unique index on the same field the database will not be bright enough to see the duplication, so you will end up with two indexes which will consume extra space and slow down row inserts/updates.

https://dba.stackexchange.com/questions/144/when-should-i-use-a-unique-constraint-instead-of-a-unique-index

## Performance

### single vs multiple row inserts

- 2 rows at a time: 3.5 - 3.5 seconds
- 5 rows at a time: 2.2 - 2.2 seconds
- 10 rows at a time: 1.7 - 1.7 seconds
- 50 rows at a time: 1.17 - 1.18 seconds
- 100 rows at a time: 1.1 - 1.4 seconds
- 500 rows at a time: 1.1 - 1.2 seconds
- 1000 rows at a time: 1.17 - 1.17 seconds

The time required for inserting a row is determined by the following factors, where the numbers indicate approximate proportions:

- Connecting: (3)
- Sending query to server: (2)
- Parsing query: (2)
- Inserting row: (1 × size of row)
- Inserting indexes: (1 × number of indexes)
- Closing: (1)

From this it should be obvious, that sending one large statement will save you an overhead of 7 per insert statement, which in further reading the text also says:

If you are inserting many rows from the same client at the same time, use INSERT statements with multiple VALUES lists to insert several rows at a time. This is considerably faster (many times faster in some cases) than using separate single-row INSERT statements.

https://dev.mysql.com/doc/refman/5.7/en/insert-optimization.html

## Enable incremental ETL

By enabling data engineers to identify new & updated records by accessing simple fields likecreated_timestampandupdated_timestamp. Make sure that both these fields are populated by the database and not the application. You should have a separate datetime or timestamp field if you want to populate it from the application.

https://towardsdatascience.com/table-design-best-practices-for-etl-200accee9cc9

## System Tables

In SQL Server these are often referred to as system tables and views. They can be found in the master database, which holds [data about the database](https://www.helenanderson.co.nz/search-sys-tables/). And in the system views within each database for specific information about each database.

In PostgreSQL, a similar collection of tables can be found in the information_schema and PostgreSQL catalog.

Examples of system views:

- sys.objects - shows each object, its type and created date
- sys.indexes - shows each index and type
- information_schema.columns - shows each column, it’s position and datatype

Examples of catalog objects:

- information_schema.tables - shows each object, its type and created date
- pg_index - shows each index and type
- information_schema.columns - shows each column, it’s position and datatype.

```sql
select user,host,plugin from mysql.user where plugin like '%native%';

ALTER USER '<dbuser>'@'localhost' IDENTIFIED WITH caching_sha2_password BY '<OLD PSWD here>';

CREATE USER '<dbuser>'@'%' IDENTIFIED WITH caching_sha2_password BY '<new_password>';
```

## Others

- https://towardsdatascience.com/6-sql-tricks-every-data-scientist-should-know-f84be499aea5
- [Sampling with SQL - Tom Moertel’s Blog](https://blog.moertel.com/posts/2024-08-23-sampling-with-sql.html)
