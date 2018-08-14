# MySQL Reference

## Connecting SQL to node.js

```
var mysql      = require('mysql');
var connection = mysql.createConnection({
  host     : 'example.org',
  user     : 'bob',
  password : 'secret'
});

connection.connect(function(err) {
  if (err) {
    console.error('error connecting: ' + err.stack);
    return;
  }

  console.log('connected as id ' + connection.threadId);
});

module.exports = connection;
```

## Issues with connecting MySQL server to node.js

```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```
Where 'password' is the new password, unsure why this works but it does.

## Using MySQL with node.js in production
To create a table if it doesn't exist!
```
var createItems = `CREATE TABLE IF NOT EXISTS items(
                        id INT NOT NULL AUTO_INCREMENT,
                        name VARCHAR(255) NOT NULL,
                        instock INT NOT NULL,
                        total INT NOT NULL,
                        description TEXT,
                        signed_out_by VARCHAR(255),
                        PRIMARY KEY (id),
                        UNIQUE (name)
                    )`;
```

Models will be creation methods to hide the actual database query.

## Selecting rows with offset
```
SELECT * FROM tbl LIMIT 5,10;  # Retrieve rows 6-15
```

