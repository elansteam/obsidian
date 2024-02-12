Создание новой группы

# Права
* [[Global permissions#CREATE_GROUP = 1|CREATE_GROUP]]

# Параметры
* `group_to_create: GroupToCreate` - минимальные данные для создание группы, где `GroupToCreate` -  [[Group.BaseModel|GroupToCreate]] 

# Статус возврата
##### MEMBER_NOT_FOUND
Возникает, если не найден добавляемый в группу пользователь 

##### DOMAIN_IN_USE
Возникает, если `domain` уже используется


