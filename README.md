# API_Yamdb

Описание:

## Проект YaMDB - это API социальной сети, она собирает оценки и отзывы пользователей на различные произведения.

### Технологии

* Django, 
* djangorestframework,
* djangorestframework_simplejwt
* postgres
* ngnix
* gunicorn
* docker

### Запуск сервера через Docker:
* Клонируем репозиторий;

* Файл для подключения базы данных;
    Создайте файл .env в директории проекта ./infra/ следующего соддержания:
    (Настройки по умолчанию)
    - DB_ENGINE=django.db.backends.postgresql
    - DB_NAME=postgres
    - POSTGRES_USER=postgres
    - POSTGRES_PASSWORD=postgres
    - DB_HOST=db
    - DB_PORT=5432

* Поднимаем контенеры - docker-compose up;
* Запускаем миграции - docker-compose exec web python manage.py migrate
* Создаем superuser - docker-compose exec web python manage.py createsuperuser
* СОбираем статику - docker-compose exec web python manage.py collectstatic --no-input

### Документация после запуска контейнеров находится по адресу  http://localhost/redoc/

### Доступные эндпоинты:

- api/v1/auth/signup/ - Авторизация
- api/v1/auth/token/ - Получение JWT-токена
- api/v1/users/ - Пользователи
- api/v1/users/me/ - Профиль
- api/v1/categories/ -  Категории произведений
- api/v1/genres/ - Жанры произведений
- api/v1/titles/ - Произведения, к которым пишут отзывы
- api/v1/titles/{title_id}/reviews - Oтзывы
- api/v1/titles/{title_id}/reviews/{review_id}/comments/ - Комментарии к отзывам

## Автор: Чумак Виталий