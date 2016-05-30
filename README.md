MySQL Connector/Python 2.1
====

This is fork of MySQL offical maintained [mysql-connector-python](https://github.com/mysql/mysql-connector-python).

MySQL Connector/Python

Copyright (c) 2009, 2015, Oracle and/or its affiliates. All rights reserved.

License information can be found in the LICENSE.txt file.


### Installation

```bash
pip install mysql-connector
```


### Documentation

Documentation for all Connector/Python versions can be found online here:
 
[dev.mysql.com/doc/connector-python/en/](http://dev.mysql.com/doc/connector-python/en/)

The source distribution of Connector/Python also contains example scripts.
They can be found in the examples/ directory.

### Examples

```python
import mysql.connector

config = {
    'user': 'root',
    'password': '',
    'host': '127.0.0.1',
    'database': 'test'
}

cnx = cur = None
try:
    cnx = mysql.connector.connect(**config)
except mysql.connector.Error as err:
    if err.errno == mysql.connector.ER_ACCESS_DENIED_ERROR:
        print('Something is wrong with your user name or password')
    elif err.errno == mysql.connector.ER_BAD_DB_ERROR:
        print("Database does not exist")
    else:
        print(err)
else:
    cur = cnx.cursor()
    cur.execute('show databases;')
    for db in cur.fetchall():
        print(db[0])
finally:
    if cur:
        cur.close()
    if cnx:
        cnx.close()

```


