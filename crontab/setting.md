## Setting

```bash
crontab -e
```

```
# --------- minutes
# | ------- hour
# | | ----  day
# | | | --  month 
# | | | | - day of week: 0=Sun, 1=Mon, 2=Tue, 3=Wed, 4=Thu, 5=Fri, 6=Sat, 7=Sun
# | | | | |
  * * * * * ./task.sh
```

### Check current task

```bash
crontab -l
```
