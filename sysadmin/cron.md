# Cron

### Create cronjob

```
sudo crontab -e
```

```
@daily /usr/bin/docker volume prune -f
```
