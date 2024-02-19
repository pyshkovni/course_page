# Импорт из модулей и пакетов

## Модули

### Создание модуля

**`Модуль` - это отдельный файл, определения и выражения внутри которого можно использовать в других файлах**.

Разберем импорт имен на примере модуля `mathematics.py`, который можно [скачать по ссылке](files/mathematics.py). Далее, добавьте скачанный модуль в ваш проект.

**Обратите внимание**, что в следующих разделах модулем будет называться файл с расширением `.py`.

Часть содержимого модуля `mathematics.py` можно также посмотреть в блоке кода ниже.

```Python
######## MODULE: mathematics ########

## Mathematics contains functions with mathematical operations are used to perform various mathematical operations,
## such as finding the roots of an equation, exponentiation, multiplication and division.
## about Sphinx documentation – https://sphinx-rtd-tutorial.readthedocs.io/en/latest/docstrings.html


def square_root(val: int) -> float:
    """
    The function returns the square root of the number.
    
    :param val: a number from an integer set
    :type val: int
    
    :return: squre root of val
    :rtype: float
    """
    return val ** .5

# и тд
```

Подробнее об используемом оформлении функций вы можете посмотреть в теме [Функции. Свойства и параметры функций](/docs/markdown/part_1/functions.md#документирование-и-аннотация-функции)

В проекте сейчас имеется два модуля:

* main.py
* mathematics.py

### Способы импорта из модуля

Самым простым способом для того, чтобы получить доступ к выражениям другого модуля (файла), является вызов оператора `import`.

В файле main.py

**Первым способом является импорт имени модуля**. Для доступа к именам функций необходимо сначала указать имя модуля, затем, после точки, указать имя функции для импорта в текущий файл. Именем модуля является имя файла без добавления суффикса `.py`.

```Python
## Способ 1 – импорт имени модуля
## пример из практики: import os, import sys

import mathematics
print(mathematics.multiply(4, 4))
```
