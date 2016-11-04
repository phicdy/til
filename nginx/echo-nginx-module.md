## Install

It needs to compile with nginx...

```bash
wget 'https://github.com/openresty/echo-nginx-module/archive/v0.60.zip'
unzip v0.60.zip
wget 'http://nginx.org/download/nginx-1.11.2.tar.gz'
tar -xzvf nginx-1.11.2.tar.gz
cd nginx-1.11.2/

# --prefix : path to install nginx
# --module-path : path to install module
# --add-dynamic-module: path of echo-nginx
./configure --prefix=/opt/nginx \
    --modules-path=/usr/local/nginx/modules \
    --add-dynamic-module=../echo-nginx-module

make -j2
make install
```

## nginx.conf setting

```bash
# need to set before events block
load_module "/usr/local/nginx/modules/ngx_http_echo_module.so";

events {
} 

http {
	server {
		location /sleep {
			echo_sleep 5;
			# if you want to use proxy_pass and echo_sleep, it needs to divide path
			#  https://github.com/openresty/echo-nginx-module/issues/5
			echo_exec /proxy;
		}

		location /proxy {
			proxy_pass http://other.server.com;
		}
	}
}
```

## References

* https://heartbeats.jp/hbblog/2016/02/nginx-dynamic-modules.html
* https://github.com/openresty/echo-nginx-module
