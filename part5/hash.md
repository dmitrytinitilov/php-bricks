# Понятие хеша

Способы отслеживания пользователя с помощью куки. 

Рассмотрим простейший способ генерации хеша. В идеале, хеш – это просто набор случайных символов. Мы же воспользуемся функциями mt_rand и md5

$hash = md5(mt_rand(10000,1000000));

Безусловно, такой хеш надежным не назовешь, но для тренировочных целей  его будет достаточно.

Теперь создадим таблицу hashes с полями id, hash

Когда пользователь заходит на наш сайт первый раз, мы генерируем хеш и сохраняем его в куке пользователя. Также добавляем его в нашу базу данных.

Если пользователь заходит повторно, то мы считываем его хеш из куки и проверяем его по нашей базе данных.


**Практика:**
1.  Запрашиваем у пользователя имя. Создаешь хеш и сохраняем в БД имя и хеш. Если пользователь приходит к нам еще раз. Выводим ему его имя(по хешу, который хранится в куке)
1.	Сохранение состояния прямоугольника для каждого пользователя
2.	Задача на пиксель и создание треккинг куки
3.	Создание корзины
4.	Учет количества товаров в корзине
