# [SQLBolt (Intro, Lessons 1-4, 13-18)](https://sqlbolt.com/)  

SQL: Structured Query Language

- designed to allow technical and non-technical users to query, manipulate, and transform data from relational database
- provides safe and scalable storage for millions of sites and applications

Relational Databases

- represents a collection of related (2-dimensional) tables
- each table has a fixed number of named columns (attributes/properties of the table) and any number of rows of data

### Lesson 1: SELECT queries

- `SELECT` statements (queries) are used to *retrieve* data from a SQL database
- query is a statement which declares what data we are looking for, where to find it in the database, and how to transform it before it's returned

```sql
/*Select query for a specific columns*/
SELECT column, another_column, ...
FROM mytable;
/*result will be a 2-dimensional set of rows and columns, but only with the columns that we requested*/
```

```sql
/*Select query for all columns by using asterisk*/
SELECT * 
FROM mytable;
```

### Lesson 2&3: Queries with constraints

- `WHERE` clause is used to filter certain results from being returned
- applied to each row of data by checking specific column values to determine whether it should be included in the results or not

```sql
/*Select query with constraints*/
SELECT column, another_column, …
FROM mytable
WHERE condition
    AND/OR another_condition
    AND/OR …;
```

- Complex clauses are constructed by joining `AND` or `OR` logical keywords
- allows the query to run faster due to the reduction in unnecessary data being returned

#### Useful Operators
| Operator            | Condition                                            | Example                       |
|---------------------|------------------------------------------------------|-------------------------------|
| =, !=, < <=, >, >=  | Standard numerical operators                         | col_name != 4                 |
| BETWEEN … AND …     | Number is within range of two values (inclusive)     | col_name BETWEEN 1.5 AND 10.5 |
| NOT BETWEEN … AND … | Number is not within range of two values (inclusive) | col_name NOT BETWEEN 1 AND 10 |
| IN (…)              | Number exists in a list                              | col_name IN (2, 4, 6)         |
| NOT IN (…)          | Number does not exist in a list                      | col_name NOT IN (1, 3, 5)     |

#### Text Specific Operators
| Operator   | Condition                                                                                             | Example                                                           |
|------------|-------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------|
| != or <>   | Case sensitive exact string inequality comparison                                                     | col_name != "abcd"                                                |
| LIKE       | Case insensitive exact string comparison                                                              | col_name LIKE "ABC"                                               |
| NOT LIKE   | Case insensitive exact string inequality comparison                                                   | col_name NOT LIKE "ABCD"                                          |
| %          | Used anywhere in a string to match a sequence of zero or more characters (only with LIKE or NOT LIKE) | col_name LIKE "%AT%"(matches "AT", "ATTIC", "CAT" or even "BATS") |
| _          | Used anywhere in a string to match a single character (only with LIKE or NOT LIKE)                    | col_name LIKE "AN_"(matches "AND", but not "AN")                  |
| IN (…)     | String exists in a list                                                                               | col_name IN ("A", "B", "C")                                       |
| NOT IN (…) | String does not exist in a list                                                                       | col_name NOT IN ("D", "E", "F")                                   |

- All strings must be quoted so that the query parser can distinguish words in the string from SQL keywords.

### SQL Lesson 4: Filtering and sorting Query results

- `DISTINCT` used to discard rows that have a duplicate column value
- `GROUP BY` used to discard duplicates based on specific columns using grouping

```sql
/*Select query with unique results*/
SELECT DISTINCT column, another_column, …
FROM mytable
WHERE condition(s);
```

- `ORDER BY` used to sort results by a given column in ascending/descending order
- when used, each row is sorted alpha-numerically based on the specified column's value

```sql
/*Select query with ordered results*/
SELECT column, another_column, …
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC;
```

- `LIMIT` and `OFFSET` are useful when indicating the subset of the results you care about
- `LIMIT` reduces the number of rows to return
- `OFFSET` (optional) will specify where to begin counting the number rows from

```sql
/*Select query with limited rows*/
SELECT column, another_column, …
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

## [Practice](https://www.w3schools.com/sql/trysql.asp?filename=trysql_select_all)  

## [Cheatsheet](http://www.cheat-sheets.org/sites/sql.su/)  

## [A Primer on SQL](https://openlibra.com/en/book/a-primer-on-sql-3rd-edition)  