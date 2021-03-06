#Быстрый старт

1. Устанавливаем composer

    https://getcomposer.org/download/
    
    установка composer под OpenServer
    http://nikolaev-web.ru/blog/installing_the_composer_on_openServer/
    
    Проверяем настроены ли у нас пути к php
    
    ```cli
    php -v
    ```
    
    Далее загружаем composer
    
    ```cli
    php -r "readfile('http://getcomposer.org/installer');" | php -- --disable-tls
    ```
    
    Пробуем запустить composer
    ```cli
    php composer.phar -V
    ```
    
    Создадим composer.bat
    
    ```cli
    echo @php "%~dp0composer.phar" %*>composer.bat
    ```
    
    Проверить установился ли Composer
    ```
    composer -V
    ```
    Если composer не найден, нужно убедиться, что прописаны переменные среды
    ```
    %USERPROFILE%\AppData\Roaming\Composer\vendor\bin
    ```
    
    Часто нужны следующие пути
    ```
%USERPROFILE%\AppData\Local;%USERPROFILE%\AppData\Roaming;%USERPROFILE%\AppData\Roaming\composer\vendor\bin;%USERPROFILE%\AppData\Roaming\composer;C:\OpenServer\modules\php\PHP-5.6;
    ```
     
    Добавим extension_dir в php.ini
    
    ```
    extension_dir="ext"
    ```
     
    Обновимся до последней версии
    
    ```
    composer self-update
    ```
    
    Если возникают проблемы с OpenSSL заглядываем в php.ini
    
    для помощи могут понадобиться
    
    ```
    php --ini, php -m and composer show -p
    ```
    
    
2. Устанавливаем через Composer инсталлятор Laravel 

    ```
    composer global require "laravel/installer"
    ```

3. Создаем новый проект. Выходим из папки PHP и переходим в папку проекта

    ```
    laravel new
    ```

4. Если папка vendor не появилась, выполняем в папке

    ```
    composer update
    ```
    
    ```
    composer update --no-scripts  
    ```
    
5. По умолчанию, любая ошибка отображается ввиде сообщения      Whoops, looks like something went wrong. Чтобы это исправить, заходим в папку config, находим app.php в нем находим параметр APP_DEBUG и ставим его true
    
    ```php
        'debug' => env('APP_DEBUG', true),
    ```
    
6. Если возникает ошибка RuntimeException in Encrypter.php line 43: The only supported ciphers are AES-128-CBC and AES-256-CBC with the correct key lengths , то в корне проекта необходимо сделать файл .env

Затем сгенерировать ключ с помощью команды

```
php artisan key:generate
```

Копируем ключ и добавляем его в файл .env, в APP_KEY. Получаем строчку вида
 
```
APP_KEY=base64:vash_code_zdes
```

7. По адресу http://lara.org/public/ должна открыться стартовая страница Laravel

**Полезное чтиво:**

1. Устанавливаем Composer под OpenServer
http://nikolaev-web.ru/blog/installing_the_composer_on_openServer/

