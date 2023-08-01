## PostgreSQL and `psql` Tips and "Gotchas"

1. **Case Sensitivity**: PostgreSQL is case sensitive. By default, it assumes all table names and columns are lowercase. If you create a table or column with a mixed-case name, refer to it using double quotes, like `"MyTable"`.

2. **Semicolons are Required**: In `psql`, all SQL statements must end with a semicolon. If you see a message like `ERROR: syntax error at end of input`, it often means you've forgotten a semicolon.

3. **String Literals Need Single Quotes**: When inserting or updating text in PostgreSQL, make sure to wrap the string in single quotes (`'Your Text'`). Double quotes are used to refer to columns or table names.

4. **Transaction Control**: PostgreSQL uses a "commit" model for saving changes. If you start a transaction with `BEGIN` and make some changes, you won't see them saved in the database until you run `COMMIT`. To discard the changes, run `ROLLBACK`.

5. **Watch Out for NULLs**: In SQL, `NULL` isn't considered equal to anything, not even another `NULL`. This can lead to unexpected results when filtering data. To check for `NULL`, use `IS NULL` or `IS NOT NULL`.

6. **Use LIMIT During Development**: When running SELECT queries during development, use the `LIMIT` clause to avoid returning too many records accidentally, which can slow down your system.

7. **Watch Out for SQL Injection**: Never concatenate strings to build SQL queries without proper sanitization, as this can lead to SQL injection vulnerabilities. PostgreSQL provides the `E'your_text'` syntax to escape strings.

8. **Primary Keys and Indexes**: Remember to create primary keys for your tables as they uniquely identify each row in the database. Also, make use of Indexes. They can greatly speed up data retrieval but remember that they slow down data modification and consume more storage.

9. **Error Messages**: Pay close attention to error messages. PostgreSQL’s error messages come with a SQLSTATE error code, which can help you determine the cause of the problem.

10. **Data Types**: Choose your data types carefully. For example, prefer INTEGER over VARCHAR for numeric data. Incorrect choice of data types can lead to wasted disk space, decreased performance, and unwanted behaviors.

11. **psql Commands**: Remember that the commands that are specific to the `psql` interface (like `\dt` to list tables or `\q` to quit) are not standard SQL - they won't work in a different SQL client or in your application's PostgreSQL library.

---
