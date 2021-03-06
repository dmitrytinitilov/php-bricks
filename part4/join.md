# Связи между таблицами. JOIN. Агрегатные функции

Есть таблица workers и departments. Попробуем выбрать работников с их отделами.

```sql
SELECT workers.name as w_name, departments.name as d_name
FROM workers, departments
WHERE workers.dep_id = departments.id
```

Теперь в PHP мы передаем таблицу с двумя полями w_name и d_name.


Проблема такого подхода, является то, что в начале из двух таблиц генерируется таблица, содержащая все возможные комбинации записей первой и второй таблиц. Если в первой таблице N записей, а во второй M, то в промежуточных вычислениях мы получаем таблицу с M*N записей. Если мы работаем с небольшими таблицами порядка 10000 строчек,  то получим таблицу 100 миллионов записей. В дальнейшем с помощью WHERE мы вернем ее к 10K записей. Такой подход нерационален как по памяти, так и по времени.

```sql
SELECT workers.name as w_name, departments.name as d_name
FROM workers JOIN departments 
WHERE workers.dep_id = departments.id
```

JOIN объединит две таблицы, но при такой записи мы не получим выигрыша. Мы по прежнему получаем все комбинации в таблице, а потом их фильтруем

К счастью JOIN позволяет объединять таблицы сразу по условию

```sql
SELECT workers.name as w_name, departments.name as d_name
FROM workers JOIN departments 
ON workers.dep_id = departments.id
```

Попробуем сократить наш запрос, используя псевдонимы на этапе таблиц

```sql
SELECT w.name as w_name, d.name as d_name
FROM workers as w JOIN departments as d 
ON w.dep_id = d.id
```

Наш запрос имеет один недостаток – если работник не находится в каком-либо отделе, то он не попадет в результирующую выборку.

Чтобы исправить эту ситуацию, воспользуемся LEFT JOIN

```sql
SELECT w.name as w_name, d.name as d_name
FROM workers as w LEFT JOIN departments as d
ON w.dep_id = d.id
```

Отличие LEFT JOIN от JOIN состоит в том, что записи первой (левой) таблицы берутся в любом случае. Если им не найдены соответствующие поля с таблицы справа, то вместо них подставляется NULL

RIGHT JOIN аналогичен только для таблицы справа

**Связи между таблицами**

users  - profile (один к одному)<BR>
workers – departments (один ко многим)<BR>
posts – hashtags (многие ко многим)<BR>

На практике связь «многие ко многим» реализуется через промежуточную таблицу


**Полезное чтиво:**

1. Понимание JOIN'ов сломано. Это точно не пересечение кругов, честно
https://habr.com/ru/post/448072/


**Практика:**

1. Создать таблицу departments(id,name) с названиями отделов, добавить поле dep_id в workers. Выбрать всех работников с названием отделов
2. SpeedDating. Есть таблица с именами девушек, есть таблица с именами парней. Есть таблица знакомств - кто с кем познакомился. Вывести для каждой девушки список парней, которые с ней познакомились.








