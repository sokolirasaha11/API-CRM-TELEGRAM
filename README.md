# Общая информация
Здесь описаны внешние и внутренние запросы API CRM 
```
http://51.250.11.212:7002/api/{ССЫЛКА ЗАПРОСА}
```
Донаты на лечение принимаются.

## account_auth 
авторизация по БД
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

## telegram_preauth
проверка на наличие файла сессии
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


## telegram_auth 
проверка на наличие файла сессии
```
//обязательные
  code: int,
  flag: bool
```
| props | type | description | obligatory
|:----------------:|:---------:|:----------------:|:----------------:|
| code | int | Код подтверждения из тг, для входа в свой аккаунт | + |
| flag | bool | Контроль вызываемой функции | + |

## telegram_load 
авторизация в телеграмме
```
// нету обязательных props / запрос работает с данным которые уже крутятся в системе!
//получаем
  obj: "string"
```

## telegram_handler 
подгрузка пользователь с которыми есть диалог
```
// нету обязательных props / запрос работает с данным которые уже крутятся в системе!
```

## telegram_send 
отправка новых сообщений
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

## load_tgdialog 
загрузка диалога и добавление в бд
```
//обязательные
  id: int
```
| props | type | description | obligatory
|:----------------:|:---------:|:----------------:|:----------------:|
| id | int | ID диалога | + |

## accountid_and_messenger 
получение диалога
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
| id_account | int | id аккаунта из бд | + |
| messenger | string | мессенджр из бд | - |


#### дополнительные источники -> http://51.250.11.212:7002/docs
