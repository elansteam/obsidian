## `id: int`
> [!info] Id группы #MongoUniceIndex #Autoincrement 

## `name: str`
> [!info] Отображаемое имя группы

## `domain: str`
> [!info]  Доменное имя группы #DomainName

## `description: str`
> [!info] Описание группы

## `members: dict[int, int]`
> [!info] Словарь участников типа `user_id : personal_role_code`, где `personal_role_code` - закодированные права у пользователя в группе  

## `owner: int`
> [!info] `id`  cоздателя группы

## `template_roles: dict[str, int]`
> [!info] Шаблонные роли, с помощью которых можно удобно переключать права пользователя в группе. Словарь `role_name : personal_role_code`. Могут быть роли по умолчанию
