# Урок 3. Права доступа и безопасность

## Задание
* Создать два произвольных файла.
Первому присвоить права на чтение и запись для владельца и группы, только на чтение — для всех.
Второму присвоить права на чтение и запись только для владельца. Сделать это в численном и символьном виде.
Назначить новых владельца и группу для директории целиком.

```
touch file01 file02



chmod 664 file01

chmod u=rw file02

ll

chmod u=rw,g=rw,o=r file01

chmod 600 file02

ll
```

## Управление пользователями:

* создать пользователя, используя утилиту useradd и adduser;
* удалить пользователя, используя утилиту userdel.

```
useradd -s /bin/bash -m -d /home/testuser_hw03 testuser_hw03

sudo useradd -s /bin/bash -m -d /home/testuser_hw03 testuser_hw03

tail /etc/passwd

sudo passwd testuser_hw03 

sudo adduser testuser_hw03_2 

tail /etc/passwd

sudo userdel -rf testuser_hw03

tail /etc/passwd
```

## Управление группами:

* создать группу с использованием утилит groupadd и addgroup;
попрактиковаться в смене групп у пользователей;
добавить пользователя в группу, не меняя основной;

```
sudo groupadd newgroup_hw03

sudo usermod -g newgroup_hw03 testuser_hw03_2 

tail /etc/passwd

sudo usermod -aG testuser_hw03_2 

sudo usermod -aG newgroup_hw03 testuser_hw03_2 

tail /etc/passwd

sudo addgroup newgr_hw03

sudo usermod -aG newgr_hw03 testuser_hw03_2 

tail /etc/passwd

getent group
```
* Создать пользователя с правами суперпользователя. Сделать так, чтобы sudo не требовал пароль для выполнения команд.
```
sudo nano /etc/sudoers

sudo visudo 



getent groups

getent group

tail /etc/passwd

sudo su testuser_hw03_2
```

![visudo](/pic/Linux_hw03.png)


## Дополнительные (необязательные) задания

* Используя дополнительные материалы, выдать одному из созданных пользователей право на выполнение ряда команд, требующих прав суперпользователя (команды выбираем на своё усмотрение).

* Создать группу developer и нескольких пользователей, входящих в неё.
Создать директорию для совместной работы.
Сделать так, чтобы созданные одними пользователями файлы могли изменять другие пользователи этой группы.

```
sudo visudo

sudo groupadd developer

sudo usermod -aG second_user 

getent user

getent users

getent --help

tail /etc/passwd

sudo usermod -aG developer second_user 

sudo usermod -aG developer testuser_hw03_2 

tail /etc/passwd

getent group 

sudo mkdir developer_folder

pwd

sudo chmod 1770 /home/afilosof/homework03/developer_folder/

cd developer_folder/

sudo cd developer_folder/
```

* Создать в директории для совместной работы поддиректорию для обмена файлами, но чтобы удалять файлы могли только их создатели.

* Создать директорию, в которой есть несколько файлов.
Сделать так, чтобы открыть файлы можно было, только зная имя файла, а через ls список файлов посмотреть было нельзя.

# Решение

```
echo homework3

mkdir homework03

cd homework03

touch file01 file02

chmod 664 file01

chmod u=rw file02

ll

chmod u=rw,g=rw,o=r file01

chmod 600 file02

ll

echo Управление пользователями:

echo task2

useradd -s /bin/bash -m -d /home/testuser_hw03 testuser_hw03

sudo useradd -s /bin/bash -m -d /home/testuser_hw03 testuser_hw03

tail /etc/passwd

sudo passwd testuser_hw03 

sudo adduser testuser_hw03_2 

tail /etc/passwd

sudo userdel -rf testuser_hw03

tail /etc/passwd

echo task03

pwd

sudo groupadd newgroup_hw03

sudo usermod -g newgroup_hw03 testuser_hw03_2 

tail /etc/passwd

sudo usermod -aG testuser_hw03_2 

sudo usermod -aG newgroup_hw03 testuser_hw03_2 

tail /etc/passwd

sudo addgroup newgr_hw03

sudo usermod -aG newgr_hw03 testuser_hw03_2 

tail /etc/passwd

getent group

echo task03+

sudo nano /etc/sudoers

sudo visudo 



getent groups

getent group

tail /etc/passwd

sudo su testuser_hw03

sudo su testuser_hw03_2

echo donemainhw03

sudo visudo

sudo groupadd developer

sudo usermod -aG second_user 

getent user

getent users

getent --help

tail /etc/passwd

sudo usermod -aG developer second_user 

sudo usermod -aG developer testuser_hw03_2 

tail /etc/passwd

getent group 

sudo mkdir developer_folder

pwd

sudo chmod 1770 /home/afilosof/homework03/developer_folder/

cd developer_folder/

sudo su testuser_hw03

sudo su testuser_hw03_2

sudo su second_user

sudo su adim

sudo su admin

sudo visudo 

sudo su testuser_hw03_2

chmod g+rw developer_folder/

sudo chmod g+rw developer_folder/

cd developer_folder/

sudo cd developer_folder/

exit
```