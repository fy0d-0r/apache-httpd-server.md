# Apache Httpd Server

## Packages
```
apache2
apache2-doc
apache2-utils
libapache2-mod-*
```

## Configuration Files and Directories
```
/etc/apache2/sites-available/ #contain available sites configurations
```

## Basics
Enabling/Disabling modules
```
# a2enmod <MODULE>
# a2dismod <MODULE>
```
Enabling/Disabling sites
```
# a2ensite <SITE>
# a2dissite <SITE>
```

## Creating Custom Sites(Virtual Hosts)

```
# mkdir -p /var/www/example.com/public_html
# mkdir /var/www/example.com/logs

# mkdir -p /var/www/example.org/public_html
# mkdir /var/www/example.org/logs
```

```
# vim /etc/apache2/sites-available/example.com.conf
# vim /etc/apache2/sites-available/example.org.conf
```

```
<VirtualHost *:80>
	ServerAdmin webmaster@example.com
	ServerName example.com
	ServerAlias www.example.com
	DocumentRoot /var/www/example.com/public_html/
	ErrorLog /var/www/example.com/logs/error.log
	CustomLog /var/www/example.com/logs/access.log combined
</VirtualHost>
```
We can create multiple sites. For enabling perl,
```
<VirtualHost *:80>
	ServerAdmin admin@example.org
	ServerName example.org
	ServerAlias www.example.org
	DocumentRoot /var/www/example.org/public_html/
	ErrorLog /var/www/example.org/logs/error.log
	CustomLog /var/www/example.org/logs/access.log combined
	Options ExecCGI
	AddHandler cgi-script .pl
</VirtualHost>
```

```
# a2ensite example.com
# a2ensite example.org
# systemctl reload apache2
```

```
# apache2ctl -S
```

> NOTE: specific ip address in <VirtualHost> tap i.e <VirtualHost 1.2.3.4:80> has higher priority than wildcard.

## Rewrite Engine

- used to redirect one url to another url

```
# a2enmod rewrite
# systemctl restart apache2.service
```

/etc/apache2/000-default.conf
```
DocumentRoot /var/www/html
<Directory /var/www/html>
	AllowOverride All
</Directory>
```
This tells apache that the mod rewrite will be able to override the url for this virtual host at this directory level.


/var/www/html/.htaccess
```
RewriteEngine On
RewriteRule ^index.html$ test.html
```

.htaccess
```
Redirect www.example.com example.com
```

### Regular Expressions

## Enabling HTTPS

### Certificate Authority 

`https://letsencrypt.org/`

### Certbot

- can be used for both nginx and apache

```
$ certbot --version
```


## OpenSSL













