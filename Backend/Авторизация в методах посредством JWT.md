Это спецификация того, как защищать методы FastApi конкретно в **Elan**.


# Авторизация в глобальных методах
Рассмотрим абстрактный  FastApi метод, который нужно защитить авторизацией конкретных нам [[Global permissions|прав]].

```python
@router.post(
	"/path/to/method",
	# some other args below ...
)
async def abstract_example_method(param1: Type1, param2: Type2
								 _current_user: User = Depends(auth_user(
									 Permissions.FIRST,
									 Permissions.SECOND,
									 Permissions.THIRD
								 ))):
	... # some method code below
```
Сигнатура защищенного метода может быть любая, но обязана в себя включать поле `_current_user: User` и инициализировать через `Depends(auth_user(perms))`, где `perms` - глобальные права в системе или же [[Global permissions]]
после авторизации в аргументе `_current_user` будет находиться пользователь, от чьего имени вызвали метод.
 
# Возврат
Если авторизация произошла с ошибкой то возможны следующие статусы:


## 401 - Unauthorized
### TOKEN_EXPIRED
Возникает в случае, когда время жизни токена подошло к концу.
### VALIDATE_ERROR
Возникает при ошибке декодировки токена. Например при ошибочном формате токена и т.д
### COULD_NOT_FIND_USER
Возникает, если токен кодирует не существующего пользователя

## 403 - Forbidden
#### ACCESS_DENIED
Возникает в случае нехватки прав.

В `responce` хранит поле `required_permissions`, которое содержит в себе список недостающих для обращения к методу прав 
##### Пример возврата
```json
{
	"status": "ACCESS_DENIED",
	"response": {
		"required_permissions": [
			"FIRST",
			"SECOND",
			"THIRD"
		]
	}
}
```