## MySQL on CentOS7

http://stackoverflow.com/questions/25136498/ansible-answers-to-mysql-secure-installation

```yaml
- hosts: local
  become: yes
  vars_files:
    - mysql.yml
  tasks:
	- name: copy cnf to /etc/my.cnf.d/
      copy: src=./setting/etc/my.cnf.d dest=/etc/
    - name: copy cnf to /root/.my.cnf:welcome
      copy: src=./setting/etc/my.cnf.d/server.cnf dest=/root/.my.cnf owner=root mode=0600
    - name: install MariaDB
      yum: name=mariadb-server state=present
      notify:
        - enable and restart MariaDB
        - Sets the root password
        - Deletes anonymous MySQL server user for localhost
        - Deletes anonymous MySQL server user for localhost.localdomain
        - Secures the MySQL root user for IPV6 localhost (::1)
        - Secures the MySQL root user for IPV4 localhost (127.0.0.1)
        - Secures the MySQL root user for localhost domain (localhost)
        - Removes the MySQL test database
    - name: install MySQL-python
      yum: name=MySQL-python state=present

  handlers:
# MariaDB iniialization
    - name: enable and restart MariaDB
      service: name=mariadb.service enabled=yes state=restarted
    - name: Sets the root password
      mysql_user: user=root password={{ mysql_root_password }} host=localhost login_user=root login_password={{ mysql_root_password }}
    - name: Deletes anonymous MySQL server user for localhost
      mysql_user: user='' state=absent login_user=root login_password={{ mysql_root_password }}
    - name: Deletes anonymous MySQL server user for localhost.localdomain
      mysql_user: user='' host=localhost.localdomain state=absent login_user=root login_password={{ mysql_root_password }}
    - name: Secures the MySQL root user for IPV6 localhost (::1)
      mysql_user: user="root" password="{{ mysql_root_password }}" host="::1" login_user=root login_password={{ mysql_root_password }}
    - name: Secures the MySQL root user for IPV4 localhost (127.0.0.1)
      mysql_user: user="root" password="{{ mysql_root_password }}" host="127.0.0.1" login_user=root login_password={{ mysql_root_password }}
    - name: Secures the MySQL root user for localhost domain (localhost)
      mysql_user: user="root" password="{{ mysql_root_password }}" host="localhost" login_user=root login_password={{ mysql_root_password }}
    - name: Removes the MySQL test database
      mysql_db: db=test state=absent login_user=root login_password={{ mysql_root_password }}
```

### mysql.yml

```yaml
---
mysql_root_password: secure_pass
```
