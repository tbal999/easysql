# easysql
easiliy work with sql in go with this
Currently uses the MSSQL driver: github.com/denisenkom/go-mssqldb

Simply import it into your go project.

then use as following:

rowcount, output, error := easysql.SQLquery("login string", "query)

the output is a []string so you can work with it in go easily.
it can't handle all formats - for example datetime - so if you have a DATETIME output in SQL just change it to VARCHAR and it will work.



