## Change proxy

```bash
git config --global http.proxy http://your.proxy:8080
git config --global https.proxy http://your.proxy:8080

# check setting
git config --list

# remove proxy setting
git config --global http.proxy ""
git config --global https.proxy ""
```
