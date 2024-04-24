# Операционные системы и виртуализация (Linux) (семинары)
## Урок 6. Запуск стека для веб-приложения
### Задание

• Установить Nginx и настроить его на работу с PHP-FPM.

• Установить Apache. Настроить обработку PHP. Добиться одновременной работы с Nginx.

• Настроить схему обратного прокси для Nginx (динамика - на Apache).

• Установить MySQL. Создать новую базу данных и таблицу в ней.

•* Установить пакет phpmyadmin и запустить его веб-интерфейс для управления MySQL.

•* Настроить схему балансировки трафика между несколькими серверами Apache на стороне Nginx с помощью модуля ngx_http_upstream_module.


# Решение

• Установить Nginx и настроить его на работу с PHP-FPM.

```
nano /etc/netplan/01-network-manager-all.yaml 

sudo apt install nginx -y

nginx status

nginx --help

nginx

sudo service nginx status

ip a

sudo apt install apache2 -y

```

После установки nginx и apache настроены на один порт!

Настройка nginx

```
ls -a

cd /etc/nginx

ll

sudo nano nginx.conf 

ll conf.d/

alias -l

alias list

alias

ll sites-enabled/

sudo nano default

sudo nano sites-enabled/default

sudo nginx -t

cd

sudo nano /etc/apache2/apache2.conf 

sudo nano /etc/apache2/ports.conf
```
Настройка портов ports.conf
 
```
 5 Listen 9876
 6
 7 <IfModule ssl_module>
 8         Listen 443
 9 </IfModule>
10
11 <IfModule mod_gnutls.c>
12         Listen 443
13 </IfModule>
14
```

```
sudo nano /etc/apache2/sites-enabled/000-default.conf 

cd /var/www/html

nano index.html 

sudo nano index.html 

sudo service apache2 restart

sudo nano /etc/nginx/sites-enabled/default 

sudo cp ~/.nanorc /root

sudo nano /etc/nginx/sites-enabled/default 

sudo service nginx restart

sudo nano /etc/nginx/sites-enabled/default 

sudo service nginx restart

sudo nano info.php

sudo apt install libapache2-mod-php -y

```
![nginx](/pic/hw0601.png)
![apache2](/pic/hw0602.png)

• Установить ***MySQL***. Создать новую базу данных и таблицу в ней.

```
sudo apt install mysql-server

sudo mysql

sudo service mysql status
```
### Команды SQL:
```
show databases;

use gb;

show tables;

SELECT* FROM users;

```
![](/pic/hw0603.png)

### Простой сервер на Python

```
sudo apt install python3-dev pip

cd

ll

nano python-server.py
```

Создаём python-server.py
```
from flask import Flask
import datetime
app = Flask(__name__)
@app.route("/")
def first():
    return f"<h1>{datetime.datetime.now()}</h1>"
app.run("0.0.0.0", 6789)
```

Запускаем простой сервер на python 

```
python3 python-server.py 

python3 -m pip install flask

python3 python-server.py 

exit
```

![](/pic/hw0604.png)