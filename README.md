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

------------

Potrzebne dwa kontenery 

Projekt WWW
sudo docker run -d -v /home/srv/public_html/ergomed/:/var/www/html -p 8000:80 --add-host 'DOCKER_HOST:$DOCKER_HOST' alcalbg/php5.6-apache

Pod adresem localhost:8000 będzie widoczna zawartośc katalogu: 
/home/srv/public_html/ergomed/


Docker z BD
sudo docker run -d -v /home/srv/public_html/ergomed/:/var/www/html -p 3000:80  --add-host 'DOCKER_HOST:172.17.0.1' docker pull cytopia/mysql-5.5




Lista działajacych dokerów:
docker ps

Pobieranie adresu IP DOCKERA
docker inspect <container ID>

Zmiana hasła dla mysql w dockerze 
docker exec -it idkontenera mysql -uroot -p
SET PASSWORD FOR 'root' = PASSWORD('lukasz');

Wykonywanie poleceń konsolowych w konkretnym dokerze
docker exec -it IDDOKER /bin/bash



