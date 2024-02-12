## `id: int`
> [!info] ID группы #UniqueIndex #Autoincrement 

## `name: str`
> [!info] Отображаемое имя группы

## `domain: str | None`
> [!info]  Доменное имя группы #UniqueIndex #DomainName

## `description: str`
> [!info] Описание группы

## `members: list[GroupMember]`


## `owner: int`
> [!info] ID cоздателя группы

## `group_roles: list[GroupRole]`
> [!info] Список групповых ролей

## `contests: list[int]`
> [!info] Список id контестов группы

