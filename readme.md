# Инструкцию по установке модулей на сайт

В папке `kasko-module` лежат все необходимые файлы.

## Предварительная настройка

В файле `backend/private.php` необходимо ввести Ваш логин и пароль, который Вы можете запросить у вашего менеджера в поддержке сервиса Умный полис (helpdesk@b2bpolis.ru).


```php
define("ITFORM_LOGIN", 'your_login');
define("ITFORM_PASSWORD", 'your_password');
```

Настроить адрес электронной почты для отправки писем с заказами на ваш адрес: настраивается в файле: `backend/mail.php`

```php
$address = 'your@email.com';
```

# Подключение модуля

Чтобы встроить калькулятор на страницу необходимо подключить необходимый набор файлов на страницу.

Подключаем стили и js код на страницу, где будет установлен модуль.

### Подключение стилей

```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/semantic-ui/2.2.4/components/icon.min.css"/>
<link rel="stylesheet" href="css/app.min.css">
<link rel="stylesheet" href="https://qostya.github.io/atomic-emmet/dist/style.css">
```

### Подключение скриптов

Внизу, до закрывающего тега `<body>` необходимо подключить следующие скрипты:

```html
<script src="./js/config.js"></script>
<script src="./js/vendors.min.js"></script>
<script src="./js/templates.js"></script>
<script src="./js/app.min.js"></script>
```

### Вывод калькулятора

В месте где будет выводиться калькулятор, вставьте строку:

```html
<div ng-app="KaskoApp" class="b-app" ui-view ng-class="'b-app--' + currentBrandName"></div>
```

Пример подключение см. в файле:
`index.html`

#### config.js

Также необходимо указать путь до папки `backend`.
Для этого нужно настроить объект с настроками `proxyPath` и
 `proxyPathC` в файле: `js/config.js`
