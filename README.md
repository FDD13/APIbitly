# Обрезка ссылок с помощью Bitly

Программа для сокращения ссылок или подсчета кликов по сокращенной ссылке на основе [Bitly API](https://dev.bitly.com/).

---

## Установка виртуального окружения

Виртуальное окружение устанавливается для каждого проекта. Оно позволяет использовать определенные версии библиотек. Для того чтобы создать виртуальное окружение необходимо в терминале прописать код

```
python -m venv venv
```
После чего создасться папка venv, в которую можно будет устанавливать необходимые для проекта библиотеки

## Требования

Требуется Python 3.0+ либо песочница как [Repl.it](https://replit.com/). Также необходим токен Bitly API и установить библиотеки:
1. requests
2. python-dotenv

---

__Переменные окружения__

Необходимо зарегистрироваться на сайте [Bitly API](https://dev.bitly.com/). Bitly не даст вам данные, пока вы не получите персональный ключ – “токен”. Он нужен для взаимодействия с API Bitly. Для того чтобы получить токен, необходимо пройти на страницу [Setting/Integrations](https://app.bitly.com/settings/integrations/)

* BITLY_TOKEN

Так как токен является одной из чувтствительных информаций, необходимо спрятать ее от публично доступной системы. Для решения этой задачи нужно создать файл .env, после чего в нем прописать все чувствительные данные, а сам файл доавить в другой файл .gitignore

---

## Запуск программы

В проекте используется модуль под названием argparse, который позволяет принимать аргументы командной строки. Этот модуль является простым способом  настройки поведения программы.
Для запуска программы необходимо запустить код в командной строке:
```
python main.py -h
```
После чего пользователю необходимо заменить "URL" на нужный адрес. Введя стандарную ссылку, пользователь получит сокращенную версию
```
Введите ссылку: https://www.google.com/
Битлинк  bit.ly/334mR4H
```
при введении сокращенной ссылки (битлинк), пользовательно получет колличество переходов на эту самую ссылку:
```
Введите ссылку: bit.ly/334mR4H
Количество кликов 0 
```

## Примечания

Подробней о функциях программы:

__def shorten_link(url, header)__ - принимая во вход ссылку, функция отправляет запрос на API и возвращает сокращенную версию ссылки.
__def count_clicks(url, header)__ - принимая во вход ссылку, функция отправляет запрос на API и возвращает количество переходов по битлинку.
__def is_bitlink(url, header)__ - это функиц принимает во вход ссылку. Обращаясь к API, функция проверяет является ли функция битлинком и в зависимости от ответа возвращает True или False. Данная функция нужна для того, чтобы распознать битлинк и вызвать функцию подсчета кликов или функцию сокращения ссылки, если введена обычная ссылка