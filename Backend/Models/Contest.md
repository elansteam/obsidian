
Заметим, что у контеста нет типа. То есть нельзя задать тип контесту как IOI и так далее. Идея такая, что все жто указывается в сцепленном мониторе.

То есть у контеста есть несколько мониторов, которые привязаны к контесту. Или только один? Думаю только один. 

Рассмотрим следующие типы оценивания:
* **IOI**
* **ACM**
* **Scoring/SHAD**

Каждый из них по особенному считает баллы и ранжирует участников. Это значит, что для использования какой либо системы оценивания ее должна поддерживать каждая задача в контесте.

##### Требования типов оценивания
###### ACM
От задачи требуется чекер решил / не решил
###### IOI
От задачи требуется через, который по решению устанавливает баллы
###### Scoring/SHAD
Тут может быть хитрый постпроцессор, но его тут не будет так как я не понял, как можно его использовать..
От задачи требуется заранее заданное количество баллов 

Следовательно у задачи должно быть несколько полей, которые необходимо заполнить, чтобы задача поддерживала формат. Только если все задач поддерживают тип оценивания, его можно будет включить на мониторе контеста

я Представляю контест как интерфейс доступа к задачам + агрегация всех участников. Монитор штука, которая есть у всех контестов, однако может быть и скрыта.


![[Contest.BaseModel]]

