
1. Copy httpd binary to same directory like /usr/sbin/
2. Copy /etc/httpd directory under /etc
3. Change IP or port in copied httpd.conf
4. Copy httpd.service from /usr/lib/systemd/system/ to same directory
5. Edit copied httpd.service to load copied httpd.conf
6. Create symlink of copied service from /etc/systemd/system/multi-user.target.wants/ to /usr/lib/systemd/system/<copied httpd.service>
7. Reload daemon by systemctrl daemon-reload

### Copied httpd.service

```bash
[Unit]
Description=The Apache HTTP Server for uncheck flag API
After=network.target remote-fs.target nss-lookup.target
Documentation=man:httpd(8)
Documentation=man:apachectl(8)

[Service]
Type=notify
EnvironmentFile=/etc/sysconfig/httpd
ExecStart=/usr/sbin/secondhttpd -f /etc/secondhttpd/conf/httpd.conf $OPTIONS -DFOREGROUND
ExecReload=/usr/sbin/secondhttpd -f /etc/secondhttpd/conf/httpd.conf $OPTIONS -k graceful
ExecStop=/bin/kill -WINCH ${MAINPID}
# We want systemd to give httpd some time to finish gracefully, but still want
# it to kill httpd after TimeoutStopSec if something went wrong during the
# graceful stop. Normally, Systemd sends SIGTERM signal right after the
# ExecStop, which would kill httpd. We are sending useless SIGCONT here to give
# httpd time to finish.
KillSignal=SIGCONT
PrivateTmp=true

[Install]
WantedBy=multi-user.target
```

### References

* [CENTOS7でapacheを複数起動](http://blog.livedoor.jp/k_shin_pro/archives/44027682.html)
* [\[apache\]Apache を同一サーバ上で複数プロセス起動するときに注意する点](http://d.hatena.ne.jp/amari3/20111219/1324305891)
