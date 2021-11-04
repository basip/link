## Upgrading database for Link instances from v1.1.x to v1.2.x

### Problem

When you run new docker-compose script, all containers starting, but user doesn't see Link application login page in browser.

If you check link-app container logs with command ```docker logs link-app```, you will see
```
t=2021-11-04T12:13:14+0000 lvl=eror msg="database is unavailable" attempts=0 err="Error 1130: Host '192.168.176.6' is not allowed to connect to this MySQL server"
t=2021-11-04T12:13:24+0000 lvl=eror msg="database is unavailable" attempts=10 err="Error 1130: Host '192.168.176.6' is not allowed to connect to this MySQL server"
t=2021-11-04T12:13:34+0000 lvl=eror msg="database is unavailable" attempts=20 err="Error 1130: Host '192.168.176.6' is not allowed to connect to this MySQL server"
t=2021-11-04T12:13:44+0000 lvl=eror msg="database is unavailable" attempts=30 err="Error 1130: Host '192.168.176.6' is not allowed to connect to this MySQL server"
```

Obviously there are database connection problems. Let's fix them.

### Solution

The user needs to update the mysql server root user to allow remote connection (from the link app container)

1. Copy script ```db-upgrade.sql``` on target machine to ```/home/link-upgrade``` 
2. Run command below when new docker-compose script already running and all docker containers have STATUS = UP

```bash
docker exec -i link-db /bin/sh -c "mysql -uroot -pQwerty12345" < /home/link-upgrade/db-upgrade.sql
```

Check link-app container logs
```bash
docker logs link-app
```
last 10 rows will be 
```bash
2021-11-04 12:16:54,537 INFO success: laravel-queue-sip-service_00 entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
2021-11-04 12:16:54,537 INFO success: laravel-queue-device-logs_00 entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
2021-11-04 12:16:54,537 INFO success: nginx entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
2021-11-04 12:16:54,537 INFO success: laravel-queue-device-task_04 entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
2021-11-04 12:16:54,537 INFO success: laravel-queue-device-task_01 entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
2021-11-04 12:16:54,537 INFO success: laravel-queue-device-task_00 entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
2021-11-04 12:16:54,537 INFO success: laravel-queue-device-task_03 entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
2021-11-04 12:16:54,538 INFO success: laravel-queue-device-task_02 entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
2021-11-04 12:16:54,538 INFO success: laravel-queue-announces_00 entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
2021-11-04 12:16:54,538 INFO success: laravel-queue-alerts_00 entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
```

Then check if Link application is available in your browser.

### Thanks
