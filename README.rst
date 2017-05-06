Torndb
======

Unmaintained
------------

This package is not actively maintained, and since it exists primarily
for backwards compatibility with the module provided in Tornado prior
to version 3.0, I do not intend to make major changes or merge pull
requests that do so.  New projects are encouraged to choose a different
database package. Anyone interested in producing an updated version of
`torndb` is welcome to create a fork (under a new name)

Description
-----------

Torndb is a simple wrapper around `MySQLdb` that originally appeared
in Tornado (http://www.tornadoweb.org).  It is being moved into
a separate package for Tornado 3.0.

Limitations
-----------

Torndb does not support Python 3, or any database drivers other than
`MySQLdb` or `pymysql`.

Installation
------------

``pip install torndb``

Documentation
-------------

http://torndb.readthedocs.org

Change by Tsung 2016.11.21
--------------------------
增强一个小小功能。
1. Connection连接对象增加一个属性：last_executed, 用以获取最后一次执行的完整SQL，可以方便的查看、调试SQL语句

Change by Tsung 2017.5.7
--------------------------
自定义字典escape格式，方便在update时进行格式转换。
1. 使用示例
``` python
    db = torndb.Connection("127.0.0.1", "test", user="root", password="root")
    sql = 'update test set %s where id=%s'
    d_set = {'name': 'n3', 'age': '50'}
    params = [d_set, 2]
    db.update(sql, *params)
```