## `id: int`
> [!info] Id пользователя в виде числа #MongoUniceIndex #Autoincrement

## `domain: str`
>[!info]  Доменное имя пользователя #DomainName 

## `name: str`
>[!info] Отображаемый ник пользователя

## `password_hash: str`
> [!info] Хэш пароля пользователя

## `first_name: str`
> [!info] Имя

## `last_name: str`
>[!info] Фамилия 

## `mid_name: str | None`
> [!info] Отчество

## `groups: list[int]`
>[!info] Список id групп, в которых состоит пользователь

## `roles: list[str]`
>[!info] Список имен ролей, которыми обладает пользователь

## `email: str | None`
> [!info] Электронная почта. Она либо есть либо ее нет. #MongoUniceIndex 