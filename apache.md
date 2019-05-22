<!-- TITLE: Apache -->
<!-- SUBTITLE: A quick summary of Apache -->

# Apache

## Certbot

Create certificate (Don't modify apache config)
```text
certbot certonly -d local.joejiko.com,local.auth.joejiko.com,local.controls.house -w /var/www/local.joejiko.com/app-base/public
```

Test configuration
```text
certbot certonly -d local.joejiko.com,local.auth.joejiko.com,local.controls.house -w /var/www/local.joejiko.com/app-base/public --staging --dry-run
```

