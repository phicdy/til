## Store data to MariaDB by MySQLdb

```python
import MySQLdb

try:
	mariadb_connection = MySQLdb.connect(
		host='localhost',
		user='root',
		passwd='your_pass',
		db='your_db')
	cursor = mariadb_connection.cursor()
	cursor.execute("INSERT INTO user(name, address) VALUES (%s,%s)", ('hoge', 'hoge'))
	mariadb_connection.commit()
	syslog.syslog(syslog.LOG_INFO, "The last inserted id was: ", cursor.lastrowid)
	mariadb_connection.close()
except Exception as error:
	syslog.syslog(syslog.LOG_INFO, "Error: {}".format(error))
	return False, 'Error: Failed to store'
return True, ''
```
