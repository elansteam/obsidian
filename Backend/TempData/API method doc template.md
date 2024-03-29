> [!tip] Название API метода в заголовке файла, где вместо знака / точка

1) Краткое описание метода
2) Права для доступа к методу
3) Параметры
4) **Статусы возврата** и примеры ответа и запроса

# Статусы возврата
Статус возврата это индикатор выполнение метода.
Ключевые особенности этой методологии

Если метод защищен то статус возврата [[Авторизация в методах посредством JWT#Возврат|может быть таким]]

## Особенности ответа
Если код ответа отличен от `200`  то обязано  присутствовать поле `"status"`, которое как раз и характеризует статус ошибки.

## Особенности формата
* Отсутствие статуса или код `200` это выполнение метода без ошибок
* Отсутствие примера ответа означает, что ответ это в точности `{"status": "current_status"}` для любого `current_status`, для которого не указан пример ответа

## Формат ошибки
```json
{
	"status": "some_status",
	"data": {
		// here some data
	}
}
```
В таком формате описываается каждая ошибка, иначе формат вывода может быть типа `responce_model`


Пример документации к методу:
![[platform.getLoginAutentificationMethods|Пример документации к методу]]


