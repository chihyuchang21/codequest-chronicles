# 1. PostgreSQL Setup and Basic Commands
- **Installation**: Download PostgreSQL from the [official website](https://www.postgresql.org/download/) or use PostgreSQL.app for Mac users.
- **Basic Commands**:
    - Default schema is `public`; use `\dn` to list all schemas.
    - SQL statements end with `;`. Multi-line statements are supported until `;` is added.
    - Comments start with `--`.
    - **Case Sensitivity**: SQL commands are generally case insensitive, but enclosing identifiers in `""` (double quotes) preserves case (e.g., `SELECT "authorId" FROM posts;`).
    - Access example code from this [link](https://shwu10.cs.nthu.edu.tw/courses/databases/2020-spring/sql_query/blob/master/01-postgresql-example.md).

# 2. Core SQL Concepts
- **Data Definition Language (DDL)**: Used to define and modify database structures.
    - `CREATE TABLE` – Creates a new table.
    - `ALTER TABLE` – Modifies an existing table.
    - `DROP TABLE` – Deletes a table from the database.
- **Data Manipulation Language (DML)**: Used to manage records in tables.
    - `INSERT INTO` – Adds new records to a table.
    - `SELECT` – Retrieves data from a table.
    - `UPDATE` – Modifies existing records.
    - `DELETE FROM` – Removes records from a table.
- **Schema Example**:
    - Columns can have various types, such as `integer`, `text`, `varchar(255)`.
    - Constraints can enforce rules, including `NOT NULL`, default values, and relationships through `PRIMARY KEY` and `FOREIGN KEY`.
    - Example schema setup: Creating a `posts` table with a `FOREIGN KEY` linking `authorId` to a user in the `users` table.

# 3. Data Insertion and Querying
- **Inserting Data**:
    - String values should be enclosed in single quotes (e.g., `'Today is a good day!'`).
    - Bulk insertions are possible using `generate_series` for dummy data.
    - Example:
      ```sql
      INSERT INTO posts(text, "authorId")
      VALUES ('Sample post text', 1);
      ```
    - **Dummy Data Generation**:
      ```sql
      INSERT INTO posts(text, "authorId")
      SELECT 
        'Dummy post ' || i || '.',
        round(random() * 10) + 1
      FROM generate_series(1, 20) AS s(i);
      ```
- **Basic Querying**:
    - A typical query may look like:
      ```sql
      SELECT * 
      FROM posts 
      WHERE ts > 147988213 AND text ILIKE '%good%'
      ORDER BY ts DESC, id ASC
      LIMIT 2;
      ```
    - **Performance Analysis**: Use `EXPLAIN ANALYZE` before the query to display query execution plan and timing.

# 4. Indexing and Performance Optimization
- **Managing Large Data**:
    - For tables with many rows, batch inserts and efficient queries become critical.
    - Example for adding many rows at once:
      ```sql
      INSERT INTO posts(text, "authorId")
      SELECT 
        'Bulk insert text ' || i || '.',
        round(random() * 10) + 1
      FROM generate_series(1, 1000000) AS s(i);
      ```
- **Indexing**:
    - **B-tree Index**: Commonly used for numerical columns (e.g., `ts` - timestamp).
      ```sql
      CREATE INDEX posts_idx_ts ON posts USING btree(ts);
      ```
    - **GIN Index for Text Searches**: Useful for optimizing searches with `ILIKE`. Requires `pg_trgm` extension for advanced text search.
        - Installation of extension:
          ```sql
          CREATE EXTENSION pg_trgm;
          ```
        - Example of GIN indexing for text:
          ```sql
          CREATE INDEX posts_idx_text_trgm ON posts USING gin(text gin_trgm_ops);
          ```
    - **Performance Comparison**:
        - Without GIN index:
          ```sql
          EXPLAIN ANALYZE SELECT * FROM posts WHERE text ILIKE '%some text%';  -- slower
          ```
        - With GIN index:
          ```sql
          EXPLAIN ANALYZE SELECT * FROM posts WHERE text ILIKE '%some text%';  -- faster
          ```
- **Checking Indexes**: Use `\di` in PostgreSQL to list all available indexes in the database.





