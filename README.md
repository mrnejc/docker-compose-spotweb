za update sources

$ docker-compose stop
$ cd spotweb
$ git pull
$ cd ..
$ docker-compose up -d

če GUI javi:

"Spotweb contains updated global settings settings. Please run 'bin/upgrade-db.php' from a console window "

$ docker exec -it dockerspotweb_php_1 /bin/sh
$ cd /opt/spotweb
$ php bin/upgrade-db.php
