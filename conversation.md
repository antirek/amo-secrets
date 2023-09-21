
### Conversation

#### Проблема

когда менеджер пишет первым - мы получаем в сообщении в converation_id, который ничего не обозначает

#### Решение 1
conversation_id нам надо будет где-то как-то сохранить и потом использовать для отправки сообщений в амо

#### Решение 2
иной вариант: задать новый conversation_id, котоый будет наш, нам извесетн и отправлять сообщения как бы мы хотели
например, как номер телефона

задать conversation_id можно с помощью бота тихим сообщением
задавать нужно только если нет converation.client_id


`````

<<< from amo
// менеджер первый написал клиенту
{
    "account_id": "2b13cae0-24f7-4058-b9ad-c13ee05e1b53",
    "time": 1695282809,
    "message": {
      "receiver": {
        "id": "3e056d0f-a553-4d94-9822-57c257891f22",
        "name": "Сергей",
        "phone": "89135292926"
      },
      "sender": {
        "id": "3cfae55d-387e-409f-9be4-4baab963ee02",
        "name": ""
      },
      "source": {
        "external_id": "c218c790-9be5-4dba-99f8-cbe2b408df25"
      },
      "conversation": {
        "id": "8bdd3f03-b37e-46d0-ace2-4ac5735ea484"
      },
      "timestamp": 1695282809,
      "msec_timestamp": 1695282809904,
      "message": {
        "id": "c1c59db4-64bd-4589-a7db-eb23b13f1cbc",
        "type": "text",
        "text": "start",
        "markup": null,
        "tag": "",
        "media": "",
        "thumbnail": "",
        "file_name": "",
        "file_size": 0
      }
    }
  }


>> to amo 
(bot), за бота отвечает sender.ref_id

{
  "event_type": "new_message",
  "payload": {
    "silent": true,
    "timestamp": 1695282040,
    "msgid": "my_int22-5f2832423423599",
    "conversation_id": "89135292926",
    "conversation_ref_id": "8bdd3f03-b37e-46d0-ace2-4ac5735ea484",
    "sender": {
      "id": "89135292926",
      "ref_id": "dd6e40cd-bbd2-42f2-a92e-ce7db79ae6bb",
      "name": "Artyom"
    },
    "receiver": {
      "id": "89135292926",
      "name": "Artyom"
    },
    "message": {
      "type": "text",
      "text": "закреп с amo_apps_central"
    }
  }
}

>> to amo
// conversation_id соответствует номеру телефона
{
    "event_type": "new_message",
    "payload": {
      "timestamp": 1695281590,
      "msgid": "5d2798a8-f353-4c59-8181-650d0cf44542",
      "conversation_id": "89135292926",
      "sender": {
        "id": "89135292926",
        "name": "Artyom"
      },
      "message": {
        "type": "text",
        "text": "message amo_apps_central"
      }
    }
  }


<<< from amo
// в новых сообщениях амо есть converation.client_id
{
    "account_id": "2b13cae0-24f7-4058-b9ad-c13ee05e1b53",
    "time": 1695284360,
    "message": {
      "receiver": {
        "id": "3e056d0f-a553-4d94-9822-57c257891f22",
        "name": "Сергей",
        "phone": "89135292926"
      },
      "sender": {
        "id": "3cfae55d-387e-409f-9be4-4baab963ee02",
        "name": ""
      },
      "source": {
        "external_id": "c218c790-9be5-4dba-99f8-cbe2b408df25"
      },
      "conversation": {
        "id": "8bdd3f03-b37e-46d0-ace2-4ac5735ea484",
        "client_id": "89135292926"
      },
      "timestamp": 1695284360,
      "msec_timestamp": 1695284360957,
      "message": {
        "id": "222006b5-c0e4-4695-b72d-280aeab6401e",
        "type": "text",
        "text": "как так",
        "markup": null,
        "tag": "",
        "media": "",
        "thumbnail": "",
        "file_name": "",
        "file_size": 0
      }
    }
  }

`````