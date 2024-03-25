### Телеграмм бот

Регистрация бота
1. Обращаемся к @BotFather
2. Выбираем команду /newbot
3. Пишем имя для бота, на конце должно быть слово «bot» или «_bot».
4. Ответным сообщением получим токен, сохраняем его.

### Возможные настройки:
/setname	- имя
/setdescription	- краткое описание
/setabouttext	- описание бота
/setuserpic	- 


Далее у нас два варианта работы через установку Webhook тогда все сообщения от пользователей из Telegram будут обрабатываться скриптом на сайте https://example.com/bot.php.

### Установка Webhook 
https://api.telegram.org/bot<token>/setWebhook?url=https://example.com/bot.php
Удаление Webhook 
https://api.telegram.org/bot<token>/deleteWebhook?url=https://example.com/bot.php


### Обработка входящих сообщений
Сообщения приходят POST запросом с типом application/json, получить его можно следующим образом:
$data = file_get_contents('php://input');
$data = json_decode($data, true);
Для просмотра входящих данных сразу будем записывать их в файл:
file_put_contents(__DIR__ . '/message.txt', print_r($data, true));
