# exampletask
GREEN-API: тестовая страница
Одностраничное приложение (HTML + JavaScript, без зависимостей) для работы с WhatsApp через GREEN-API.
Демо: https://nicoruvich.github.io/exampletask/
Возможности
Страница вызывает четыре метода GREEN-API и показывает ответ в поле справа (только для чтения):
Метод	Что делает	HTTP
`getSettings`	Возвращает настройки инстанса	GET
`getStateInstance`	Возвращает состояние инстанса (например, `authorized`)	GET
`sendMessage`	Отправляет текстовое сообщение	POST
`sendFileByUrl`	Отправляет файл по ссылке	POST
Как пользоваться
Зарегистрируйтесь в личном кабинете GREEN-API и создайте инстанс на бесплатном тарифе разработчика.
Отсканируйте QR-код в WhatsApp на телефоне, чтобы подключить номер к инстансу.
Откройте страницу и введите `idInstance` и `ApiTokenInstance` из карточки инстанса.
Нажимайте кнопки методов. Результат появится в поле «Ответ».
Для `sendMessage` и `sendFileByUrl` укажите номер получателя в международном формате без `+` и пробелов (например, `77771234567`). Для `sendFileByUrl` нужна прямая ссылка на файл.
Как это работает
Страница отправляет запросы на адрес вида:
```
https://api.green-api.com/waInstance{idInstance}/{метод}/{ApiTokenInstance}
```
Для отправки номер преобразуется в `chatId` формата `77771234567@c.us`.
Пример тела запроса для `sendMessage`:
```json
{ "chatId": "77771234567@c.us", "message": "Hello World!" }
```
Для `sendFileByUrl`:
```json
{ "chatId": "77771234567@c.us", "urlFile": "https://example.com/img/horse.png", "fileName": "horse.png" }
```
Безопасность
`idInstance` и `ApiTokenInstance` вводятся вручную, нигде не сохраняются и отправляются только на `api.green-api.com`. Не публикуйте их в репозитории.
Структура проекта
```
index.html   # вся страница: разметка, стили и скрипт
README.md
```
Запуск локально
Откройте `index.html` в браузере. Сборка и сервер не нужны.
