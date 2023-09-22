[![Main Kittygram workflow](https://github.com/momtheprogram/kittygram_final/actions/workflows/main.yml/badge.svg?branch=main)](https://github.com/momtheprogram/kittygram_final/actions/workflows/main.yml)

# Проект Киттиграм - это социальная сеть для любителей котиков.
Kittygram - социальная сеть, специально созданная для хозяев и просто любителей милых кошечек. Здесь делятся фотографиями питомцев. Это так же платформа для заведения новых друзей с общими кошачьими интересами.

## Как развернуть
1. Скачайте docker-compose.yml из репозитория https://github.com/momtheprogram/kittygram_final/blob/main/docker-compose.yml
2. Создайте файл .env
```
touch .env
```
3. Создайте файл с переменными окружения
```
POSTGRES_DB=<БазаДанных>
POSTGRES_USER=<имя пользователя>
POSTGRES_PASSWORD=<пароль>
DB_NAME=<имя БазыДанных>
DB_HOST=db
DB_PORT=5432
SECRET_KEY=<ключ Django>
DEBUG=<DEBUG True/False>
ALLOWED_HOSTS=<разрешенные хосты>
```

4. Запустите Dockercompose
```
sudo docker compose -f docker-compose.yml pull
sudo docker compose -f docker-compose.yml down
sudo docker compose -f docker-compose.yml up -d
```
5. Сделайте миграции и соберите статику
```
sudo docker compose -f docker-compose.yml exec backend python manage.py migrate
sudo docker compose -f docker-compose.yml exec backend python manage.py collectstatic
sudo docker compose -f docker-compose.yml exec backend cp -r /app/collected_static/. /backend_static/static/ 
```

## Автодеплой на Git Hub Action
Добавьте перменные в Secrets
```
DOCKER_PASSWORD - пароль от Docker Hub
DOCKER_USERNAME - имя пользователя Docker Hub
HOST - ip сервера
SSH_KEY - ключ ssh для доступа к удаленному серверу
SSH_PASSPHRASE - пароль ssh
TELEGRAM_TO - id пользователя TELEGRAM
TELEGRAM_TOKEN - TELEGRAM токен
USER - имя пользователя сервера
```

## Технологии

2. Backend:
Django
DRF
Gunicorn
Pillow
Подробней в requirements.txt

4. Сервер:
nginx

5. Деплой
Docker
Docker compose

## Автор: Natalia Lyakhovitskaya https://github.com/momtheprogram
