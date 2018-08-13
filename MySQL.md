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
https://www.terlici.com/2015/08/13/mysql-node-express.html


