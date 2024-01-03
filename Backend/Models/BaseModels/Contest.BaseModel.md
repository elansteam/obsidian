> [!danger]
> FULL OF BANANAS
> Нужна сессия, чтобы разобраться
> https://t.me/c/1939230635/1/2091


## `id: int`
> [!info] ID контеста #UniqueIndex #Autoincrement . Глобально уникальный ID

## `name: str`
> [!info] Отображаемое имя контеста

## `domain: str | None`

> [!info]  Доменное имя контеста #UniqueIndex #DomainName

## `description: str`
> [!info] Описание контеста

## `members: list[int]`
#TODO #TODO_MARK: возможно, монга офигеет от размера документа в коллекции и хранение списка участников станет точкой отказа БД
#TODO #TODO_ANDREW этого вообще нет
## `owner: int`
> [!info] ID cоздателя группы

