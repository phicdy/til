
```python
url = URL(
	'mysql+mysqldb',
	'user',
	'pass',
	'localhost',
	3306,
	'db_name',
	None
)
try:
	engine = create_engine(url, encoding='utf-8')
	store_sessionmaker = sessionmaker(autocommit=False, bind=engine)
	session = store_sessionmaker()
	users = session.query(User) \
		.filter(User.name == 'Suzuki') \
		.all()
	for user in users:
		user.age = 15
	session.commit()
except SQLAlchemyError as error:
	SyslogPrinter.print_error_info("Error: {}".format(error))
	session.rollback()
session.close()
```
