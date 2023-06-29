[![.github/workflows/main.yml](https://github.com/TwoSay95/kittygram_final/actions/workflows/main.yml/badge.svg)](https://github.com/TwoSay95/kittygram_final/actions/workflows/main.yml)

![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E) ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![Django](https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=django&logoColor=white) ![DjangoREST](https://img.shields.io/badge/DJANGO-REST-ff1709?style=for-the-badge&logo=django&logoColor=white&color=ff1709&labelColor=gray) ![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white) ![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white) ![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white)

## Описание проекта

Социальная сеть для любителей котиков. Смотрите на питомцев и следите за их достижениями!

## Технологии

- Python 3.9
- Django 3.2.3
- Django REST framework 3.12.4
- Nginx
- Gunicorn
- Docker
- Фронтенд приложение React

### Доступные методы
Для работы с пользователями использованы стандартные пути из библиотеки  
<a href="https://djoser.readthedocs.io/en/latest/sample_usage.html">Djoser</a>

Некоторые запросы:

Получить всех котов:

```bash
GET api/cats/
```
Добавить нового кота:
```bash
POST api/cats/
```

С остальными методами можно ознакомиться в файле backend/kittygram_backend/urls.py и backend/cats/views.py
Документация методов также доступна по ссылке
```bash
/api/docs/
```

## Запуск проекта из образов с DockerHub

Для запуска необходимо создать папку проекта, например `kittygram` и перейти в нее:

```bash
mkdir kittygram
cd kittygram
```

В папку проекта скачиваем файл `docker-compose.production.yml` и запускаем его:

```bash
sudo docker compose -f docker-compose.production.yml up -d
```

Произойдет скачивание образов, создание и включение контейнеров.

## Запуск проекта из исходников GitHub

Клонируем репозиторий на свой компьютер: 

```bash 
git clone git@github.com:TwoSay95/kittygram_final.git
```

Выполняем запуск:

```bash
sudo docker compose -f docker-compose.yml up -d
```

## После запуска необходимо выполнить миграции и собрать статистику

После запуска необходимо выполнить сбор статистики и миграции бэкенда. Статистика фронтенда собирается во время запуска контейнера, после чего он останавливается. 

```bash
sudo docker compose exec backend python manage.py migrate

sudo docker compose exec backend python manage.py collectstatic

sudo docker compose exec backend cp -r /app/collected_static/. /static/static/
```

И далее проект доступен на: 

```
http://localhost:9000/
```

## Остановка оркестра контейнеров

```bash
sudo docker compose -f docker-compose.yml down
```

## Автор

Молотков Виктор https://github.com/TwoSay95