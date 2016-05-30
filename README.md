MySQL Connector/Python
====

### Requirements

mysql-connector (version >= 2.2.3) requires [Protobuf C++](https://developers.google.com/protocol-buffers/docs/downloads) (version >= 2.6.0)

Install **Protobuf** on your platform. e.g., on macOS: `brew install protobuf`, and then specify the install paths:
```bash
# Use the proper paths based on your installation
export MYSQLXPB_PROTOBUF_INCLUDE_DIR=/usr/local/opt/protobuf/include
export MYSQLXPB_PROTOBUF_LIB_DIR=/usr/local/opt/protobuf/lib
export MYSQLXPB_PROTOC=/usr/local/opt/protobuf/bin/protoc
```

### Installation

From PyPI (recommend)
```bash
pip install mysql-connector
```

From source code
```bash
python setup.py install
```

### Documentation

Documentation for all Connector/Python versions can be found online here:

[dev.mysql.com/doc/connector-python/en/](http://dev.mysql.com/doc/connector-python/en/)

The source distribution of Connector/Python also contains example scripts. They can be found in the examples/ directory.

### Examples

```python
import mysql.connector
from mysql.connector import errorcode

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
    if err.errno == errorcode.ER_ACCESS_DENIED_ERROR:
        print('Something is wrong with your user name or password')
    elif err.errno == errorcode.ER_BAD_DB_ERROR:
        print("Database does not exist")
    else:
        print(err)
else:
    cur = cnx.cursor()
    cur.execute('show databases;')
    for row in cur.fetchall():
        print(row)
finally:
    if cur:
        cur.close()
    if cnx:
        cnx.close()
```
