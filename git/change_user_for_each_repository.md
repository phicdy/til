## Change user for each repository

```bash
cd repository_to_change_user
git config user.name "your_name"
git config user.email "your_email"

# check config
cat .git/config
#[core]
#        repositoryformatversion = 0
#        filemode = true
#        bare = false
#        logallrefupdates = true
#        ignorecase = true
#        precomposeunicode = true
#[remote "origin"]
#        url = https://github.com/phicdy/til.git
#        fetch = +refs/heads/*:refs/remotes/origin/*
#[branch "master"]
#        remote = origin
#        merge = refs/heads/master
#[user]
#        name = phicdy
#        email = phicdy@gmail.com
```
