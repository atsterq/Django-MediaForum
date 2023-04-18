## Описание:

Yatube - форум для обмена информацией. Через него можно создавать посты, добавляя к ним картинки, вступать в тематические группы, просматривать и комментировать посты других людей. Этот проект - открытое API, оно позволит вам интегрировать все функции yatube в произвольный клиент.

## Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/atsterq/api_final_yatube
```

```
cd api_final_yatube
```

Cоздать и активировать виртуальное окружение:

```
python -m venv venv
```

```
source venv/Scripts/activate
```

Установить зависимости из файла requirements.txt:

```
python -m pip install --upgrade pip
```

```
pip install -r requirements.txt
```

Выполнить миграции:

```
python manage.py migrate
```

Запустить проект:

```
python manage.py runserver
```

## Примеры запросов к API:

### Создание токена доступа:

- Отправьте POST запрос на адрес

```
http://127.0.0.1:8000/api/v1/jwt/create/
```

- C телом в JSON формате

```
{
    "username": "testuser",
    "password": "testpassword123!"
}

```

- Ответ API

```
{
    "refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTY4MTg5ODk3NiwianRpIjoiOTc5NDJhMzc5OGEyNDQ1ZTg2YzRlODAxYmU0MGMxN2QiLCJ1c2VyX2lkIjoxfQ.pfuF1anEC2kqTuO-gxR6NLKxsZ2M8-gwNRX7Ty6kC6k",
    "access": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjgyNjc2NTc2LCJqdGkiOiI0NGYxZjRkODMwNzQ0MTNiYmI2NTkxMzEyMjBmNzkwNSIsInVzZXJfaWQiOjF9.D8yqU8noXYe2AkCPdp-J2MJ32nL127KBoYSWudsWQxo"
}
```
### С токеном доступа можно создать новый пост:

- POST запрос на

```
http://127.0.0.1:8000/api/v1/posts/
```

- с телом запроса

```
{
  "text": "Тестовый пост"
}
```

- даст ответ 

```
{
    "id": 1,
    "author": "testuser",
    "text": "Тестовый пост",
    "pub_date": "2023-04-18T10:58:37.815602Z",
    "image": null,
    "group": null
}
```

### Добавление комментария к посту:

- POST запрос на адрес

```
http://127.0.0.1:8000/api/v1/posts/1/comments/
```

- ответ API

```
{
    "id": 1,
    "author": "testuser",
    "text": "Тестовый комментарий",
    "created": "2023-04-18T11:02:00.869685Z",
    "post": 1
}
```

### Некоторые другие доступные эндпойнты:

- список сообществ
```
http://127.0.0.1:8000/api/v1/groups/
```
- подписки
```
http://127.0.0.1:8000/api/v1/follow/
```
- удаление публикации
```
http://127.0.0.1:8000/api/v1/posts/{id}/
```

