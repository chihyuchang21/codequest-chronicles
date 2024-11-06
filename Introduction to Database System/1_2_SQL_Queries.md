# SQL Queries - Key Concepts

## 1. PostgreSQL Basics
- **Installation**: Download from [PostgreSQL official website](https://www.postgresql.org/download/). For Mac users, try [PostgreSQL.app](http://postgresapp.com/).
- **Commands**:
    - `$ createdb <db>`: Create a new database.
    - `$ psql <db> [user]`: Connect to a database.
    - `\h` or `\?`: Get command help.
    - **SQL Basics**:
        - SQL is case-insensitive but can use `""` to differentiate cases (e.g., `SELECT "authorId" FROM posts;`).
        - Comments are marked with `--`.

## 2. Structured Query Language (SQL)
- **Data Definition Language (DDL)**: Defines schema structure.
    - `CREATE TABLE …`
    - `ALTER TABLE …`
    - `DROP TABLE …`
- **Data Manipulation Language (DML)**: Operates on records.
    - `INSERT INTO … VALUES …`
    - `SELECT … FROM … WHERE …`
    - `UPDATE … SET … WHERE …`
    - `DELETE FROM … WHERE …`

## 3. Creating Tables and Relations
- **Column Types**: Integer, bigint, real, double, varchar(10), text, etc.
- **Primary Key**: A unique identifier for each row, often of type `serial`.
    - Automatically creates an index for faster lookups.
- **Foreign Key**: Ensures referential integrity between tables.
    - Example: `post.authorId` must reference a valid `user.id`.
    - `ON DELETE` options:
        - `NO ACTION` (default): Prevents deletion if linked records exist.
        - `CASCADE`: Deletes all related records when a user is deleted.

## 4. Inserting Rows
- **String values** should be enclosed in single quotes.
- Example insert:
  ```sql
  INSERT INTO posts(text, "authorId", ...)
  VALUES ('Today is a good day!', 5, ...);
