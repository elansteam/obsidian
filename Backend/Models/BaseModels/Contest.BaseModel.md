## `id: int`
> [!info] ID контеста #UniqueIndex #Autoincrement . Глобально уникальный ID

## `name: str`
> [!info] Отображаемое имя контеста

## `description: str`
> [!info] Описание контеста

## `linked_group: int`
>[!info] Группа, частью которой является контест


## `creator: int`
> [!info] ID cоздателя контеста



## `tasks: list[int]`
> [!info] список id задач, которые есть в контесте



## `domain: str/ None`
> [!info]  Доменное имя контеста #UniqueIndex #DomainName


