Spotweb from docker-compose
===========================

Quick config:
-------------

After pulling this project, get spotweb sources too:

```
$ git submodule update --init --recursive
```

Fix cache path permissions since internal user with id **www-data** (id 82) must have accesss:

```
$ mkdir spotweb-src/cache
$ sudo chown 82:82 spotweb-src/cache
```

Create MariaDB docker volume:

```
$ docker volume create spotweb-db
```

And start it up:

```
$ docker-compose up -d
```

... and visit http://localhost:9080


After going thru *spotweb* setup **spotweb-src/dbsettings.php.inc** should look like:

```
<?php

$dbsettings['engine'] = 'pdo_mysql';
$dbsettings['host'] = 'db';
$dbsettings['dbname'] = 'spotweb';
$dbsettings['user'] = 'spotweb';
$dbsettings['pass'] = 'spotweb';
$dbsettings['port'] = '3306';
$dbsettings['schema'] = '';
```

To update *Spotweb* sources:
----------------------------


```
$ docker-compose stop
$ cd spotweb
$ git pull
$ cd ..
$ docker-compose up -d
```

If GUI reports:

"Spotweb contains updated global settings settings. Please run 'bin/upgrade-db.php' from a console window "

```
$ docker exec -it dockerspotweb_php_1 /bin/sh
$ cd /opt/spotweb
$ php bin/upgrade-db.php
```
