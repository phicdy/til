## 変数のraw文字列化

```python
'%r'%hoge
```

```bash
~ $ python3
Python 3.6.0 (default, Feb  7 2017, 18:05:03)
[GCC 4.2.1 Compatible Apple LLVM 8.0.0 (clang-800.0.42.1)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> hoge = '\n'
>>> print(hoge)


>>> print('%r'%hoge)
'\n'
```
