После деплоя стенда, переходим в браузере по адресу
`http://192.168.100.101/postfixadmin/public/setup.php`

Вводим произвольный, но соответствующий политикам, пароль, для теста использовался `P@ssw0rd8`

Прожимаем `Enter`, будет сгенерирована строка, которую необходимо вставить вместо строки в следующем файле

```
/usr/share/nginx/html/postfixadmin/config.inc.php
  вместо строки
    $CONF['setup_password'] = 'changeme';
```

после подстановки строки `$CONF['setup_password']`, возвращаем в браузер и создаем учетную запись суперпользователя,
использую во всех полях тот же пароль, что и ранее, для теста использовался `P@ssw0rd8`
Жмем `Enter`, видим следующее сообщение:

будет предложен переход на страницу
`http://192.168.100.101/postfixadmin/public/login.php`

Далее, можно отправлять сообщения, через `telnet` с хоста, на котором был развернут стенд,

Для отправки сообщения с хоста подключаемся к `postfix`, на стенде
`telnet 192.168.100.101 25`

```
helo domain.dlt
mail from: root@domain.tld
rcpt to: root@localhost
data

Hello, world!

.
quit
```

Cообщения появятся в файле
`less /var/spool/mail/root`
