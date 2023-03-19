# api_final
api final
#Yatube API

##Описание

Этот проект позволяет использовать приложение Yatube через API: получать, создавать, редактировать посты и комментарии к ним, получать списки групп и подпсываться на авторов.

##Установка

Для установки необходимо:

 - Клонировать репозитории из GitHub с помощью команды git clone 'SSH-ключ' в терминале;
 - Создать виртуальное окружение, активировать его;
 - Установить все необходимые пакеты командой pip install -r requirements.

##Примеры

####Получение публикаций

Исполняем GET-запрос на эндпоинт http://127.0.0.1:8000/posts/
Можно передать необязательные параметры limit и offset:

{
    "limit": 2,
    "offset": 4
}

Или GET-запрос на эндпоинт http://127.0.0.1:8000/posts/?limit=2&offset=4

Пример ответа:

{
    "count": 123,
    "next": "http://127.0.0.1:8000/cats/?limit=2&offset=6",
    "previous": "http://127.0.0.1:8000/cats/?limit=2&offset=2",
    "results": [
        {}
    ]
}

####Создание поста

Выполняем POST-запрос на эндпоинт http://127.0.0.1:8000/posts/
В теле запроса передаем обязательный аргумент text
Можно также добавить аргумент image в виде строки (изображение кодируется в формат base64),
и необязательный аргумент group  

{
    "text": "string",
    "image": "string",
    "group": 0
}

Пример ответа:

{
    "id": 0,
    "author": "string",
    "text": "string",
    "pub_date": "2019-08-24T14:15:22Z",
    "image": "string",
    "group": 0
}

####Получение токена

Выполняем POST-запрос на эндпоинт http://127.0.0.1:8000/api/v1/jwt/create/
В теле запроса передаем обязательные аргументы: имя и пароль

{
    "username": "string",
    "password": "string"
}

Пример ответа:

{
    "refresh": "string",
    "access": "string"
}