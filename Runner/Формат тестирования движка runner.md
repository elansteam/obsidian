> [!info] Что такое `runner_assert.json`?
> В этой спецификации описывается формат файла `runner_assert.json`. Это служебный формат, который разработчики используют для тестирования работы движка. Если вы являетесь пользователем тестирующей системы, скорее всего, этот раздел документации вам не нужен.

Файл `runner_assert.json` используется как для внутреннего тестирования системы, так и для проверки работоспособности чекеров/валидаторов тестов/проверки самих тестов и так далее.
Файл представляет собой конфигурацию для runner, prerun-хуки (скрипты, которые должны быть выполнены до запуска runner'а: с помощью них можно установить требуемые переменные окружения). 

Ниже - пример валидного файла в формате JSON с комментариями:
```json
{
	"runner_config": {
		"limits": {
			"cpu_time_limit": 1000,
			"real_time_limit": 5000,
			"memory_limit": 1048576,
			"allow_write_files": false,
			"allow_read_files": false,
			"threads_amount": 1, // пока не поддерживается, значение игнорируется runner'ом
		},
		"executable_path": "/usr/bin/g++",
		"args": ["val.cpp", "-Wall", "-O2", "-o", "val.o"],
		"working_dir": "/elan/tmp/submissions/submission2406",
		"streams": {
			"forward_streams": true,
			"input_stream_file": "input.txt",
			"output_stream_file": "output.txt",
			"error_stream_file": "error.txt"
		}
	},
	"extras": {
		"prerun_hooks": ["cp /elan/files/testing/testlib.h ."], // bash команды, которые будут выполнены перед запуском раннера
		"postrun_hooks": ["cat $OUTPUT_FILE_STREAM"] // bash команды, которые будут выполнены после запуска раннера
	},
	"testing_data": {
		"verdict": "OK"
	}
}
```

В секции `runner_config` указываются параметры для конфигурации runner-а, смотреть [[Интерфейс runner engine#Аргументы вызова движка|документацию движка]].

В секции `extras` указываются `prerun` и `postrun` хуки - программы, которые будут выполняться соответственно перед тестовым запуском движка и после него. Эти команды нужны для гибкой настройки окружения, в котором будет проводиться тестирование движка.

>[!danger] Обратите внимание!
>Команды в `prerun` и `postrun` хуках выполняются не через runner, а напрямую, то есть не имеют никаких ограничений. Это безопасно, потому что данный формат предполагается использовать только для тестирования движка его разработчиками. Пожалуйста, будьте осторожны при передаче небезопасных значений в эти переменные.

Если хотя бы один из `prerun` хуков вернет ненулевой код возврата, запуск runner'а не будет проводиться, а тест движка будет считаться непройденным (failed).
Если хотя бы один из `postrun` хуков вернет ненулевой код возврата, тест движка будет считаться непройденным (failed).

В секции `testing_data` указываются ожидаемый результаты runner'а - вердикт. 
- `verdict: str` - буквенное обозначение вердикта

## Примеры
Ниже - примеры конфигурации файла `runner_assert.json`.
### Общее тестирование
Просто проверим, не выполняя никаких практических задач, что runner не упадет. Вызовем команду `uname -a` для получения информации о системе.
```json
{
	"runner_config": {
		"limits": {
			"cpu_time_limit": 10,
			"real_time_limit": 10,
			"memory_limit": 1024,
			"allow_write_files": false,
			"allow_read_files": false,
			"threads_amount": 1,
		},
		"executable_path": "/usr/bin/uname",
		"args": ["-a"],
		"working_dir": "/tmp",
		"streams": {
			"forward_streams": true,
			"input_stream_file": "input.txt",
			"output_stream_file": "output.txt",
			"error_stream_file": "error.txt"
		}
	},
	"extras": {
		"prerun_hooks": ["echo Hello, Elan!"],
		"postrun_hooks": ["cat $OUTPUT_FILE_STREAM | grep Linux"]
	},
	"testing_data": {
		"verdict": "OK"
	}
}
```

### Тестирование запуска python-файлов
Тут проверим, что в системе работает `python` и с помощью него можно запускать файлы.
Обратите внимание, что все содержимое теста находится в файле `runner_assert.json`: Python-файл для теста создается через prerun-hook, а корректность вычисления проверяется в postrun-hook.
```json
{
	"runner_config": {
		"limits": {
			"cpu_time_limit": 500,
			"real_time_limit": 500,
			"memory_limit": 1024,
			"allow_write_files": false,
			"allow_read_files": false,
			"threads_amount": 1,
		},
		"executable_path": "/usr/bin/python3",
		"args": ["test.py"],
		"working_dir": "/tmp",
		"streams": {
			"forward_streams": true,
			"input_stream_file": "input.txt",
			"output_stream_file": "output.txt",
			"error_stream_file": "error.txt"
		}
	},
	"extras": {
		"prerun_hooks": ["echo \"print(2 + 2)\" > $ELAN_RUNNER_ENV/test.py"],
		"postrun_hooks": ["grep -q 4 $ELAN_RUNNER_ENV/output.txt || exit 1"]
	},
	"testing_data": {
		"verdict": "OK"
	}
}
```