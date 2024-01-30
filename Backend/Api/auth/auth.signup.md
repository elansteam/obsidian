Регистрация пользователя в системе

# Права
Не требуются

# Параметры
**`UserSignup` base model:**
* `domain: str | None` - будущее доменное имя
* `first_name: str` - имя
* `last_name: str`  - фамилия 
* `mid_name: str | None` - отчество
* `email: str` - электронная почта

# Статусы возврата
#### OK
Возвращает объект созданного пользоватяля вида [[User.BaseModel]]

##### Пример входных данных
```json
{
  "password": "string",
  "first_name": "string",
  "last_name": "string",
  "email": "string4"
}
```
##### Пример выходных данных
```json
{
  "status": "OK",
  "response": {
    "_id": 2,
    "email": "string4",
    "domain": null,
    "password_hash": "$2b$12$gbJvAR/2nQaccGzIbIuqceH6eUfItXQIuLgMFAcNZtf09xZWx3Mie",
    "first_name": "string",
    "last_name": "string",
    "mid_name": null,
    "roles": []
  }
}
```

#### EMAIL_IN_USE
Возникает в случае, когда уже зарегистрирован пользователь с электронной почтой `email`

#### DOMAIN_IN_USE
Возникает в случае, когда уже зарегистрирован пользователь или другой объект с доменом `domain`