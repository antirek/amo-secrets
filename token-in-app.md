
## схема передачи достоверных данных на widget-api

1. widget-ui запрашивает у widget-api uuid интеграции

2. widget-ui запрашивает у amoCRM jwt-токен

3. widget-ui передает данные на widget-api с токеном

4. widget-api проверяет токен


## пример запроса у amoCRM jwt-токена

const r = await $.ajax('/ajax/v2/integrations/' + uuid + '/disposable_token');
выполнять в браузере в авторизованном приложении amoCRM с виджетом

## пример контента jwt-токена

`````js
{
  "iss": "https://mobilontestdev.amocrm.ru",
  "aud": "https://amo-apps-auth.services.mobilon.ru",
  "jti": "a38c9245-2f72-433f-9e46-a7040e88bce9",
  "iat": 1722250828,
  "nbf": 1722250828,
  "exp": 1722252628,
  "account_id": 31263018,
  "subdomain": "mobilontestdev",
  "client_uuid": "c439f6b2-8d4e-4a27-a9e1-bdd4beb1e400",
  "user_id": 886,
  "is_admin": true
}

`````
