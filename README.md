# parse_bm_tg
Выборка русскоязычных разговорных групп (TG) из Brandmeister для их автоматического обновления на страничке.

Скопируйте `parse_tg.py` в /usr/local/sbin/

Скопируйте скрипт `1tg` в /etc/cron.weekly/ для еженедельного обновления списка TG.

Авторизация на BM не нужна. После окончания работы скрипта в папке /tmp/ видим файл tg.txt который будет скопирован в /var/www/html/

В нужном месте php-странички создаём форму для отображения скачанного и обработанного списка из файла tg.txt:

```HTML
<?php
   $filePath = __DIR__ . '/tg.txt';
   if (file_exists($filePath) && is_readable($filePath)) {
       $fileContent = file_get_contents($filePath);
       echo "<pre>" . htmlspecialchars($fileContent) . "</pre>";
   } else {
       echo "<p>Файл <code>tg.txt</code> не найден или недоступен для чтения.</p>";
   }
?>
```
Дальше всё зависит от дизайна и может выглядеть как на [сайте rn6ljt](http://176.192.125.149:88/).
