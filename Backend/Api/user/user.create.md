Создание пользователя.
# Права
* [[Global permissions#CREATE_USER|CREATE_USER]]
# Параметры
* `user_to_create: UserToCreate` - минимальные данные для создание пользователя, где `UserToCreate` -  [[UserToCreate.BaseModel|UserToCreate]]
# Статусы возврата
## ОК
Пример входных данных:
```json
{
	"domain": "newUser",
	"name": "user",
	"password": "123456",
	"first_name": "Alex",
	"last_name": "Bolabab",
	"groups": [],
	"roles": ["admin"],
}
```

## IncorrectDomainNameFormat
Возникает при случае ввода `domain` в неправильном формате #TODO понять что такое формат `domain`

## DomainNameAlreadyExists
Возникает, если сущность с таким же`domain` уже существует

## GroupNotFound
Возникает, если хотя бы одной из групп в `groups` не существует.
* `not_found: list[int]` - список `id` групп из `groups`, которых не существует
Пример запроса:
```json
{
	"domain": "newUser",
	"name": "user",
	"password": "123456",
	"first_name": "Alex",
	"last_name": "Bolabab",
	"groups": [1, 2, 3, 14, 132, 122],
	"roles": ["admin"]
}
```


Пример ответа:
```json
{
	"status": "GroupNotFound",
	"not_found": [132, 14, 122];
}
```
В данном случае ошибка из за того, что группы с `id = 132, 14, 122` не найдены в БД
## RoleNotFound
Возникает, если хотя бы одной из ролей в `roles` не существует.
* `not_found: list[int]` - список `name`  ролей из `roles`, которых не существует
Пример запроса:
```json
{
	"domain": "newUser",
	"name": "user",
	"password": "123456",
	"first_name": "Alex",
	"last_name": "Bolabab",
	"groups": [1, 2, 3, 14, 132, 122],
	"roles": ["admin", "foo", "bar", "baz"]
}
```


Пример ответа:
```json
{
	"status": "GroupNotFound",
	"not_found": ["foo", "baz"];
}
```
В данном случае ошибка из за того, что роли с `name = "foo", "baz"` не найдены в БД

## EmailAlreadyExists
Создание пользователя.
# Права
* [[Global permissions#CREATE_USER|CREATE_USER]]
# Параметры
* `user_to_create: UserToCreate` - минимальные данные для создание пользователя, где `UserToCreate` -  [[UserToCreate.BaseModel|UserToCreate]]
# Статусы возврата
## ОК
Пример входных данных:
```json
{
	"domain_name": "newUser",
	"name": "user",
	"password": "123456",
	"first_name": "Alex",
	"last_name": "Bolabab",
	"groups": [],
	"roles": ["admin"],
}
```

## IncorrectDomainNameFormat
Возникает при случае ввода `domain_name` в неправильном формате #TODO понять что такое формат `domain_name`

## DomainNameAlreadyExists
Возникает, если сущность с таким же`domain_name` уже существует

## GroupNotFound
Возникает, если хотя бы одной из групп в `groups` не существует.
* `not_found: list[int]` - список `id` групп из `groups`, которых не существует
Пример запроса:
```json
{
	"domain_name": "newUser",
	"name": "user",
	"password": "123456",
	"first_name": "Alex",
	"last_name": "Bolabab",
	"groups": [1, 2, 3, 14, 132, 122],
	"roles": ["admin"]
}
```


Пример ответа:
```json
{
	"status": "GroupNotFound",
	"not_found": [132, 14, 122];
}
```
В данном случае ошибка из за того, что группы с `id = 132, 14, 122` не найдены в БД
## RoleNotFound
Возникает, если хотя бы одной из ролей в `roles` не существует.
* `not_found: list[int]` - список `name`  ролей из `roles`, которых не существует
Пример запроса:
```json
{
	"domain_name": "newUser",
	"name": "user",
	"password": "123456",
	"first_name": "Alex",
	"last_name": "Bolabab",
	"groups": [1, 2, 3, 14, 132, 122],
	"roles": ["admin", "foo", "bar", "baz"]
}
```


Пример ответа:
```json
{
	"status": "GroupNotFound",
	"not_found": ["foo", "baz"];
}
```
В данном случае ошибка из за того, что роли с `name = "foo", "baz"` не найдены в БД

## EmailAlreadyExists
=======
Возникает в случае, если с `email` уже существует пользователь