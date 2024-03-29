Логгер для накапливания записей в памяти
========================================

Этот странный логгер можно использовать в модулях для систем, где нет встроенного PSR-3 логгера или в обработчиках 
запросов к API, когда вместе с ответом на запрос нужно отдать отладочную информацию о процессе обработки запроса.

Типичная схема работы с логгером:

````php
$logger = new ProcessLogger(...);

$logger->info(...);

..
$logger->info(...);

...

$logger->debug(...);

...

$logger->info(...);

...

if($logger instanceof ProcessLogger) $text = $logger->flush();

````

Выгрузку накопленных записей и сохранение их в файл можно выполнять, например в методе `__destruct` основного класса
вашего модуля. Или в методе формирования ответа на запрос API.

Единственный нестандартный метод логгера — `flush()` который объединяет в строку все записи, используя для их
объединения символ переноса строки и выдает текст, готовый для записи в файл.
