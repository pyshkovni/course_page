# Задача №2. Изменение списка покупок. Форматированный вывод

**Рекомендации**

Перед тем, как приступить к разбору решения, попробуйте решить задачу самостоятельно.

## Условие задачи

Внимательно прочтите условие задачи и скопируйте в среду разработки.

```Python
# Приведем список покупок в магазине

shop_list = ['Картофель', 'Горошек', 'Рис', 'Хлеб']

# Измените список согласно пунктам задания
# Выведите результат каждого пункта на консоль по очереди

# а. Вставьте рыбу между горошком и рисом

# b. Добавьте фрукты из списка fruits в конец списка shop_list
                 
# c. Удалите из списка shop_list картофель

# d. Какими по счету стоят хлеб и апельсин? Выведите номера на консоль в формате:
#   Номер "продукта" в списке - N 

```

## Решение

Заметим, что в задаче идет работа с элементами списка, что говорит нам об использовании методов списка. 

Чтобы посмотреть доступные методы, предварительно выведите в консоль список методов через функцию `dir()`

```Python
shop_list = ['Картофель', 'Горошек', 'Рис', 'Хлеб']
print(dir(shop_list))
```

Для изучения возможностей методов изучите документацию [по ссылке](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists), либо воспользуйтесь поисковиком.

### Пункт a.

В задаче требуется вставить строку между двумя известными элементами списка. Для этого можно воспользоваться методом `insert()`.

```Python
# а. Вставьте рыбу между горошком и рисом

shop_list.insert(2,'Рыба')
print(shop_list)
```

**Обратите внимание! Результат работы метода без присвоения имени переменной**

Рассмотрим, что произошло, если бы мы работу метода `insert` записали бы в переменную.

```Python
new_list = shop_list.insert(2,'Рыба')
print(new_list)  # Ответ None?
```

Переменная `shop_list` получит значение `None`, то есть в ней пустой тип данных. Дело в том, что некоторые методы меняют сам исходный объект. Это актуально для списков, так как они являются изменяемыми типами данных. Как правило, результатом работы функции или метода является число, строка или другой тип данных. Но в данном, результатом функции является ничего `None`. Это тип данных, который отображает пустые данные.

Поэтому, если функция или **метод ничего не возвращает**, но при этом меняет исходный объект, **то присваивать результату работы функции или метода имя переменной не нужно**!

### Пункт b.

Требуется дополнить список `shop_list` элементами другого списка `fruits`. Для добавления в конец существует два метода: `append()` и `extend()`, подробнее о которых была рассмотрено [в объяснении вопроса 4](list_and_tuples.md#ответ-на-вопрос-4). В данном случае используем метод `extend()`

```Python
# b. Добавьте фрукты из списка fruits в конец списка shop_list

fruits = ['Яблоко', 'Апельсин', 'Клубника']

shop_list.extend(fruits)
print(shop_list) 
```

### Пункт c.

Есть несколько способов удаления элементов из списка. 

* с помощью метода `remove` - в аргументах указывается **искомый элемент**, который будет удален из списка
* с помощью метода `pop` - в аргументах указывается **индекс искомого элемента**. Метод **возвращает элемент** списка, но из списка он удаляется.
* с помощью оператора `del` - указывается оператор и элемент через индексацию списка.

Рассмотрим три способа по отдельности.

```Python
# c. Удалите из списка shop_list картофель

# ЗАМЕТКА
# раскомментируйте вариант, который хотите проверить
# закомментируйте остальные варианты
# Быстро закомментировать строку или область Ctrl + /

# вариант 1 
shop_list.remove("Картофель")
print(shop_list)

# вариант 2
# del shop_list[0]
# print(shop_list)

# вариант 3
# item = shop_list.pop(0))
# print(item, shop_list, sep=" ")
```

### Пункт d.

Задача кажется не трудной. Выведем индексы искомых элементов.

```Python
# d. Какими по счету стоят хлеб и апельсин? Выведите номера на консоль в формате
# Номер "продукта" в списке - N 

fitem = 'Хлеб'
sitem = 'Апельсин'

print(
    shop_list.index(fitem),
    shop_list.index(sitem),
    sep="/n"
    )
```

Теперь попробуем вывести результат в предложенном виде.

```Python
print("Номер товара '" ,fitem, "'в списке", shop_list.index(fitem))

# Номер товара ' Хлеб 'в списке 2
```

Довольно неудобно в таком виде выводить строки, так как сложно расставлять переменные. Также возможен вариант сложения строк, но здесь большая вероятность наткнуться на другой тип данных, с которым строки складывать нельзя.

### Форматирование строк

Удобным методом для объединения значений переменных в одной строке является `format()`. Разберем пример использования.

```Python
print("Номер товара '{}' в списке - {} ".format(fitem, shop_list.index(fitem)))

# Номер товара 'Хлеб' в списке 2
```

Все переменные указываются в аргументах метода. Полученные переменные по порядку подставляются в строку на месте фигурных скобок `{}`.

Однако и у такого способа **есть недостаток**. Если строка содержит много переменных для вставки, то очень легко запутаться, где та или иная переменная будет находится. Пример подобной строки `"htpps://www.ranepa.ru/profile/func?={}/{}/{}/{}".format()`.

Поэтому появилось упрощение записи метода `format()` - `f-строка`. Принцип прост. Пишем строку, в которой расставляем фигурные скобки `{}` на местах, где вставить переменные, ставим перед кавычками строки `f`, а внутри фигурных скобок расставляем имена переменных.

```Python
print(f"Номер товара '{fitem}' в списке - {shop_list.index(fitem)}")
# Номер товара 'Хлеб' в списке 2
```

Формирование сложных строк с помощью `f-строк` не обязателен, но **для формирования ссылок url или путей к файлу** такой способ является **предпочтительным**.