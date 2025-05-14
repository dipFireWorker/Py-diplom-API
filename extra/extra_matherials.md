# Дополнительные материалы

## 1. Как работать с конфигурационными файлами (.ini)
Для чтения конфигурационных файлов в формате .ini используйте встроенный модуль configparser.

[Документация](https://docs.python.org/3/library/configparser.html)

[Конфигурационные файлы в Python](https://habr.com/ru/articles/485236/)

Пример использования:
```python
from configparser import ConfigParser

config = ConfigParser()
config.read('config.ini')

interval = int(config['SETTINGS']['sync_interval'])
token = config['SETTINGS']['yandex_token']
```
Совет: проверьте, существует ли файл конфигурации, и содержатся ли в нем нужные секции и ключи, прежде чем использовать.




## 2. Как логгировать
Для логирования используйте встроенный модуль logging, который позволяет записывать сообщения в файл или консоль, указывая уровень важности (INFO, ERROR и др.).

[Документация](https://docs.python.org/3/library/logging.html)

[Логирование в Python](https://habr.com/ru/companies/wunderfund/articles/683880/)

Пример использования:
```python
import logging

logger = logging.getLogger("BackupLogger")
logger.setLevel(logging.INFO)

handler = logging.FileHandler("backup.log")
formatter = logging.Formatter('%(asctime)s - %(levelname)s - %(message)s')
handler.setFormatter(formatter)
logger.addHandler(handler)

logger.info("Программа запущена")
logger.error("Ошибка при загрузке файла")
```
Совет: Используйте разные уровни (debug, info, warning, error, critical) в зависимости от ситуации.




## 3. Как обрабатывать ошибки

Используйте конструкции try / except, чтобы ловить и обрабатывать исключения. Это особенно важно при работе с сетью, файлами и пользовательскими вводами.

[Документация](https://docs.python.org/3/tutorial/errors.html)

[Как правильно обрабатывать исключения](https://habr.com/ru/companies/wunderfund/articles/736526/)

Пример использования:
```python
try:
    with open("some_file.txt", "r") as f:
        content = f.read()
except FileNotFoundError:
    logger.error("Файл не найден")
except Exception as e:
    logger.error(f"Произошла непредвиденная ошибка: {e}")
```
Совет: Всегда старайтесь логгировать ошибки, чтобы потом было проще их отследить.




## 4. Как работать с виртуальным окружением и requirements.txt

Виртуальное окружение позволяет изолировать зависимости проекта.

[Документация venv](https://docs.python.org/3/library/venv.html)

[Создание и использование виртуальных сред](https://docs-python.ru/standart-library/modul-venv-python/)

[Документация pip](https://pip.pypa.io/en/stable/cli/pip_install/)

[Файл requirements.txt в Python и как его создать](https://teletype.in/@pythontalk/requirements)

Пример использования:
```bash
python -m venv venv            # создать окружение
source venv/bin/activate       # Linux/macOS
venv\Scripts\activate          # Windows

pip install requests           # установить зависимости
pip freeze > requirements.txt  # сохранить зависимости
```

Пример requirements.txt:
```ini
requests==2.31.0
tqdm==4.67.1
```
Совет: Храните venv/ в .gitignore, чтобы не загружать его в GitHub.
