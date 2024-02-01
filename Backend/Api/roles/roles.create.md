Создание новой роли в системе

# Права
* CREATE_ROLE

# Параметры
`RoleCreate` - базовая модель входных данных
* `name: str` - имя будущей роли
* `description: str` - описание будущей роли
* `role_code: int` - код прав роли. Не отрицателен

# Статусы возврата
#### OK
```json
{
  "name": "test_test",
  "description": "string",
  "role_code": 1
}
```

Возвращает объект созданной роли
```json
{
  "status": "OK",
  "response": {
    "_id": "test_test",
    "name": "test_test",
    "description": "string",
    "role_code": 1
  }
}
```

#### ROLE_ALREADY_EXISTS
Возникает тогда, когда пытаются создать роль с уже занятым названием
