# #COFFEE Хранение паролей на сервере

Допустим мы храним пароли наших пользователей в незашифрованном виде. Тогда при авторизации нам необходимо сравнить $user_password

Если мы будем хранить пароли на сервере в незашифрованном виде, то при любой утечке из базы данных пароли наших пользователей могут быть считаны(скомпроментированы)

Что мы можем сделать в этой ситуации? Давайте зашифруем наши пароли.



**Восстановление пароля**



**Радужные таблицы и соль**

md5(password)

md5(password+id);


