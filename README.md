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

## Create a Custom Site
```
$ vim /etc/apache2/sites-available/example.com.conf
```


## Virtual Hosts






