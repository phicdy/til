## Store data to MariaDB by SQLAlchemy

## Install

```bash
pip install sqlalchemy
yum install -y Mysql-python
```

## Store

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
"""Data storage class by SQLAlchemy
"""
from sqlalchemy import create_engine
from sqlalchemy.engine.url import URL
from sqlalchemy.exc import SQLAlchemyError
from sqlalchemy.orm import sessionmaker

from User import User

url = URL(
	'mysql+mysqldb',
	'root',
	'your_pass',
	'localhost',
	3306,
	'your_db',
	None
)
engine = create_engine(url, encoding='utf-8')
store_sessionmaker = sessionmaker(autocommit=False, bind=engine)
session = store_sessionmaker()
try:
	user = User(name='hoge', address='hoge@hoge.com')
	session.add(user)
	session.commit()
except SQLAlchemyError as error:
	syslog.syslog(syslog.LOG_INFO, "Error: {}".format(error))
	session.rollback()
session.close()
```

## Data class

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
"""User table class for SQLAlchemy
"""
from sqlalchemy import Column, VARCHAR, INTEGER
from sqlalchemy.ext.declarative import declarative_base

Base = declarative_base()

class User(Base):
    __tablename__ = 'user'
    id = Column(INTEGER, primary_key=True)
    name = Column(VARCHAR(256))
    address = Column(VARCHAR(256))
```
