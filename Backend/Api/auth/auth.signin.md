
Аутентификация пользователя в системе. Генерирует **JWT**, которые будут для авторизации в методах.

Подробнее [[Авторизация в методах посредством JWT]]
# Права
Не требуются

# Параметры
* `login: str` - логин
* `password: str` - пароль для входа
* `login_type: Literal["email"] | Literal["domain"] | Literal["id"]` - тип логина
# Статусы возврата

#### OK

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
	"status": "OK",
	"response": {
		"access_token": "askjdsalkjdsalkjaslkj",
		"refresh_token": "asdasdsdaasdlkjasdlkj"
	}
}
```

## INVALID_PASSWORD
Возникает, когда введен неправильный пароль

## INVALID_LOGIN
Возникает, когда введенный логин не существует
