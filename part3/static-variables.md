# # Статические переменные

Главное отличие статической переменной от нестатической в том, что статическая сохраняет свое значение и область памяти после завершения функции.

```php
<?php
function funct(){
     static $int = 0;          // верно
     static $int = 1+2;        // неверно  (поскольку это выражение)
     static $int = sqrt(121);  // неверно  (поскольку это тоже выражение)

     $int++;
     echo $int;
}
```

**Подробнее**
http://www.php.su/learnphp/vars/?statvars


**Практика:**

1.	Сделать функцию, которая считает количество своих вызовов
2.	Сделать функцию копилку
3.	Бонусное задание: сделать калькулятор. Функции для подсчета выносим в библиотеку
