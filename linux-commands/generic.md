<!-- TITLE: Generic -->
<!-- SUBTITLE: Generic linux commands -->

# File system
## Mount windows network drive
```text
mount -t cifs -o username=jiko,password={password},vers=1.0 //jiko-alpha/www /media/jiko/alpha

mount -a
```

## Find
Example: all .htaccess files in /var/www
```text
find /var/www -iname .htaccess -print
```

## .inputrc
### Fix backspace
```text
"\e[3~": delete-char # this is actually equivalent to "\C-?": delete-char # VT "\e[1~": beginning-of-line "\e[4~": end-of-line # kvt "\e[H":beginning-of-line "\e[F":end-of-line # rxvt and konsole (i.e. the KDE-app...) "\e[7~":beginning-of-line "\e[8~":end-of-line
```

## Rsync

```text
#!/bin/sh
rsync -avzh --force --exclude-from '.rsyncexclude' --filter "P blog/" --filter "P nextlevel/" --progress --delete-after --delete-excluded -e "ssh -p 2275" root@giterdone.postcardmania.com:/home/git1/public_html/files/ ~/public_html/files
```

## Make directory with missing parents
Will make var and www folders if they are missing
```text
mkdir -p /var/www/sync
```

# Cron
## Run cron as user
```text
$ crontab -u www-data -e
```


# SSH
## Run remote command as sudo with inline password
```text
 ssh remwebqa.bhn.net "echo {password} | sudo -S cp /from/file.txt /to"
```
