# Общая информация
Здесь описаны внешние и внутренние запросы API CRM 
```
http://51.250.11.212:7002/api/{ССЫЛКА ЗАПРОСА}
```
Донаты на лечение принимаются.
Для более быстрого продвижения по этому API, советуем посетить - https://core.telegram.org/

## account_auth 
Метод делает запрос к базе данных (далее БД), проверяет наличие пользователя в БД по паролю и логину;
При отсутствие пользователя добавляет его в БД.
```
//обязательные
  "login": "string",
  "password": "string",
  "id_api": int,
  "api_hash": "string"
//получаем
  obj: "string"
```
| props | type | description | obligatory
|:----------------:|:---------:|:----------------:|:----------------:|
| login | string | Логин пользователя для авторизации | + |
| password | string | Пароль пользователя для авторизации | + |
| id_api | 0 | данные с mytelegram.org | + |
| api_hash | string | данные с mytelegram.org | + |
```python
#пример использования
requests.post(f"{host}:{port}/api/account_auth", json={"login": number, "password": password, "id_api": api_id, "api_hash": api_hash}).json()
```

## telegram_preauth
Методо делает запрос к БД, проверяет наличие сохранённых данных, а после делает запрос в API телеграм, проверяет налачие файла сессии ( при необходимости создаёт ) и возвращает объект телеграм клиента.
```
//обязательные
  "phone": "string",
  "code": "string",
  "user_id": int,
  "password": "string"
```
| props | type | description | obligatory
|:----------------:|:---------:|:----------------:|:----------------:|
| phone | string | Телефон пользователя в телеграм | + |
| code | string | Код авторизации из телеграм | + |
| user_id | int | ID из телеграма | + |
| password | string | Пароль для авторизации в телеграме | + |
```python
#пример использования
requests.post(f"{host}:{port}/api/telegram_preauth", json={"phone": number, "password": password})
```

## telegram_auth 
Метод делает запрос к телеграм API и авторизирует пользователя по введённым данным ( код доступа ), после делает запрос к БД, получает пользователей и обновляет телеграм ID пользователя
```
//обязательные
  code: int,
  flag: bool
```
| props | type | description | obligatory
|:----------------:|:---------:|:----------------:|:----------------:|
| code | int | Код подтверждения из тг, для входа в свой аккаунт | + |
| flag | bool | Контроль вызываемой функции | + |
```python
#пример использования
requests.post(f"{host}:{port}/api/telegram_auth", json={"flag": False})
```

## telegram_load
Метод делает запрос к телеграм API и загружает диалоги пользователя;
Возвращает эти диалоги!
```
// нету обязательных props / запрос работает с данным которые уже крутятся в системе!
//получаем
  obj: "string"
```
```python
#пример использования
requests.post(f"{host}:{port}/api/telegram_load").json()
```

## telegram_handler
Метод делает запрос к телеграм API, и отслеживает новые сообщения, добавляя их в БД.
```
// нету обязательных props / запрос работает с данным которые уже крутятся в системе!
```
```python
#пример использования
requests.post(f"{host}:{port}/api/telegram_handler", timeout=1)
```

## telegram_send 
Метод делает запрос к телеграм API, передаёт ID пользователя, сообщение, а также ID диалога, после чего отправляет сообщение.
```
//обязательные
  "id_account": int,
  "answer": "string"
//необязательные
  "messenger": "string"
```
| props | type | description | obligatory
|:----------------:|:---------:|:----------------:|:----------------:|
| id_account | int | ID из телеграма | + |
| messenger | string | Выбор мессенджера в который доставляется сообщение | - |
| answer | string | Сообщение  | + |
```python
#пример использования
requests.post(f"{host}:{port}/api/telegram_send", json={'user_id': user_id, 'answer': text_dialog})
```

## load_tgdialog 
Метод делает запрос к API телеграмм полностью выгружает все сообщения из диалога который соответствует переданному ID.
```
//обязательные
  id: int
```
| props | type | description | obligatory
|:----------------:|:---------:|:----------------:|:----------------:|
| id | int | ID диалога | + |
```python
#пример использования
requests.post(f"{host}:{port}/api/load_tgdialog", json={'user_id': user_id}).json()
```

## get_messages/accountid_and_messenger
Метод делает запрос к БД, передаёт ID пользователя, после чего получает все сообщения пользователя. 
```
//обязательные
  "id_account": int,
//необязателльные
  "messenger": "string"
//получаем
  obj: "string"
```
| props | type | description | obligatory
|:----------------:|:---------:|:----------------:|:----------------:|
| id_account | int | id аккаунта из БД | + |
| messenger | string | мессенджр из БД | - |
```python
#пример использования
requests.post(f"{host}:{port}/api/get_messages/accountid_and_messenger", json={"id_account": id_acc,"messenger": "telegram"}).json()
```

#### дополнительные источники -> http://51.250.11.212:7002/docs
#### Telegram APIs -> https://core.telegram.org/
![Alt-текст](https://c.tenor.com/_V8TTKAXYB0AAAAC/spongebob-squarepants-sunglasses.gif "Орк")
