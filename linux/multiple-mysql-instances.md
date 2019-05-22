mysql@.service

```text
[Unit]
Description=MySQL Community Server (Multi)
After=network.target

[Install]
WantedBy=multi-user.target

[Service]
User=mysql
Group=mysql
PermissionsStartOnly=true
ExecStart=/usr/sbin/mysqld --defaults-group-suffix=@%I
TimeoutSec=600
Restart=on-failure
RuntimeDirectory=mysqld
RuntimeDirectoryMode=755

Usage:
service mysql@replica01 start
service mysql@replica02 start
```


/etc/mysql/mysql.conf.d/mysqld.cnf

```text
[mysqld@replica01]
user            = mysql
pid-file        = /var/run/mysqld/replica01.pid
socket          = /var/run/mysqld/replica01.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql/replica01
tmpdir          = /tmp
lc-messages-dir = /usr/share/mysql
skip-external-locking
bind-address            = 0.0.0.0
key_buffer_size         = 16M
max_allowed_packet      = 16M
thread_stack            = 192K
thread_cache_size       = 8

[mysqld@replica02]
bind-address            = 0.0.0.0
log-error=/var/log/mysql/replica02.log
user            = mysql
pid-file        = /var/run/mysqld/replica02.pid
socket          = /var/run/mysqld/replica02.sock
port            = 3307
basedir         = /usr
datadir         = /var/lib/mysql/replica02
tmpdir          = /tmp
query_cache_size=64M
innodb_buffer_pool_size=1024M

```

~/.my.cnf

```text
[mysql]
user=root
password=
socket=/var/run/mysqld/mysqld.sock
port=3308

[mysql@replica01]
user=root
password=
socket=/var/run/mysqld/replica01.sock
port=3306

[mysql@replica02]
user=root
password=
socket=/var/run/mysqld/replica02.sock
port=3307

[mysqldump]
user=root
password=
socket=/var/run/mysqld/mysqld.sock
port=3308

[mysqldump@replica01]
user=root
password=
socket=/var/run/mysqld/replica01.sock
port=3306

[mysqldump@replica02]
user=root
password=
socket=/var/run/mysqld/replica02.sock
port=3307
```


mysqldump --defaults-group-suffix=@replica01 ...