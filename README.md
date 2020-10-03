# easysql - developed on 26th Sep.
Easily work with sql in go with this!
Currently uses the MSSQL driver: github.com/denisenkom/go-mssqldb
But you can fork it and replace it with another driver (i think)

Simply import it into your go project.

then use as following:
- login string is the connection i.e "Server=localhost;Database=master;Trusted_Connection=True"
- query is the SQL query in full
 
rowcount, output, error := easysql.SQLquery("login string", "query")

- rowcount = int which tells you how many rows pulled
- output = []string, the result of the SQL query (including column headers)

You can work with output using type conversion to change items from string to int or float or whatever you want.

Literal example:

```
sqlLogin := `Server=localhost;Database=master;Trusted_Connection=True;`

sqlQuery := `SELECT TABLE.COLUMN FROM TABLE`

numberOfRowsRetrieved, Result, err := backendsql.SQLquery(sqlLogin, sqlQuery)

```

This library can't handle all formats (or at least i haven't figured out how to make it work yet) - for example datetime - so if you have a DATETIME output in SQL just change it to VARCHAR and it will work.
Any format it cannot handle it will let you know by replacing all items in the column to 'CHANGE_TO_VARCHAR(255)' or something similar.



