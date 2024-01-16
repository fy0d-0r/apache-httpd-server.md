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
$ a2enmod <MODULE>
$ a2dismod <MODULE>
```
Enabling/Disabling sites
```
$ a2ensite <SITE>
$ a2dissite <SITE>
```

## Creating Custom Sites(Virtual Hosts)
```
$ vim /etc/apache2/sites-available/example.com.conf
```

```
<VirtualHost *:80>
	ServerAdmin webmaster@example.com
	ServerName example.com
	ServerAlias www.example.com
	DocumentRoot /srv/www/example.com/public_html/
	ErrorLog /srv/www/example.com/logs/error.log
	CustomLog /srv/www/example.com/logs/access.log combined
</VirtualHost>
```

