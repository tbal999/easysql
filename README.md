# easysql - developed on 26th Sep.
Easily import string data with SQL in go (for data analysis) with this!
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
package main

import (
	"fmt"

	"github.com/tbal999/easysql"
)

func main() {
	sqlLogin := `Server=localhost;Database=master;Trusted_Connection=True;`

	sqlQuery := `SELECT COLUMN FROM TABLE`

	numberOfRows, result, err := easysql.SQLquery(sqlLogin, sqlQuery)

	if err != nil {
		fmt.Println(err.Error())
	}

	for index := range result {
		fmt.Println(result[index])
	}

	fmt.Printf("Grabbed %d rows", numberOfRows)
}
```

This library currently can't handle all types - for example datetime - so if you have a DATETIME output in SQL just change it to VARCHAR(255) and it will work.
Any format it cannot handle it will let you know by replacing all items in the column to 'CHANGE_TO_VARCHAR'. So then you can just adjust the SQL query slightly.



