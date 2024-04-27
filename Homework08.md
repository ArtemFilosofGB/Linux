# Урок 8. Скрипты Bash
## Задание

• Написать скрипт очистки директорий.
На вход принимаддет путь к директории.
Если директория существует, то удаляет в ней все файлы с расширениями .bak, .tmp, .backup.
Если директории нет, то выводит ошибку.

• Создать скрипт ownersort.sh, который в заданной папке копирует файлы в директории, названные по имени владельца каждого файла.
Учтите, что файл должен принадлежать соответствующему владельцу.

## Результат

Код скриптов в текстовом виде (каждый скрипт в отдельном файле).
Кодировка файлов UTF-8.

Данная промежуточная аттестация оценивается по системе «зачёт» / «не зачёт»
— «Зачёт» ставится, если Слушатель успешно выполнил задание 1 или 2 задания
— «Незачёт» ставится, если Слушатель не выполнил задание.

Критерии оценивания

1 — Слушатель написал скрипт очистки директорий
2 — Слушатель создал скрипт ownersort.sh

# Решение
## Генерация bak файлов
![](/pic/hw08create.png)
В качестве агрумента чтсло файлов
create_bak.sh

```
if [ "$1" = "" ]; then
  echo "Использование: $0 <количество создаваемых файлов>"
  exit 1
fi
now=$(date '+%Y-%m-%d')
prefix="${now}_temp"
echo "Создание файлов, колличество - $1 "
echo "now=$now"
for i in $(seq 1 $1); do
  file="${prefix}_${i}.bak"
  touch $file
done
```


## Удаление  временных файлов

![](/pic/hw08_clean.png)
Как аргумент принимает путь для удаления 
script_clean.sh

```bash
cleanup_directory() {
    directory=$1
    # Проверяем существование директории
    if [ -d "$directory" ]; then
        # Удаляем файлы с расширениями .bak, .tmp, .backup
        find "$directory" -type f \( -name "*.bak" -o -name "*.tmp" -o -name "*.backup" \) -delete
        echo "Директория успешно очищена от файлов срасширениями .bak, .tmp, .backup."
    else
        echo "Ошибка: Директория не существует."
    fi
}
# Принимаем путь к директории как аргумент
if [ $# -ne 1 ]; then
    echo "Использование: $0 <путь к директории>"
    exit 1
fi
# Вызываем функцию для очистки директории
cleanup_directory "$1"
```

### Сортировка по владельцу файла
![](/pic/hw08ownsort.png)


```bash
 GNU nano 6.2                                                                                 ownersort.sh                                                                                    M     
 1 #!/bin/bash
 2
 3 ownersort() {
 4     directory=$1
 5
 6     if [ -d "$directory" ]; then
 7         # Создаем директории для каждого владельца файла
 8         find "$directory" -type f | while read file; do
 9             owner=$(stat -c %U "$file")
10             mkdir -p "$directory/$owner"
11             cp -p "$file" "$directory/$owner"
12             rm -r "$file"
13         done
14         
15         echo "Файлы успешно скопированы в директории, названные по имени их владельцев."
16     else
17         echo "Ошибка: Директория не существует."
18         exit 1
19     fi
20 }
21
22 # Принимаем путь к директории как аргумент
23 if [ $# -ne 1 ]; then
24     echo "Использование: $0 <путь к директории>"
25     exit 1
26 fi
27
28 # Вызываем функцию для сортировки файлов
29 ownersort "$1"
```