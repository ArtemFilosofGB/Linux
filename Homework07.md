# Операционные системы и виртуализация (Linux) (семинары)
## Урок 7. Запуск веб-приложения из контейнеров
### Задание

![](/pic/Homework07.png)


• Установить в виртуальную машину или VDS Docker, настроить набор контейнеров через docker compose по инструкции.
Часть с настройкой certbot и HTTPS опустить, если у вас нет настоящего домена и белого IP.

• Запустить два контейнера, связанные одной сетью (используя документацию).
Первый контейнер БД (например, образ mariadb:10.8), второй контейнер — phpmyadmin.
Получить доступ к БД в первом контейнере через второй контейнер (веб-интерфейс phpmyadmin).

_Установка Docker_


```
echo seminare7

sudo apt install docker.io docker-compose -y

sudo service apache2 stop

sudo service nginx stop
```

_Просмотр_

`ss -ntlp`

`sudo docker ps -a`
`sudo docker ps`

_Удаление_

`sudo docker -rm 37e9f84a9b64`

_Просмотр образов_

`sudo docker images`

_Поиск и скачивание контейнера_


```
sudo docker search nginx

sudo docker pull nginx

sudo docker ps

sudo docker ps -a
```

_Запуск контейнера(одного)_

```
sudo docker run -d -p 8888:80 --name my_nginx -v /var/www/html:/usr/share/nginx/html --restart always nginx

sudo docker ps -a

sudo docker ps
```

[localhoct:8888](localhoct:8888 "В браузере")

_Войти в контейнер_

`sudo docker exec -ti my_nginx bash`

_Остановка, удаление активного, удаление истории, удаление образа_

```
sudo docker ps
sudo docker ps -a
sudo docker images

sudo docker stop my_nginx

sudo docker rm 37e9f84a9b64

sudo docker rmi nginx

sudo docker ps

sudo docker ps -a
```

### WORDPRESS

[https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-docker-compose-ru](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-docker-compose-ru "Wordpress")

```
mkdir wordpress && cd wordpress

mkdir nginx-conf

nano nginx-conf/nginx.conf

nano .env

nano .dockerignore

nano docker-compose.yml

nano docker-compose -d

nano docker-compose up -d

sudo docker-compose up -d

sudo docker ps
```
