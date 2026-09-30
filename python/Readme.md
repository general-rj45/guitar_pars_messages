# Данные скрипты нужны для выкачки с сай Guitar Tabs сообщений с форума

Для этого требуется 

1. Запустить flaresolverr для обхода cloudflair

```
docker run -d flaresolverr/flaresolverr:latest -p 8191:8191
```

2. Открыть ноутбук parsing_theme.ipynb и вписать енвы

```
SAVE_DIR = "Mobile_Apps_Feedback"
API_URL = "http://192.168.1.23:8191/v1"
BASE_URL = "https://www.ultimate-guitar.com"
FORUM_URL = "https://www.ultimate-guitar.com/forum/forumdisplay.php?f=94"
```

Описание:
Папка для сохранения результатов
Далее адрес прокси докера который мы ранее подняли
Базовый URL сайта
Ссылка на нужную группу тем

3. Далее запускаем local_parsing_html.ipynb

В нём правим только 

```
ROOT_DIR = Path("ug_bug_reports_threads")
OUT_FILE = Path("ug_bug_reports_simple.json")
```

Описание:
путь к папке
путь файла с json

4. Полученный json уже минимального размера можно напрямую отправлять в чатгпт 


Опционально. Для теста работы можно использовать ноутбук test_parsing_guitar.ipynb

В ответе должен быть валидный html и не быть 403 и похожих ошибок.