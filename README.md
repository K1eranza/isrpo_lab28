# Games API - список любимых игр

Веб-API для управления списком любимых игр. Лабораторная работа №28

## Описание

API позволяет выполнять полный CRUD (Create, Read, Update, Delete) для управления списком игр:

- Получить список всех игр
- Получить конкретную игру по ID
- Добавить новую игру
- Обновить существующую игру
- Удалить игру
- Получить список избранных игр
- Валидация данных (защита от пустого названия)

## Запуск проекта

cd GamesApi && dotnet run


Сервер запустится на `http://localhost:5083`

## Маршруты API

| Метод | Маршрут | Описание | Статусы |
|-------|---------|----------|---------|
| GET | /api/games | Получить все игры | 200 |
| GET | /api/games/{id} | Получить игру по id | 200 / 404 |
| GET | /api/games/favourites | Получить избранные игры | 200 |
| POST | /api/games | Добавить новую игру | 201 / 400 |
| PUT | /api/games/{id} | Обновить игру | 200 / 404 |
| DELETE | /api/games/{id} | Удалить игру | 204 / 404 |

## Примеры curl-команд

### GET все игры

curl http://localhost:5083/api/games


### GET игру по ID

curl http://localhost:5083/api/games/1


### GET избранные игры

curl http://localhost:5083/api/games/favourites


### POST добавить игру
```
curl -X POST http://localhost:5083/api/games -H "Content-Type: application/json" -d "{\"title\": \"Hollow Knight\", \"genre\": \"Metroidvania\", \"releaseYear\": 2017, \"isFavourite\": true}"
```

### PUT обновить игру
```
curl -X PUT http://localhost:5083/api/games/2 -H "Content-Type: application/json" -d "{\"title\": \"The Witcher 3: Wild Hunt\", \"genre\": \"Action RPG\", \"releaseYear\": 2015, \"isFavourite\": true}"
```

### DELETE удалить игру
```
curl -X DELETE http://localhost:5083/api/games/1
```

### Проверка валидации (пустое название - ошибка 400)

```
curl -i -X POST http://localhost:5083/api/games -H "Content-Type: application/json" -d "{\"title\": \"\", \"genre\": \"RPG\", \"releaseYear\": 2020}"
```

## Технологии

- ASP.NET Core Web API
- C# (.NET 6+)
- In-memory хранилище



