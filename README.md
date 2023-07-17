# Проект парсинга PEP
[![Python](https://img.shields.io/badge/-Python-464646?style=flat&logo=Python&logoColor=ffffff&color=043A6B)](https://www.python.org/)
[![BeautifulSoup4](https://img.shields.io/badge/-BeautifulSoup4-464646?style=flat&logo=BeautifulSoup4&logoColor=ffffff&color=043A6B)](https://www.crummy.com/software/BeautifulSoup/)
[![Prettytable](https://img.shields.io/badge/-Prettytable-464646?style=flat&logo=Prettytable&logoColor=ffffff&color=043A6B)](https://github.com/jazzband/prettytable)
[![Logging](https://img.shields.io/badge/-Logging-464646?style=flat&logo=Logging&logoColor=ffffff&color=043A6B)](https://docs.python.org/3/library/logging.html)

# Проект парсинга документации Python
Парсер собирает данные обо всех PEP документах, сравнивает статусы и
записывает их в файл, также реализованы сбор информации о статусе версий,
скачивание архива с документацией и сбор ссылок о новостях в Python, логирует
свою работу и ошибки в командную строку и файл логов.

## Технологии проекта

- Python — высокоуровневый язык программирования.
- BeautifulSoup4 - библиотека для парсинга.
- Prettytable - библиотека для удобного отображения табличных данных.
- Logging - Логирование работы и отслеживания ошибок

### Содержание: 
- [Проект парсинга PEP](#проект-парсинга-pep)
- [Проект парсинга документации Python](#проект-парсинга-документации-python)
  - [Технологии проекта](#технологии-проекта)
    - [Содержание:](#содержание)
  - [Как запустить проект](#как-запустить-проект)
  - [Описание работы](#описание-работы)
  - [Три способа вывода собранных данных пользователю:](#три-способа-вывода-собранных-данных-пользователю)
    - [_Доступные аргументы командной строки_](#доступные-аргументы-командной-строки)
    - [Автор](#автор)


## Как запустить проект
Выполните следующие команды в терминале:

1. Клонировать проект из репозитория
```
git clone https://github.com/Esperansa08/bs4_parser_pep.git
```
2. Создать, активировать виртуальное окружение и в него установить зависимости:
```
python -m venv venv
```
```
venv/Scripts/activate
```
```
pip install -r requirements.txt 
```
3. Запустить парсер из командной строки, например:
```
python src/main.py pep --output pretty
```

## Описание работы

Парсер рабоет в четырех режимах, для каждого из которых присвоена своя функция:
1. сбор версий языка и их авторов - `whats_new`;
2. сбор информации о версиях - `latest_versions`;
3. сбор информации о стандартах PEP - `pep`;
4. скачивание документации - `download`.

## Три способа вывода собранных данных пользователю:
- Обычный вывод в консоль (stdout); 

  Пример:  python src/main.py latest-versions

  Вывод:
  
  Ссылка на документацию Версия Статус
https://docs.python.org/3.13/ 3.13 in development
https://docs.python.org/3.12/ 3.12 pre-release
https://docs.python.org/3.11/ 3.11 stable
https://docs.python.org/3.10/ 3.10 security-fixes
https://docs.python.org/3.9/ 3.9 security-fixes
https://docs.python.org/3.8/ 3.8 security-fixes
https://docs.python.org/3.7/ 3.7 EOL
https://docs.python.org/3.6/ 3.6 EOL
https://docs.python.org/3.5/ 3.5 EOL
https://docs.python.org/2.7/ 2.7 EOL
https://www.python.org/doc/versions/ All versions

- Вывод в консоль в табличном виде (аргументы ```-o {pretty}```);
  Пример:
  python src/main.py pep --output pretty
  Вывод:
+-------------+------------+
| Статус      | Количество |
+-------------+------------+
| Active      | 31         |
| Accepted    | 51         |
| Final       | 274        |
| Draft       | 24         |
| Superseded  | 20         |
| Deferred    | 37         |
| Withdrawn   | 56         |
| Rejected    | 122        |
| April Fool! | 1          |
| Total       | 616        |
+-------------+------------+

- Сохранение в формате csv (аргументы ```-o {file}```) в папку ```/src/results/```;
Пример:
python src/main.py whats-new --output file

В родительской директории ```src/``` будет создана новая ```results/```, 
в которую сохранится файл с результатами работы парсера.

Настроено логирование работы парсера.  
Лог сохраняется в папку ```/src/logs/```.

### _Доступные аргументы командной строки_
Для просмотра режимов работы парсера в терминале введите команду 
с именованным аргументом ```-h``` или ```--help```:  
```
python src/main.py -h
```
Результат работы команды будет следующим:
```
usage: main.py [-h] [-c] [-o {pretty,file}] {whats-new,latest-versions,download,pep}

Парсер документации Python

positional arguments:
  {whats-new,latest-versions,download,pep}
                        Режимы работы парсера

optional arguments:
  -h, --help            show this help message and exit
  -c, --clear-cache     Очистка кеша
  -o {pretty,file}, --output {pretty,file}
                        Дополнительные способы вывода данных
```


### Автор 

 * Савельева Анастасия (Visteria09@yandex.ru, https://github.com/Esperansa08) 