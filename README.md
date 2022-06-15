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
  "id_api": 0,
  "api_hash": "string"
```

## telegram_preauth
проверка на наличие файла сессии
```
//обязательные
  "phone": "string",
  "code": "string",
  "flag": true,
  "user_id": 0,
  "answer": "string",
  "password": "string"
```

## telegram_auth 
проверка на наличие файла сессии
```
//обязательные
  code: “int”,
  flag: ‘bool’
```

## telegram_load 
авторизация в телеграмме
```

```

## telegram_handler 
подгрузка пользователь с которыми есть диалог
```

```

## telegram_send 
“ловля” новых сообщений
```
//обязательные
  "id_account": 0,
  "messenger": "string"
```

## load_tgdialog 
загрузка диалога и добавление в бд
```
//обязательные
  id: int
```

## accountid_and_messenger 
получение диалога
```
//обязательные
  "id_account": 0,
  "messenger": "string"
```

