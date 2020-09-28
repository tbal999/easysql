# easysql
easiliy work with sql in go with this
Currently uses the MSSQL driver: github.com/denisenkom/go-mssqldb

Simply import it into your go project.

then use as following:

rowcount, output, error := easysql.SQLquery("login string", "query)

- rowcount = int which tells you how many rows pulled
- output = []string, the result of the SQL query (including column headers)

You can work with output using type conversion to change items from string to int or float or whatever you want.

This library can't handle all formats - for example datetime - so if you have a DATETIME output in SQL just change it to VARCHAR and it will work.
Any format it cannot handle it will let you know by replacing all items in the column to 'CHANGE_TO_VARCHAR(255)' or something similar.



