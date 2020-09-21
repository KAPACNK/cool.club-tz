# Установка приложения и инструкции к API

### 1. Разворачиваем докер :
```sh
docker-compose up -d
```
### 2. Переходим в директорию src
```sh
cd src
```

### 3. Устанавливаем laravel
```sh
composer update --ignore-platform-reqs
```

### 4. Копируем содержимое .env.example в .env

### 5. Даем разрешение на запись/чтение логов 
```sh
sudo chmod -R 777 storage
```

### 6. Генерируем ключ для приложения 
```sh
php artisan key:generate
```

### 7. Делаем миграцию 
```sh
docker exec -it php_ php artisan migrate --force
```

### 8. Заполняем бд тестовыми данными
```sh
docker exec -it php_ php artisan db:seed
```

___
# Примеры запросов
### Получить всех пользователей
Запрос:
```
curl -X GET http://localhost:8080/api/users
```
Ответ: 
```json
[
    {
        "id": 1,
        "email": "NLaHp7U@mail.ru",
        "first_name": "egixANZ",
        "last_name": "Snn7iUn"
    },
    {
        "id": 2,
        "email": "MwoMRz3@mail.ru",
        "first_name": "nczZhKO",
        "last_name": "s1LCLs1"
    }
]
```

### Получить пользователя по id
Запрос:
```
curl -X GET http://localhost:8080/api/users/1
```
Ответ: 
```json
{
    "id": 1,
    "email": "NLaHp7U@mail.ru",
    "first_name": "egixANZ",
    "last_name": "Snn7iUn"
}
```

### Фильтрация пользователей по мероприятию
Запрос:
```
curl -XGET http://localhost:8080/api/users/event/15
```
Ответ:
```json
[
    {
        "id": 28,
        "email": "zwQshYg@mail.ru",
        "first_name": "MBlnMmf",
        "last_name": "B5jDi0V"
    }
]
```

### Добавление нового пользованеля
Запрос:
```
curl -d "email=qwe@qwe.ru&first_name=qwe&last_name=ewq" -X POST http://localhost:8080/api/users
```
Ответ:
```json
{
    "email": "qwe@qwe.ru",
    "first_name": "qwe",
    "last_name": "ewq",
    "id": 31
}
```

### Редактирование существуещего пользователя
Запрос:
```
curl -d "id=31&email=www@www.ru&first_name=www&last_name=www" -X PUT http://localhost:8080/api/users
```
Ответ:
```json
{
    "email": "www@www.ru",
    "first_name": "www",
    "last_name": "www",
    "id": 31
}
```

___
### Запуск тестов: 

```sh
docker exec php_ php artisan test
```


