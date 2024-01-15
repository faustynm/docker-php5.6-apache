# docker-php5.6-apache
Docker image with old php 5.6 running on apache2 with usual php extensions:

- php5.6
- php5.6-bcmath
- php5.6-curl
- php5.6-gd
- php5.6-mcrypt
- php5.6-mbstring
- php5.6-mysql
- php5.6-sqlite3
- php5.6-soap
- php5.6-xml
- php5.6-zip
- php5.6-xdebug

Based on Debian stretch

# sample usage
`docker run -d -v /var/www/html:/var/www/html -p 8000:80 alcalbg/php5.6-apache`

visit http://localhost:8000/

------
Potrzebne dwa kontenery 

---
Projekt WWW

sudo docker run -d -v /home/srv/public_html/ergomed/:/var/www/html -p 8000:80 --add-host 'DOCKER_HOST:$DOCKER_HOST' alcalbg/php5.6-apache

Pod adresem localhost:8000 będzie widoczna zawartośc katalogu: 
/home/srv/public_html/ergomed/
---

Docker z BD

Lista działajacych dokerów:

docker ps

Pobieranie adresu IP DOCKERA:

docker inspect <container ID>

// uruchomienie maszyny na dokerze

docker pull cytopia/percona-5.5
docker run -i -e MYSQL_ROOT_PASSWORD=lukasz --add-host 'DOCKER_HOST:172.17.0.8' docker pull cytopia/percona-5.5

// dostęp do dockera przez konsole

sudo docker exec -it b360b0c07eeb bash
lub
sudo docker exec -it IDDOKER /bin/bash

Zmiana hasła dla mysql w dockerze:

docker exec -it idkontenera mysql -uroot -p

// możliwośc połączenia z zewnątrz w mysql

ALTER USER root@% IDENTIFIED BY 'lukasz';
UPDATE mysql.user SET host='%' WHERE user='root';

// wgranie bazy sql

docker exec -i b360b0c07eeb mysql -u root -plukasz ergomed < ergomed.sql


------------
docker pull alcalbg/php5.6-apache
docker run -d -v /home/srv/public_html/ergomed/:/var/www/html -p 8000:80 alcalbg/php5.6-apache


docker pull cytopia/percona-5.5
docker run -i -e MYSQL_ROOT_PASSWORD=lukasz -t cytopia/percona-5.5
docker exec -it d4bf6fc60f31 mysql -uroot -p
create database ergomed;
SET PASSWORD FOR 'root' = PASSWORD('lukasz');
UPDATE mysql.user SET host='%' WHERE user='root';
docker exec -i d4bf6fc60f31 mysql -u root -plukasz ergomed < ergomed.sql

docker exec -it d4bf6fc60f31 mysql -uroot -p
UPDATE `operatorzy` SET `haslo` = md5('lukasz'), `ostatnia_zmiana_hasla` = '2024-01-15' WHERE `nazwa_uz` = 'admin' AND `nazwa_uz` = 'admin';


SET PASSWORD FOR 'root' = PASSWORD('lukasz');

