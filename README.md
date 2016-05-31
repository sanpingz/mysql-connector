MySQL Connector/Python
====

This is a fork of MySQL offical maintained [mysql-connector-python](https://github.com/mysql/mysql-connector-python).
Aim to get started easily for beginners.


### Installation

```bash
pip install mysql-connector
```


### Documentation

Documentation for all Connector/Python versions can be found online here:
 
[dev.mysql.com/doc/connector-python/en/](http://dev.mysql.com/doc/connector-python/en/)


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
    for row in cur.fetchall():
        print(row[0])
finally:
    if cur:
        cur.close()
    if cnx:
        cnx.close()

```


