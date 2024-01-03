Аутентификация пользователя в системе. Генерирует **JWT**, которые будут для авторизации в методах.

Подробнее [[Авторизация в методах посредством JWT]]

# Права
Не требуются

# Параметры
* `login: str` - логин, может быть как `email` либо `domain_name`
* `password: str` - пароль для входа

# Статусы возврата

## OK

Возвращает два токена:
* `access_token: str` 
* `refresh_token: str`

Пример запроса:
```json
{
	"login_type": "email",
	"login": "example@gmail.com",
	"password": "123321"
}
```
Пример ответа:

```json
{
	status: "OK",
	"access_token": "askjdsalkjdsalkjaslkj",
	"refresh_token": "asdasdsdaasdlkjasdlkj"
}
```

## WrongPassword
Возникает, когда введен неправильный пароль

## WrongLogin
Возникает, когда введенный логин не существует
