
```bash
DocumentRoot "/var/www/html"
<Directory "/var/www/html">
	# Redirect http://host/ to http://host/hoge
	Redirect /index.html /hoge
</Directory>
```
