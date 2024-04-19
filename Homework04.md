# Урок 4. Подключение сторонних репозиториев, ручная установка пакетов


## Задание

• Подключить дополнительный репозиторий на выбор: Docker, Nginx, Oracle MySQL. Установить любой пакет из этого репозитория.

**MySQL**
```
sudo apt install libapache2-mod-php -y

sudo apt install mysql-server

sudo mysql

sudo service mysql status
```

**nginx**

```
sudo apt install nginx -y

nginx status

nginx --help

nginx

sudo service nginx status

ip a

cd /etc/nginx

sudo nano nginx.conf 
```
• Установить и удалить deb-пакет с помощью dpkg.
```
cd Загрузки

ls

sudo dpkg -i ./google-chrome stable_current_amd64.deb

``` 

• Установить и удалить snap-пакет.

```
sudo snap install telegram-desktop
sudo snap remove telegram-desktop
```

![tg](/pic/linux_telegram.png)


• Добавить задачу для выполнения каждые 3 минуты (создание директории, запись в файл).
```
sudo mrdir homework04
cd homework04/
touch file.log
crontab -e
```

Добавление задачи в cron
```
27 */3 * * * * mkdir /home/afilosof/homework04/new_cron_dir

28 */3 * * * * echo "Hello now: $(date)" >> /home/afilosof/homework04/file.log

```
![](/pic/Linux_hw04.png)
Просмотр файла

```
watch 0.5 file.log
```

* Подключить PPA-репозиторий на выбор. Установить из него пакет. Удалить PPA из системы.

* Создать задачу резервного копирования (tar) домашнего каталога пользователя. Реализовать с использованием пользовательских crontab-файлов.