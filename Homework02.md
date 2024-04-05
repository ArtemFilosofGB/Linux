# Операционные системы и виртуализация (Linux) (семинары)
## Урок 2. Работа с файлами и ссылками

### Задание

• Используя команду cat, создать два файла с данными, а затем объединить их.

Просмотреть содержимое созданного файла.
Переименовать файл, дав ему новое имя.

```
mkdir homework02

cd homework02/

cat > file01

cat > file02

cat file01 file02 > file0102

cat file0102

mv file0102 newfile
```

###  Созадании директории и файлы.

• Создать файл file1 и наполнить его произвольным содержимым.
Скопировать его в file2.
```
cat > file1

cp file1 file2

cat file2 
```
Создать символическую ссылку file3 на file1.
Создать жёсткую ссылку file4 на file1.
Посмотреть, какие айноды у файлов.
```
tree

ln file1 file3

tree

rm file3

tree

ln -s file1 file3

ln file1 file4

ls -ali
```
Удалить file1.
```
rm file1
```
Что стало с остальными созданными файлами?
Попробовать вывести их на экран.
```
afilosof@afilosof-VirtualBox:~/homework02$ rm file1

afilosof@afilosof-VirtualBox:~/homework02$ cat file3

cat: file3: Нет такого файла или каталога

afilosof@afilosof-VirtualBox:~/homework02$ cat file4

random info

4643413843141348443153513513

afilosof@afilosof-VirtualBox:~/homework02$ cat file2

random info

4643413843141348443153513513
```



• Дать созданным файлам другие, произвольные имена.
```
mv file2 newfile2

mv file3 newfile3

mv file4 newfile4
```

Терминал:
```
afilosof@afilosof-VirtualBox:~/homework02$ tree

.

├── file2

├── file3 -> file1

└── file4



0 directories, 3 files

afilosof@afilosof-VirtualBox:~/homework02$ mv file2 newfile2

afilosof@afilosof-VirtualBox:~/homework02$ mv file3 newfile3

afilosof@afilosof-VirtualBox:~/homework02$ mv file4 newfile4

afilosof@afilosof-VirtualBox:~/homework02$ tree

.

├── newfile2

├── newfile3 -> file1

└── newfile4


```
Создать новую символическую ссылку.
```
afilosof@afilosof-VirtualBox:~/homework02$ ln -s newfile2 linkfile2

afilosof@afilosof-VirtualBox:~/homework02$ tree

.

├── linkfile2 -> newfile2

├── newfile2

├── newfile3 -> file1

└── newfile4


```
Переместить ссылки в другую директорию.

```
afilosof@afilosof-VirtualBox:~/homework02$ mkdir folder

afilosof@afilosof-VirtualBox:~/homework02$ mv linkfile2 folder/linkfile2

afilosof@afilosof-VirtualBox:~/homework02$ mv newfile3 folder/newfile3

afilosof@afilosof-VirtualBox:~/homework02$ tree

.

├── folder

│   ├── linkfile2 -> newfile2

│   └── newfile3 -> file1

├── newfile2

└── newfile4

```

### Результат

Текст команд, которые применялись при выполнении задания.
Присылаем в формате текстового документа: задание и команды для решения (без вывода).
Формат — PDF (один файл на все задания).

### Решение

```
mkdir homework02

cd homework02/

cat > file01

cat > file02

cat file01 file02 > file0102

cat file0102

mv file0102 newfile

cat >> file02

mv file01 newfile02

tree

cat newfile02 

mkdir foldertodel

tree

mv file02 foldertodel/

mv newfile02 foldertodel/

tree

rm -r foldertodel

tree

cat > file1

cp file1 file2

cat file2 

tree

exit

cd homework02/

tree

ln file1 file3

tree

rm file3

tree

ln -s file1 file3

ln file1 file4

ls -ali

rm file1

cat file3

cat file4

cat file2

tree

mv file2 newfile2

mv file3 newfile3

mv file4 newfile4

tree

ln -s newfile2 linkfile2

tree

mkdir folder

mv linkfile2 folder/linkfile2

mv newfile3 folder/newfile3

tree

exit
```