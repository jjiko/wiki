<!-- TITLE: Mysql -->
<!-- SUBTITLE: A quick summary of Mysql -->

# mysqldump
Dump from remote to local
```text
mysqldump --add-drop-database --databases j5 jblog xbx | ssh -v local.joejiko.com "mkdir -p ~/mysql && cat >> ~/mysql/db-$(date '+%F').sql"
```

Dump local
```text
mysqldump --add-drop-database --databases j6 | mkdir -p ~/mysql && cat >> ~/mysql/alpha-db-$(date '+%F').sql
```

# mysql cli

Import
```text
mysql --defaults-group-suffix < file.sql
```
