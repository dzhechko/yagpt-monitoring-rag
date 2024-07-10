## YaGPT чат-бот для работы с pdf-файламм

### Краткая информация
Данный YaGPT-бот реализует [Retrieval-Augmented Generation (RAG)](https://github.com/yandex-cloud-examples/yc-yandexgpt-qa-bot-for-docs/blob/main/README.md) подход
и использует следующие компоненты:
- [Yandex GPT](https://cloud.yandex.ru/services/yandexgpt)
- [Yandex GPT for Langchain](https://pypi.org/project/yandex-chain/)
- [YC MDB Opensearch](https://cloud.yandex.ru/docs/managed-opensearch/)
- [Streamlit](https://streamlit.io/)
- [LangChain](https://python.langchain.com/)

### Структура репозитория и порядок работы с ботом
- в файле ``.env`` находятся системные переменные (которые при запуске в облаке можно указать как secrets)
```
YAGPT_FOLDER_ID = 
YAGPT_API_KEY = 
MDB_OS_PWD = 
MDB_OS_HOSTS = fqdn-host1,fqdn-host2,fqdn-host3 
mdb_prefix = 
```
`YAGPT_FOLDER_ID` - id фолдера в yandex cloud, внутри которого используется сервис yandexgpt

`YAGPT_API_KEY` - api ключ для доступа к yandexgpt, создается после создания сервисного аккаунта и привязан к нему, подробнее по [ссылке](https://yandex.cloud/ru/docs/foundation-models/api-ref/authentication#service-account_1)

`MDB_OS_PWD` - админский пароль доступа к Базе Данных (БД)

`MDB_OS_HOSTS` - список fqdn хостов БД, на которых будет размещаться индекс, через запятую

`mdb_prefix` - префикс по-умолчанию перед названием индекса БД, позволяет администратору различать индексы разных тенантов между собой

- файл `requirements.txt` традиционно содержит в себе список необходимых для работы программы модулей, которые устанавливаются командой 
```pip install -r requirements.txt ```
- в папке `images` хранится логотип компании, который можно использовать в графическом интерфейсе streamlit
- `YaGPT-RAG-bot-01.py` - запускаемый файл для streamlit community cloud, в котором через web интерфейс нужно указывать креды для YandexGPT (`YAGPT_FOLDER_ID` и `YAGPT_API_KEY`)
- `YaGPT-RAG-bot-02.py` - запускаемый файл для streamlit community cloud, в котором через web интерфейс НЕ нужно указывать креды для YandexGPT (`YAGPT_FOLDER_ID` и `YAGPT_API_KEY`), они указываются в "секретах" streamlit community cloud при запуске приложения
- для упрощения запуска в облаке в исходном коде отключена проверка сертификата на MDB Opensearch

### Запуск в Streamlit Community Cloud
Вы можете развернуть это приложение через Streamlit Community Cloud, следуя [следующим инструкциям](https://docs.streamlit.io/streamlit-community-cloud/get-started)

