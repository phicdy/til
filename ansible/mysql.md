
```yaml
- name: create user who can select and update name
  mysql_user: 
	user=update_name
	password=hoge
	priv=test_db.user:select,update(name) 
	host=localhost
	state=present 
	login_user=root 
	login_password=root_pass
```
