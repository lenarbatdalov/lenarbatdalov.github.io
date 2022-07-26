# Отправка сообщений
<p>Отправка сообщений использую расширение wazzup.<br>Идентификаторы каналов можно получить из настроек модуля.</p>
<p></p>

### Параметры запроса
> POST
> /api/dev/cbext/clientbase/wazzup/message

| Параметр | Тип данных | Описание |
| --- | --- | --- |
| *channelId | <code>String</code> | Идентификатор канала для рассылки
| *recipient | <code>String</code> | Получатель сообщения
| fieldName | <code>String</code> | Необязательный. Только для Telegram. <br>Отправить использую username контакта в <br>Telegram (без «@» в начале) или phone.
| text | <code>String</code> | Текст сообщения.
| contentUri | <code>String</code> | Ссылка для скачивания файла.

### Успешный ответ
```js
HTTP 200 OK
{
  "messageId": "e6d1336e-0bf1-4d15-b149-868cb75ad70f",
  "chatId": "...462619791...",
  "channelId": "...4-534c-4393-9b15-ff...",
  "chatType": "telegram",
  "username": "__username__",
  "text": "Hello, world! again"
}
```

### Примеры запроса
```js
fetch("./api/dev/cbext/clientbase/wazzup/message", {
  method: "POST",
  credentials: 'include',
  headers: {
    "X-Auth-Token": CB.globals.x_auth_token,
    "Content-Type": 'application/vnd.api+json'
  },
  body: JSON.stringify({
    channelId: '...4-534c-4393-9b15-ff...',
    recipient: '__username__',
    fieldName: 'username'
    text: 'Hello, world! again',
  }),
})
.then(response => console.log(response));
```
```bash
curl https://distr/api/dev/cbext/clientbase/wazzup/message \
  -X POST \
  -H 'X-Auth-Token: <access_token>' \
  -H 'Content-Type: application/vnd.api+json' \
  -d '{
      "channelId": "...4-534c-4393-9b15-ff...",
      "recipient": "79...",
      "fieldName": "phone",
      "text":      "Hello, world!",
    }'
```
