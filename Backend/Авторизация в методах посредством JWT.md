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
 
## Импорты
* Перечисление `Permissions` и метод `auth_user` лежат в `auth.utils` проекта

## Возврат
В случае провала авторизации защищенный метод вернет `HTTPException` с кодом `403` #TODO подумать как это можно обыграть


# Авторизация в группах
#comingsoon