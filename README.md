# Subscription Service

Тестовый сервис для управления пользовательскими подписками.

API позволяет:
- создавать подписки
- получать список подписок
- получать подписку по ID
- обновлять подписки
- удалять подписки
- получать подписки пользователя
- рассчитывать суммарную стоимость подписок с фильтрами

# Base URL: http://localhost:8080/api/v1

# Технологии

- Go
- Gin
- PostgreSQL
- Swagger (OpenAPI 3.1)

# Эндпоинты

| Метод | Путь | Описание |
|------|------|----------|
| POST | /subscriptions | Создать подписку |
| GET | /subscriptions | Получить все подписки |
| GET | /subscriptions/{id} | Получить подписку по ID |
| PUT | /subscriptions/{id} | Обновить подписку |
| DELETE | /subscriptions/{id} | Удалить подписку |
| GET | /subscriptions/user/{user_id} | Получить подписки пользователя |
| GET | /subscriptions/sum | Получить сумму подписок |

# Получение суммы подписок
GET /subscriptions/sum
### Query параметры

| Параметр | Тип | Описание |
|--------|----|---------|
| user_id | uuid | ID пользователя |
| service | string | название сервиса |
| from | date | начало периода (YYYY-MM-DD) |
| to | date | конец периода (YYYY-MM-DD) |

### Пример запроса
GET /api/v1/subscriptions/sum?user_id=60601fee-2bf1-4721-ae6f-763679a0c5ba&service=spotify&from=2025-07-01&to=2025-09-30

# Пример запроса на создание подписки

```json
{
  "service_name": "kino",
  "price": 330,
  "user_id": "60601fee-2bf1-4721-ae6f-763679a0c5ba",
  "start_date": "08-2025"
}
```
# Пример данных в системе
```json
  {
    "id": "d1a43563-5db7-4e32-aff2-66cf10324f32",
    "service_name": "spotify",
    "price": 440,
    "user_id": "60601fee-2bf1-4721-ae6f-763679a0c5ba",
    "start_date": "07-2025",
    "end_date": "09-2025"
  },
  {
    "id": "313b6a37-5888-4c45-b326-8638c43a12f6",
    "service_name": "kino",
    "price": 330,
    "user_id": "60601fee-2bf1-4721-ae6f-763679a0c5ba",
    "start_date": "08-2025",
    "end_date": null
  }
```

## Swagger (OpenAPI)
Спецификация API находится в файле: api/openapi.yaml
Чтобы открыть Swagger UI:
1.	Перейдите на сайт
https://editor.swagger.io/
2.	Вставьте содержимое файла openapi.yaml.
