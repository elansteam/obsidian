## `id: int`
> [!info] ID пользователя в виде числа #UniqueIndex #Autoincrement

## `domain: str | None`
>[!info]  Доменное имя пользователя (ник) #DomainName #UniqueIndex 

## `password_hash: str`
> [!info] Хэш пароля пользователя

## `first_name: str`
> [!info] Имя

## `last_name: str`
>[!info] Фамилия 

## `mid_name: str | None`
> [!info] Отчество

## `groups: list[int]`
>[!info] Список ID групп, в которых состоит пользователь

## `roles: list[str]`
>[!info] Список имен ролей, которыми обладает пользователь

## `email: str | None`

> [!info] Электронная почта. #UniqueIndex 
