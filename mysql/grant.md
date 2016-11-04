
## Allow only a specific column update

```mysql
GRANT UPDATE (name) on test.user to 'hoge'@'localhost' identified by password 'pass';
```

### Reference

* http://d.hatena.ne.jp/mir/20051012/p2
* http://qiita.com/shuntaro_tamura/items/2fb114b8c5d1384648aa
