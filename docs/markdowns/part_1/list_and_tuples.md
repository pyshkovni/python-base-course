# Коллекции. Списки и кортежи

## Полезная информация о print

Функция `print()` имеет необычные аргументы. В консоль можно выводить сразу несколько аргументов, разделяя их запятой. Аргументы могут быть разных типов данных.

```Python
print("Переменная а:", 10)
```

Обратите внимание, что между строкой и числом ставится пробел, который ставится по умолчанию. Если после всех аргументов для вывода в консоль написать аргумент с именем `sep`, то вместо пробела, будет другой разделяющий символ. Например, набор символов `\n`, который позволяет сделать перенос строки на следующую.

```Python
print("Покупки", "апельсин", "яблоко", "банан", sep="\n")
```

Именованный аргумент `end` убирает символ переноса строки по умолчанию и ставит то, что указано в функции.

```Python
print(1, end=" ")
print(2, end=" ")
print(3, end=" ")
```

## Разновидности коллекций

Мы разобрали несколько типов данных (`int`, `float` и `str`), которые позволяют нам представить данные в виде абстракции. Но что если, нам нужно обратиться к совокупности подобных абстракций. 

Для этого в Python выделяют `коллекции` - объекты-контейнеры, которые хранят другие объекты, чтобы обращаться к ним как к единой абстрации. Это позволяет также применять специальные функции и методы.

В Python существуют следующие коллекции.

* Списки `list`
* Кортежи `tuple`
* Множества `set`
* Словари `dict`

### Списки

Рассмотрим списки `list` – **изменяемые коллекции, которые можно формировать из любых объектов**, а также добавлять в список и удалять из него элементы.

Примеры создания списков в блоке кода ниже.

```Python
shop_lst = ['apple', 'banana', 'orange']  # список строк
primes = [1, 2, 3, 10, 15, -20]  # список чисел

# пустой список
empty_lst = []
# или
empty_lst = list()

# список может состоять из списков и переменных
lst = [[1, 2, 3], [4, 5, 6], digits]

# то есть, список может включать что угодно!
lst = [1, ["a", True], "b"]
```

**Обратите внимание на имя переменной `lst`**. Так можно указать, что за переменной скрывается список, но не использовать при этом символ `i`, который часто можно встретить как имя переменной цикла

Список, как и строки, можно индексировать поэлементно.

```Python
shop_lst = ['apple', 'banana', 'orange']

# индексация списков
print(shop_lst[0])
print(shop_lst[::-1])
```

### Методы

Некоторые типы данных обладают специфическими свойствами. Например, строку `str`, которая содержит символы _abc_, можно отобразить в верхнем регистре, как _ABC_, а число `int` нельзя перевести в верхний регистр. 

`Метод` – **это функция, которая задана для конкретного типа данных** _(функция, которая определена внутри класса)_. Методы также принимают параметры и выполняют определенный код, но они всегда привязаны к конкретному типу данных. Поэтому **нельзя вызвать метод, которого у соответствующего типа данных нет**.

Использование методов можно увидеть в [Задаче №1](first_task.md). Для исследуемой строки был использованы методы `find` `rfind` и `split`. Методы также существуют и для списков. Ниже приведены некоторые из них.

Название        | Обозначение
:--             | :--
`append(x)`     | добавить элемент в конец списка
`insert(i, x)`  | вставить элемент перед указанным индексом
`pop(i)`        | вытащить элемент из списка по индексу и убрать его из списка

Пример использования метода списка `append`.

```Python
lst = [1, 2, 3]  # список чисел
lst.append(4)    # метод добавления числа в конец списка

100.append(4)      # Ошибка! Такого метода для int не существует
```

### Кортежи. Отличия от списков

Кроме списков часто можно встретить кортежи `tuple` - **неизменяемые коллекции**. Кортеж можно создать следующим образом.

```Python
rainbow = ("red", "green", "blue")  # кортеж строк
empty_tpl = ()  # пустой кортеж
# или
empty_tpl = tuple()
```

**Для чего нужен кортеж?**

1. **Он создается быстрее списка**. Следует помнить, что коллекция занимает в памяти компьютера зарезервированное место, а по соседству с ней могут находиться ячейки, занятые другими объектами. Кроме того, каждый элемент коллекции нужно пронумеровать и в случае, если коллекция имеет возможность хранить новые элементы, то все индексы предыдущих элементов будут сдвигаться. Такой коллекцией является список и для его создания и изменения требуется много времени, в отличии от работы с кортежем.

Проверить данное утверждение можно следующем образом. Чтобы вывести в консоль информацию о существующих методах для типа данных, можно использовать функцию `dir()`.

```Python
# вывод в консоль результата функции dir для кортежа tuple 
print(dir(tuple()))
```

Вывод будет выглядеть следующим образом.

```
['__add__', '__class__', '__class_getitem__', ... , 'count', 'index']
```

Мы получили **список доступных методов** для типа данных `tuple`. Обратите внимание, что методы, которые начинаются с двойного подчеркивания, мы не рассматриваем. Это _магические методы Python_, о которых подробнее можно узнать в объектно-ориентированном программировании на Python. После них начинаются имена методов без нижнего подчеркивания, которые нам и нужны. **Из доступных для кортежа методов есть только два: `count` и `index`**.

Теперь рассмотрим доступные методы для списка.

```Python
# аналогично для списков list
print(dir(list()))
```

Для списков вывод будет выглядеть следующим образом.

```
[ ... , '__str__', '__subclasshook__', 'append', 'clear', 'copy', 'count', 'extend', 'index', 'insert', 'pop', 'remove', 'reverse', 'sort']
```

**Для списков доступно 11 методов!** В списки можно добавлять значения, удалять их, менять порядок элементов и тд. Для кортежей можно посчитать количество идентичных элементов и найти индекс элемента (методы `count` и `index`, соответственно). Поэтому списки `list` являются изменяемыми коллекциями, а кортежи `tuple` неизменяемыми.

**Для чего еще нужен кортеж?**

2. В Python многие операции работают за счет кортежей. Например, множественное присвоение. Также некоторые функции возвращают пары значений, которые сформированы в кортежи, как показано в примере b. Об этом мы поговорим в следующих разделах.

    a. множественное присвоение

    ```Python
    x, y, z = 1, 2, 3

    # на самом деле выглядит как два кортежа
    (x, y, z) = (1, 2, 3)
    ```

    b. возвращаемые значения

    ```Python
    for i in enumerate(rainbow):
        print(i, type(i))
    ```

### Проблема изменяемых коллекций

В чем разница между изменяемыми и неизменяемым коллекциями? Например, между `list` и `tuple`.

Рассмотрим следующий пример. Создадим список городов _towns_. Иногда можно возникнуть необходимость дублировать объект, чтобы не менять исходник. Поэтому мы попробуем создадим копию через создании переменной _cities_ и добавим к копии списка новый город.

**Обратите внимание! Для чисел или строк описанный выше способ сработает!**

```Python
x = 1
y = x

y = y + 100
print(x, y) # 1 101
```

Тем не менее, для списка ответ будет несколько иным.

```Python
# список городов
towns = ["Москва", "Санкт-Петербург", "Казань"] 
# Дублируем его в другую переменную

cities = towns
cities.append("Новосибирск")

# посмотрим на cities и towns
print("cities -", cities)
print("towns -", towns)
```

**То есть, изменив что-то в одном списке, изменения происходят и в исходном!**

Для кортежа ситуация будет такой же, как и чисел

```Python
rainbow = ("red", "green", "blue")
# Выше мы объявили кортеж цветов rainbow
# дублируем его в другую переменную
colors = rainbow
colors += ("violet",)

# посмотрим на colors и rainbow
print("colors -", colors)
print("rainbow -", rainbow)
```

Конечно, методы вызываемые для списка меняют сам список, вне зависимости от количества имен переменных, которые к нему привязаны. Вы можете провести сложение списков и увидите, что они действительно изменятся. Однако, учитывайте, что **методы списка `list` меняют сам список и для всех переменных, которые к нему привязаны, тоже произойдут изменения**. Для кортежей будет происходить **создание нового кортежа `tuple` с новым набором элементов**. Поэтому кортежи являются неизменяемыми.

Ниже приведен список изменяемых и неизменяемых типов данных в Python.

Неизменяемые                  | Изменяемые
:--                           | :--
числа `int`                   | списки `list`
вещественные числа `float`    | словари `dict`
кортежи `tuple`               | множества `set`
строки `str`                  |
логический тип данных `bool`  |

### Множества

Немного о множествах. **Множество `set` – это изменяемая коллекция уникальных неупорядоченных элементов**.

Множество можно создать с помощью `set()`. Также существует запись с помощью фигурных скобок при наличии более одного элемента.

```Python
A = set([1, 2, 3, 3])
B = {2, 3, 7, 8}

print(A)  # {1, 2, 3}
```

В множество **каждый элемент может входить только один раз**! Например, если записать в множестве строку, то получим множество символов, которые не повторяются.

```Python
letters = set('Hello World!')
print(letters)  # {' ', '!', 'e', 'o', 'l', 'W', 'd', 'r', 'H'}
```

Как и в математике, множества в Python имеют те же свойства: объединение, пересечение и другие операции о которых подоробнее вы можете узнать [по ссылке](https://proglib.io/p/samouchitel-po-python-dlya-nachinayushchih-chast-8-metody-raboty-so-mnozhestvami-2022-12-11).

**Промежуточный итог и справка по вопросам**

Теперь вы знаете что такое списки и кортежи, какие для них встречаются методы. Следующие параграфы посвящены вопросам по теме. Постарайтесь ответить на предложенные вопросы **сначала самостоятельно, потом перейти к объяснениям**. В объяснениях будет рассмотрен подробнее новый материал, поэтому обязательно изучите их.

## Вопросы по теме

### Вопрос 1

Каким будет результат выполнения кода ниже?

```Python
a = [10, 20]
b = a
b += [30, 40]
print(a)
print(b)

# [10, 20], [10, 20, 30, 40]
# [10, 20, 30, 40], [10, 20, 30, 40]
```

### Вопрос 2

Каким будет результат выполнения кода ниже?

```Python
a = ['раз', 'два', 'три']
print('четыре'.join(a))

# ['раз', 'два', 'три', 'четыре']
# ['раз два три четыре']
# 'раз два три четыре'
# 'разчетыредвачетыретри'
```

### Вопрос 3

Каким будет результат выполнения кода ниже?

```Python
lst = [1, 2, 3]
lst_cpy = lst.copy()
print(lst_cpy is lst)

# True
# False
# None
# Error
```

### Вопрос 4

Каким будет результат выполнения кода ниже?

```Python
lst = [13, 56, 17]
lst.append([87])
lst.extend([45, 67])
print(lst)

# [13, 56, 17, 87, 45, 67]
# [13, 56, 17, [87], 45, 67]
# [13, 56, 17, [87], [45, 67]]
# [13, 56, 17, 87, [45, 67]]
```

### Вопрос 5

Каким будет результат выполнения кода ниже?

```Python
strLst = list("Python")
strLst.sort()
str_ = " ".join(strLst)

print(str_)

# ['h', 'n', 'o', 'P', 't', 'y']
# h n o P t y
# ['P', 'h', 'n', 'o', 't', 'y']
# P h n o t y
```

### Вопрос 6

Каким будет результат выполнения кода ниже?

```Python
lst = [1, 2, 3]
lst *= -3

print(lst)

# []
# [-3, - 6, - 9]
# [3, 2, 1]
# Error
```

### Вопрос 7

Каким будет результат выполнения кода ниже?

```Python
lst = [0, 2, 3, 4]
lst.pop(1)
print(lst)

# [0, 1, 2, 3, 4]
# [0, 2, 3, 4, 1]
# [0, 3, 4]
# Error
```

### Вопрос 8

Каким будет результат выполнения кода ниже?

```Python
grif = ['Гарри', 'Гермиона', 'Рон', 'Невилл']
slis = grif.index('Драко')
print(slis * 3)

# Драко Драко Драко
# Гарри
# Гарри Гарри Гарри
# ['', '', '']
# Error 
```

### Вопрос 9

Каким будет результат выполнения кода ниже?

```Python
lstOne = list('bob')
lstTwo = list('obo')
lstThree = list('bo')

print(lstOne + lstTwo - 2 * lstThree)

# ['bob', 'o']
# ['b', 'o', 'bob', 'o']
# []
# Error
```

### Вопрос 10

Каким будет результат выполнения кода ниже?

```Python
fvar = 0,3
ivar = 3
print(fvar * ivar)

# 0,9
# [0, 3], [0, 3], [0, 3]
# (0, 3, 0, 3, 0, 3)
# Error
```

### Вопрос 11

Каким будет результат выполнения кода ниже?

```Python
lst = [2, 4, 6, 8]
lst = lst + (10, )
print(lst)

# [12, 4, 6, 8]
# [12, 14, 16, 18]
# [2, 4, 6, 8, 10]
# TypeError
```

### Вопрос 12

Каким будет результат выполнения кода ниже?

```Python
tup = (1, 'Python', 'P')
var = tup[1:2]
print(type(var))

# <class 'string'>
# <class 'tuple'>
# <class 'list'>
# Error
```

## Ответы на вопросы и пояснения

### Ответ на вопрос 1

Каким будет результат выполнения кода ниже?

```Python
a = [10, 20]
b = a
b += [30, 40]
print(a)
print(b)

# [10, 20], [10, 20, 30, 40]
# [10, 20, 30, 40], [10, 20, 30, 40]  <- правильно
```

**Обратите внимание!**

Т.к. b и а отсылаются к одному объекту, использование += на b меняет значение и a, и b.

### Ответ на вопрос 2

Каким будет результат выполнения кода ниже?

```Python
a = ['раз', 'два', 'три']
print('четыре'.join(a))

# ['раз', 'два', 'три', 'четыре']
# ['раз два три четыре']
# 'раз два три четыре'
# 'разчетыредвачетыретри'  <- правильно
```

**Обратите внимание!**

Метод `.join` объединяет список строк в одну большую строку. В данном случае _'четыре'_ выступает как строка-соединитель.

### Ответ на вопрос 3

Каким будет результат выполнения кода ниже?

```Python
lst = [1, 2, 3]
lst_cpy = lst.copy()
print(lst_cpy is lst)

# True
# False  <- правильно
# None
# Error
```

**Обратите внимание!**

Так как `lst_cpy` и `lst` отсылаются к разным объектам, сравнение через `is` выдаст `False`. Подробнее про оператор `is` [по ссылке](https://developers.sber.ru/help/gigachat/catalog/v-chem-raznicza-mezhdu-i-is-na-python).

### Ответ на вопрос 4

Каким будет результат выполнения кода ниже?

```Python
lst = [13, 56, 17]
lst.append([87])
lst.extend([45, 67])
print(lst)

# [13, 56, 17, 87, 45, 67]
# [13, 56, 17, [87], 45, 67]  <- правильно
# [13, 56, 17, [87], [45, 67]]
# [13, 56, 17, 87, [45, 67]]
```

**Обратите внимание!**

Функция `.append()` просто добавляет аргументы в конец списка «как есть», в то время как `.extend()` сначала расширяет список, а затем дополняет его аргументами.

### Ответ на вопрос 5

Каким будет результат выполнения кода ниже?

```Python
strLst = list("Python")
strLst.sort()
str_ = " ".join(strLst)

print(str_)

# ['h', 'n', 'o', 'P', 't', 'y']
# h n o P t y
# ['P', 'h', 'n', 'o', 't', 'y']
# P h n o t y  <- правильно
```

**Обратите внимание!**

Сначала мы создаём список `strLst = ['P', 'y', 't', 'h', 'o', 'n']`, который тут же сортируем. В итоге получаем `['P', 'h', 'n', 'o', 't', 'y']`

Затем этот список мы превращаем в строку, где каждый элемент `strLst` будет разделён при помощи пробела. Итоговый вариант `(P h n o t y)` и выводим на экран

### Ответ на вопрос 6

Каким будет результат выполнения кода ниже?

```Python
lst = [1, 2, 3]
lst *= -3

print(lst)

# []  <- правильно
# [-3, - 6, - 9]
# [3, 2, 1]
# Error
```

**Обратите внимание!**
При умножении списка на 0 или отрицательное число, мы получаем пустой список.

### Ответ на вопрос 7

Каким будет результат выполнения кода ниже?

```Python
lst = [0, 2, 3, 4]
lst.pop(1)
print(lst)

# [0, 1, 2, 3, 4]
# [0, 2, 3, 4, 1]
# [0, 3, 4]  <- правильно
# Error
```

**Обратите внимание!**

Функция `pop(n)` убирает элемент с индексом n из списка. В данном случае `pop(1)` удаляет элемент 2, оставляя лишь `[0, 3, 4]`

### Ответ на вопрос 8

Каким будет результат выполнения кода ниже?

```Python
grif = ['Гарри', 'Гермиона', 'Рон', 'Невилл']
slis = grif.index('Драко')
print(slis * 3)

# Драко Драко Драко
# Гарри
# Гарри Гарри Гарри
# ['', '', '']
# Error  <- правильно
```

**Обратите внимание!**

Задача `index()` — найти позицию, на которой находится аргумент в заданном списке
Так как элемента 'Драко' в списке `grif` не существует, то и выводится ошибка

### Ответ на вопрос 9

Каким будет результат выполнения кода ниже?

```Python
lstOne = list('bob')
lstTwo = list('obo')
lstThree = list('bo')

print(lstOne + lstTwo - 2 * lstThree)

# ['bob', 'o']
# ['b', 'o', 'bob', 'o']
# []
# Error  <- правильно
```

**Обратите внимание!**

У типа данных `list` нет операции вычитания. Отсюда и ошибка: `TypeError: unsupported operand type(s) for -: 'list' and 'list'`

### Ответ на вопрос 10

Каким будет результат выполнения кода ниже?

```Python
fvar = 0,3
ivar = 3
print(fvar * ivar)

# 0,9
# [0, 3], [0, 3], [0, 3]
# (0, 3, 0, 3, 0, 3)  <- правильно
# Error
```

**Обратите внимание!**

`fvar = 0,3` создаёт переменную, в которой хранится `tuple` вида (0, 3). В итоге умножая это дело на `ivar`, равный 3, мы получаем итоговый ответ — `(0, 3, 0, 3, 0, 3)`

### Ответ на вопрос 11

Каким будет результат выполнения кода ниже?

```Python
lst = [2, 4, 6, 8]
lst = lst + (10, )
print(lst)

# [12, 4, 6, 8]
# [12, 14, 16, 18]
# [2, 4, 6, 8, 10]
# TypeError  <- правильно
```

**Обратите внимание!**

TypeError — операция конкатенирования («склеивания») возможна лишь между списком `list` и списком. В данном случае (10, ) — это `tuple`.

### Ответ на вопрос 12

Каким будет результат выполнения кода ниже?

```Python
tup = (1, 'Python', 'P')
var = tup[1:2]
print(type(var))

# <class 'string'>
# <class 'tuple'>  <- правильно
# <class 'list'>
# Error
```

**Обратите внимание!**

Элемент `tup[1:2]` всё ещё является частью типа данных `tuple`. Если вывести `print(var)`, то консоль выведет `('Python', )`.
