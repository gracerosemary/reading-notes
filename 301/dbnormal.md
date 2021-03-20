## Database Normalization
- process used to organize a db into tables/columns
- table should only support a specific topic
- limit table to one purpose to reduce redundant data
- eliminates issues stemming from db modification

### Three main reasons to normalize a db
1. minimize duplicate data
2. minimize / avoid data modification issues
3. simplify queries

### Definition of Database Normalization
3 common forms: 1st (1NF), 2nd (2NF), 3rd (3NF)
- forms are progressive (to qualify for 3rd normal form, a table must first satisfy the rules for 2NF and 1NF. 
- 1NF: information is stored in a relational table with each column containing atomic values. No repeating groups of columns. 
- 2NF: table is in 1NF and all columns depend on the table's primary key. 
- 3NF: table is in 2NF and all columns are not transitively dependant on the primary key.