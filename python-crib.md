# Установка ПО

Python 
- [Дистрибутив](https://www.python.org/) 
- [Python 3.8.7 32bit for Win7](https://www.python.org/ftp/python/3.8.7/python-3.8.7.exe)
- [32 или 64](https://docs-python.ru/tutorial/ustanovka-python/vybiraem-razrjadnost-windows/)
- [Using Python on Windows](https://docs.python.org/3/using/windows.html#using-on-windows)

PyCharm
- [Дистрибутив](https://www.jetbrains.com/ru-ru/pycharm/download/#section=windows) 
- [Как установить и настроить](https://pythonchik.ru/osnovy/faq-po-rabote-s-pycharm)
- Плагины:
    * [Нейронная сеть для автокомплита](https://plugins.jetbrains.com/plugin/12798-tabnine-ai-autocomplete-javascript-c-python-ruby-rust-go-php--)
    * [подсвечивание скобочек разными цветами](https://plugins.jetbrains.com/plugin/10080-rainbow-brackets)
    * [меняет стить написание переменных](https://plugins.jetbrains.com/plugin/7160-camelcase)

VSCode
- [Дистрибутив](https://code.visualstudio.com/)

 Git Bash 
- [Дистрибутив](https://gitforwindows.org/)

```bash 
which python #  проверим расположения разных исполняемых файлов python
pip -q install bcrypt # инсталяция пакета в глобальную директорию
$ python -c "import bcrypt; print(bcrypt.hashpw('password'.encode('utf-8'), bcrypt.gensalt()))" # выполнение кода из коммандной строки

```

 
## Установка пакетов

 - [Работа с менеджером пакетов PIP](https://pythonchik.ru/okruzhenie-i-pakety/pip--menedzher-python-paketov)
 - [Еще статья](https://python-scripts.com/upgrade-pip-windows)

 ```bash
 pip --version # Проверка установки pip
 pip install package-name # Установка пакета (но лучше как ниже)
 pip install Django==2.2  # Установка пакета определенной версии
 pip -q install package-name # инсталяция пакета в глобальную директорию
 # Зачем использовать python -m pip: https://habr.com/ru/company/otus/blog/475392/
 python3.8 -m pip package-name # Установка пакета для определенного интерпретатора
 python -m pip install --upgrade pip # Обновление pip
 pip show <имя_пакета> # Проверка куда ставятся пакеты

 pip help	# Справка по командам
 pip search package_name	#П оиск пакета
 pip show package_name	#И нформация об пакете
 pip install package_name	# Установка пакета(ов)
 pip uninstall package_name	# Удаление пакета(ов)
 pip list	# Список установленных пакетов
 pip install -U	# Обновление пакета(ов)
 --user # устанавливает пакет(ы) локально только для текущего пользователя.
 ```

Пример requirements.txt :
```text
flake8==3.8.4
flake8-broken-line==0.3.0
flake8-isort==4.0.0
flake8-plugin-utils==1.3.1
flake8-polyfill==1.0.2
flake8-return==1.1.2
pytest==5.3.2
Django==2.2
```

```bash
pip install -r requirements.txt # Установка пакетов из файла со списком
pip freeze > requirements.txt # Сохранение установленных пакетов в список
```
 


## Виртуальное окружение 

 - [Виртуальное окружение](https://python-scripts.com/virtualenv)
 - [Описание стандартного модуля VENV](https://docs.python.org/3/library/venv.html#module-venv)
 - [Описание модуля virtualenvwrapper](https://virtualenvwrapper.readthedocs.io/en/latest/install.html) 
 - https://habr.com/ru/post/157287/  

```bash
# Перейти в папку проекта
python -m venv myvenv
# Python, запусти модуль (-m) venv, он установит виртуальное окружение.
# Назови это виртуальное окружение "myvenv", чтобы его можно было вызвать по имени.
# Имя можно задать любое, мы в примерах будем использовать "venv". 
source venv/Scripts/activate # активировать окружение
deactivate  # отключить окружение


### 
pip install virtualenvwrapper-win # пакет управления виртуальными средами
mkvirtualenv <name_venv>  # Создание новой среды
workon # вывести список всех окружений 
workon <name_venv> # Активируем окружение 
lsvirtualenv # List all of the enviornments stored in WORKON_HOME
rmvirtualenv <name_venv> # Удалить окружение
add2virtualenv <full or relative path> # If a virtualenv environment is active, appends <path> to virtualenv_path_extensions.pth inside the environment’s site-packages, which effectively adds <path> to the environment’s PYTHONPATH. If a virtualenv environment is not active, appends <path> to virtualenv_path_extensions.pth inside the default Python’s site-packages. If <path> doesn’t exist, it will be created. 
deactivate # Выходим из окружения

### Находясь в одном из окружений, можно ставить пакеты через Pip, как обычно и нет необходимости добавлять ключ --user:
pip3 install markdown
```

> Для Windows можно указать в переменных среды WORKON_HOME для переопределения пути, где хранятся виртуальные окружения.
> По умолчанию, используется путь %USERPROFILE%\Envs.

> От нас не требуется определять переменные виртуальной среды WORKON_HOME и PROJECT_HOME. В virtualenvwrapper имеются 
> установленные по умолчанию переменные для них, но вы можете перезаписать их, указав значения.

## Линтеры

**Flake8**:
[Статья про линтер flake8 и его установку в IDE](https://habr.com/ru/company/dataart/blog/318776/)

```bash
# Проверка проекта в консоли 
pip install flake8 # Устаовка flake8 
flake8 my_project # Запустить для проверки ошибок в папке проекта

# Дополнения для линтера Flake8 
pep8-naming # проверяет имена классов, функций и переменных на соответствие PEP8;  
flake8-broken-line # отслеживает применение устаревших переносов (через обратный слеш \);
flake8-return # проверяет значения, возвращаемые функциями;
flake8-isort # проверяет правильность порядка импортов.

# Контроль линтером в момент коммита 
flake8 --install-hook git # Установить хук для Git
git config --bool flake8.strict true И настроить сам гит, чтобы учитывать правила Flake8
```

# Шпаргалка Python

## Простые объекты

### Числа

```py
None # не определена, не имеет никакого значения

### элементарные операции + - * / идентичны
x = a//b # целое от деления
x = a%b  # остаток от деления
x = a**b # а в степени b 
1e+16 # 1*10 в 16 степени
100 ** 0.5 # заменяет возведение в степень
round(23.456, 2) # 23.46 Округление 

### булевые операции. порядок выполнения: 
not # смена значения
and # булево умножение
or  # булево сложение
== <= >= != # равно, меньше+равно, больше+равно, не равно
a > b > c # Тройное сравнение  b=5; 3 < b < 7 == True

### системы счисления
x = 0b11101010      # в десятичной
y = 0o0732          # в восьмиричной
z = 0xFA0B          # в шестнадцатиричной
a = int('Z56RS', base=36)   # Создание числа в 36-ричной системе
print(x,y,z,a)              # print выведет все числа в десятичной системе
bin(x), oct(x), hex(x)      # Выведет строку-представление числа x в 2/8/16-ричной системе соответственно

### алгоритм перевода в любую систему счисления (число получается перевернутое)
base = 7            # база системыв счисления
x = int(input())    # вводим число
while x > 0:
    digit = x % base        # получаем последнюю цифру
    print(digit, end = '')  # выводим цифру, без перевода каретки
    x //= base              # отрезаем последнюю цифру
```

### Строки 

```python

### Методы строк 
'sdf  sdf'.split() # разбить строку по пробелам 
'sdf.  sdf'.split('. ') # разделить строку по разделителю. получить список
'.sdf  sdf.'.strip('.') # Убирает лишние символы в начале и в конце  
', '.join(iterator) # Сборка строки из значений любой коллекции через запятую 
'sdfdf "sd" sad' # если нужно вывести кавычки в тексте они должны отличатся от обрамляющих
'er '*3 = 'er er er' # Умножение строки
'АБВ' < 'АБЯ' == False # Сравнение строк происходит посимвольно по коду символа Unicode
'привет'.encode() # decode(<кодировка>) Строку из UTF8 в Unicode 
b'\xd0\xdf\xd1\x80' # строка байт.  b'\xd0\xdf\xd1\x80'.decode('utf8') можно преобразовывать 
len("sdg dgf") # длина строки 
'Тойота RAV4'.find('а') # ==5 # Поиск подстроки в строке
'Тойота RAV4'.rfind('а') # ==5 # С конца строки Поиск подстроки в строке 
'Тойота RAV4'.replace('а', 'б') # замена всех значений в строке
'Тойота RAV4'.upper() # 'ТОЙОТА RAV4' # к верхнему регистру
'Тойота RAV4'.lower() # 'тойота rav4' # к нижнему регистру
'Тойота RAV'.isalpha() # Все ли символы буквы? 
'12345'.isdigit() # Все ли символы цифры?
'Тойота RAV4'.isalnum() # В строке только цифры и буквы? 

### Срезы 
'Привет'[1] # 'p' - второй символа  
'Привет'[-2] # 'е' - Второй с конца
'Привет'[2:4] # 'ив' - С третьего по пятый
'Привет'[2:-1] # 'иве' - с третьего по предпоследний
'Привет'[-3:-1] # 'ве' - с предпоследнего по третий с конца
'Привет'[:4] # 'Прив' - первые четыре  
'Привет'[4:] # 'ет' - С пятого 
'Привет'[::2] # 'Пие' - Брать каждый втоой символ
'Привет'[::-1] # 'тевирП' - Развернуть строку. Брать по одному с конца  

### f-строки
print(f'На улице сейчас {weather}.') 


```

### Переменные

```py
x = y = z = 100 # Множественная инициализация. Все значения равны 100 
x, y, z = 100, 150, 102 # Присвоение сразу трем значениям
type(<переменная>) # определить тип переменной
isinstance(x, int) # Проверка на тип значения int (str, float)
id(x) # идентификатор места хранения переменных. если одинаково значит переменные одни и те же
```

### Преобразования

 - Между системами счисления - схема Горнера
```py
str() # к строке
int() # к целому
float() # к дробному числу
x, y = map(int, input.split()) # map - применяет функцию {1} к каждому значению {2} 

```

### Списки list
```py
list = [2, 4, 6, 8, 10, 12, 14, 16, 18]
len(list) == 9 # длина списка
list[<c>:<по>:<чередуя>] # срез списка. начало с 0. с конца с -1
list.append('sdf') # добавить значение в конец списка
# индексы словаря:
  0         1          2        3
['Ночь', 'Улица', 'Фонарь', 'Аптека']
  -4       -3         -2       -1
list[-1] # получить последний элемент  
list = [x for x in list if x.strip()!=''] # Фильтр пустых строк в списке строк.

### Методы списков
L = [1,2,3,4,5,6]
Срезы аналогичны строкам. (см. Строки)
Сравнение списков аналогично строкам (см. Строки)
[1, 2] * 3 == [1, 2, 1, 2, 1, 2] # Поверхностная копия, ссылаются на первые два элемнта 
5 in [1, 77, 5] == True # Проверка на вхождение элемента
L[0] = "ty" # Заменить первый элемент на "ty"

L.append('123')  # Добавить элемент в список
L.extend([234, 'ewe']) # Расширить список на два указанных элемента, добавить в конец
L + [5, 5, 7] # Расширить список на три указанных элемента
L.insert(2, 'WWW') # Вставка значения на третье место
del L[3] # Удаляет значение из списка по 
L.remove('WWW') # L.remove(4) Удаляет значение из списка по значению или по 
индексу  
reversed(list) # развернуть список с конца 
[5, 5, 7].count(5) == 2 # подсчет количества конкретных значений в списке
min(L) max(L) # получить минимальные и максимальное значения из списка list
L.sort() # сортировка массива 



```

### Словари dict
```py
dict = { 'key': 'value'} 
dict['key'] = 'dict' 
# не может быть двух одинаковых ключей
dict.keys()  # список ключей
dict.value() # список значений
", ".join(dict.values()) # Все значения через запятую
### Расширение словоря
dict['голова'] = 'head' # Добавили новую пару ключ : значение
for track, music_band in favorite_songs.items(): # Обход всех ключей и значений словаря

```

### Кортежи tuple 

```py
Не изменяемые объекты
Нельзя добавлять напрямую
Нельзя удалять 
Можно складывать (3, 4) + ("rf", "go") = (3, 4, "rf", "go")
```

### Множества (сеты) set

```py
# не упорядочен
# удобно объединять 
bands = ['Пикник', 'Ария', 'Блестящие', 'Блестящие']
unique_band_names = set(bands) # содержит уникальные группы
s = set('сервер')
# {'в', 'е', 'с', 'р'} выведет только уникальные буквы
s.add('н') # добавить элемент
set1.union(set2) # сложение множеств. объединить два множества без повторений
set1.difference(set2) # вычитание множеств. возвращает новое множество, которое содержит только те элементы, которые присутствуют в set1, но отcутствуют в set2
set1.intersection(set2) # пересечение двух множеств, то есть элементы, которые есть в обоих 

```

### Условия 

```py
if beaufort == 0: 
elif:
else:
```

### Циклы

```py
### for
for iterator in list: # перебор значений коллекций: списков, словарей, сетов
for key, value in dict.items(): # перебор ключей и значений словаря
for key in dict.keys(): # for key in dict   # перебор ключей словаря
for val in dict.values(): # перебор значений словаря
      
range(a, b) # генератор чисел для итерации с a до b-1. Запомнить принцип легко: если на месте a стоит ноль, range(0, N) вернёт ровно N значений
reversed(range(1, 13)) # Обратный отсчет с 12 до 1 
reversed(list) # развернуть список с конца
for i in range(-1, 10): # Перебрать все числа в диапазоне от -1 до 9
    continue # break 
else:
   d=1  # Выполняется один раз после выполнения всего цикла
### while
while a==b: 
else: 
```

Enumerate Она позволяет нам автоматически считать итерации цикла.

```python
my_list = ['яблоко', 'банан', 'вишня', 'персик']

for c, value in enumerate(my_list, 1):
    print(c, value)

# Результат:
# 1 яблоко
# 2 банан
# 3 вишня
# 4 персик

```

### Функции

```py
def hello(name: int = 5 ) -> str: # объявление функции
    """Print a Fibonacci series up to n.""" # описание функции  
    return 'boo' # возврт значений из функции  
    pass # заглушка   
hello.__annotations__ # Печать данные о принимаемых и возвращаемых параметрах
# Annotations: {'name': <class 'int'>, 'return': <class 'str'>}
hello.__doc__ # Печать документации 
# """Print a Fibonacci series up to n."""

```

### Как работает yield 

https://habr.com/ru/post/132554/

### Файлы

```py
# Чтения файла по строкам
with open("/path/to/file") as f:
    for line in f:
        print(line)
        
# Запись в файл строкой за строкой 
f = open("/path/tofile", 'w')
for e in aList:
    f.write(e + "\n") 
f.close()
```



### Обработка исключений

```py
Traceback (most recent call last):
  File "main.py", line 27, in <module>
    print(1 / a)
ZeroDivisionError: division by zero 

try:
except ZeroDivisionError:
except ValueError: 

try: # Пример. Обработка ошибок сетевого соединения
    response = requests.get(url)
except requests.ConnectionError:
return '<сетевая ошибка>'
```

## Замыкания

### Глобальная и локальная область видимости
```python
global_variable = 'Глобальная'


def some_func(passed_variable):
    local_variable = 'Локальная'
    return(f'{global_variable} '
           f'{local_variable} '
           f'{passed_variable}')

print(some_func('Параметр'))
# Будет напечатано: Глобальная Локальная Параметр
```

### Функция возвращает функцию

Вложенную функцию inside_func() можно не только вызывать внутри some_func() 
(как это было в примере выше), но и вернуть её, как результат выполнения объемлющей 
функции. Возвращаемое значение можно присвоить переменной:

```python
global_variable = 'Глобальная'


def some_func(passed_variable):
    local_variable = 'Локальная'

    def inside_func():
        inside_local_variable = 'Внутренняя'
        return (f'{global_variable} '
                f'{local_variable} '
                f'{passed_variable} '
                f'{inside_local_variable}')
    return inside_func

# Здесь вызывается функция some_func() 
# и результат её работы присваивается переменной kind_of_magic 
kind_of_magic = some_func('Параметр')

# Здесь рождается магия: some_func() вернула функцию, 
# значит, kind_of_magic — это функция
# и её можно вызвать:
print(kind_of_magic())
# Будет напечатано: Глобальная Локальная Параметр Внутренняя

# Можно создать ещё одну функцию
another_magic = some_func('Другой параметр')
print(another_magic())
# Будет напечатано: Глобальная Локальная Другой параметр Внутренняя
```

kind_of_magic() и another_magic() — это функции в глобальной области видимости, 
которым доступны переменные из enclosing scope функции inside_func(). Каждая из 
этих функций — вполне самостоятельна и будет работать, даже если после создания 
этих функций уничтожить «родительскую» функцию some_func():

```python
global_variable = 'Глобальная'


def some_func(passed_variable):
    local_variable = 'Локальная'

    def inside_func():
        inside_local_variable = 'Внутренняя'
        return(f'{global_variable} '
               f'{local_variable} '
               f'{passed_variable} '
               f'{inside_local_variable}')
    return inside_func

# Создали две функции
kind_of_magic = some_func('Параметр')
another_magic = some_func('Другой параметр')

del some_func  # Уничтожили функцию some_func()

# Всё равно сработает
print(kind_of_magic())
# Будет напечатано: Глобальная Локальная Параметр Внутренняя

print(another_magic())
# Будет напечатано: Глобальная Локальная Другой параметр Внутренняя

# А это уже не сработает: 
# some_func() удалена, создать новую функцию не получится.
misery_of_magic = some_func('Пробуем последний раз')
# NameError: name 'some_func' is not defined
```
Функция some_func() — это, по факту, своеобразная фабрика для создания и настройки 
копий функции inside_func(). После удаления some_func() вся её контекстная область 
видимости будет сохранена, потому что на эту область видимости существуют ссылки в 
объектах kind_of_magic и another_magic

### Вложенная функция принимает аргументы
Вложенная функция может принимать и обрабатывать аргументы.
```python
def some_func(passed_variable):
    def inside_func(passed_inside_variable):
        return f'{passed_variable}, {passed_inside_variable}'
    return inside_func

# Создали функцию hello()
hello = some_func('Привет')
# В контексте функции hello() значением passed_variable будет строка 'Привет'

# Вызваем hello() с параметром для inside_func()
print(hello('Стёпа'))
# Будет напечатано: Привет, Стёпа

byebye = some_func('До свидания')
# В контексте функции byebye() 
# значением passed_variable будет строка 'До свидания'

print(byebye('Марк Лутц'))
# Будет напечатано: До свидания, Марк Лутц

# Но значение переменной passed_variable в контексте hello() cохранилось:
# оно по-прежнему 'Привет'
print(hello('Лера'))
# Будет напечатано: Привет, Лера
```

> Замыкание (closure) — это способность вложенной функции запоминать локальное 
> состояние контекстной области объемлющей функции.

С помощью замыкания на основе some_func() были созданы функции hello() и byebye(), 
каждая со своей уникальной контекстной областью для inside_func().

У замыканий может быть и более сложное поведение:

```python
# В зависимости от уровня сложности (volume)
# функция возвращает различное написание фразы.
def speech(text, volume):
    def whisper():
        return f'{text.lower()}...'

    def scream():
        return f'{text.upper()}!!!11'

    if volume < 50:
        return whisper
    return scream

easy_closure = speech('Замыкание - это просто', 99)
print(easy_closure())
# Будет напечатано: ЗАМЫКАНИЕ - ЭТО ПРОСТО...!!!11
```

## Декораторы

Функции можно определять внутри других функций, а можно передать функцию как аргумент 
в другую функцию — и вызвать её там.

Чтобы измерить время выполнения функций sleep_one_sec() и sleep_two_sec(), нужно 
написать функцию, которая будет вычислять и печатать время выполнения этих функций.

```python
import time


def sleep_one_sec():
    time.sleep(1)
    print('Перерыв 1 секунда')
    return 'Возвращаемое значение'
        

def sleep_two_sec():
    time.sleep(2)


# Функция для измерения времени
# принимает на вход тестируемую функцию
def time_of_function(func):
    def wrapper():
        # Засекаем время перед выполнением тестируемой функции
        start_time = time.time()
        # Вызываем тестируемую функцию и 
        # cохраняем результат выполнения в переменную
        result = func()
        # Вычисляем, округляем и печатаем разницу
        # между временем старта и актуальным временем
        execution_time = round(time.time() - start_time, 1)
        print(f'Время выполнения функции: {execution_time} с.')
        # Возвращаем результат выполнения тестируемой функции
        # Если этого не сделать, результат нельзя будет использовать
        # в дальнейшем коде 
        return result
    return wrapper


# Передаём функцию sleep_one_sec() в time_of_function()
measured_sleep_one_sec = time_of_function(sleep_one_sec)
print(measured_sleep_one_sec())
# Будет напечатано:
# Перерыв 1 секунда
# Время выполнения функции: 1.0 с.
# 1


# Передаем функцию sleep_two_sec() в time_of_function()
measured_sleep_two_sec = time_of_function(sleep_two_sec)
measured_sleep_two_sec()
# Будет напечатано: Время выполнения функции: 2.0
```

Для работы с декораторами в Python добавлен синтаксический сахар (англ. syntactic sugar), 
упрощённый синтаксис.

```python
import time

# Функция для измерения времени 
def time_of_function(func):
    def wrapper():
        start_time = time.time()
        result = func()
        execution_time = round(time.time() - start_time, 1)
        print(f'Время выполнения функции: {execution_time} с.')
        return result       
    return wrapper

def sleep_one_sec():
    time.sleep(1)

# Декорироваие без синтаксического сахара:
sleep_one_sec = time_of_function(sleep_one_sec)

# То же самое декорирование с применением синтаксического сахара:
# имя функции-декоратора (с символом @) 
# ставится перед объявлением декорируемой функции
@time_of_function
def sleep_one_sec():
    time.sleep(1)

# После декорирования любой вызов функции sleep_one_sec() 
# будет автоматически сопровождаться измерением времени её выполнения
sleep_one_sec()
# Будет напечатано: Время выполнения функции: 1.0

# Когда необходимость в замерах отпадёт — декоратор можно убрать
```

Декораторы могут менять не только поведение декорируемой функции, но и значение, 
возвращаемое этой функцией:

```python
def uppercase(func):
    def wrapper():
        original_result = func()
        return f'Большие {original_result.upper()}'
    return wrapper


@uppercase
def greet():
    return 'маленькие буквы'


print(greet())
# Будет напечатано: Большие МАЛЕНЬКИЕ БУКВЫ
```

Исключение неправильного двойного декорирования:
Для решения этой проблемы авторы стандартной библиотеки functools написали декоратор @wraps
[Как работает этот декоратор](https://docs.python.org/3/library/functools.html#functools.update_wrapper). 
В коде ниже он использован правильно:

```python
from functools import wraps


def first_decorator(func):
    @wraps(func)  # Задекорировали обёртку
    def wrapper1():
        """Это декоратор first_decorator."""        
        print(f'Докстринг декорируемой функции: {func.__doc__}')
        print(f'Декорируется функция {func.__name__}')
        return func()        
    return wrapper1

def second_decorator(func):
    @wraps(func)  # И здесь задекорировали обёртку
    def wrapper2():
        """Это декоратор second_decorator."""        
        print(f'Докстринг декорируемой функции: {func.__doc__}')
        print(f'Декорируется функция {func.__name__}')
        return func()        
    return wrapper2

@first_decorator
@second_decorator
def do_nothing():
    """Я ничего не знаю. Я никуда не летаю."""
    ...

do_nothing()

```

### Работа с аргументами *args и **kwargs

Чтобы декоратор был универсальным — он должен принимать на вход функции с любым количеством и типом параметров.
Для этого в Python есть конструкции ```*args``` и ```**kwargs```.

```python
def any_func(*args, **kwargs):
    pass
```
Этот синтаксис означает, что функция готова принять любое количество позиционных ```(`args* от *arguments)*``` и именованных ```(**kwargs` от keyword arguments)``` аргументов.
> С переменной *args можно работать как с кортежем, а с переменной **kwargs — как со словарём.
Такой синтаксис может применяться в любых функциях (не только в декораторах). Имена args и kwargs не предустановлены, но общеприняты.

Самое время решить задачу по ограничению прав доступа к определённым страницам сайта: изменить несколько view-функций так, чтобы они выполнялись, только если пользователь авторизован.
Решение понятно: написать декоратор, проверяющий авторизацию, и обернуть им нужные view-функции.

```python
from django.shortcuts import redirect
...

def authorized_only(func):
    # Функция-обёртка в декораторе может быть названа как угодно
    def check_user(request, *args, **kwargs):
        # В любую view-функции первым аргументом передаётся объект request,
        # в котором есть булева переменная is_authenticated,
        # определяющая, авторизован ли пользователь.
        if request.user.is_authenticated:
            # Возвращает view-функцию, если пользователь авторизован.
            return func(request, *args, **kwargs)
        # Если пользователь не авторизован — отправим его на страницу логина.
        return redirect('/auth/login/')        
    return check_user

# Декорируем view-функцию
@authorized_only
def some_view(request):
    # Доступно только авторизованным!
    ...
```





## ООП

Дополнительные материалы: 
 - ООП в Pyton https://learn-free.site/python-oop-2020/ 

> **Интерфейс класса** — это функциональная часть класса, через которую происходит взаимодействие 
> с самим классом или с экземпляром этого класса.

> **Наследование** — способ описать новый класс на базе существующего. 
> При этом в дочернем классе можно сохранить или переопределить свойства и методы родительского класса.

> **Инкапсуляция** — объединение и скрытие методов и свойств, и предоставление доступа к ним через простой внешний интерфейс.

> **Полиморфизм** — возможность взаимодействовать с объектами разных типов через одинаковые интерфейсы, 
<обращаться к свойствам и методам, общим для всех объектов.


```py
class Contact:
    def __init__(self, name, phone, birthday):
        self.name = name
        self.phone = phone
        self.birthday = birthday
        print(f'Создан новый контакт: "{name}"')

    def show(self):
        print(f'Имя: {self.name}, '
              f'телефон: {self.phone}, '
              f'день рождения: {self.birthday}')

    def __str__(self):
        # Можно задать любую строку, например Не печатай меня, ведь я — объект!,
        # но лучше пусть при печати выводится что-то осмысленное:
        # название объекта и имя
        return f'Контакт: {self.name}'

# создаём объект:
ivan = Contact(name='Иван', phone='+155512345', birthday='2.12.1985')
# При создании объект будет напечатно: Создан новый контакт: "Иван"

# печатаем объект:
print(ivan)
# Будет напечатано: "Контакт: Иван" 

---

class User:
    def __init__(self, name, phone):
        self.name = name
        self.phone = phone

    def show(self):
        print(f'{self.name} ({self.phone})')


# наследуем класс Friend от User
class Friend(User):
    # Пишем конструктор класса-наследника,
    # чтобы он принимал все нужные параметры
    def __init__(self, name, phone, address):
        # наследуем функциональность конструктора из класса-родителя
        super().__init__(name, phone)
        # добавляем новую функциональность: свойство address
        self.address = address

    # полностью переопределяем родительский метод show()
    def show(self):
        print(f'Имя: {self.name} || '
              f'Телефон: {self.phone} || '
              f'Адрес: {self.address}') 
```

## Библиотеки. Полезные  модули

### Специальные атрибуты Python

Функции в Python обладают набором специальных атрибутов, через которые доступна
«служебная информация». Описание атрибутов [есть в документации](https://docs.python.org/3/reference/datamodel.html#index-34).

С их помощью можно, например, получить имя функции (__name__) или содержимое 
docstring — строковой переменной, в которой кратко описан объект (__doc__):

```python
def what_my_name():
    """Это docstring функции what_my_name()."""
    ...

print(f'Имя функции: {what_my_name.__name__}')
# Будет напечатано: Имя функции: what_my_name

print(f'Докстринг функции: {what_my_name.__doc__}')
# Будет напечатано: Докстринг функции: Это docstring функции what_my_name().
```
Вывести список доступных свойств и методов любого объекта в Python можно так:
```python
def what_my_name():
    """Это docstring функции what_my_name()."""
    ...

print(dir(what_my_name))
```

### Подключение модулей

```py
### 
import random # Подключение всего модуля. 
random.random()
import random as r # Подключение модуля под определенным именем
r.random() 
from random import choice, randint # Подключение отдельных функций
randint(0, 23) # Можно вызывать не указывая модуль
from random import * # Подлключение всех функций
random() # Можно вызывать любую функцию не указывая модул
```

### random

```py
import random 
random.randint(0, 23) # функция randint() генерирует случайное целое число  
random.random() # случайное дробное число
random.choice(list) # случайный элмент списка
```

### math

```py
import math 
math.sqrt(16) # квадратный корень
```
### decimal

```py
import decimal # Работа с числами с фиксированной точностью
```

### datetime


```py

import datetime as dt
dt.datetime(1961, 4, 12, 9, 7, 0) # 1961-04-12 09:07:00 
landing_time - start_time # Можно вычитать даты. Результат: 1:48:00 -> тип timedelta
dt.utcnow() #  текущий момент времени
dt.datetime.utcnow() # прямой вызов текущего времени
timedelta(days, hours, minutes, seconds, microseconds) # тип. хранение промежутков времени
period = dt.timedelta(hours=3) # промежуток времени в три часа. 3:00:00 
moscow_moment = dt.datetime.utcnow() + dt.timedelta(hours=3) # московское время
dt.strftime('%H:%M') # форматированный вывод времени. 10:31 Параметры: %B — месяц, %Y — год и %S — секунды, %A — название дня недели по-английски, %U — номер недели в году
```

### requests и urllib

https://pythonru.com/biblioteki/kratkoe-rukovodstvo-po-biblioteke-python-requests


```py
import urllib.parse # Кириллица в адресной строке
urllib.parse.quote(s) # зашифрованная строка  0%B0%D0%BA%D0%BE%D0%B5%20backend
urllib.parse.unquote(encoded)  # расшифрованная обратно строка

import requests
response = requests.get('https://ya.ru/white') # запрос текста страницы
response.text # текст страницы
response.status_code # 200. код ответа
response.headers # заголовки
request_headers = {'Accept-Language': 'ru'}
request_params = {'u': '', 'T': ''};    url = 'http://wttr.in'
response = requests.get(url, params=request_params, headers=request_headers) # запрос с параметрами
```

### PIL Работа с картинками

```py
# Работа с картинками https://pypi.org/project/Pillow/
from PIL import Image
```

### Отслеживаем прогресс выполнения

https://habr.com/ru/post/483400/

 - [Progress](https://github.com/verigak/progress/) 
 - [tqdm](https://github.com/tqdm/tqdm)
 - [alive-progress](https://github.com/rsalmei/alive-progress


# Алгоритмы



## Однопроходные алгоритмы

```py
flag = flag or (x==find) # Проверка наличия значения find 
### 
 
```

## Алгоритмы с массивами

> Присваивание переменной другой переменной с **неизменяемым** значением 
> осуществляется **по значению**. В первой переменной окажется дубликат 
> значения второй переменной

> Присваивание переменной другой переменной с **изменяемым** значением 
> осуществляется **по ссылке**. В первой переменной окажется тот же объект, 
> что и во второй. При изменении значения в любой из переменных изменятся 
> данные в объекте и соответственно в обоих переменных

```bash
### Работа со стеком

# Заполнение стека
A=[0]*1000 #Пустой стек
top=0 # Уровень стека (граница)
x=int(input(x)) # вводим первое значение
while x!=0: # запускаем цикл заполнения стека. допустим при введенном нуле 
            # нужно остановиться
  A[top]=x 
  top += 1
  x=int(input(x))
  
# перебор стека с конца
for k in range(top, -1, -1) 
  print(A[k]) # или А[k]=0
```

## Нарезка итерируемых объектов

https://dev-gang.ru/article/python-narezka-iteriruemyh-obektov-90rl7lex2e/

# Документирование

 - [Статья по базовым аспектам документирования](https://pythonchik.ru/osnovy/dokumentirovanie-koda-v-python)

Пример документирования класса: 

```py

class TextSplitter:
    """
    Класс TextSplitter используется для разбивки текста на слова
    Основное применение - парсинг логов на отдельные элементы
    по указанному разделителю.
    Note:
        Возможны проблемы с кодировкой в Windows
    
    Attributes
    ----------
    file_path : str
        полный путь до текстового файла
    lines : list
        список строк исходного файла

    Methods
    -------
    load()
        Читает файл и сохраняет его в виде списка строк в lines
    get_splitted(split_symbol=" ")
        Разделяет строки списка по указанному разделителю
        и возвращает результат в виде списка
    """

    def __init__(self, file_path: str):
        self.file_path = file_path.strip()
        self.lines = []

    def load(self) -> None:
        """Метод для загрузки файла в список строк lines

        Raises
        ------
        Exception
            Если файл пустой вызовется исключение
        """

        with open(self.file_path, encoding="utf-8") as f:
            for line in f:
                self.lines.append(line.rstrip('\n'))
            if len(self.lines) == 0:
                raise Exception(f"file {self.file_path} is empty")

    def get_splitted(self, split_symbol: str = " ") -> list:
        """Разбивает текстовые строки lines, преобразуя строку в 
        список слов по разделителю

        Если аргумент split_symbol не задан, в качестве разделителя
        используется пробел

        Parameters
        ----------
        split_symbol : str, optional
            разделитель
        """

        split_list = []
        for str_line in self.lines:
            split_list.append(str_line.split(split_symbol))
        return split_list

```

## 

# Тестирование 

## Docstring и Doctest Документируй это 

[Doctest документация](https://docs.python.org/3/library/doctest.html)

Docstring — это строковая переменная, которую размещают сразу за объявлением модуля, 
функции, класса или метода. Docstring принято обрамлять тройными двойными кавычками (РЕР257).
Доступ до этой переменной можно получить так: ```имя_функции.__doc__```.

В docstring вносят краткое смысловое описание класса или функции, к которой она 
относится. В ней же, при необходимости, сохраняют результаты проведённых тестов.

```python
def movie_quotes(name):
    """Возвращает цитаты известных персонажей из фильмов

    >>> movie_quotes('Элли')
    'Тото, у меня такое ощущение, что мы не в Канзасе!'

    >>> movie_quotes('Шерлок')
    'Элементарно, Ватсон!'

    >>> movie_quotes('Дарт Вейдер')
    'Я — твой отец.'

    >>> movie_quotes('Леонид Тощев')
    'Персонаж пока не известен миллионам.'
    """
    quotes = {
        'Элли': 'Тото, у меня такое ощущение, что мы не в Канзасе!',
        'Шерлок': 'Элементарно, Ватсон!',
        'Дарт Вейдер': 'Я — твой отец.',
        'Thomas A. Anderson': 'Меня. Зовут. Нео!',
    }
    return quotes.get(name, 'Персонаж пока не известен миллионам.')
```

В Python есть стандартная библиотека doctest; при запуске она ищет в Docstrings 
эти ёлочки и исполняет инструкции, следующие за ними; затем doctest сравнивает 
полученный результат с ожидаемым, указанным на следующей за инструкцией строке в 
docstring.

Запустите doctest для файла с функцией ```movie_quotes()```: выполните из директории 
с файлом команду ```python3 -m doctest <название файла.py>```

В файле можно настроить и автоматический запуск тестирования: нужно импортировать 
doctest в код и добавить вызов теста.

```python
# Код с докстрингами

if __name__ == "__main__": 
    import doctest
    doctest.testmod()
```

Теперь doctest будет запускаться автоматически при выполнении файла.
```bash
python3 <название файла.py>
# Вначале будет выполнен doctest, а затем - код файла
```

## Assert. Вкалывают роботы.

Assert работает по такой логике: разработчик передаёт в него какое-то утверждение, 
и если оно истинно — assert не возвращает ничего, тест пройден. Если утверждение 
оказалось ложным — выбрасывается исключение с сообщением об ошибке, а исполнение 
кода прерывается.
```python
# Синтаксис:
assert <проверяемое утверждение>, <'Сообщение об ошибке'>

# В этом примере утверждение (первый аргумент) - True. 
# Код продолжит выполняться, сообщение не будет выведено
assert 1 == 1, 'Хьюстон, у нас проблемы'

# В этом примере утверждение (первый аргумент) - False
assert 2 + 2 == 5, 'Хьюстон, у нас проблемы'

# в результате будет вызвано исключение с текстом из второго аргумента,
# а выполнение кода будет остановлено
>Traceback (most recent call last):
>  File "1.py", line 25, in <module>
>    assert False, 'Хьюстон, у нас проблемы'
>AssertionError: Хьюстон, у нас проблемы
```

При переносе длинных строк в assert замыкайте в скобки только переносимую строку, 
и фрагмент на каждой строке обрамляйте в кавычки:
```python
x = 3
assert 2 + x == 4, ('Очень длинная строка, в которой многословно, '
                    'с лирическими отступлениями, описывается, '
                    'какой именно тест провален.')
```

Протестировать функцию с помощью assert достаточно просто: в первом аргументе 
нужно сравнить результат реального вызова функции и ожидаемый результат.
```python
def movie_quotes(name):
    """Возвращает цитаты известных персонажей из фильмов."""
    quotes = {
        'Элли': 'Тото , у меня такое ощущение, что мы не в Канзасе!',
        'Шерлок': 'Элементарно, Ватсон!',
        'Дарт Вейдер': 'Я — твой отец.',
        'Thomas A. Anderson': 'Меня зовут Ханс. Ханс Кристиан Андерсен.',
    }
    return quotes.get(name, 'Персонаж пока не известен миллионам.')

# Утверждаем, что если в movie_quotes() передать 'Шерлок' -
# функция вернёт 'Элементарно, Ватсон!'.
assert movie_quotes('Шерлок') == 'Элементарно, Ватсон!', (
   "movie_quotes('Шерлок') не вернул ожидаемый результат!")
```

При обработке инструкций assert Python преобразовывает каждую из них примерно в такую конструкцию:
```python
if __debug__:
    if not <утверждение>:
        raise AssertionError(<сообщение об ошибке>) 
```
Эта инструкция работает только в том случае, когда для встроенной константы 
Python ```__debug__``` установлено значение True. При оптимизации проекта это значение 
меняют на False, и в таком режиме ассерты игнорируются.

Пример тестовой функции: 
```python
def test_invert(invertaser):
    """Тест алгоритма инвертирования строки."""

    print(f'{test_invert.__doc__}')
    print(f'Тестирование алгоритма {invertaser.__name__}')

    source = 'Попугай'
    inversed = 'йагупоП'

    assert invertaser(source) == inversed, (
        f'Алгоритм в {invertaser.__name__} работает неправильно со строкой "{source}" ')
    
    source = ''
    inversed = ''

    assert invertaser(source) == inversed, (
        f'Алгоритм {invertaser.__name__} работает неправильно с пустой строкой')

    print(f'Тест для {invertaser.__name__} пройден успешно')


# Ниже - несколько функций, инвертирующих строку. 
# Их и будем тестировать.
def recursion_invertor(text):
    """Инвертирует строчку рекурсивно"""
    if len(text) == 0:
        return text
    else:
        return recursion_invertor(text[1:]) + text[0]


def slice_invertor(text):
    """Инвертирует строчку срезом"""
    return text[::-1]


def iterator_invertor(text):
    """Инвертирует строчку обратной итерацией"""
    return ''.join(reversed(text))


def reverselist_invertor(text):
    """Инвертирует строчку переворотом списка"""
    inversed_list = list(text)
    inversed_list.reverse()
    return ''.join(inversed_list)

# Вызов тестирующей функции для каждой функции-инвертора
test_invert(recursion_invertor)
test_invert(slice_invertor)
test_invert(iterator_invertor)
test_invert(reverselist_invertor)
```

## Test Driven Development (TDD)

Высший пилотаж в этой разработке — сначала придумать модуль и написать для него 
тесты, а потом написать код, соответствующий этим тестам.

Перед вами заготовка для класса Calculator. Класс пока не написан, но по docstring 
можно понять, что он будет делать:

```python
class Calculator:
    """Производит арифметические действия."""
    def summ(self, *args):
        """Возвращает сумму значений любого количества принятых аргументов."""
        pass

    def square(self, num):
        """Возвращает квадратный корень из аргумента."""
        pass
```
Этого достаточно, что бы написать тесты.

Можно сохранить тесты в том же файле, что и тестируемая программа, но лучше разместить 
их в отдельной директории в отдельном файле. Для этого есть несколько причин:
 - модуль с тестом может быть запущен автономно из командной строки;
 - код тестов легко отделить от программы;
 - тестируемый код может быть легче переработан.

```
├── code
│   ├── __init.py__         
│   └── calculator.py       # Тестируемые функции живут тут
└── test
    ├── __init__.py   
    └── test_calculator.py  # Тесты лежат здесь
```

Паттерн тестирования AAA (Arrange, Act, Assert): 

Большинство тестов можно разделить на три части:
 - Arrange (настройка) — в этом блоке кода мы подготавливаем данные для теста. Обычно это создание экземпляра класса тестируемого юнита.
 - Act — выполнение или вызов тестируемого сценария.
 - Assert — проверка того, что тестируемый вызов ведёт себя ожидаемо.

Такой подход называется «паттерн AAA». Считается, что он улучшает структуру теста и его читабельность.

Теперь можно посмотреть на тесты для класса Calculator:
```python
import sys
import os
import unittest
# Добавим возможность импорта из директории calculator в наш тест
sys.path.append(os.path.abspath('../calculator'))
from calculator import Calculator


class TestCalc(unittest.TestCase):
    """Тестируем Calculator."""
    def test_summ(self):
        # summ возвращает сумму принятых аргументов
        # Arrange - подготавливаем данные для теста.
        # Создаем экземпляр класса Calculator()
        calc = Calculator()

        # Act - выполнение тестируемого сценария.
        # Вызываем метод summ
        act = calc.summ(3, -3, 5)

        # Assert - проверяем, что метод работает
        self.assertEqual(act, 5, 'Метод summ работает неправильно')

    def test_square(self):
        # square() возвращает квадратный корень аргумента
        calc = Calculator()
        act = calc.square(4)
        self.assertEqual(act, 2, 'Метод square работает неправильно')

    # Корень из отрицательного числа не является действительным числом
    def test_square_negative_value(self):
        calc = Calculator()
        # Проверяем, что при вызове с отрицательным числом 
        # выбрасывается исключение ValueError
        # assertRaises обрабатывается с помощью менеджера контекста with
        with self.assertRaises(ValueError):
            act = calc.square(-1)
```

После запуска тестов командой ```python3 -m unittest -v test_calculator.py``` в консоль будет выведено несколько сообщений о проваленных тестах:

Этого и следовало ожидать: тесты ожидают, что методы summ() и square() работают, а на самом-то деле они ничего не возвращают и не выбрасывают исключений: эти методы ещё не написаны.
По методологии TDD так и должно быть. Теперь можно написать методы, соответствующие тестам и проверить работу методов тестами.


## Библиотека Unittest

 - [Документация Unittest 1](https://docs.python.org/3/library/unittest.html)
 - [Документация Unittest 2](https://pythonworld.ru/moduli/modul-unittest.html)

При работе с Unittest код должен быть устроен по определённым правилам:
 - Вместо инструкций ```assert``` в Unittest применяют методы встроенного класса ```unittest.TestCase```
 - Тесты помещаются в классы, наследующиеся от ```unittest.TestCase```.
 - Тесты — это методы класса.
 - Имена тестов должны начинаться с префикса ```test_```.
 - Для тестирования запускается специально обученный скрипт (такие скрипты называются 
   test runner), он подготавливает условия для проведения тестов и вызывает все 
   методы, начинающиеся с ```test_```.

### Пример тестов 
```python
# file.py

def series_sum(incoming):
    """Конкатенирует все элементы списка, приводя их к строкам."""
    return ''.join(str(i) for i in incoming) 
```
 - В начале кода в файл импортируется библиотека Unittest и тестируемая функция; 
 - затем создаётся класс ```TestSeriesSum``` — наследник встроенного класса ```TestCase```.
 - В классе создаются несколько методов, «тестов» (по-английски они называются 
   test case, но в русском языке прижился перевод «тест»).
 - В каждом test case проверяются разные варианты работы функции ```series_sum()```: 
   она вызывается с различными аргументами, и результат вызова сравнивается с 
   ожидаемым результатом. Для сравнения применяется встроенный метод ```assertEqual``` (аналог ```assert a == b```):
```python
# test_one.py

import unittest
from file import series_sum  # Импорт тестируемой функции


class TestSeriesSum(unittest.TestCase):
    """Тестируем series_sum."""
    def test_mixed_numbers(self):  # Это - test case
        # Вызов тестируемой функции
        call = series_sum([1, 2.5, 3, 4])
        # Ожидаемый результат
        result = '12.534'
        # Проверка: идентичен ли результат вызова ожидаемому результату
        self.assertEqual(call, result,
                         'Функция series_sum() не работает '
                         'со списком чисел')

    def test_mixed_numbers_strings(self):  # И это - test case
        call = series_sum([1, 'fff', 3, 4])
        result = '1fff34'
        self.assertEqual(call, result,
                         'Функция series_sum не работает со смешанным списком')

    def test_empty(self):  # И это - тоже test case
        call = series_sum([])
        result = ''
        self.assertEqual(call, result,
                         'Функция series_sum не работает с пустым списком')

if __name__ == '__main__':
    unittest.main()
```

Кроме метода assertEqual в Unittest есть множество других методов на все случаи жизни

```
assertEqual(a, b)       a == b
assertNotEqual(a, b)	a != b
assertTrue(x)	        bool(x) is True
assertFalse(x)	        bool(x) is False
assertIs(a, b)	        a is b
assertIsNot(a, b)	    a is not b
assertIsNone(x)	        x is None
assertIsNotNone(x)	    x is not None
assertIn(a, b)	        a in b
```

Другие методы (их список постоянно пополняется) можно найти в 
[официальной документации библиотеки Unittest](https://docs.python.org/3/library/unittest.html#unittest.TestCase.debug).


### Запуск тестов из консоли

```bash
python3 -m unittest test_one.py
python3 -m unittest -v test_one.py # Для получения подробного отчёта команда выполняется с флагом -v
```
Будет вызван test runner, который найдёт в файле все методы, начинающиеся с ```test_``` 
и выполнит инструкции в них.

### Управление тестами. Декораторы

Unittest позволяет пропускать (не выполнять) классы тестов и отдельные тесты. 
Для этого в библиотеке есть специальные декораторы:

 - **@unittest.skip(reason)** — пропустить тест. В параметре reason описывается причина пропуска.
 - **@unittest.skipIf(condition, reason)** — пропустить тест, если условие condition истинно.
 - **@unittest.skipUnless(condition, reason)** — пропустить тест, если условие condition ложно.

Можно отмаркировать тест меткой «тест не работает, но это так и задумано».
 - **@unittest.expectedFailure** — ставит на тесте отметку «ожидаемая ошибка».

Пример листинга с пропущенными тестами:
```python
import unittest
import sys


class TestExample(unittest.TestCase):
    """Демонстрирует возможности по пропуску тестов."""
    @unittest.skip('Этот тест мы просто пропускаем')
    def test_show_msg(self):
        self.assertTrue(False, 'Значение должно быть истинным')

    @unittest.skipIf(sys.version_info.major == 3 and sys.version_info.minor == 9,
                     'Пропускаем, если питон 3.9')
    def test_python3_9(self):
        # Тест будет запущен, только если версия питона отлична от 3.9.
        # В условиях можно проверять версии библиотек, доступность внешних сервисов,
        # время или дату - любые данные
        pass

    @unittest.skipUnless(sys.platform.startswith('linux'), 'Тест только для Linux')
    def test_linux_support(self):
        # Тест будет запущен только в Linux
        pass

    @unittest.expectedFailure
    def test_fail(self):
        self.assertTrue(False, 'Ожидаем истинное значение')


if __name__ == '__main__':
    unittest.main()
```

### Фикстуры

Чтобы упростить код и не повторяться — в Unittest есть встроенные методы фикстур.

test fixtures (на сленге — «фикстуры») — это фиксированные объекты и данные для выполнения тестов. Перед началом теста в коде создаются объекты и данные, на которых будет проведено тестирование.

**Встроенный метод setUp()**

Автоматически вызывается перед запуском каждого test case:

```python
...
class TestCalc(unittest.TestCase):
    """Тестируем Calculator."""
    def setUp(self):
        """Подготовка прогона теста. Вызывается перед каждым тестом."""
        # Arrange - подготавливаем данные для теста
        self.calc = Calculator()

    def test_summ(self):
        act = self.calc.summ(3, -3, 5)
        self.assertEqual(act, 5, 'Метод summ работает неправильно')
    
    # Другие test case
    ...
...
```

**Встроенный метод setUpClass()**

вызывается лишь один раз, перед запуском всех test case класса.

Обратите внимание: setUpClass — это «метод класса» (class method), его обязательно декорировать, а его первый аргумент должен называться cls. Для вызова метода класса не требуется создавать объект, такой метод можно вызвать напрямую из класса.

```python
...

class TestCalc(unittest.TestCase):
    """Тестируем Calculator."""
    @classmethod
    def setUpClass(cls):
        """Вызывается однажды перед запуском всех тестов класса."""
        # Arrange - подготавливаем данные для теста
        cls.calc = Calculator()

    def test_summ(self):
        act = TestCalc.calc.summ(3, -3, 5)
        self.assertEqual(act, 5, 'Метод summ работает неправильно')

    def test_square(self):
        act = TestCalc.calc.square(4)
        self.assertEqual(act, 2, 'Метод square работает неправильно')

    # Корень из отрицательного числа не является действительным числом
    def test_square_negative_value(self):
        with self.assertRaises(ValueError):
           TestCalc.calc.square(-1)
```
Очевидно, что в примере с тестированием класса Calculator будет правильнее и проще один раз задать условия для тестов, чем заново создавать экземпляр перед каждым тестом.

Еще методы для фикситур: 
```python
import unittest


def setUpModule():
    """Вызывается один раз перед всеми классами, которые есть в файле."""
    print('> setUpModule')


def tearDownModule():
    """Вызывается один раз после всех классов, которые есть в файле."""
    print('> tearDownModule')


class TestExample(unittest.TestCase):
    """Демонстрирует принцип работы тестов."""

    @classmethod
    def setUpClass(cls):
        """Вызывается один раз перед запуском всех тестов класса."""
        print('>> setUpClass')

    @classmethod
    def tearDownClass(cls):
        """Вызывается один раз после запуска всех тестов класса."""
        print('>> tearDownClass')

    def setUp(self):
        """Подготовка прогона теста. Вызывается перед каждым тестом."""
        print('>>> setUp')

    def tearDown(self):
        """Вызывается после каждого теста."""
        print('>>> tearDown')

    def test_one(self): # это -- test case 
        print('>>>> test_simple')

    def test_one_more(self): # это -- еще один test case
        print('>>>> test_simple')


if __name__ == '__main__':
    unittest.main()
```





## Модуль pytest

```bash
$ pip install pytest # установка pytest
$ pytest --version # проверка установки и версии
# Перейти в директорию с тестами 
# ~/Dev/homework$ ls
# homework.py pytest.ini tests
$ pytest # Запустить pytest
#Команда запустит все тесты из подпапки tests/
```

- Как используют в Яндексе https://habr.com/ru/company/yandex/blog/242795/
- PyTest на Хабре https://habr.com/ru/post/269759/ 



# Django

 - [Документация](https://developer.mozilla.org/ru/docs/Learn/Server-side/Django) на developer.mozilla.org
 - [Документация](https://django.fun/docs/) на django.fun

##  Установка  

```bash
# Установка 
pip install Django==2.2
# scaffolding. Предварительные настройки проекта
django-admin startproject yatube # Заполнить настройки проекта Yatube 

# Создаст следующую структуру проекта 
Yatube //папка проекта
├── yatube //основная рабочая папка с кодом проекта
|   ├── manage.py
|   └── yatube //папка с настройками проекта
|       ├── __init__.py
|       ├── settings.py
|       ├── urls.py
|       └── wsgi.py
├── venv //папка виртуального окружения
├── README.md
├── .gitignore

# полный список команд Django
python yatube/manage.py --help
python manage.py createsuperuser # добавить администратора
python manage.py runserver #запустить сервер

python manage.py startapp post # создать новое приложение post
# Структура файлов приложения
posts
├── __init__.py
├── admin.py
├── apps.py
├── migrations
│   └── __init__.py
├── models.py
├── tests.py
└── views.py

```


## Django ORM (Object-Relational Mapping)

[Документация](https://developer.mozilla.org/ru/docs/Learn/Server-side/Django/Models) 
по полям модели на developer.mozilla.org

[Документация Django ORM](https://docs.djangoproject.com/en/3.0/topics/db/queries/)

### Django Python shell

```bash
Запуск:
(venv) $ python manage.py shell 
```

Следующая команда импортирует библиотеку logging и включит вывод отладочной информации:
[Документация по logging](https://docs.python.org/3/library/logging.html)

```python
>>> import logging
>>> log = logging.getLogger('django.db.backends')
>>> log.setLevel(logging.DEBUG)
>>> log.addHandler(logging.StreamHandler()) 
```



### Создание модели

```python
"""
Класс: Post
Свойства:
- Текст публикации
- Дата публикации
- Автор 
"""

# так выглядит синтаксис модели - класса, с которым работает ORM
class Post(models.Model): # класс Post, наследник класса Model из библиотеки models
    # свойство text типа TextField
    text = models.TextField() 
    
    # свойство pub_date типа DateTimeField, текст "date published" это заголовок
    # поля в интерфейсе администратора. auto_now_add говорит, что при создании
    # новой записи автоматически будет подставлено текущее время и дата
    pub_date = models.DateTimeField("date published", auto_now_add=True)
    
    # свойство author типа ForeignKey, ссылка на модель User
    author = models.ForeignKey(User, on_delete=models.CASCADE, related_name="posts") 

""" 
Для всех моделей Django ORM создаст в БД таблицы. Описанные через синтаксис 
имя_свойства = models.тип_данных() свойства модели определят названия и типы 
данных в колонках таблицы БД

Для модели Post в базе данных будет создана таблица с колонками text, 
pub_date  и author, причём в колонке author должны быть указаны Primary Key 
записей  из таблицы User

Обратите внимание на поле author. Оно ссылается на автора поста, на модель 
User, и для этого поля указано свойство related_name="posts". Тут снова 
начинается магия: в каждом объекте модели User автоматически будет создано 
свойство с таким же названием (posts), и в нём будут храниться ссылки на все
объекты модели Post, которые ссылаются на объект User. На практике это 
означает, что в объекте записи есть поле author, в котором хранится ссылка 
на автора(например, admin), а в объекте пользователя admin появилось поле 
posts, в котором хранятся ссылки на все посты этого автора. И теперь можно 
получить список постов автора, обратившись к его свойству posts
"""

# ТИПЫ ПОЛЕЙ ORM
# Описание всех стандартных типов полей:
# https://docs.djangoproject.com/en/2.2/ref/models/fields/#field-types 
models.TextField() # для хранения произвольного текста
models.CharField(max_length=400) # символьное поле 

models.ForeignKey(User, on_delete=models.CASCADE, related_name="posts")     
# поле, в котором указывается ссылка на другую модель, 
# на её Primary Key (pk). Параметр on_delete=models.CASCADE обеспечивает 
# связность данных. если из таблицы User будет удалён пользователь, то будут  
# удалены все связанные с ним посты.

models.DateTimeField (auto_now_add=True) # для хранения даты и времени
models.DateField()      # для хранения даты
models.DurationField()  # промежутка времени
models.TimeField()      # просто времени 

models.BooleanField()   # для хранения данных типа bool
models.EmailField()     # для хранения строки, но с обязательной проверкой синтаксиса email
models.FileField()      # для хранения файлов
models.ImageField()     # для хранения файлов картинок


# Пример модели

from django.db import models
from django.contrib.auth import get_user_model

USER_MODEL = get_user_model()

class Group(models.Model):
    """
    Описание модели сообщества
    """
    title = models.CharField('Заголовок', max_length=200)
    slug = models.SlugField('Имя сообщества', unique=True)
    description = models.TextField('Описание сообщества')

    def __str__(self):
        return self.title


class Post(models.Model):
    """
    Описание модели записи блога
    """
    text = models.TextField('Текст записи')
    pub_date = models.DateTimeField('Дата публикации', auto_now_add=True)
    author = models.ForeignKey(USER_MODEL,
                               verbose_name='Автор',
                               on_delete=models.CASCADE,
                               related_name="posts"
                               )
    group = models.ForeignKey(Group,
                              verbose_name='Сообщество',
                              on_delete=models.CASCADE,
                              related_name="group",
                              blank=True,
                              null=True
                              )
```

### Выполнение миграции

```bash
# Добавить модели
yatube/settings.py

INSTALLED_APPS = [
    'posts',  # наше приложение posts**
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
] 

python manage.py makemigrations # Создание миграций. Создаст posts/migrations/0001_initial.py
python manage.py migrate # Выполнение миграции (создание таблиц)

```


### CRUD-операции

 - Create: ```Model.objects.create()``` — создание объекта в базе
 - Read: ```Model.objects.get(id=N)``` — чтение объекта по его ключу
 - Update: ```object.property= 'new value'``` и потом ```object.save()``` — изменение объекта
 - Delete: ```object.delete()``` — удаление объекта из базы



```commandline
>>> from posts.models import Post, User
>>> Post.objects.all() 
Запрос к базе возвращает специальный объект QuerySet
Чтобы получить определённый объект, можно обратиться к нему по его primary key
me = User.objects.get(pk=3)
```
Новый объект в базе можно создать методом create():

```commandline
# создаём объект, передаём свойства
>>> new = Post.objects.create(author=me, text="Смотри, этот пост я создал через shell!")
# посмотрим, какой id присвоен этому объекту в базе
>>> new.id
39
# а что в поле text?
>>> new.text
"Смотри, этот пост создан через shell!"
# а что в поле author?
>>> new.author
<User: admin>
# смотрим, что записано в поле username того объекта, на который ссылается поле author
>>> new.author.username
'admin' 
```
Чтобы изменить этот объект, надо присвоить новое значение одному из его полей и вызвать метод save()

```commandline
# присваиваем новое значение полю text
>>> new.text = "Смотри, этот пост обновлён!"
# но пока что значение изменено лишь в коде. В БД всё ещё хранится старое значение
# чтобы отправить новое значение в базу данных — вызываем метод save()
>>> new.save() 
```

Удалить объект из базы можно методом delete(). При вызове этот метод дополнительно 
удалит и все связанные объекты, для которых был задан параметр ```on_delete=models.CASCADE```

```commandline
>>> new.delete() 
```


###  Фильтрация объектов

```commandline
# найти все объекты, значение поля author у которых равно me
# в этой переменной хранится объект User с pk=3
>>> Post.objects.filter(author=me)
<QuerySet [<Post: Oops, I did it again!>, <Post: Утромъ гольдъ Дерсу Узала...>]>
```

Увидеть SQL-запрос, который будет отправлен к базе, можно с помощью команды ```.query```

```commandline
>>> print(Post.objects.filter(author=me).query)
SELECT "posts_post"."id", "posts_post"."text", "posts_post"."pub_date", 
"posts_post"."author_id", "posts_post"."group_id" FROM "posts_post" WHERE 
"posts_post"."author_id" = 1 
```

В Django ORM аналог команд WHERE выглядит так: указывается имя поля, затем 
два знака подчеркивания __, название фильтра и его значение:

```commandline
# найти посты, где поле text__содержит строку "again"
>>> Post.objects.filter(text__contains='again')
<QuerySet [<Post: Oops, I did it again!>]>
```

При запросе указываются именованные параметры функции filter(). 
Имя параметра состоит из имени поля и суффикса, указывающего, какой оператор применять. 

Доступные операторы:

 - **exact** — точное совпадение. 

```
«Найти пост, где поле id точно равно 1»
ORM: ```Post.objects.filter(id__exact=1)``` или ```Post.objects.filter(id=1)```
```

На SQL это условие выглядит так: ```SELECT ... WHERE id = 1.```
Сравнение работает и с None. Выражение ```Post.objects.filter(text=None)``` 
превратится в ```SELECT ... WHERE text IS NULL```

 - **contains** — поиск по тексту в поле text. 

```   
«Найти пост, где в поле text есть слово "oops" именно в таком регистре»
ORM: ```Post.objects.filter(text__contains="oops")```
SQL: ```SELECT ... WHERE text LIKE '%oops%';```
```

 - **in** — вхождение в множество.
   
```
«Найти пост, где значение поля id точно равно одному из значений: 1, 3 или 4»
ORM: Post.objects.filter(id__in=[1, 3, 4])
SQL: SELECT ... WHERE id IN (1, 3, 4);
```

Если вместо списка будет передана строка, она разобьётся на символы: 
```
«Найти пост, где значение поля text точно равно "o", "p" или "s"»
ORM: Post.objects.filter(text__in="oops")
SQL: SELECT ... WHERE text IN ('o', 'p', 's');
```


 - **Операторы сравнения** 
   - gt — > (больше),
   - gte — => (больше или равно),
   - lt — < (меньше),
   - lte — <= (меньше или равно).

```
«Найти пост, где значение поля id больше пяти»
ORM: Post.objects.filter(id__gt=5)
SQL: SELECT ... WHERE id>5;
```
 - **startswith, endswith** Операторы сравнения с началом и концом строки

```
«Найти посты, где содержимое поля text начинается со строки "Утромъ"»
ORM: Post.objects.filter(text__startswith="Утромъ")
SQL: SELECT ... WHERE text LIKE Утромъ% ESCAPE
```

 - **range** — вхождение в диапазон

```py
import datetime
start_date = datetime.date(1890, 1, 1)
end_date = datetime.date(1895, 3, 31)
Post.objects.filter(pub_date__range=(start_date, end_date))
# SQL: SELECT ... WHERE pub_date BETWEEN '1890-01-01' and '1895-03-31';
# выберет посты, опубликованные в диапазоне с 1 января 1890 до 31 марта 1895 
```

При работе с частями дат можно применять дополнительные суффиксы 
**date, year, month, day, week, week_day, quarter** и указывать для них дополнительные условия:

Такой же синтаксис применяется и для времени: **hour, minute, second.**

```python
# условия для конкретной даты
Post.objects.filter(pub_date__date=datetime.date(1890, 1, 1))
Post.objects.filter(pub_date__date__lt=datetime.date(1895, 1, 1))
# условия для года и месяца
Post.objects.filter(pub_date__year=1890)
Post.objects.filter(pub_date__month__gte=6)
# условия для квартала
Post.objects.filter(pub_date__quarter=1) 
```

 - **isnull** — проверка на пустое значение.

```
ORM: Post.objects.filter(pub_date__isnull=True)
SQL: SELECT ... WHERE pub_date IS NULL;
```

#### Объединение условий

В одном запросе можно указать несколько условий одновременно. Для этого последовательно 
вызовите методы ```filter()``` с различными параметрами. Будет сгенерирован SQL-запрос, 
в котором все условия объединены оператором ```AND```.
Исключить данные из выборки можно методом ```exclude()```

```py
# выбрать посты, начинающиеся со слова "Утромъ" 
# исключить из выборки посты автора me
# и показать только те посты, которые опубликованы не ранее 30 января 1895 года
>>> Post.objects.filter(
...     text__startswith='Утромъ'
... ).exclude(
...     author=me 
... ).filter(
...     pub_date__gte=datetime.date(1895, 1, 30)
... ) 
```

#### Сортировка и ограничение количества результатов

```order_by("-pub_date")``` — сортировать результаты по полю ```pub_date``` в обратном порядке 
(от больших значений к меньшим) ```[:11]``` — вернуть не более одиннадцати результатов из найденных.

```commandline
>>> print(Post.objects.order_by("-pub_date")[:11].query)
SELECT "posts_post"."id", "posts_post"."text", "posts_post"."pub_date", 
"posts_post"."author_id", "posts_post"."group_id" FROM "posts_post" ORDER 
BY "posts_post"."pub_date" DESC LIMIT 11 
```

Сортировку и ограничение числа возвращаемых результатов можно объединить с фильтрацией:

```commandline
>>> Post.objects.filter(text__startswith='Утромъ').order_by("-pub_date")[:2] 
```

### Загрузка связанных записей

Django предлагает два способа загрузки связанных записей:
 - ```select_related(relation)``` — загрузка связанных данных с помощью JOIN. В результате обработки получается один запрос, который, помимо основной модели, загружает и связанные данные из дополнительных таблиц.
 - ```prefetch_related(relation)``` — «ленивая» подгрузка связанных данных с помощью дополнительных запросов. В этом случае Django ORM сперва запрашивает данные из основной таблицы, запоминает первичные ключи связанных записей, а затем делает ещё один запрос для загрузки связанных данных, ключи которых есть в первой выборке.

Для ```select_related``` хватило только одного запроса!
```python
>>> related = Post.objects.select_related('author').all()
>>> for post in related:
...     tmp = f"{post.text} Автор {post.author.username}"
... 
# запрашиваем данные FROM "posts_post"
# и, дополнительно, данные автора INNER JOIN "auth_user":
# всё в одном запросе
(0.000) SELECT "posts_post"."id", "posts_post"."text", "posts_post"."pub_date", "posts_post"."author_id", "posts_post"."group_id", "auth_user"."id", "auth_user"."password", "auth_user"."last_login", "auth_user"."is_superuser", "auth_user"."username", "auth_user"."first_name", "auth_user"."last_name", "auth_user"."email", "auth_user"."is_staff", "auth_user"."is_active", "auth_user"."date_joined" FROM "posts_post" INNER JOIN "auth_user" ON ("posts_post"."author_id" = "auth_user"."id"); args=()
>>>
```

А вот так работает ```prefetch_related```:

```python
>>> related = Post.objects.prefetch_related('author').all()
>>> for post in related:
...     tmp = f"{post.text} Автор {post.author.username}"
... 
# запрашиваем все посты FROM "posts_post"
(0.000) SELECT "posts_post"."id", "posts_post"."text", "posts_post"."pub_date", "posts_post"."author_id", "posts_post"."group_id" FROM "posts_post"; args=()
# а теперь запрашиваем авторов FROM "auth_user", но только с перечисленными id: 
# WHERE "auth_user"."id" IN (1, 2)
# Django ORM получил список необходимых id из результатов первого запроса
(0.000) SELECT "auth_user"."id", "auth_user"."password", "auth_user"."last_login", "auth_user"."is_superuser", "auth_user"."username", "auth_user"."first_name", "auth_user"."last_name", "auth_user"."email", "auth_user"."is_staff", "auth_user"."is_active", "auth_user"."date_joined" FROM "auth_user" WHERE "auth_user"."id" IN (1, 2); args=(1, 2)
```


### Агрегирующие функции

 - **count()** Чтобы узнать количество полученных строк, можно вызвать метод ```count()``` 
   для ```objects```, дописав его к конструкции, делающей выборку
   
```python
#  выбираем посты, опублибликованные позже (gt) июня 1854 года, затем пересчитываем их
>>> Post.objects.filter(pub_date__month__gt=6, pub_date__year=1854).count()

(0.012) SELECT COUNT(*) AS "__count" FROM "posts_post" WHERE (django_datetime_extract('month', "posts_post"."pub_date", 'UTC') > 6 AND "posts_post"."pub_date" BETWEEN '1854-01-01
00:00:00' AND '1854-12-31 23:59:59.999999'); args=(6, '1854-01-01 00:00:00', '1854-12-31 23:59:59.999999')
30 
```

- **aggregate()** - применяет агрегирующие функции к определённой выборке или ко всей таблице.

В Django есть несколько агрегирующих функций, вот самые популярные из них:
 - **Avg**: вернёт среднее значение по указанной колонке в выборке
 - **Count**: вернёт количество записей в выборке, как и метод count(), описанный выше
 - **Max**: вернёт максимальное значение по указанной колонке в выборке
 - **Min**: вернёт минимальное значение по указанной колонке в выборке
 - **Sum**: вернёт сумму значений по указанной колонке в выборке

Эти функции хранятся в модуле django.db.models, перед применением их надо импортировать в код.

```python
>>> from django.db.models import Max, Count
#  найти максимальное значение id для объектов Post
>>> Post.objects.aggregate(Max("id"))
(0.000) SELECT MAX("posts_post"."id") AS "id__max" FROM "posts_post"; args=()
{'id__max': 43}

#  пересчитать объекты id в модели Post
>>> Post.objects.aggregate(Count("id"))
(0.000) SELECT COUNT("posts_post"."id") AS "id__count" FROM "posts_post"; args=()
{'id__count': 37}
37 
```

### Связи между таблицами

При создании модели Post мы добавили в неё ссылку на автора, на модель User, и указали 
related_name="posts".

```python
class Post(models.Model):
    # ... какой-то код
    author = models.ForeignKey(
        User, on_delete=models.CASCADE, related_name="posts"
    ) 
```
У модели User автоматически появится свойство posts, оно ссылается на все записи текущего автора.
```python
>>> leo = User.objects.get(id=2)
(0.000) SELECT "auth_user"."id", "auth_user"."password", "auth_user"."last_login", "auth_user"."is_superuser", "auth_user"."username", "auth_user"."first_name", "auth_user"."last_name", "auth_user"."email", "auth_user"."is_staff", "auth_user"."is_active", "auth_user"."date_joined" FROM "auth_user" WHERE "auth_user"."id" = 2; args=(2,)
>>> leo.username
'leo'

>>> leo.posts.count()
#  leo.posts — это выборка тех объектов из модели Post, 
#  у которых в поле author_id стоит "2" (которые связаны с leo), 
#  потому что leo — это объект User с id=2
(0.000) SELECT COUNT(*) AS "__count" FROM "posts_post" WHERE "posts_post"."author_id" = 2; args=(2,)
36 
```
Свойство posts у объекта модели User появилось в результате того, что модель Post 
ссылается на User. И, благодаря магии ORM, мы можем получить все записи автора, 
обратившись к свойству posts.

Свойства, ссылающиеся на объекты, имеют специальный тип: менеджер объектов. 
До сих пор мы работали с менеджером объектов objects, делая запросы вида 
User.objects.get(id=2) или Post.objects.all()

Чтобы применить агрегирующие функции к связанным данным из других таблиц, 
запрос делается через аннотирование, методом annotate()

 - **Метод annotate()** - в результате к полученным объектам добавляется новое свойство, содержащее результат вычисления
В следующем примере аргумент posts_count — это имя нового свойства объекта, оно появится у объектов модели User:
```python
# Достать из модели User все объекты, 
# создать свойство posts_count и записать в него число постов, связанных с автором.
# posts — это свойство модели User, менеджер объектов
>>>> annotated_results = User.objects.annotate(posts_count = Count('posts'))
>>> 
>>> annotated_results
(0.001) SELECT "auth_user"."id", "auth_user"."password", "auth_user"."last_login", "auth_user"."is_superuser", "auth_user"."username", "auth_user"."first_name", "auth_user"."last_name", "auth_user"."email", "auth_user"."is_staff", "auth_user"."is_active", "auth_user"."date_joined", COUNT("posts_post"."id") AS "posts_count" FROM "auth_user" LEFT OUTER JOIN "posts_post" ON ("auth_user"."id" = "posts_post"."author_id") GROUP BY "auth_user"."id", "auth_user"."password", "auth_user"."last_login", "auth_user"."is_superuser", "auth_user"."username", "auth_user"."first_name", "auth_user"."last_name", "auth_user"."email", "auth_user"."is_staff", "auth_user"."is_active", "auth_user"."date_joined"  LIMIT 21; args=()
<QuerySet [<User: admin>, <User: leo>]> 
```

```python
#  перебрать в цикле список пользователей annotated_results 
#  и для каждого объекта вывести свойство name
#  и новое свойство posts_count, которое хранит число постов пользователя
>>> for item in annotated_results:
...     print(f"Постов у пользователя {item.username}: {item.posts_count}")
... 
(0.000) SELECT "auth_user"."id", "auth_user"."password", "auth_user"."last_login", "auth_user"."is_superuser", "auth_user"."username", "auth_user"."first_name", "auth_user"."last_name", "auth_user"."email", "auth_user"."is_staff", "auth_user"."is_active", "auth_user"."date_joined", COUNT("posts_post"."id") AS "posts_count" FROM "auth_user" LEFT OUTER JOIN "posts_post" ON ("auth_user"."id" = "posts_post"."author_id") GROUP BY "auth_user"."id", "auth_user"."password", "auth_user"."last_login", "auth_user"."is_superuser", "auth_user"."username", "auth_user"."first_name", "auth_user"."last_name", "auth_user"."email", "auth_user"."is_staff", "auth_user"."is_active", "auth_user"."date_joined"; args=()
Постов у пользователя admin: 2
Постов у пользователя leo: 36
#  хорошо, что у нас пока что не 100500 авторов 
```
Разница между annotate() и aggregate():

Метод annotate() возвращает объекты и добавляет к ним новые свойства:
```python
>>> rez = User.objects.annotate(written_posts = Count('posts'))
>>> rez[1].written_posts
36
#  у объекта класса User появилось свойство written_posts, 
#  хотя в модели User оно не описано
```
Метод aggregate() отдает только значение, результат работы агрегирующей функции:
```python
>>> Checks.objects.aggregate(average_price=Avg('price'))
{'average_price': 127.01}
```



## Создание пользователей

Создание суперпользователя: 
```bash
python manage.py createsuperuser 
http://127.0.0.1:8000/admin/ # админка
```

### Модуль django.contrib.auth

В состав исходного кода фреймворка Django входит директория /contrib — «склад 
полезных вещей», набор готовых приложений для решения стандартных задач. Приложение 
django.contrib.auth было установлено автоматически вместе с Django при подготовке окружения. 

В модуле django.contrib.auth есть файл urls.py:

```python
from django.contrib.auth import views
from django.urls import path

urlpatterns = [
        path('login/', views.LoginView.as_view(), name='login'),
        path('logout/', views.LogoutView.as_view(), name='logout'),
   
        path('password_change/', views.PasswordChangeView.as_view(), name='password_change'),
        path('password_change/done/', views.PasswordChangeDoneView.as_view(), name='password_change_done'),
       
        path('password_reset/', views.PasswordResetView.as_view(), name='password_reset'),
        path('password_reset/done/', views.PasswordResetDoneView.as_view(), name='password_reset_done'),
        path('reset/<uidb64>/<token>/', views.PasswordResetConfirmView.as_view(), name='password_reset_confirm'),
        path('reset/done/', views.PasswordResetCompleteView.as_view(), name='password_reset_complete'),
]
```
По именам (параметр name)  для URL-шаблонов списка urlpatterns можно будет обращаться к страницам.

Если посмотреть исходный код модуля django/contrib/auth/views.py то мы найдём множество Class Based View.
Class Based View — это классы, по своему назначению аналогичные view-функциям, они так же обрабатывают запросы и возвращают ответ.
Поищите в файле названия классов, в имени которых есть слово "View", и найдите 
в них свойство template_name: это предустановленные названия шаблонов, необходимых для работы с пользователями

```python
class LoginView(SuccessURLAllowedHostsMixin, FormView):
    template_name = 'registration/login.html'
class LogoutView(SuccessURLAllowedHostsMixin, TemplateView):
    template_name = 'registration/logged_out.html'
class PasswordResetView(PasswordContextMixin, FormView):
    template_name = 'registration/password_reset_form.html'
class PasswordResetDoneView(PasswordContextMixin, TemplateView):
    template_name = 'registration/password_reset_done.html'
class PasswordResetConfirmView(PasswordContextMixin, FormView):
    template_name = 'registration/password_reset_confirm.html'
class PasswordResetCompleteView(PasswordContextMixin, TemplateView):
   template_name = 'registration/password_reset_complete.html'
class PasswordChangeView(PasswordContextMixin, FormView):
    template_name = 'registration/password_change_form.html'
class PasswordChangeDoneView(PasswordContextMixin, TemplateView):
    template_name = 'registration/password_change_done.html' 
```

 - LoginView — страница с формой авторизации;
 - LogoutView — страница выхода, дающая пользователю возможность прекратить работу с сайтом;
 - PasswordResetView — страница восстановления пароля, здесь можно ввести свой email и получить ссылку для восстановления доступа;
 - PasswordResetDoneView — страница уведомления о том, что ссылка на восстановление пароля отправлена;
 - PasswordChangeView — эта страница будет доступна по ссылке при восстановлении пароля, здесь пользователь сможет задать новый пароль;
 - PasswordChangeDoneView — страница уведомления о том, что пароль изменён.

В этом списке не хватает страницы регистрации, её мы создадим отдельно.

Надо будет создать такие шаблоны для нашего проекта Yatube в users/templates/:

```
registration/login.html
registration/logged_out.html
registration/password_reset_form.html
registration/password_reset_done.html
registration/password_reset_confirm.html
registration/password_change_form.html
registration/password_change_done.html
И еще signup.html для регистрации новых пользователей
```

Создание отдельного приложения users
Для того чтобы собрать весь код для управления регистрацией пользователей в одном месте, самостоятельно создайте новое приложение users и добавьте его в начало списка INSTALLED_APPS в конфиге сайта.
Скорее всего, вам пригодится консольная команда

```commandline
$ python manage.py startapp 
```



## Регистрация модели в админке

```python
# в файле posts/admin.py
@admin.register(Post)
class PostAdmin(admin.ModelAdmin):
    """
    Описание модели постов для адин. страницы
    """
    list_display = ("pk", "text", "pub_date", "author") # поля в таблице 
    search_fields = ("text",) # поля для поиска 
    list_filter = ("pub_date",) # поля для фильтра
    empty_value_display = "-пусто-"
```

### Конфигурация модели

```python
"""
Для настройки отображения модели в интерфейсе админки применяют класс  
ModelAdmin. Он связывается с моделью и конфигурирует отображение данных этой 
модели. В этом классе можно настроить параметры отображения. Полный список  
параметров есть в документации.

В файле posts/admin.py создайте класс PostAdmin, наследующийся от  admin.
ModelAdmin, и зарегистрируйте его как источник конфигурации для модели Post
"""

from django.contrib import admin
from .models import Post

class PostAdmin(admin.ModelAdmin):
    # перечисляем поля, которые должны отображаться в админке
    list_display = ("text", "pub_date", "author") 
    # "pk" для вывода ключа, ID записи
    # list_display = ("pk", "text", "pub_date", "author") 
    
    # добавляем интерфейс для поиска по тексту постов
    search_fields = ("text",) 
    # добавляем возможность фильтрации по дате
    list_filter = ("pub_date",) 
    # это свойство сработает для всех колонок: где пусто - там будет эта строка
    empty_value_display = "-пусто-"  
# при регистрации модели Post источником конфигурации для неё назначаем класс 
# PostAdmin
admin.site.register(Post, PostAdmin)
```
Остальные поля для управления выводом модели в админке:
https://docs.djangoproject.com/en/3.0/ref/contrib/admin/#django.contrib.admin.ModelAdmin

## Проектирование структуры адресов

 - Данные проекта хранятся в БД.
 - Для взаимодействия с БД в коде создаются модели.
 - Пользователь обращается к какой-то странице сайта, Django сверяет 
   запрошенный адрес с шаблонами адресов в файле urls.py.
 - Каждый шаблон адреса в urls.py связан с определённой функцией или классом, 
   которые обрабатывают входящие данные. Такие функции (или классы) 
   называются View 
 - View обращается к моделям и через них получает необходимые данные из БД.  
   Эти данные View передает в шаблоны (Template).
 - Данные выводятся в шаблон и генерируется HTML-документ, который
   возвращается пользователю.

```python
# Примеры: 
urlpatterns = [
# правила для сопоставления шаблонов URL и функций
    path('', include("posts.urls"))
    path('', views.index), 
    path('user', views.account),
    path('user/<int:user-id>', views.user_page),
    path('user/login', views.login),
    path('user/<str: user-name>', views.user_page_name),
] 
# Urls.py проекта: yatube/urls.py
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    # импорт правил из приложения posts
    path("", include("posts.urls")),
    # импорт правил из приложения admin
    path("admin/", admin.site.urls),
] 

# Urls.py приложения posts/urls.py
from django.urls import path
from . import views

urlpatterns = [
    path("", views.index, name="index")
]
```

Функция path() принимает такие параметры: path(route, view, name):
 - route — шаблон веб-адреса (URL). Получив HTTP-запрос, Django идет по 
   списку urlpatterns сверху вниз, пока не найдёт совпадение запрошенного адреса с 
   route в одном из вызовов path(). Если нет ни одного совпадения, 
   пользователю вернётся сообщение об ошибке 404: «Страница не найдена».
 - view — это имя view-функции. Если Django найдёт совпадение с шаблоном, то 
   перенаправит вызов в указанную view-функцию.
 - name — имя для path(), к нему можно обратиться из кода, чтобы установить 
   ссылку на страницу сайта.

Дополнительные параметры функции path(), о которых можно прочесть в 
[документации](https://docs.djangoproject.com/en/3.0/ref/urls/#django.urls.path)

## Настройка статичных файлов (static)

Перед публикацией проекта на боевом сервере все статические файлы проекта 
собираются в единую директорию. Сборка запускается командой collectstatic

Создайте две директории с названием static: одну в корне проекта, для сборки, 
вторую — в приложении posts, для статики приложения. В файл yatube/settings.py 
после переменной STATIC_URL добавьте новую переменную STATIC_ROOT

```python
# задаём адрес директории, куда командой *collectstatic* будет собрана вся статика
STATIC_ROOT = os.path.join(BASE_DIR, "static") 
```
Добавить папки статики в .gitignore

Если по каким-то причинам необходимо назвать папку со статикой иным именем — 
адрес такой папки нужно зарегистрировать в переменной STATICFILES_DIRS 
в yatube/settings.py

Обычно статику собирают в отдельную директорию прямо перед публикацией проекта 
на боевом сервере. Отдавать клиенту файлы из этой директории будет отдельный, 
быстрый и эффективный, сервер, например — nginx

[Файлы Bootstrap от Яндекс](https://code.s3.yandex.net/backend-developer/learning-materials/static.zip)
для статики

##  Эмуляция почтового сервера

Подключим модуль filebased.EmailBackend: он будет сохранять текст отправленных электронных 
писем в файлы в отдельную директорию. Добавьте в settings.py следующий код:

Создайте папку /sent_emails в головной директории проекта.
Теперь при запросе на восстановление пароля система будет делать вид, что отправила 
письмо, но эти письма будут «отправляться» в директорию sent_emails.

```python
#  подключаем движок filebased.EmailBackend
EMAIL_BACKEND = "django.core.mail.backends.filebased.EmailBackend"
# указываем директорию, в которую будут складываться файлы писем
EMAIL_FILE_PATH = os.path.join(BASE_DIR, "sent_emails")
```

Для работы с почтой в Django есть специальный модуль Mail, отправкой писем занимаются 
функции из этого модуля:
 - send_mail() — для отправки единичного письма получателю.
 - send_mass_mail() — для отправки множества писем.
 - mail_admins — отправить письмо администраторам сайта. Список адресов администраторов 
   перечисляется в списке ADMINS в settings.py.
 - mail_managers — для отправки писем менеджерам сайта. Большой проект может управляться 
   большим количеством сотрудников, и в списке MANAGERS конфига можно задать список 
   их почтовых адресов, по которым будет идти служебная рассылка.

Самый простой способ отправить письмо из собственной view-функции или класса — вызвать 
стандартную функцию Django send_mail() и передать ей на вход необходимые данные:

```python
from django.core.mail import send_mail

send_mail(
    'Тема письма',
    'Текст письма.',
    'from@example.com',  # Это поле "От кого"
    ['to@example.com'],  # Это поле "Кому" (можно указать список адресов)
    fail_silently=False, # Сообщать об ошибках («молчать ли об ошибках?»)
)
```


## View обработка

В файл posts/views.py добавить views-функцию index
```python
# Пример работы с view
from django.http import HttpResponse
from .models import Post

def index(request):
    # одна строка вместо тысячи слов на SQL
    latest = Post.objects.order_by('-pub_date')[:10]
    # собираем тексты постов в один, разделяя новой строкой
    output = []
    for item in latest:
        output.append(item.text)
    return HttpResponse('\n'.join(output))

# Еще пример работы с view
from django.shortcuts import render, get_object_or_404
from .models import Post, Group

def index(request):
    latest = Post.objects.order_by('-pub_date')[:11]
    return render(request, 'index.html', {"posts": latest})

def group_posts(request, slug):
    group = get_object_or_404(Group, slug=slug)
    posts = Post.objects.filter(group=group).order_by("-pub_date")[:12]
    return render(request, 'group.html', {"group": group, "posts": posts})

Post.objects.all() # получить все записи модели Post
Post.objects.get(id=1) 
# получить запись модели Post, у которой значение 
# поля id равно 1. Поскольку поле id — это первичный ключ, а Django 
# автоматически создаёт у модели свойство pk, то альтернативная запись этого 
# же запроса будет такой: Post.objects.get(pk=1).
Post.objects.filter(pub_date__year=1854) 
# запрос вернёт объекты, у которых 
# значение года в поле pub_date равно 1854. Обратите внимание на синтаксис 
# фильтрации: двойное нижнее подчёркивание между названиями поля и фильтра. 
# Подробнее о функции filter() в документации:
# https://docs.djangoproject.com/en/3.0/ref/models/querysets/#django.db.models.query.QuerySet.filter
Post.objects.filter(text__startswith="Писать не хочется") # пример фильтра 
# по текстовому полю, он вернёт записи, начинающиеся с указанной в фильтре 
# строки.

get_object_or_404() # Функция ищет в базе объект модели, и если не находит — 
# прерывает работу view-функции и возвращает страницу с ошибкой 404


```

### Замыкания. Проверка авторизации

 надо изменить код проекта так, чтобы определённые функции сайта были доступны только 
 авторизованным пользователям: например, у неавторизованных пользователей не должно 
 быть возможности создать пост, подписаться на автора или отправить комментарий. 
 Для этого некоторые view-функции должны проверять авторизацию:

```python
from django.shortcuts import redirect
...

def only_user_view(request):
    if not request.user.is_authenticated:
        # Если пользователь не авторизован - отправляем его на страницу логина.
        return redirect('/auth/login/')
    # Если пользователь авторизован — здесь выполняется полезный код функции.
```

Самое время решить задачу по ограничению прав доступа к определённым страницам сайта: изменить несколько view-функций так, чтобы они выполнялись, только если пользователь авторизован.
Решение понятно: написать декоратор, проверяющий авторизацию, и обернуть им нужные view-функции.

```python
from django.shortcuts import redirect
...

def authorized_only(func):
    # Функция-обёртка в декораторе может быть названа как угодно
    def check_user(request, *args, **kwargs):
        # В любую view-функции первым аргументом передаётся объект request,
        # в котором есть булева переменная is_authenticated,
        # определяющая, авторизован ли пользователь.
        if request.user.is_authenticated:
            # Возвращает view-функцию, если пользователь авторизован.
            return func(request, *args, **kwargs)
        # Если пользователь не авторизован — отправим его на страницу логина.
        return redirect('/auth/login/')        
    return check_user

# Декорируем view-функцию
@authorized_only
def some_view(request):
    # Доступно только авторизованным!
    ...
```

### Декоратор @login_required

[Этот декоратор устроен несколько сложнее](https://docs.djangoproject.com/en/2.2/_modules/django/contrib/auth/decorators/#login_required): 
он умеет принимать параметры и работать с Class Based Views.

Декоратор @login_required импортируется из django.contrib.auth.decorators:

```python
from django.contrib.auth.decorators import login_required

@login_required
def my_view(request):
    ...
```

Если незалогиненный пользователь обратится к странице, доступной только для авторизованных 
пользователей, то декоратор ```@login_required``` перенаправит его на страницу авторизации. 
Если пользователь авторизуется — он вернётся на ту страницу, с которой он пришёл. 
Адрес этой страницы будет передан в GET-параметре в переменной ```next```:```/auth/login?next=any-page-url```

Измените шаблон ```users/templates/registration/login.html``` — добавьте блок с проверкой 
переменной **next**. Текст из блока ```{% if next %}``` будет показан только тем пользователям,
которые переадресованы на страницу авторизации с других страниц.

```html
{% extends "base.html" %}
{% block title %}Войти{% endblock %}
{% block content %}
{% load user_filters %}

<div class="row justify-content-center">
  <div class="col-md-8 p-5">
    <div class="card">
      <div class="card-header">Войти на сайт</div>
      <div class="card-body">
        {% if form.errors %}
        <div class="alert alert-danger" role="alert">
          Имя пользователя и пароль не совпадают. Введите правильные данные.
        </div>
        {% endif %}

        {% if next %}            
            <div class="alert alert-info" role="alert">
              Вы обратились к странице, доступ к которой возможен только для залогиненных пользователей.<br>
              Пожалуйста, авторизуйтесь.
            </div>
        {% else %}
            <div class="alert alert-info" role="alert">
              Пожалуйста, авторизуйтесь.
            </div>
        {% endif %}

        <form method="post" action="{% url 'login' %}">
          {% csrf_token %}
          <input type="hidden" name="next" value="{{ next }}">
          <div class="form-group row">
              <label for="{{ form.username.id_for_label }}" class="col-md-4 col-form-label text-md-right">Имя пользователя</label>
              <div class="col-md-6">
                  {{ form.username|addclass:"form-control" }}
              </div>
          </div>

          <div class="form-group row">
              <label for="{{ form.password.id_for_label }}" class="col-md-4 col-form-label text-md-right">Пароль</label>
              <div class="col-md-6">
                  {{ form.password|addclass:"form-control" }}
              </div>
          </div>

          <div class="col-md-6 offset-md-4">              
              <button type="submit" class="btn btn-primary">
                Войти
              </button>
              <a href="{% url 'password_reset' %}" class="btn btn-link">
                Забыли пароль?
              </a>
          </div>
        </form>
      </div> <!-- card body -->
    </div> <!-- card -->
  </div> <!-- col -->
</div> <!-- row -->

{% endblock %}
```

Теперь view-функции тех страниц, куда разрешён доступ только под логином (это, например, 
страница создания нового поста), можно обернуть декоратором ```@login_required```; после 
этого проверка и переадресация неавторизованных пользователей на страницу логина 
будет происходить автоматически.



## Шаблоны 

### Установка директории templates

```python
# директория в главной папке проекта
TEMPLATES_DIR = os.path.join(BASE_DIR, "templates") 
TEMPLATES = [
    {
        "BACKEND": "django.template.backends.django.DjangoTemplates",
        "DIRS": [TEMPLATES_DIR], #Указать путь к шаблонам
        "APP_DIRS": True,
        "OPTIONS": {
            "context_processors": [
                "django.template.context_processors.debug",
                "django.template.context_processors.request",
                "django.contrib.auth.context_processors.auth",
                "django.contrib.messages.context_processors.messages",
            ]
        },
    }
] 
```

### Рендеринг шаблона

```python
from django.shortcuts import render

def my_index(request):
    # какой-то код
    title = 'Заголовок страницы'
    body = 'Текст страницы'
    # Сгенерированные во view-функции данные сохраняем в словарь
    context = {'title': title, 'body': body}

    # вызов функции render():
    # первый параметр — это всегда request, объект запроса
    # второй параметр - имя шаблона, в который будут "обёрнуты" данные
    # третий параметр - словарь с переменными, которые передаются  в шаблон
    return render(request, 'index.html', context) 
```

```html
<h1>{{ title }}</h1>
<p>{{ body }}</p> 
```

В словаре context можно передать в шаблон любые данные: строки, списки, словари,
объекты классов — всё, что необходимо. Обратиться в шаблоне к элементу словаря, 
свойству объекта или элементу списка можно через точечную нотацию:

```html
{{ var_dict.key }} — обращение к ключу словаря
{{ var_instance.attribute }} — обращение к свойству или методу класса
{{ var_list.0 }} — обращение к элементу списка 
```

### Теги

[Документация](https://docs.djangoproject.com/en/2.2/ref/templates/builtins/#ref-templates-builtins-tags) 
по тегам шаблонизатора

Для более сложных конструкций, влияющих на логику исполнения кода, существуют 
элементы разметки, теги. Это иное, чем HTML-теги, в коде они выделяются 
конструкциями {% и %}. Теги шаблонизатора могут быть одиночные:

```html
{% include "footer.html" %} 
```
или парные, состоящие из открывающего и закрывающего тегов: 
```html
{% block %}
  тело тега
{% endblock %} 
```

```html
{% if user.is_authenticated %}
  Привет, {{ user.username }}.
{% else %}
  Будет здорово, если вы авторизуетесь!
{% endif %}
```

Комментарии
```html
{% comment "Опциональный текст, комментарий к комментарию" %}
  <p>Этот кусок шаблона временно отключен {{ create_date|date:"c" }}</p>
  <p>Уходя, гасите свет.</p>
{% endcomment %}

{# Однострочный комментарий, пригодится для заметок **#}
<!-- И это -- тоже комментарий -->
```

### Фильтры в HTML-шаблонах 

[Документация](https://docs.djangoproject.com/en/3.0/ref/templates/builtins/#ref-templates-builtins-filters) 
по фильтрам шаблонизатора

Фильтры обрабатывают значения переменных или аргументов других тегов. В коде 
фильтры присоединяются к имени переменной через символ |

**length** - Вернёт длину строки или последовательности, переданной в переменной
variable:
```html
{{ variable|length }} 
```

**safe** - Чтобы HTML-теги не вываливались на страницу, а выполняли своё 
предназначение (форматировали и структурировали страницу) — в шаблоне необходимо
применять фильтр safe
```python
# views.py
...
def poem(request):
    text = ('Вчера Крокодил<br>улыбнулся так злобно,<br>Что мне до сих '
            'пор<br>за него неудобно.<br><i>Рената Муха</i>'
            )
    context = {'poem': text}
    render(request, 'poem.html', context) 
```
```html
{# poem.html #}
<h2>Стихотворение</h2>
{{ poem|safe }} 
```

**linebreaksbr** - Он заменяет символы перевода строки \n на HTML-теги \<br>.

**date** - работает только с объектами типа date и datetime: он форматирует дату
[по маске](https://docs.djangoproject.com/en/2.2/ref/templates/builtins/#date). 
За основу взят стандарт, принятый в языке программирования PHP. 
```html
{{ pub_date|date:"j.m.Y" }} {# выведет 2.02.2020 #} 
{{ pub_date|date:"j F Y" }} {# выведет 2 февраля 2020 #}
{{ pub_date|date:"d.m.y" }} {# выведет 02.02.20 #}
{{ pub_date|date:"d M Y" }} {# выведет 02 фев 2020 #} 
```

Фильтры можно объединять в цепочку:

```html
{{ variable|title|truncatewords:4 }} 
```

### Пример Template

```html
{# шаблон base.html **#}
<!DOCTYPE html>
<html>
<head>
  <title>
    {% block title %}
      The Last Social Media You'll Ever Need | Yatube
    {% endblock %}
  </title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  {% include "header.html" %}
  <nav id="sidebar">
    {% block sidebar %}
    <ul>
      <li><a href="/">Главная</a></li>
      <li><a href="/about/">О сайте</a></li>
      <li><a href="/list/">Сообщения</a></li>
    </ul>
    {% endblock %}
  </nav>
  <div id="content">
  {% block content %}
    Контент не подвезли :(
  {% endblock %}
  </div>
  {% include "footer.html" %}
</body>
</html> 
```

```html
{# шаблон header.html **#}
<div id="top-of-site">
{# здесь описана шапка сайта, она повторяется на всех страницах проекта #}
  <img src="images/logo.jpg" alt="Yatube" />
  <div id="site-name">Yatube</div>
</div>
```

```html
{# шаблон footer.html **#}
<div id="bottom-of-site">
{# здесь описан «подвал» сайта, он одинаков для всех страниц проекта #}
  <img src="images/logo.jpg" alt="Yatube" /> Yatube
  <div id="copyright">© Все права принадлежат всем</div>
</div>c 
```
Все шаблоны, подключенные через include, могут напрямую работать со словарём context

Для переопределения содержимого в теге block применяют тег extends:
Одиночный тег extends сообщает системе, в каком шаблоне нужно переопределить 
блоки, описанные следом за этим тегом

```python
from django.shortcuts import render

def messages(request):
    # какой-то код
    title = 'Ваши сообщения'
    messages = [
        'Вы почти разобрались с шаблонами!', 
        'Сломалось? Бывает, не беда.',
        'У вас получится!', 
    ]
    # Сгенерированные во view-функции данные сохраняем в словарь
    context = {'title': title, 'messages': messages}

    # вызов функции render():
    # первый параметр — это всегда request, объект запроса
    # второй параметр - имя шаблона, в который будут "обёрнуты" данные
    # третий параметр - словарь с переменными, которые передаются  в шаблон
    return render(request, 'messages.html', context) 
```
Из view-функции вызван шаблон messages.html. В самом начале этого шаблона стоит 
тег {% extends "base.html" %}, а в коде определены блоки title, sidebar и 
content: блоки с такими же названиями есть и в шаблоне base.html.

```html
{# шаблон messages.html #}

{% extends "base.html" %}

{# Задали заголовок в блоке title, текст заголовка взяли из словаря context #}
{% block title %}
  {{ title }}
{% endblock %}

{% block sidebar %}
  <ul>
    <li><a href="/">Главная</a></li>
    <li><a href="/about/">О сайте</a></li>
    {# Ссылку на страницу "Сообщения" сделали простым текстом и покрасили в красный #}
    <li><span style="color: red;">Сообщения</span></li>
  </ul>
{% endblock %}

{% block content %}
  {# Вывели все сообщения из списка context, как в Python #}
  {% for msg in messages %}
    <p>{{ msg }}</p>
  {% endfor %}
{% endblock %} 
```
Когда Django вызывает какой-то шаблон и видит в нём тег extends 
"any_template.html", то 
 - будет вызван шаблон any_template.html; при необходимости в нём будут 
   выполнены все инструкции из тегов {% include ... %};  
 - в шаблоне any_template.html будут заменены все одноимённые блоки, которые в 
   вызванном шаблоне перечислены по именам после тега extends.

### Ветвления, циклы и ссылки

#### Ветвления

Тег ветвления (тег проверки условия) if похож на оператор ветвления в Python

```html
{% if news %}
    У вас {{ news|length }} обновлений новостей
{% elif is_holiday %}
    Новостей нет, сегодня же праздник!
{% else %}
    Сегодня нет новостей.
{% endif %} 
```
В условиях {% if %} работают операторы сравнения <, >, <=, >=, !=, ==, 
логические операторы or, and, not, операторы тождественности is и вхождения in, 
круглые скобки и стандартные правила приоритета операций.

В условиях можно применять и фильтры:
```html
{% if news|length >= 100 %}
 Сегодня больше сотни новостей! Что случилось?
{% endif %}
```

#### Циклы 

**for**

Тег for выполняет определённый код для каждого элемента списка, переданного в цикл.

```html
{% for key, value in dict_data.items %}
    Ключ '{{ key }}': Значение '{{ value }}'
{% endfor %} 
```
Помимо обычных переменных в циклах создаются и вспомогательные, они доступны в специальной переменной forloop:
 - forloop.counter — текущий счетчик выполнений цикла, начинается с 1;
 - forloop.counter0 — текущий счетчик выполнения цикла, начинается с 0;
 - forloop.revcounter — сколько итераций осталось до конца цикла, начинается с 1;
 - forloop.revcounter0 — сколько итераций осталось до конца цикла, начинается с 0;
 - forloop.first — вернёт True на первой итерации цикла, в остальных случаях вернёт False;
 - forloop.last — вернёт True на последней итерации цикла, в остальных случаях вернёт False;
 - forloop.parentloop — если цикл был запущен внутри другого цикла, то в этой переменной находится переменная forloop родительского цикла.

**empty**

Необязательный тег {% empty %}, вложенный в for, сработает, если переданный в цикл список пуст:

```html
<ul>
{% for news in news_list %}
    <li>{{ news.title }}</li>
{% empty %}
    <li>Список новостей пуст.</li>
{% endfor %}
</ul> 
```

**ifchanged**

Вложенный в for тег {% ifchanged %} запоминает значение переданных параметров
или своего тела между запусками цикла, — и если они не поменялись, скрывает его.
В этом листинге HTML-заголовок \<h2> с названием месяца будет выводиться на 
страницу только если в предыдущей итерации цикла название месяца было другим.

```html
<h1>Архив новостей за {{ year }}</h1>

{% for news in news_items %}
    {% ifchanged %}
        <h2>{{ news.pub_date|date:"F" }}</h2>
    {% endifchanged %}

    <h3>{{ news.pub_date|date:"d.m.Y" }} | {{ news.title}}</h3>
{% endfor %} 
```
В результате работы цикла получится примерно такой HTML-код:
```html
<h1>Архив новостей за 2019</h1>
<h2>Январь</h2>
<h3>1.01.2019 | С Новым Годом!</h3>
<h3>2.01.2019 | С Днём научной фантастики!</h3>
<h3>3.01.2019 | С Днём рождения соломинки для коктейлей!</h3>
<h2>Февраль</h2>
<h3>1.02.2019 | С Днём работника лифтового хозяйства!</h3>
<h3>2.02.2019 | С Днём сурка!</h3>
<h3>2.02.2019 | С Днём сурка!</h3>
<h3>2.02.2019 | С Днём сурка!</h3>
```

**url**

Тег {% url %} генерирует ссылки на страницы проекта. Из кода шаблона можно 
обратиться к именам адресов, зарегистрированных в списке urlpatterns в файле 
urls.py, и передать параметры, если они требуются:

```python
urlpatterns = [
    path('', views.index, name='index'),
    path('/detail/<int:pk>/', views.details, name='detail'),
    ...
]
```
Первый параметр тега url — это name пути из файла urls.py:
```html
<a href="{% url 'index' %}">Главная</a>
```
```html
urlpatterns = [
    path('/detail/<int:pk>/', views.details, name='detail'),
    path('/<str:username>/<int:id>/', views.article, name='article'),
]

{# передаём один параметр #}
<a href="{% url 'detail' 1 %}">Подробнее об объекте 1</a> {# получится ссылка detail/1 #}
<a href="{% url 'detail' pk=1 %}">Подробнее об объекте 1</a>
<a href="{% url 'detail' pk=object.id %}">Подробнее об объекте {{ object.id }}</a>

{# передаём несколько параметров #}
<a href="{% url 'article' 'anton' 16 %}">Статья с ID=16, автор: anton</a>
<a href="{% url 'article' username='anton' id=16 %}">Статья с ID=16, автор: anton</a>
<a href="{% url 'article' username=article.username id=article.id %}">Статья с ID={{ article.id }}, 
   автор: {{ article.username }}</a> 
```

### Включение статики в шаблоны

```bash
python manage.py collectstatic
```

После того как вы собрали статику и запустили проект с помощью команды runserver, 
можете попробовать открыть какой-нибудь файл из директории STATIC_ROOT через HTTP.
Например, по ссылке http://127.0.0.1:8000/static/bootstrap/dist/js/bootstrap.js 
в браузере откроется код JavaScript-библиотеки.
Ссылка состоит из нескольких частей:

 - http://127.0.0.1:8000/ — адрес вашей локальной машины и порт, на котором запущен Django.
 - /static/ — эта часть пути управляется служебным приложением 
   Django django.contrib.staticfiles. Поменять эту часть пути вы можете в переменной 
   STATIC_URL в файле настроек проекта yatube/settings.py
 - bootstrap/dist/js/bootstrap.js — это путь к файлу в папке STATIC_ROOT

Чтобы добавить ссылку на подгрузку файла в шаблон, необходимо загрузить модуль для работы 
со статикой командой {% load static %}, а в адресах подключаемых файлов применять 
тег {% static "адрес_файла_относительно_директории_статики" %}:

```html
{% load static %}
<script src="{% static "bootstrap/dist/js/bootstrap.js" %}"></script> 
```

### Базовый шаблон

Создадим базовый HTML-файл на основе [примера](https://getbootstrap.com/docs/4.3/getting-started/introduction/#starter-template) 
из документации по Bootstrap и определим стандартные блоки для заголовка страницы и тела

```html
<!doctype html>
<html>

<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <title>{% block title %}The Last Social Media You'll Ever Need{% endblock %} | Yatube</title>
    <!-- Загрузка статики -->
    {% load static %}
    <link rel="stylesheet" href="{% static 'bootstrap/dist/css/bootstrap.min.css' %}">
    <script src="{% static 'jquery/dist/jquery.min.js' %}"></script>
    <script src="{% static 'bootstrap/dist/js/bootstrap.min.js' %}"></script>
</head>

<body>

    <main>
        <div class="container">
            <h1>{% block header %}The Last Social Media You'll Ever Need{% endblock %}</h1>
            {% block content %}
            <!-- Содержимое страницы -->
            {% endblock %}
        </div>
    </main>

</body>

</html> 
```

Сохраните этот файл в папку templates под именем base.html. Теперь измените 
шаблон главной страницы index.html:

```html
{% extends "base.html" %}
{% block title %}Последние обновления на сайте{% endblock %}
{% block header %}Последние обновления на сайте{% endblock %}
{% block content %}

    {% for post in posts %}
    <h3>
        Автор: {{ post.author.get_full_name }}, Дата публикации: {{ post.pub_date|date:"d M Y" }}
    </h3>
    <p>{{ post.text|linebreaksbr }}</p>
    {% if not forloop.last %}<hr>{% endif %}
    {% endfor %}

{% endblock %}
```

### Добавление шапки и подвала сайта 

Создайте файл templates/nav.html с таким содержимым:
```html
<nav class="navbar navbar-light" style="background-color: #e3f2fd;">
    <a class="navbar-brand" href="/"><span style="color:red">Ya</span>tube</a>
    <nav class="my-2 my-md-0 mr-md-3">
        {% if user.is_authenticated %}
        Пользователь: {{ user.username }}.
        <a class="p-2 text-dark" href="{% url 'password_change' %}">Изменить пароль</a>
        <a class="p-2 text-dark" href="{% url 'logout' %}">Выйти</a>
        {% else %}
        <a class="p-2 text-dark" href="{% url 'login' %}">Войти</a> |
        <a class="p-2 text-dark" href="{% url 'signup' %}">Регистрация</a>
        {% endif %}
    </nav>
</nav>
```

Подключите файл templates/nav.html к базовому шаблону templates/base.html тегом {% include %}:

```html
<!doctype html>
<html>
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
        <title>{% block title %}The Last Social Media You'll Ever Need{% endblock %} | Yatube</title>
        <!-- Загрузка статики -->
        {% load static %}
        <link rel="stylesheet" href="{% static 'bootstrap/dist/css/bootstrap.min.css' %}">
        <script src="{% static 'jquery/dist/jquery.min.js' %}"></script>
        <script src="{% static 'bootstrap/dist/js/bootstrap.min.js' %}"></script>
    </head>
    <body>
        {% include 'nav.html' %}
        <main>
            <div class="container">
                {% block content %}
                <!-- Содержимое страницы -->
                {% endblock content %}
            </div>
        </main>

    </body>
</html>
```
Тем же способом добавьте файл шаблона для блока, отображаемого внизу страницы, его называют «подвал» или "footer". Назовём его footer.html

```html
<footer class="pt-4 my-md-5 pt-md-5 border-top">
    <p class="m-0 text-dark text-center ">Социальная сеть <span style="color:red">Ya</span>tube </p>
</footer>
```


## Формы

### Generic Views

При обращении к какому-нибудь URL специальный обработчик path() вызывает объект, 
передавая ему в качестве аргумента объект типа request, а на выходе ожидает объект типа response.
Вызываемым объектом может быть view-функция, но можно вызвать классы и их методы.
 - View-функция — такие функции называют ещё «функции представления» (от слова "view") или просто «представление». Это самый простой тип view-объектов. Функция получает на вход стандартный объект request и возвращает объект типа response. Объекты response могут быть созданы встроенными функциями-помощниками, например, функцией render(). Вызов view-функции: path('view/', my_view)
 - Class-based view — по аналогии название можно перевести как «представление, основанное на классе» или «представление-класс». Мы будем использовать термин «view-класс». Такой класс должен наследоваться от специальных родительских классов Generic Views. Из файлов urls.py можно вызывать метод view-класса as_view(). Вызов метода view-класса: path('view/', ClassName.as_view())

Generic Views — это встроенные в Django view-классы, созданные для решения стандартных задач. В переводе Generic Views — это «общий вид» или «базовое представление». Популярные Generic Views:
 - FormView обрабатывает формы на основе моделей.
 - TemplateView упрощает вывод данных в шаблон.
 - CreateView связывает модель и пользовательскую веб-форму, предназначенную для создания новой записи в базе.

На основе Generic Views создают классы-наследники: view-классы, обладающие свойствами и методами Generic Views; это классическое ООП в действии.

### Связь модели, формы и view-класса

Создание форм на основе моделей:
1. Создаётся (или выбирается существующая) модель.
2. На основе модели создаётся класс формы.
3. Объект формы (экземпляр, созданный на основе класса формы) передаётся в специальный view-класс.
4. View-класс передаёт объект формы в шаблон, создаёт и возвращает пользователю страницу с веб-формой.

Для создания форм на основе моделей есть предустановленный класс ModelForm: от него можно наследовать классы для генерации форм.
Вот пример создания формы через ModelForm:

```python
    from django.db import models
    from django.forms import ModelForm
    
    
    # создадим модель, в которой будем хранить данные формы
    class Book(models.Model):
        name = models.CharField(max_length=100)
        isbn = models.CharField(max_length=100)
        pages = models.IntegerField(min_value=1)
    
    
    class BookForm(ModelForm):
        class Meta:
            # эта форма будет работать с моделью Book
            model = Book
            # на странице формы будут отображаться поля 'name', 'isbn' и `pages`
            fields = ['name', 'isbn', 'pages']
```
Теперь надо вывести эту форму на страницу: передать её во view-функцию или view-класс. 
Это стандартная задача, и её тоже упростили: в Django для этого есть отдельный Generic View CreateView.

```python
from django.views.generic import CreateView
from .forms import BookForm

class BookView(CreateView):
    form_class = BookForm
    success_url = "/thankyou" # куда переадресовать пользователя после успешной отправки формы
    template_name = "new_book.html"
```

В HTML-шаблон передаётся переменная form:

**new_book.html:**
```shell
<form method="post">
    {% csrf_token %}
    {{ form.as_p }}
    <input type="submit" value="Отправить">
</form>
```
**urls.py**
```python
#  теперь из файла urls.py для пути new_book/ 
#  можно вызвать метод as_view() класса BookView
#  этот метод унаследован классом BookView от родителя 
urlpatterns = [
    # ...
    path("new_book/", views.BookView.as_view(), name="new_book")
] 
```

### Добавление формы регистрации

Вот план дальнейшей работы:
1. На основе встроенного класса **UserCreationForm** напишем класс **CreationForm**, 
   он создаст объект формы регистрации, данные из которой будут передаваться в модель **User**.
2. На основе *Generic Views* **CreateView** создадим view-класс **SignUp**, 
   который вызовет шаблон и передаст в него форму **CreationForm**.
3. Создадим HTML-шаблон, он примет объект form из view-класса **CreateView**.
4. Добавим вызов view-класса **SignUp** в *urls.py*.


#### 1. Создание формы на основе класса UserCreationForm

В модуле django/contrib/auth/forms.py для создания формы регистрации заготовлен класс 
UserCreationForm (наследник знакомого вам встроенного класса ModelForm), на основе которого 
создаётся форма регистрации.

**django/contrib/auth/forms.py**

```python
class UserCreationForm(forms.ModelForm):
    """
    A form that creates a user, with no privileges, from the given username and
    password.
    """
    # ... 
```

В исходном коде класса UserCreationForm видно, что форма создается на основе модели User. 
Класс UserCreationForm (как и любые наследники класса ModelForm) считывает и добавляет 
свойства модели как поля формы.

Сейчас мы создадим класс CreationForm, наследника класса UserCreationForm. Классу ModelForm 
он будет приходиться внуком: ModelForm → UserCreationForm → CreationForm.

Класс CreationForm можно было бы и не создавать, а напрямую подключить встроенный 
класс UserCreationForm из пакета django.contrib.auth, но для нашей работы нужно внести изменения 
в работу предустановленного класса: хочется вывести на страницу не все поля, а лишь те, 
которые нужны для регистрации именно на нашем сайте.

> В Django принято хранить формы в отдельном файле, и мы последуем этому правилу.

#### 2. Отображение формы

Создайте в файле users/views.py view-класс SignUp, унаследовав его от Generic View CreateView:

```python
#  импортируем CreateView, чтобы создать ему наследника
from django.views.generic import CreateView

#  функция reverse_lazy позволяет получить URL по параметру "name" функции path()
#  берём, тоже пригодится
from django.urls import reverse_lazy

#  импортируем класс формы, чтобы сослаться на неё во view-классе
from .forms import CreationForm


class SignUp(CreateView):
    form_class = CreationForm
    success_url = reverse_lazy("signup") #  где signup — это параметр "name" в path()
    template_name = "signup.html"
```

 - form_class — из какого класса взять форму
 - success_url — куда перенаправить пользователя после успешной отправки формы
 - template_name — имя шаблона, куда будет передана переменная form с объектом HTML-формы. Всё это чем-то похоже на вызов функции render() во view-функции.

Теперь в шаблон signup.html будет выведена форма, описанная в классе CreationForm. 
После отправки этой формы пользователь будет переадресован на страницу, для которой 
в urls.py указано имя name="signup". Данные, отправленные через форму, будут переданы 
в модель User и сохранены в БД

#### 3. Добавление шаблона

Для удобства организации кода создайте директорию users/templates. Это будет директория 
шаблонов приложения Users.

Django будет работать с такими директориями, если в settings.py в директиве TEMPLATES 
для ключа APP_DIRS установить True. После установки этого ключа Django будет искать шаблоны 
не только в головной директории templates, но и в папках templates в директориях 
приложений (если такие папки там есть).

В users/templates создайте файл signup.html и добавьте в него код для отображения формы:

```html
{% extends "base.html" %}
{% block title %}Зарегистрироваться{% endblock %}
{% block content %}

<form method="post" action="{% url 'signup' %}">
  {% csrf_token %}
  {{ form.as_p }}
  <input type="submit" value="Зарегистрироваться">
</form>
{% endblock %}
```

#### 4. Добавление страницы регистрации в urls.py

Для адресов страниц, относящихся к регистрации и входу на сайт, мы будем использовать префикс auth/.
Подключите файлы urls.py приложений Users и Auth к головному urls.py по аналогии с уже подключённым posts.urls.
После изменений ваш файл yatube/urls.py должен выглядеть так:
```python
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    #  регистрация и авторизация
    path("auth/", include("users.urls")),

    #  если нужного шаблона для /auth не нашлось в файле users.urls — 
    #  ищем совпадения в файле django.contrib.auth.urls
    path("auth/", include("django.contrib.auth.urls")),

    #  раздел администратора
    path("admin/", admin.site.urls),
      
    #  обработчик для главной страницы ищем в urls.py приложения posts
    path("", include("posts.urls")),
]
```
Теперь добавьте в файл users/urls.py адрес страницы регистрации пользователей:
```python
from django.urls import path
from . import views

urlpatterns = [
    # path() для страницы регистрации нового пользователя
    # её полный адрес будет auth/signup/, но префикс auth/ обрабатывается в головном urls.py
    path("signup/", views.SignUp.as_view(), name="signup")
]
```

### Устройство форм в Django
Форма в Django описывается в классе, похожем на модель. Класс должен быть унаследован от встроенного класса Form:

```python
from django import forms

class ContactForm(forms.Form):
        name = forms.CharField(label="Введите имя")
        sender = forms.EmailField(label="Email для ответа")
        subject = forms.CharField(label="Тема сообщения", initial='Письмо администратору', max_length=100)
        message = forms.CharField(widget=forms.Textarea)
        cc_myself = forms.BooleanField(label="Отправить себе копию", required=False)
```
Форма состоит из полей разных типов, все они описаны в [документации](https://docs.djangoproject.com/en/2.2/ref/forms/fields/#built-in-field-classes).
Когда в шаблоне поле превращается в HTML-код, то используется виджет, определённый 
параметром widget. Виджет — это шаблон, по которому генерируется HTML-код поля формы.

Основные типы полей, которые вам будут встречаться:

 - BooleanField — соответствует типу bool. Виджет по умолчанию отрисовывает чекбокс ```<input type="checkbox">```
 - CharField — поле для ввода текста, по умолчанию используется виджет однострочного поля ввода ```<input type="text">```. 
   Виджет можно заменить: если указать в параметрах ```widget=forms.Textarea```, 
   будет отрисовано поле многострочного ввода, ```<textarea>```
 - ChoiceField — поле выбора из выпадающего списка, ```<select>```
 - EmailField — однострочное поле ввода текста, но с обязательной проверкой введённой 
   строки на соответствие формату email
 - FileField — поле для отправки файла, в шаблоне отрисует тег ```<input type="file">```. 
   Есть аналогичное поле для отправки только файлов изображений: ```ImageField```
 - IntegerField — поле для ввода чисел: ```<input type="number">```

Можно самостоятельно создавать новые типы полей и новые виджеты. В Django есть 
множество готовых виджетов, например, для превращения поля ввода в визуальный редактор.

### Работа с формами из кода

```python
>>> from django import forms
>>> class Registration(forms.Form):
...     firstname = forms.CharField(label="Введите имя", initial='Лев')
...     lastname = forms.CharField(label="Введите фамилию", initial='Толстой')
... 
>>> form = Registration()
# напечатаем результат, чтобы увидеть HTML-код, который выведет метод as_p()
>>> print(form.as_p())
<p><label for="id_firstname">Введите имя:</label> <input type="text" name="firstname" value="Лев" required id="id_firstname"></p>
<p><label for="id_lastname">Введите фамилию:</label> <input type="text" name="lastname" value="Толстой" required id="id_lastname"></p>
```
Каждый из этих методов можно вызывать из шаблона командами form.as_table , form.as_p или form.as_ul
- **as_p()** -  обрамляет каждую пару тегов «label + поле» в HTML-тег ```<p>```
- **as_table()** - форма выводится в HTML-таблицу
- **as_ul()** - Вывод списком

```python
>>> print(form.as_table())
<tr><th><label for="id_firstname">Введите имя:</label></th><td><input type="text" name="firstname" value="Лев" required id="id_firstname"></td></tr>
<tr><th><label for="id_lastname">Введите фамилию:</label></th><td><input type="text" name="lastname" value="Толстой" required id="id_lastname"></td></tr>

>>> print(form.as_ul())
<li><label for="id_firstname">Введите имя:</label> <input type="text" name="firstname" value="Лев" required id="id_firstname"></li>
<li><label for="id_lastname">Введите фамилию:</label> <input type="text" name="lastname" value="Толстой" required id="id_lastname"></li>
```

Когда форма заполнена и отправлена, Django получит данные и проверит их на корректность. 
В случае, если отправленная информация не прошла валидацию, то объект form получит 
список ошибок в атрибуте {{ form.errors }}

### Работа с полями формы	

С объектом формы можно работать через цикл for:
```python
>>> for field in form:
...     print(field)
... 
# поля формы будут напечатаны по очереди
<input type="text" name="firstname" value="Лев" required id="id_firstname">
<input type="text" name="lastname" value="Толстой" required id="id_lastname">
```
В шаблоне этот же код выглядит так:
```html
{% for field in form %}
        {{ field }}
{% endfor %}
```

### Доступ к полям формы по именам
Иногда удобно вывести в шаблон поля формы не циклом, а отдельным кодом.
В шаблоне для доступа к полю применяют точечную нотацию: ```form.field_name```

```html
<form method="post">{% csrf_token %}
        {{ form.firstname }}
        {{ form.lastname }}
        <input type="submit" value="Send message">
</form>
```
В Python-коде доступ к полям можно получить, обратившись к объекту ```form``` как к словарю, где ключом является имя поля.
```python
>>> print(form['firstname'])
<input type="text" name="firstname" value="Лев" required id="id_firstname">
```

Атрибуты полей формы
При выводе формы в шаблон доступны атрибуты объекта ```field```:
 - field.label — метка поля, параметр label из описания поля в классе: ```label="Введите имя"```
 - field.label_tag — этот атрибут формирует полный тег ```label``` для поля: ```<label for="id_firstname">Введите имя:</label>```
 - field.id_for_label — здесь хранится значение, которое в HTML-теге ```label``` указывает, 
   для какого именно поля формы создан этот ```label```. В примере ```<label for="id_firstname">Введите имя:</label>``` значением тега ```field.id_for_label``` будет ```id_firstname```
 - field.value — значение, которое ввёл пользователь
 - field.html_name — атрибут name тега ```input```
 - field.help_text — текст подсказки, который можно передать в коде
 - field.errors — этот атрибут будет заполнен, если при проверке отправленных данных произошла ошибка

Измените код шаблона users/templates/signup.html так, чтобы он соответствовал стандарту Bootstrap:

```html
{% extends "base.html" %}
{% block title %}Зарегистрироваться{% endblock %}
{% block content %}

<div class="row justify-content-center">
    <div class="col-md-8 p-5">
        <div class="card">
            <div class="card-header">Зарегистрироваться</div>
            <div class="card-body">

                    {% for error in form.errors %}
                        <div class="alert alert-danger" role="alert">
                            {{ error }}
                        </div>
                    {% endfor %}


                <form method="post" action="{% url 'signup' %}">
                    {% csrf_token %}

                    {% for field in form %}
                        <div class="form-group row" aria-required={% if field.field.required %}"true"{% else %}"false"{% endif %}>
                                <label for="{{ field.id_for_label }}" class="col-md-4 col-form-label text-md-right">{{ field.label }}{% if field.field.required %}<span class="required">*</span>{% endif %}</label>
                                <div class="col-md-6">
                                    {{ field }}
                                    {% if field.help_text %}
                                    <small id="{{ field.id_for_label }}-help" class="form-text text-muted">{{ field.help_text|safe }}</small>
                                    {% endif %}
                                </div>
                        </div>
                    {% endfor %}

                    <div class="col-md-6 offset-md-4">              
                            <button type="submit" class="btn btn-primary">
                                Зарегистрироваться
                            </button>
                    </div>
                </form>
            </div> <!-- card body -->
        </div> <!-- card -->
    </div> <!-- col -->
</div> <!-- row -->

{% endblock %}
```

### Создание фильтра

Наш код не выводит HTML-атрибута class в тегах input. Вот наш код:
```html
<div class="form-group row" aria-required="false">
        <label for="id_first_name" class="col-md-4 col-form-label text-md-right">Имя</label>
        <div class="col-md-6">
            <input type="text" name="first_name" maxlength="30" id="id_first_name"> 
        </div>
</div>
```
А вот код, который должен быть:
```html
<div class="form-group row" aria-required="false">
        <label for="id_first_name" class="col-md-4 col-form-label text-md-right">Имя</label>
        <div class="col-md-6">
            <input type="text" class="form-control" name="first_name" maxlength="30" id="id_first_name"> 
        </div>
</div>
```

Создадим собственный фильтр для Django-шаблонов.
Создайте папку users/templatetags, а в ней — два пустых файла: __init__.py и user_filters.py.

Фильтр даст нам возможность указывать CSS-класс в HTML-коде любого поля формы.
У объекта field есть метод as_widget(). Ему можно передать параметр с перечнем HTML-атрибутов, которые мы хотим изменить.
Финальный код фильтра будет выглядеть так:

```python
from django import template
# В template.Library зарегистрированы все теги и фильтры шаблонов
# добавляем к ним и наш фильтр
register = template.Library()


@register.filter 
def addclass(field, css):
        return field.as_widget(attrs={"class": css})

# синтаксис @register... , под которой описана функция addclass() - 
# это применение "декораторов", функций, обрабатывающих функции
# мы скоро про них расскажем. Не бойтесь соб@к
```
Теперь в коде шаблона можно указать фильтр addclass с параметром 
form-control: ```{{ field|addclass:"form-control" }}```.

Чтобы фильтр был доступен в шаблоне — предварительно загрузите его в шаблон тегом {% load user_filters %}.
Финальный код шаблона формы регистрации будет выглядеть так:
```html
{% extends "base.html" %}
{% block title %}Зарегистрироваться{% endblock %}
{% block content %}
{# загружаем фильтр #}
{% load user_filters %}

<div class="row justify-content-center">
    <div class="col-md-8 p-5">
        <div class="card">
            <div class="card-header">Зарегистрироваться</div>
            <div class="card-body">
                
              {% for error in form.errors %}
                  <div class="alert alert-danger" role="alert">
                      {{ error|escape }}
                  </div>
                {% endfor %}

                <form method="post" action="{% url 'signup' %}">
                    {% csrf_token %}

                    {% for field in form %}
                        <div class="form-group row" aria-required={% if field.field.required %}"true"{% else %}"false"{% endif %}>
                                <label for="{{ field.id_for_label }}" class="col-md-4 col-form-label text-md-right">{{ field.label }}{% if field.field.required %}<span class="required">*</span>{% endif %}</label>
                                <div class="col-md-6">

                                    {# подключаем фильтр и указываем класс #}
                                    {{ field|addclass:"form-control" }}

                                    {% if field.help_text %}
                                    <small id="{{ field.id_for_label }}-help" class="form-text text-muted">{{ field.help_text|safe }}</small>
                                    {% endif %}
                                </div>                
                        </div>
                    {% endfor %}

                    <div class="col-md-6 offset-md-4">              
                            <button type="submit" class="btn btn-primary">
                                Зарегистрироваться
                            </button>
                    </div>
                </form>
            </div> <!-- card body -->
        </div> <!-- card -->
    </div> <!-- col -->
</div> <!-- row -->

{% endblock %}
```

### Шаблоны страниц входа и восстановления доступа

Мы составили список страниц, необходимых для входа, регистрации и восстановления пароля. Этот список есть в django/contrib/auth/views.py:

```python
class LoginView(SuccessURLAllowedHostsMixin, FormView):
    template_name = 'registration/login.html'
class LogoutView(SuccessURLAllowedHostsMixin, TemplateView):
    template_name = 'registration/logged_out.html'
class PasswordResetView(PasswordContextMixin, FormView):
    template_name = 'registration/password_reset_form.html'
class PasswordResetDoneView(PasswordContextMixin, TemplateView):
    template_name = 'registration/password_reset_done.html'
class PasswordResetConfirmView(PasswordContextMixin, FormView):
    template_name = 'registration/password_reset_confirm.html'
class PasswordResetCompleteView(PasswordContextMixin, TemplateView):
    template_name = 'registration/password_reset_complete.html'
class PasswordChangeView(PasswordContextMixin, FormView):
    template_name = 'registration/password_change_form.html'
class PasswordChangeDoneView(PasswordContextMixin, TemplateView):
    template_name = 'registration/password_change_done.html'
```

В папке users/templates создайте директорию registration, а в ней — файлы с перечисленными именами. 

Когда Django ищет запрошенный шаблон, то проходит по каждой директории templates 
в приложениях из списка INSTALLED_APPS, ищет там файл, чей путь и имя совпадают с template_name

 - login.html — форма входа, пользователь вводит username и пароль. После отправки 
   форма проверяется, и если пользователь с таким именем и паролем найден, то он 
   авторизуется и перенаправляется на главную страницу
 - logged_out.html — в навигации сайта мы показываем ссылку на страницу «Выйти». 
   Когда пользователь переходит на эту страницу, то он разлогинивается и ему 
   показывается прощальная страница
 - password_change_form.html — если залогиненному пользователю надо изменить пароль, 
   то на этой странице он может указать текущий пароль и ввести новый. Если пользователь 
   правильно ввёл текущий пароль и новый соответствует требованиям безопасности, то 
   показывается страница password_change_done.html.
 - password_reset_form.html — даёт восстановить доступ к сайту. С этой страницы 
   пользователь отправляет через форму свой логин или email. На почту пользователю 
   отправляется письмо со ссылкой на страницу восстановления пароля. Об отправке 
   письма уведомляет страница password_reset_done.html Пользователь переходит по 
   ссылке из письма и попадает на страницу password_reset_confirm.html. На этой 
   странице пользователь указывает новый пароль, отправляет форму и, после валидации 
   нового пароля, попадает на страницу password_reset_complete.html.

**login.html**

Добавьте код в шаблон ```users/templates/registration/login.html```

```html
{% extends "base.html" %}
{% block title %}Войти{% endblock %}
{% block content %}
{% load user_filters %}

<div class="row justify-content-center">
  <div class="col-md-8 p-5">
    <div class="card">
      <div class="card-header">Войти на сайт</div>
      <div class="card-body">
        {% if form.errors %}
        <div class="alert alert-danger" role="alert">
          Имя пользователя и пароль не совпадают. Введите правильные данные.
        </div>
        {% endif %}

        <div class="alert alert-info" role="alert">
          Пожалуйста, авторизуйтесь.
        </div>

        <form method="post" action="{% url 'login' %}">
          {% csrf_token %}
          <input type="hidden" name="next" value="{{ next }}">
          <div class="form-group row">
              <label for="{{ form.username.id_for_label }}" class="col-md-4 col-form-label text-md-right">Имя пользователя</label>
              <div class="col-md-6">
                  {{ form.username|addclass:"form-control" }}
              </div>
          </div>

          <div class="form-group row">
              <label for="{{ form.password.id_for_label }}" class="col-md-4 col-form-label text-md-right">Пароль</label>
              <div class="col-md-6">
                  {{ form.password|addclass:"form-control" }}
              </div>
          </div>

          <div class="col-md-6 offset-md-4">              
              <button type="submit" class="btn btn-primary">
                Войти
              </button>
              <a href="{% url 'password_reset' %}" class="btn btn-link">
                Забыли пароль?
              </a>
          </div>
        </form>
      </div> <!-- card body -->
    </div> <!-- card -->
  </div> <!-- col -->
</div> <!-- row -->

{% endblock %}
```
**logged_out.html**
```html
{% extends "base.html" %}
{% block title %}Вы вышли из системы{% endblock %}

{% block content %}
<div class="row justify-content-center">
  <div class="col-md-8 p-5">
    <div class="card">
      <div class="card-header">Вы вышли из системы</div>
      <div class="card-body">
        <p>Вы вышли из своей учётной записи. Ждём вас снова!</p>
      </div> <!-- card body -->
    </div> <!-- card -->
  </div> <!-- col -->
</div> <!-- row -->

{% endblock %}
```

> Остальные страницы смотри в прокте YATube
> 

Осталось объяснить Django, какие страницы надо показывать пользователю после входа в 
аккаунт и выхода из него. Добавьте в yatube/settings.py такие настройки:

```python
# Login

LOGIN_URL = "/auth/login/"
LOGIN_REDIRECT_URL = "index" 
# LOGOUT_REDIRECT_URL = "index" 
```

## Валидация форм

Научимся обрабатывать формы во view-функциях.

В самом общем случае работа с формами происходит в таком порядке:
 - Разработчик создал модель, на её основе создал форму, эту форму вывел в шаблон. 
   Можно создать форму и без модели, если хранить полученные данные не нужно.
 - Пользователь заходит на страницу с формой, заполняет её и нажимает «Отправить», 
   браузер пользователя отправляет POST-запрос с данными на URL, указанный в 
   параметре action формы.
 - На сервере данные из формы проверяются и обрабатываются во view-функции.
 - Если данные успешно прошли проверку — они передаются для дальнейшей обработки 
   и сохранения в базе, а пользователь перенаправляется на страницу с информацией 
   об успешной отправке формы.
 - Если отправленные данные не прошли проверку, пользователю отправляется 
   уведомление об ошибке.

В Django есть полная инфраструктура для работы с формами:

 - Формы Django можно связывать с объектами модели.
 - На основе моделей можно быстро, буквально несколькими строками кода, создавать новые формы.
 - Данные, полученные от пользователя, автоматически разбираются обработчиком запроса.
 - Django умеет передавать данные, полученные от пользователя, в объект формы.
 - У форм есть система валидации — проверка переданных данных. Пользователь может 
   ошибиться или раньше времени нажать кнопку «Отправить» — в этих случаях данные 
   не пройдут проверку и пользователь получит сообщение об этом.
 - Во все формы Django по умолчанию встроена защита от злонамеренной отправки данных 
   из другого источника, Cross Site Request Forgery (CSRF).
 - В Django предусмотрен набор встроенных виджетов — шаблонов, формирующих HTML-код 
   формы: поля для ввода текста ```(HTML-тег <input type="text">)```, поля многострочного 
   ввода ```<textarea>```, чекбоксы ```<input type="checkbox">```, выпадающие списки 
   ```<select>``` и множество других, стандартных и нестандартных, элементов.

Проще всего создать форму на основе существующей модели: достаточно написать класс формы, 
ссылающийся на модель.

Модель, в которой будут храниться данные формы:

**файл models.py**
```python
class Contact(models.Model):
    name = models.CharField(max_length=100)
    email = models.EmailField()
    subject = models.CharField(max_length=100)
    body = models.TextField()
    is_answered = models.BooleanField(default=False)
```

На основе этой модели создаётся **класс** формы:

**файл forms.py**
```python
from django import forms
from .models import Contact

class ContactForm(forms.ModelForm):
    class Meta:
        # на основе какой модели создаётся класс формы
        model = Contact
        # укажем, какие поля будут в форме
        fields = ('name', 'email', 'subject', 'body')
```

Теперь во view-функции можно создать **объект** формы на основе класса ```ContactForm```

**файл views.py**
```python
def user_contact(request):
    ...
    # создаём объект формы
    form = ContactForm()

    # и передаём эту форму в HTML-шаблон
    return render(request, 'contact.html', {'form': form})

```
Если в форму передать какой-то объект «родительской» модели этой формы, то в HTML-форму 
будут выведены данные этого объекта. Это работает, например, в случаях, когда вы щелкаете 
по ссылке «Отредактировать» в социальной сети или в админ-зоне сайта.

**файл views.py**

```python
def user_contact(request):
    ...
    # запрашиваем объект модели Contact
    contact = Contact.objects.get(pk=3)

    # создаём объект формы и передаём в него объект модели с pk=3
    form = ContactForm(instance=contact)

    # передаём эту форму в HTML-шаблон
    return render(request, 'contact.html', {'form': form})
```

В результате пользователь увидит на странице заполненную HTML-форму: в неё будет выведено сообщение с pk=3. Сообщение можно будет изменить и сохранить отредактированный вариант на сервере.

Данные, переданные из форм, на сервере проверяются функциями-валидаторами. Валидатор обращается к данным (или получает их в качестве аргумента) и проверяет их значение. В случае ошибки вызывается исключение ```ValidationError```. 

Валидация поля формы может быть многоэтапной. Значения, полученные после валидации каждого из полей, будут доступны в словаре ```form.cleaned_data```. Ключи в этом словаре — названия полей формы.

### Первый способ валидации: функции-валидаторы

Функции-валидаторы обычно пишут в файле *validators.py*, в них описывают условия, 
которым должны соответствовать данные из формы. Затем для полей модели или формы 
указывают параметр ```validators```, перечисляя в нём функции-валидаторы, которые 
должны проверить это поле.

Когда создаётся объект модели или формы, в функцию-валидатор передаётся значение 
нужного поля; при ошибке валидации вызывается исключение ```ValidationError```

**файл validators.py**

```python
# функция-валидатор:
def validate_not_empty(value):
    # проверка "а заполнено ли поле?"
    if value == '':
        raise forms.ValidationError(
            'А кто поле будет заполнять, Пушкин?',
            params={'value': value},
        ) 
```

**файл models.py**
```python
class Contact(models.Model):
    # к полю name подключаем валидатор, проверяющий, что поле не пустое
    name = models.CharField(max_length=100, validators=[validate_not_empty])
    email = models.EmailField()
    subject = models.CharField(max_length=100)
    # к полю body тоже подключаем валидатор, проверяющий, что поле не пустое
    body = models.TextField(validators=[validate_not_empty])
    is_answered = models.BooleanField(default=False)
```

### Второй способ валидации: метод-валидатор

В классе формы для каждого отдельного поля можно создать метод ```clean_<имя поля>```, он вызовется автоматически при создании объекта этого класса..
Этот метод не получает никаких дополнительных параметров: он самостоятельно запросит значение из словаря ```cleaned_data```.
Такой протокол создан для того, чтобы можно было совместить работу всех валидаторов. Значение, которое вернёт этот метод, обновит значение соответствующего элемента словаря ```cleaned_data```.
Для класса ```ContactForm``` напишем валидатор, который вернёт пользователю ошибку, если в поле «Тема» (Subject) нет благодарности в адрес администратора сайта.

**файл forms.py**

```python
from django import forms
from .models import Contact

class ContactForm(forms.ModelForm):
    class Meta:
        model = Contact
        fields = ('name', 'email', 'subject', 'body')
    
    # метод-валидатор для поля subject
    def clean_subject(self):
        data = self.cleaned_data['subject']

        # если пользователь не поблагодарил администратора - считаем это ошибкой
        if "спасибо" not in data.lower():
            raise forms.ValidationError("Вы обязательно должны нас поблагодарить!")

        # метод-валидатор обязательно должен вернуть очищенные данные, 
        # даже если не изменил их
        return data
```
Классам полей формы и модели тоже можно присвоить методы валидации. Например, вы можете создать поле для ввода цвета ```ColorField``` с валидацией — и валидация этого поля будет работать во всех формах, где оно применяется.

### После валидации

Форма считается валидной, если метод формы ```.is_valid()``` возвращает True.
После валидации все данные будут переданы в словарь ```form.cleaned_data```, и для дальнейшей работы с информацией из формы данные берутся именно из этого словаря.

**файл views.py**
```python
from django.shortcuts import redirect

def user_contact(request):
    # проверим, пришёл ли к нам POST-запрос или какой-то другой:
    if request.method == 'POST':
        # создаём объект формы класса ContactForm и передаём в него полученные данные
        form = ContactForm(request.POST)

        # если все данные формы валидны - работаем с "очищенными данными" формы
        if form.is_valid():
            # берём валидированные данные формы из словаря form.cleaned_data
            name = form.cleaned_data['name']
            email = form.cleaned_data['email']
            subject = form.cleaned_data['subject']
            message = form.cleaned_data['body']
            # при необходимости обрабатываем данные
            # ...
            # сохраняем объект в базу
            form.save()
            
            # Функция redirect перенаправляет пользователя 
            # на другую страницу сайта, чтобы защититься 
            # от повторного заполнения формы
            return redirect('/thank-you/')

        # если условие if form.is_valid() ложно и данные не прошли валидацию - 
        # передадим полученный объект в шаблон
        # чтобы показать пользователю информацию об ошибке

        # заодно заполним прошедшими валидацию данными все поля, 
        # чтобы не заставлять пользователя вносить их повторно
        return render(request, 'contact.html', {'form': form})

    # если пришёл не POST-запрос - создаём и передаём в шаблон пустую форму
    # пусть пользователь напишет что-нибудь
    form = ContactForm()
    return render(request, 'contact.html', {'form': form})
```

### Формы без модели

Формы, содержимое которых не нужно сохранять в базе данных (например, это формы, которые отправляют электронные письма), не привязываются к моделям и наследуются от класса ```Form```. Они работают точно так же, как и ModelForm.
Отличие есть в вызове функций-валидаторов: аргумент ```validators``` указывается в описании поля формы, а не модели.

**файл validators.py**
```python
# функция-валидатор:
def validate_not_empty(value):
    if value == '':
        raise forms.ValidationError(
            'А кто поле будет заполнять, Пушкин?',
            params={'value': value},
        ) 
```

**файл forms.py**
```python
class ContactForm(forms.Form):
    name = forms.CharField(max_length=100, validators=[validate_not_empty])
    email = forms.EmailField()
    subject = forms.CharField(max_length=100)
    body = forms.TextField(validators=[validate_not_empty])
    is_answered = forms.BooleanField(default=False)
```

### Пример файлов для модели и формы с валидацией

Cайт коллекционера компакт-дисков: создайте форму связи, через которую посетитель 
может предложить свой CD на обмен владельцу сайта.

**models.py**
```python
from django.db import models

# Create your models here.
GENRE_CHOICES = (
    ("R", "Рок"),
    ("E", "Электроника"),
    ("P", "Поп"),
    ("C", "Классика"),
    ("O", "Саундтреки"),
)


class CD(models.Model):
    title = models.CharField(max_length=100)
    description = models.TextField(null=True, blank=True)
    artist = models.CharField(max_length=40)
    genre = models.CharField(max_length=1, choices=GENRE_CHOICES)

    def __repr__(self):
        return "Вот я такой кросавчик"
```

**forms.py**
```python
from django import forms
from .models import CD, GENRE_CHOICES


class ExchangeForm(forms.Form):
    name = forms.CharField(max_length=100)
    email = forms.EmailField()
    title = forms.CharField(max_length=100)
    artist = forms.CharField(max_length=40)
    genre = forms.ChoiceField(choices=GENRE_CHOICES)
    price = forms.DecimalField(required=False)
    comment = forms.CharField(widget=forms.Textarea, required=False)
    
    def clean_artist(self):
        data = self.cleaned_data["artist"]
        if not CD.objects.filter(artist=data).exists():
            raise forms.ValidationError("Jkjkj")
        return data 
```

**urls.py**
```python
from django.urls import path
from . import views

urlpatterns = [
    path("", views.index, name="index"),
    path("thank-you/", views.thx, name="thankyou")
]
```

**views.py**
```python
from django.shortcuts import redirect, render
from django.core.mail import send_mail
from .forms import ExchangeForm


def send_msg(email, name, title, artist, genre, price, comment):
    subject = f"Обмен {artist}-{title}"
    body = f"""Предложение на обмен диска от {name} ({email})
    Название: {title}
    Исполнитель: {artist}
    Жанр: {genre}
    Стоимость: {price}
    Комментарий: {comment}
    """
    send_mail(
        subject, body, email, ["admin@rockenrolla.net", ],
    )
    
def index(request):
    # После заполнения формы показывайте шаблон "thankyou.html"
    if request.method == 'POST':
        form = ExchangeForm(request.POST)
        if form.is_valid():
            send_msg(form['email'],
                     form['name'],
                     form['title'],
                     form['artist'],
                     form['genre'],
                     form['price'],
                     form['comment'],
                    )
            return redirect("/thank-you/")
        return render(request, "index.html", {'form': form})
    return render(request, "index.html", {"form": ExchangeForm()})

def thx(request):
    return render(request, "thankyou.html")
```

**index.html**
```html
<!DOCTYPE html>
<!-- Based on https://getbootstrap.com/docs/4.4/examples/pricing/ -->
<html lang="ru">
  <head>
    <meta charset="utf-8" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1, shrink-to-fit=no"
    />
    <title>Уголок рокнрольщика</title>

    <!-- Bootstrap core CSS -->
    <link
      rel="stylesheet"
      href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css"
      integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh"
      crossorigin="anonymous"
    />
  </head>

  <body>
  <h1>Предложение обмена</h1>
  <p class="lead">
    Предложите мне свой диск на обмен.
  </p>

  <form method="post">
    {% csrf_token %}
    {% for field in form %}
        <div>
            {{ field.label }}
            <div>{{ field }} </div>
            {{ field.errors }}
        </div>
    {% endfor %}
    <div>
        <button type="submit">
            Предложить
        </button>
    </div>
</form>

  </body>
</html>

```

**thankyou.html**
```html
<!DOCTYPE html>
<!-- Based on https://getbootstrap.com/docs/4.4/examples/pricing/ -->
<html lang="ru">
  <head>
    <meta charset="utf-8" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1, shrink-to-fit=no"
    />
    <title>Уголок рокнрольщика</title>

    <!-- Bootstrap core CSS -->
    <link
      rel="stylesheet"
      href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css"
      integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh"
      crossorigin="anonymous"
    />
  </head>

  <body>
  <div class="container">
    <h1>Спасибо</h1>
    <p class="lead">
      Обязательно отвечу на предложение в ближайшее время.
    </p>
  </div>

  </body>
</html>

```

## Юнит-тесты в Django

[Документация по тестам Django](https://docs.djangoproject.com/en/dev/topics/testing/)

При выполнении команды «создать новое приложение» ```python manage.py startapp <app_name>``` 
в директории приложения автоматически создается файл для тестов  tests.py:

```
└── <app_name>
    ├── __init.py__ 
    ├── admin.py
    ├── models.py
    ├── tests.py   # Место для тестов     
    └── views.py     
```
Лучше делать так:
 - Удалить файл ```tests.py```
 - Создать в директории приложения **пакет** *tests*: создать директорию /tests 
   и разместить в нём пустой файл ```__init__.py```
 - В этом пакете создать отдельные файлы для тестов: файл для тестирования моделей, 
   файл для views, файл для форм, файл для проверки URL.

```
└── <app_name>
    ├── __init__.py
    ├── tests
    │   ├── __init__.py  
    │   ├── test_models.py  # Тесты моделей
    │   ├── test_urls.py    # Тесты адресов     
    │   ├── test_forms.py   # Тесты форм 
    │   └── test_views.py   # Тесты представлений
    ├── admin.py
    ├── models.py
    └── views.py 
```
Перед началом работы в код файлов с тестами импортируется класс TestCase из пакета django.test. Все классы тестов должны наследоваться от него.

```python
# Каждый логический набор тестов — это класс, 
# который наследуется от базового класса TestCase
from django.test import TestCase


class Test(TestCase):
    def test_example(self):
    # пишем тест тут
    ...
```

### Smoke testing

«Дымовое тестирование» в Django выглядит так: проверяем, что главная страница доступна (возвращает статус 200).
Проверку статуса страницы проводят через программный HTTP-клиент, имитирующий работу браузера.
При программном тестировании в Django можно эмулировать браузер (веб-клиент) прямо в коде — и тестировать проект через него.

Этот программный клиент может:
 - имитировать GET- и POST-запросы, проверять заголовки ответов и содержимое страниц;
 - работать под авторизованным или неавторизованным пользователем;
 - отслеживать редиректы и проверять URL и код статуса при каждом редиректе;
 - проверять, какие HTML-шаблоны применяются для рендера запрошенной страницы и что передаётся в словаре context;

Для создания программного клиента в модуле ```django.test``` есть класс ```Client()```. Каждый экземпляр этого класса — это отдельный веб-клиент, которым можно управлять из кода.
При тестировании можно создать несколько таких клиентов: в одном можно авторизоваться, а из другого клиента работать без авторизации, тестируя сценарии для анонимных пользователей.

### Запрос к проекту через Client()

Для начала разрешите своему проекту принимать запросы от тестового сервера: в настройках проекта ```yatube/settings.py``` измените значение ключа ```ALLOWED_HOSTS```:

```python
ALLOWED_HOSTS = [
    "localhost",
    "127.0.0.1",
    "[::1]",
    "testserver",
]
```
Запустите виртуальное окружение проекта; после этого активируйте Django Python shell (интерактивный режим Django): ```$ python3 manage.py shell```

```python
(venv) $ python manage.py shell
Python 3.8.0 (default, Nov 22 2020, 23:37:58) 
[Clang 11.0.0 (clang-1100.0.33.12)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
(InteractiveConsole)
>>> from django.test import Client

# Создаём объект класса Client(), эмулятор веб-браузера
>>> guest_client = Client()

# — Браузер, сделай GET-запрос к главной странице
>>> response = guest_client.get('/')

# Какой код вернула страница при запросе?
>>> response.status_code
200  # Страница работает: она вернула код 200
```

**Объект response: ответ на запрос**

При запросе клиента возвращается специальный объект response. В нём содержится ответ сервера и дополнительная информация:
 - status_code — содержит код ответа запрошенного адреса;
 - client — объект клиента, который использовался для обращения;
 - content — данные ответа в виде строки байтов;
 - context — словарь переменных, переданный для отрисовки шаблона при вызове функции ```render()```;
 - request — объект ```request```, первый параметр view-функции, обработавшей запрос;
 - templates — перечень шаблонов, вызванных для отрисовки запрошенной страницы;
 - resolver_match — специальный объект, соответствующий ```path()``` из списка ```urlpatterns```.

**Время настоящих тестов**

В проекте Yatube в файл posts/tests/test_urls.py добавьте код тестирующего класса:

```python
# posts/tests/test_urls.py
from django.test import TestCase, Client


class StaticURLTests(TestCase):
    def test_homepage(self):
        # Создаем экземпляр клиента
        guest_client = Client()
        # Делаем запрос к главной странице и проверяем статус
        response = guest_client.get('/')
        # Утверждаем, что для прохождения теста код должен быть равен 200
        self.assertEqual(response.status_code, 200)
```
Запустите тест командой ```python3 manage.py test -v 3```

### Выборочный запуск тестов

Иногда нет необходимости выполнять все тесты проекта, а нужно запустить только определённую группу или лишь один тест. Для такого выборочного запуска можно через точечную нотацию указать путь к нужному пакету, модулю, тестирующему классу или методу:

```bash
# Запустит все тесты проекта
python3 manage.py test

# Запустит только тесты в приложении posts
python3 manage.py test posts

# Запустит только тесты из файла test_urls.py в приложении posts
python3 manage.py test posts.tests.test_urls

# Запустит только тесты из класса StaticURLTests для test_urls.py в приложении posts  
python3 manage.py test posts.tests.test_urls.StaticURLTests

# Запустит только тест test_homepage()
# из класса StaticURLTests для test_urls.py в приложении posts 
python3 manage.py test posts.tests.test_urls.StaticURLTests.test_homepage
```

### Фикстуры

Как и в Unittest для Python, в django.test можно предустановить фикстуры, исходные 
данные для тестирования. Для этого применяются те же методы, что и в Unittest: ```setUp()``` и ```setUpClass()```.

В проведённом тесте клиент был создан прямо в методе ```test_homepage()```. Если это 
единственный тест в классе — никаких проблем нет. Но когда будет пять-десять тестов 
в классе — гораздо удобнее один раз создать клиент (а лучше — два: авторизованный 
и неавторизованный), и затем в работать с ними в тестах.

### Установка Coverage

[Документация Coverage](https://coverage.readthedocs.io/en/latest/index.html)

```pip3 install coverage```

Перейдите в рабочую директорию проекта (где хранится manage.py) и запустите 
coverage: выполните ```$ coverage run --source='posts,users' manage.py test -v 2```

 - Для получения большей детализации установите для параметра ```verbosity``` значение 2.
 - Параметр ```-source='posts,users'``` (без пробела около запятой) ограничит проверку 
   coverage модулями posts и users.
 - Параметр ```--source='.'``` запустит проверку coverage всех модулей в текущей 
   директории (символ «точка» означает текущую директорию) и в её субдиректориях.
 - Если параметр ```--source``` не указывать — будет проверено покрытие тестами 
   всех модулей проекта, включая /venv. В результате в отчёт будет выведена масса 
   ненужной информации. Лучше явно указывать в параметре --source те модули или 
   директории, которые нужно проверить.

После выполнения команды coverage сформирует отчёт и сохранит его в корневой папке 
проекта, в файле .coverage.

Cам по себе файл .coverage непригоден для чтения и анализа человеком, зато из него 
можно получить отчёты в разных форматах.

Команда ```coverage report``` cамый простой способ вывести результаты в консоль. 

Все команды отображения работают с созданным отчётом .coverage. После нового 
запуска ```$ coverage run``` этот отчёт будет перезаписан.

### Unittest в Django. Models

При тестировании проекта (и, в частности, моделей) бывает необходимо записывать и 
считывать данные из базы. Чтобы не замусоривать базу данных тестовыми записями, при 
тестировании создаётся виртуальная база: её структура полностью повторяет структуру 
реальной базы Django-проекта, однако никаких данных в этой базе нет: ни постов, ни
пользователей — ничего. Все данные в этой временной базе нужно создавать в процессе 
тестирования. Запросы при тестировании делаются именно к ней, основная база не 
затрагивается. По окончании тестирования виртуальная база автоматически удаляется.

Пример теста модели: 
```python
# deals/tests/tests_models.py
from django.test import TestCase
from deals.models import Task


class TaskModelTest(TestCase):
    @classmethod
    def setUpClass(cls):
        super().setUpClass()
        # Создаём тестовую запись в БД
        # и сохраняем ее в качестве переменной класса                
        cls.task = Task.objects.create(
            title='Заголовок тестовой задачи',
            text='Тестовый текст',
            slug='test-task'
        )

    def test_title_label(self):
        """verbose_name поля title совпадает с ожидаемым."""
        task = TaskModelTest.task
        # Получаем из свойста класса Task значение verbose_name для title
        verbose = task._meta.get_field('title').verbose_name
        self.assertEquals(verbose, 'Заголовок')

    def test_title_help_text(self):
        """help_text поля title совпадает с ожидаемым."""
        task = TaskModelTest.task
        # Получаем из свойста класса Task значение help_text для title
        help_text = task._meta.get_field('title').help_text
        self.assertEquals(help_text, 'Дайте короткое название задаче')

    # Аналогичным образом можно протестировать мета полей text, slug, image  

    def test_object_name_is_title_field(self):
        """__str__  task - это строчка с содержимым task.title."""
        task = TaskModelTest.task
        expected_object_name = task.title
        self.assertEquals(expected_object_name, str(task))
```
Получить поле verbose_name напрямую, через ```task.title.verbose_name```, не получится. 
Ведь поле ```task.title``` содержит только строку "Заголовок тестовой задачи".

Для доступа до ```verbose_name``` есть другой синтаксис
```python
task._meta.get_field('title').verbose_name 
```
Таким же образом можно получить другие параметры, задаваемые при создании поля.

Если в тестах Django вы применяете методы класса ```setUpClass()``` и 
```tearDownClass()``` — обязательно вызывайте в них super(): ```super().setUpClass()``` и ```super().tearDownClass()```.

Без вызова ```super()``` все тесты сработают нормально, но вы получите ошибку:
```bash
AttributeError: type object '<имя_класса>' has no attribute 'cls_atomics'
```
Обратите внимание, что к объектам, созданным в методах класса (таких как ```setUpClass()```), 
синтаксически правильно обращаться через имя класса, а не через self.
 - Правильно: ```StaticURLTests.guest_client.get(...)```
 - Неправильно: ```self.guest_client.get(...)``` (так тоже будет работать, но возможны неприятные сюрпризы).

Проверять ```field_label``` лучше через метод ```assertEquals(field_label, 'Заголовок')```, 
а не через  ```assertTrue(field_label == 'Заголовок')```. Разница в том, что в случае 
провала теста при тестировании через ```assertTrue()``` в отчёте будет просто сказано, 
что тест провален, а при ```assertEquals()``` в консоли будет указано и актуальное значение ```field_label```. Это облегчит задачу по отладке кода.

#### Циклом по тестам: стандартный метод subTest()

Тестирование каждого поля модели может превратиться в ад: в большом проекте для 
этого придётся писать очень много похожих тестов.

В подобных ситуациях принято использовать метод subTest. Вместо написания большого 
количества однотипных тестов можно собрать все проверки и ожидаемые результаты в 
словарь — и пройти по ним циклом. Очень удобно. Много интересного о subTest можно 
узнать [в официальной документации](https://docs.python.org/3/library/unittest.html?highlight=subtest#distinguishing-test-iterations-using-subtests).

Проверка ```verbose_name``` и ```help_text``` для нескольких полей будет выглядеть так:
```python
# deals/tests/tests_models.py
from django.test import TestCase
from deals.models import Task


class TaskModelTest(TestCase):
    @classmethod
    def setUpClass(cls):
        super().setUpClass()
        # Создаём тестовую запись в БД
        # и сохраняем ее в качестве переменной класса                
        cls.task = Task.objects.create(
            title='Заголовок тестовой задачи',
            text='Тестовый текст',
            slug='test-task'
        )

    def test_verbose_name(self):
        """verbose_name в полях совпадает с ожидаемым."""
        task = TaskModelTest.task
        field_verboses = {
            'title': 'Заголовок',
            'text': 'Текст',
            'slug': 'Слаг',
            'image': 'Картинка',
        }
        for value, expected in field_verboses.items():
            with self.subTest(value=value):
                self.assertEqual(
                    task._meta.get_field(value).verbose_name, expected)

    def test_help_text(self):
        """help_text в полях совпадает с ожидаемым."""
        task = TaskModelTest.task
        field_help_texts = {
            'title': 'Дайте короткое название задаче',
            'text': 'Опишите суть задачи',
            'slug': ('Укажите адрес для страницы задачи. Используйте '
                     'только латиницу, цифры, дефисы и знаки '
                     'подчёркивания'),
            'image': 'Загрузите картинку',
        }
        for value, expected in field_help_texts.items():
            with self.subTest(value=value):
                self.assertEqual(
                    task._meta.get_field(value).help_text, expected)
...
```

####  Что в моделях нужно тестировать обязательно

В обязательном порядке тестами должен быть покрыт весь код, который вы написали сами:
 - валидации полей моделей,
 - методы по работе с моделями,
и всё, что может сломать логику работы программы.

В приложении deals обязательно нужно проверить, что при автоматическом создании 
содержимого поля slug из title текст будет правильно преобразован, а его длина будет 
не больше ста символов.

При тестировании лучше использовать данные, похожие на настоящие. Например, для 
тестирования метода ```save()``` лучше создать объект, в котором поле ```title``` будет заполнено кириллицей.

```python
# deals/tests/tests_models.py
from django.test import TestCase
from deals.models import Task


class TaskModelTest(TestCase):
    @classmethod
    def setUpClass(cls):
        super().setUpClass()
        # Создаём тестовую запись в БД
                # и сохраняем ее в качестве переменной класса                
        # Не указываем значение slug, ждем, что при создании
        # оно создастся автоматически из title.
        # А title сделаем таким, чтобы после транслитерации он стал более 
        # 100 символов 
        # (буква "ж" транслитерируется в два символа: "zh")
        # Создаём тестовую запись в БД
        # 
        cls.task = Task.objects.create(
            title='ж'*100,
            text='Тестовый текст' 
        )

    def test_text_convert_to_slug(self):
        """save преобразует в slug содержимое поля title."""
        task = TaskModelTest.task
        slug = task.slug
        self.assertEquals(slug, 'zh'*50)

    def test_text_slug_max_length_not_exceed(self):
        """Длинный slug обрезается и не больше slug max_length."""
        task = TaskModelTest.task
        max_length_slug = task._meta.get_field('slug').max_length
        length_slug = len(task.slug)
        self.assertEquals(max_length_slug, length_slug)

```

Теперь любое изменение в классе Task, затрагивающее verbose_name или max_length у 
полей title или slug, обрушит тесты. Если нужно внести изменения — сначала надо будет 
исправить тесты под новые требования, как и положено в Test-driven Development.

### Unittest в Django. Urls 

Что тестировать в test_urls.py?
 - Страницы доступны по ожидаемому адресу.
 - Для страницы вызывается ожидаемый HTML-шаблон.
 - Если у пользователя нет прав для просмотра страниц — они недоступны; происходит переадресация на ожидаемую целевую страницу.

#### Тестирование static_pages

Код приложения: 
```python
# static_pages/urls.py
from django.urls import path

from .views import About


app_name = 'static_pages'

urlpatterns = [
    path('about/', About.as_view(), name='about'),
]
```
Cтраницы в static_pages доступны любому пользователю. Единственное, что можно проверить 
при тестировании URL в этом приложении — это утверждение, что страница ```/about/``` доступна 
по ожидаемому адресу.
```python
# static_pages/tests/test_urls.py
from django.test import TestCase, Client


class StaticPagesURLTests(TestCase):
    def setUp(self):
        # Создаем неавторизованый клиент
        self.guest_client = Client()

    def test_about_url_exists_at_desired_location(self):
        """Проверка доступности адреса /page/about/."""
        response = self.guest_client.get('/page/about/')
        self.assertEqual(response.status_code, 200)

    def test_about_url_uses_correct_template(self):
        """Проверка шаблона для адреса /page/about/."""
        response = self.guest_client.get('/page/about/')
        self.assertTemplateUsed(response, 'static_pages/about.html')
```
В тесте создан клиент, через него сделано обращение к странице и проведена проверка, 
что при ответе возвращается код 200. Разумеется, если статических страниц будет больше одной, 
для их проверки хорошей идеей будет использовать **subTests**.

#### Тесты приложения deals

В проекте Todo создать новую задачу может любой посетитель, а просмотр списка задач и 
подробного описания каждой задачи доступно только авторизованным пользователям. Этими 
страницами управляет приложение deals. В нём нужно протестировать:
 - доступность всех URL приложения для авторизованного пользователя;
 - недоступность страниц ```/task/``` (список задач) и ```/task/<slug:slug>/``` 
   (полное описание отдельной задачи) для неавторизованного пользователя;
 - перенаправление неавторизованного пользователя на страницу логина при 
   попытке зайти на страницы ```/task/``` и ```/task/<slug:slug>/```.
```python
# deals/urls.py
from django.urls import path

from .views import Home, TaskList, TaskDetail, TaskAddSuccess

app_name = 'deals'

urlpatterns = [
    path('', Home.as_view(), name='home'),
    path('added/', TaskAddSuccess.as_view(), name='task_added'),
    path('task/', TaskList.as_view(), name='task_list'),
    path('task/<slug:slug>/', TaskDetail.as_view(), name='task_detail'),    
]
```

#### Тестирование общедоступных страниц
Для начала через неавторизованный клиент протестируем доступность домашней страницы и страницы с сообщением об отправке формы.
Первым делом — фикстуры в методе ```setUp()```:
```python
from django.test import TestCase, Client


class TaskURLTests(TestCase):
    def setUp(self):
        # Создаем неавторизованный клиент
        self.guest_client = Client()        

    # Проверяем общедоступные страницы
    def test_home_url_exists_at_desired_location(self):
        """Страница / доступна любому пользователю."""
        response = self.guest_client.get('/')
        self.assertEqual(response.status_code, 200)

    def test_task_added_url_exists_at_desired_location(self):
        """Страница /added/ доступна любому пользователю."""
        response = self.guest_client.get('/added/')
        self.assertEqual(response.status_code, 200)
```
#### Тесты доступности страниц для авторизованного пользователя и редиректов для неавторизованного
Для тестирования страниц ```task/``` (полный список задач) и ```task/<slug:slug>/``` 
(детальная информация об отдельной задаче) надо провести подготовку:
 - создать запись в модели Task, в результате в проекте появится страница с описанием задачи task/<slug:slug>/;
 - создать запись в модели User — чтобы авторизовать клиент;
 - создать веб-клиент с авторизованным пользователем.
```python
from django.contrib.auth import get_user_model
from django.test import TestCase, Client

from deals.models import Task

User = get_user_model()


class TaskURLTests(TestCase):
    @classmethod
    def setUpClass(cls):
        super().setUpClass()
        # Создадим запись в БД для проверки доступности адреса task/test-slug/
        Task.objects.create(
            title='Тестовый заголовок',
            text='Тестовый текст',
            slug='test-slug'
        )

    def setUp(self):
        # Создаем неавторизованный клиент
        self.guest_client = Client()
        # Создаем пользователя
        self.user = User.objects.create_user(username='AndreyG')
        # Создаем второй клиент
        self.authorized_client = Client()
        # Авторизуем пользователя
        self.authorized_client.force_login(self.user)

    def test_home_url_exists_at_desired_location(self):
        """Страница / доступна любому пользователю."""
        response = self.guest_client.get('/')
        self.assertEqual(response.status_code, 200)

    def test_task_added_url_exists_at_desired_location(self):
        """Страница /added/ доступна любому пользователю."""
        response = self.guest_client.get('/added/')
        self.assertEqual(response.status_code, 200)

    # Проверяем доступность страниц для авторизованного пользователя
    def test_task_list_url_exists_at_desired_location(self):
        """Страница /task/ доступна авторизованному пользователю."""
        response = self.authorized_client.get('/task/')
        self.assertEqual(response.status_code, 200)

    def test_task_detail_url_exists_at_desired_location_authorized(self):
        """Страница /task/test-slug/ доступна авторизованному
        пользователю."""
        response = self.authorized_client.get('/task/test-slug/')
        self.assertEqual(response.status_code, 200)

    # Проверяем редиректы для неавторизованного пользователя
    def test_task_list_url_redirect_anonymous(self):
        """Страница /task/ перенаправляет анонимного пользователя."""
        response = self.guest_client.get('/task/')
        self.assertEqual(response.status_code, 302)

    def test_task_detail_url_redirect_anonymous(self):
        """Страница /task/test-slug/ перенаправляет анонимного
        пользователя.
        """
        response = self.guest_client.get('/task/test-slug/')
        self.assertEqual(response.status_code, 302)
    
```
В Django можно проверить предположение, что с определённого адреса происходит редирект 
на другую страницу: метод assertRedirects позволяет одновременно протестировать
 - статус ответа запрошенной страницы;
 - статус ответа страницы, на которую ожидается редирект.

В функциях ```test_task_detail_url_redirect_anonymous()``` и ```test_task_list_url_redirect_anonymous()``` 
вместо метода ```assertEqual``` лучше применить ```assertRedirects```:
```python
    # Проверяем редиректы для неавторизованного пользователя
    def test_task_list_url_redirect_anonymous_on_admin_login(self):
        """Страница по адресу /task/ перенаправит анонимного
        пользователя на страницу логина.
        """
        response = self.guest_client.get('/task/', follow=True)
        self.assertRedirects(
            response, '/admin/login/?next=/task/')

    def test_task_detail_url_redirect_anonymous_on_admin_login(self):
        """Страница по адресу /task/test-slug/ перенаправит анонимного
        пользователя на страницу логина.
        """
        response = self.guest_client.get('/task/test-slug/', follow=True)
        self.assertRedirects(
            response, ('/admin/login/?next=/task/test-slug/'))
```

#### Проверка имён вызываемых HTML-шаблонов

```python
from django.contrib.auth import get_user_model
from django.test import TestCase, Client

from deals.models import Task

User = get_user_model()


class TaskURLTests(TestCase):
    @classmethod
    def setUpClass(cls):
        super().setUpClass()
        # Создадим запись в БД для проверки доступности 
        # адреса task/test-slug/
        Task.objects.create(
            title='Тестовый заголовок',
            text='Тестовый текст',
            slug='test-slug'
        )

    def setUp(self):
        # Создаем неавторизованный клиент
        self.guest_client = Client()
        # Создаем пользователя
        self.user = User.objects.create_user(username='AndreyG')
        # Создаем второй клиент
        self.authorized_client = Client()
        # Авторизуем пользователя
        self.authorized_client.force_login(self.user)

    # Проверка вызываемых шаблонов для каждого адреса
    def test_home_url_uses_correct_template(self):
        """Страница по адресу / использует шаблон deals/home.html."""
        response = self.authorized_client.get('/')
        self.assertTemplateUsed(response, 'deals/home.html')

    def test_added_url_uses_correct_template(self):
        """Страница /added/ использует шаблон deals/added.html."""
        response = self.authorized_client.get('/added/')
        self.assertTemplateUsed(response, 'deals/added.html')

    def test_task_list_url_uses_correct_template(self):
        """Страница /task/ использует шаблон deals/task_list.html"""
        response = self.authorized_client.get('/task/')
        self.assertTemplateUsed(response, 'deals/task_list.html')

    def test_task_detail_url_uses_correct_template(self):
        """Страница /task/test-slug/ использует
        шаблон deals/task_detail.html.
        """
        response = self.authorized_client.get('/task/test-slug/')
        self.assertTemplateUsed(response, 'deals/task_detail.html')
```

Опять получилось слишком много однородных тестов. Через subTest() будет лаконичнее и удобнее:
```python
from django.contrib.auth import get_user_model
from django.test import TestCase, Client

from deals.models import Task

User = get_user_model()


class TaskURLTests(TestCase):
    @classmethod
    def setUpClass(cls):
        super().setUpClass()
        # Создадим запись в БД для проверки доступности 
        # адреса task/test-slug/
        Task.objects.create(
            title='Тестовый заголовок',
            text='Тестовый текст',
            slug='test-slug'
        )

    def setUp(self):
        # Создаем неавторизованный клиент
        self.guest_client = Client()
        # Создаем пользователя
        self.user = User.objects.create_user(username='AndreyG')
        # Создаем второй клиент
        self.authorized_client = Client()
        # Авторизуем пользователя
        self.authorized_client.force_login(self.user)
    
    def test_urls_uses_correct_template(self):
        """URL-адрес использует соответствующий шаблон."""
                # Шаблоны по адресам
        templates_url_names = {
            'deals/home.html': '/',
            'deals/added.html': '/added/',
            'deals/task_list.html': '/task/',
            'deals/task_detail.html': '/task/test-slug/',
        }
        for template, reverse_name in templates_url_names.items():
            with self.subTest():
                response = self.authorized_client.get(reverse_name)
                self.assertTemplateUsed(response, template)
```

###Unittest в Django. Views

В приложении deals есть четыре view-класса. Нужно удостовериться, что в каждом из этих классов:
 - при обращении к определённому имени (указанному в path() в аргументе name) для отображения страниц вызывается ожидаемый HTML-шаблон;
 - в шаблон передан правильный контекст.

#### Проверка 1: view-классы используют ожидаемые HTML-шаблоны

Обратиться из кода к адресам приложения по имени name можно через метод ```reverse()```:
```python
self.client.get(reverse('имя_приложения:name'))
```
Для тестирования страницы ```deals:task_detail``` нужно создать запись в базе данных. 
Все остальные страницы проекта можно тестировать без предварительной подготовки. 
Дальше всё просто: берём все страницы по очереди и тестируем. Чтобы проверить, какой 
шаблон использует view-класс или view-функция, в ```django.test``` есть утверждение ```assertTemplateUsed```:
```python
#deals/tests/test_views.py
from django.contrib.auth import get_user_model
from django.test import Client, TestCase
from django.urls import reverse

from deals.models import Task

User = get_user_model()


class TaskPagesTests(TestCase):
    @classmethod
    def setUpClass(cls):
        super().setUpClass()
        # Создадим запись в БД:
        # она понадобится для тестирования страницы deals:task_detail
        Task.objects.create(
            title='Заголовок',
            text='Текст',
            slug='test-slug',
        )

    def setUp(self):
        # Создаем авторизованный клиент        
        self.user = User.objects.create_user(username='StasBasov')
        self.authorized_client = Client()
        self.authorized_client.force_login(self.user)

    def test_added_page_uses_correct_template(self):
        """URL-адрес использует шаблон deals/added.html."""
        response = self.authorized_client.get(reverse('deals:task_added'))
        self.assertTemplateUsed(response, 'deals/added.html')

    def test_home_page_uses_correct_template(self):
        """URL-адрес использует шаблон deals/home.html."""
        response = self.authorized_client.get(reverse('deals:home'))
        self.assertTemplateUsed(response, 'deals/home.html')

    def test_task_list_page_authorized_uses_correct_template(self):
        """URL-адрес использует шаблон deals/task_list.html."""
        response = self.authorized_client.get(reverse('deals:task_list'))
        self.assertTemplateUsed(response, 'deals/task_list.html')

    def test_task_detail_pages_authorized_use_correct_template(self):
        """URL-адреса используют шаблон deals/task_detail.html."""
        response = self.authorized_client.get(
            reverse('deals:task_detail', kwargs={'slug': 'test-slug'})
        )
        self.assertTemplateUsed(response, 'deals/task_detail.html')
```

Четыре теста проверяют код по одинаковому алгоритму. Разумеется, такие тесты можно 
написать лаконичнее, через ```subTest```:
```python
#deals/tests/test_views.py
from django.contrib.auth import get_user_model
from django.test import Client, TestCase
from django.urls import reverse

from deals.models import Task

User = get_user_model()


class TaskPagesTests(TestCase):
    @classmethod
    def setUpClass(cls):
        super().setUpClass()
        # Создадим запись в БД
        Task.objects.create(
            title='Заголовок',
            text='Текст',
            slug='test-slug',
        )

    def setUp(self):
        # Создаем авторизованный клиент        
        self.user = User.objects.create_user(username='StasBasov')
        self.authorized_client = Client()
        self.authorized_client.force_login(self.user)

    # Проверяем используемые шаблоны
    def test_pages_use_correct_template(self):
        """URL-адрес использует соответствующий шаблон."""
        # Собираем в словарь пары "имя_html_шаблона: name"
        templates_pages_names = {
            'deals/home.html': reverse('deals:home'),
            'deals/added.html': reverse('deals:task_added'),
            'deals/task_list.html': reverse('deals:task_list'),
            'deals/task_detail.html': (
                reverse('deals:task_detail', kwargs={'slug': 'test-slug'})
            ),
        }
        # Проверяем, что при обращении к name вызывается 
        # соответствующий HTML-шаблон
        for template, reverse_name in templates_pages_names.items():
            with self.subTest(reverse_name=reverse_name):
                response = self.authorized_client.get(reverse_name)
                self.assertTemplateUsed(response, template)
```

#### Проверка 2: в шаблон передан правильный контекст
При создании страницы в неё передаётся словарь с контекстом. При обращении к странице 
можно получить этот словарь из свойства ```context``` объекта ```response```, после 
чего проверить содержимое полей словаря ```response.context``` на совпадение с ожидаемым результатом.
```python
#deals/tests/test_views.py
from django.contrib.auth import get_user_model
from django.test import Client, TestCase
from django.urls import reverse
from django import forms  

from deals.models import Task

User = get_user_model()


class TaskPagesTests(TestCase):
    @classmethod
    def setUpClass(cls):
        super().setUpClass()
        # Создадим запись в БД
        Task.objects.create(
            title='Заголовок',
            text='Текст',
            slug='test-slug',
        )

    def setUp(self): 
        # Создаем авторизованный клиент        
        self.user = User.objects.create_user(username='StasBasov')
        self.authorized_client = Client()
        self.authorized_client.force_login(self.user)

    # Проверка словаря контекста главной страницы (в нём передаётся форма)
    def test_home_page_shows_correct_context(self):
        """Шаблон home сформирован с правильным контекстом."""
        response = self.authorized_client.get(reverse('deals:home'))
        # Словарь ожидаемых типов полей формы:
        # указываем, объектами какого класса должны быть поля формы
        form_fields = {
            'title': forms.fields.CharField,
            # При создании формы поля модели типа TextField 
            # преобразуются в CharField с виджетом forms.Textarea           
            'text': forms.fields.CharField,
            'slug': forms.fields.SlugField,
            'image': forms.fields.ImageField,
        }        

        # Проверяем, что типы полей формы в словаре context 
        # соответствуют ожиданиям
        for value, expected in form_fields.items():
            with self.subTest(value=value):
                form_field = response.context['form'].fields[value]
                # Проверяет, что поле формы является экземпляром
                # указанного класса
                self.assertIsInstance(form_field, expected)

    # Проверяем, что словарь context страницы со списком задач
    # в первом элементе списка object_list содержит ожидаемые значения 
    def test_task_list_page_shows_correct_context(self):
        """Шаблон task_list сформирован с правильным контекстом."""
        response = self.authorized_client.get(reverse('deals:task_list'))
        # Взяли первый элемент из списка и проверили, что его содержание
        # совпадает с ожидаемым
        first_object = response.context['object_list'][0]
        task_title_0 = first_object.title
        task_text_0 = first_object.text
        task_slug_0 = first_object.slug
        self.assertEqual(task_title_0, 'Заголовок')
        self.assertEqual(task_text_0, 'Текст')
        self.assertEqual(task_slug_0, 'test-slug')

    # Проверяем, что словарь context страницы task/test-slug
    # содержит ожидаемые значения 
    def test_task_detail_pages_show_correct_context(self):
        """Шаблон task_detail сформирован с правильным контекстом."""
        response = self.authorized_client.get(
                reverse('deals:task_detail', kwargs={'slug': 'test-slug'})
        )
        self.assertEqual(response.context['task'].title, 'Заголовок')
        self.assertEqual(response.context['task'].text, 'Текст')
        self.assertEqual(response.context['task'].slug, 'test-slug')
```

#### Тестирование static_pages
В проекте Todo у приложения ```static_pages``` есть лишь одна страница: ```/about/```. 
Тестирование URL и views этой страницы отличается от тестов приложения deals 
только простотой:
```python
from django.test import Client, TestCase
from django.urls import reverse


class StaticViewsTests(TestCase):
    def setUp(self):
        self.guest_client = Client()

    def test_about_page_accessible_by_name(self):
        """URL, генерируемый при помощи имени static_pages:about, доступен."""
        response = self.guest_client.get(reverse('static_pages:about'))
        self.assertEqual(response.status_code, 200)

    def test_about_page_uses_correct_template(self):
        """При запросе к staticpages:about
        применяется шаблон staticpages/about.html."""
        response = self.guest_client.get(reverse('static_pages:about'))
        self.assertTemplateUsed(response, 'static_pages/about.html')
```

### Unittest в Django. Forms

В проекте Todo форма создана на основе модели:
```python
# deals/forms.py
from django.core.exceptions import ValidationError
from django import forms
from pytils.translit import slugify

from .models import Task


class TaskCreateForm(forms.ModelForm):
    """Форма для создания задания."""
    class Meta:
        model = Task
        # Магия Джанго: через '__all__' создаётся кортеж 
        # из всех полей модели
        # labels и help_texts берутся из полей модели
        fields = '__all__'

    # Валидация поля slug
    def clean_slug(self):
        """Обрабатывает случай, если slug не уникален."""
        cleaned_data = super().clean()
        slug = cleaned_data['slug']
        if not slug:
            title = cleaned_data['title']
            slug = slugify(title)[:100]
        if Task.objects.filter(slug=slug).exists():
            raise ValidationError(f'{slug} уже существует')
        return slug
```
Метки полей формы (labels) и тексты подсказок (help_text) уже протестированы в моделях, 
второй раз их тестировать не надо. labels и help_texts лучше определять и тестировать 
в моделях, а не в формах. Обычно так и делают: это более универсальный способ. Но если 
labels и help_texts были переопределены при генерации форм — их следует проверить.

Например, в каком-то воображаемом файле forms.py форма описана так:
```python
# Воображаемый my_app/forms.py
from django import forms
from .models import Imagination

class ImaginForm(forms.ModelForm):
    class Meta:
        model = Imagination
        fields = '__all__'
        labels = {
            'title': 'Заголовок из формы',
        }

        help_texts = {
            'help_texts': 'Текст подсказки из формы',
        }
```
Проверить labels и help_text этой формы можно так:
```python
# Воображаемый my_app/tests/test_forms.py
from django.test import Client, TestCase
from my_app.forms import ImaginForm

class ImaginFormTests(TestCase):
    @classmethod
    def setUpClass(cls):
        super().setUpClass()
        cls.form = ImaginForm()

    def test_title_label(self):
        title_label = ImaginFormTests.form.fields['title'].label 
        self.assertEqual(title_label, 'Заголовок из формы')

    def test_title_help_text(self):
        title_help_text = ImaginFormTests.form.fields['title'].help_text 
        self.assertEqual(title_help_text, 'Текст подсказки из формы')
```

#### Тест стандартного поведения формы

Обычно форма работает по такому сценарию:
 - Пользователь заполняет форму и отправляет её; данные из формы уходят POST-запросом на сервер.
 - Данные проходят валидацию на сервере.
 - Если данные валидны — выполняется какое-то полезное действие: данные записываются 
   в базу, или отправляется письмо, или пользователь, отправивший данные, авторизуется на сайте.
 - В проекте Todo заполнение формы приводит к созданию новой записи в модели Task.
 - После отправки формы пользователь редиректится на страницу с сообщением об успешной отправке формы.

Имеет смысл протестировать, что
 - после успешной валидации в модели Task появится новая запись;
 - после отправки валидной формы происходит переадресация на страницу ```/added/```

Сохранение картинки можно не тестировать: это делает Django, пока что ему можно доверять.
```python
# deals/tests/tests_form.py
import shutil
import tempfile

from django.conf import settings
from django.core.files.uploadedfile import SimpleUploadedFile
from django.test import Client, TestCase
from django.urls import reverse

from deals.forms import TaskCreateForm
from deals.models import Task


class TaskCreateFormTests(TestCase):
    @classmethod
    def setUpClass(cls):
        super().setUpClass()
        # Создаем временную папку для медиа-файлов;
        # на момент теста медиа папка будет переопределена
        settings.MEDIA_ROOT = tempfile.mkdtemp(dir=settings.BASE_DIR)

        # Создаем запись в базе данных для проверки сушествующего slug
        Task.objects.create(
            title='Тестовый заголовок',
            text='Тестовый текст',
            slug='first'
        )
        # Создаем форму, если нужна проверка атрибутов
        cls.form = TaskCreateForm()

    @classmethod
    def tearDownClass(cls):
        # Модуль shutil - библиотека Python с прекрасными инструментами
        # для управления файлами и директориями:
        # создание, удаление, копирование, перемещение, изменение папок|файлов
        # Метод shutil.rmtree удаляет директорию и всё её содержимое
        shutil.rmtree(settings.MEDIA_ROOT, ignore_errors=True)
        super().tearDownClass()

    def setUp(self):
        # Создаем неавторизованный клиент
        self.guest_client = Client()

    def test_create_task(self):
        """Валидная форма создает запись в Task."""
        # Подсчитаем количество записей в Task
        tasks_count = Task.objects.count()
        # Для тестирования загрузки изображений
        # берём байт-последовательность картинки,
        # состоящей из двух пикселей: белого и чёрного
        small_gif = (
            b'\x47\x49\x46\x38\x39\x61\x02\x00'
            b'\x01\x00\x80\x00\x00\x00\x00\x00'
            b'\xFF\xFF\xFF\x21\xF9\x04\x00\x00'
            b'\x00\x00\x00\x2C\x00\x00\x00\x00'
            b'\x02\x00\x01\x00\x00\x02\x02\x0C'
            b'\x0A\x00\x3B'
        )
        uploaded = SimpleUploadedFile(
            name='small.gif',
            content=small_gif,
            content_type='image/gif'
        )
        form_data = {
            'title': 'Тестовый заголовок',
            'text': 'Тестовый текст',
            'image': uploaded,
        }
        # Отправляем POST-запрос
        response = self.guest_client.post(
            reverse('deals:home'),
            data=form_data,
            follow=True
        )
        # Проверяем, сработал ли редирект
        self.assertRedirects(response, reverse('deals:task_added'))
        # Проверяем, увеличилось ли число постов
        self.assertEqual(Task.objects.count(), tasks_count+1)
        # Проверяем, что создалась запись с нашим слагом
        self.assertTrue(
            Task.objects.filter(
                slug='testovyij-zagolovok',
                text='Тестовый текст',
                image='tasks/small.gif'
                ).exists()
        )

```
При подготовке данных для тестирования не стоит применять картинки, документы или 
какие-то иные файлы с вашего компьютера. Все данные для тестов должны быть в фикстурах.

Самый простой подход — использовать [байт-строки неизменяемые последовательности 
отдельных байтов](https://docs.python.org/3/reference/lexical_analysis.html#string-and-bytes-literals) 
и эмулировать файл картинки с помощью встроенной в Django [библиотеки SimpleUploadedFile](https://docs.djangoproject.com/en/3.0/_modules/django/core/files/uploadedfile/), 
как это и сделано в листинге.

#### Удаление тестовых картинок

При тестировании загрузки картинок модуль ```SimpleUploadFile``` не эмулирует сохранение 
файлов, а на самом деле сохраняет их в директорию ```media/tasks```. В результате после 
каждого теста в этой директории будет добавляться по картинке. Лучше прибраться за 
собой и не оставлять никакого мусора после тестов. При запуске тестов можно [создавать временную директорию](https://docs.python.org/3.7/library/tempfile.html#tempfile.TemporaryDirectory) 
для сохранения файлов. Эта операция описана в методе ```setUpClass```. Метод ```tearDownClass``` 
выполняется по окончании всех тестов класса, и в нём через метод ```shutil.rmtree()``` 
временная папка удаляется — вместе с загруженными в неё файлами. Теперь всё чистенько, как будто ничего и не было.

#### Тест дополнительных сценариев формы

Запись в поле ```slug``` должна быть уникальной, однако при заполнении поля (ручном или 
автоматическом) может быть создано неуникальное значение. В такой ситуации запись 
в базе данных не должна создаваться, а сайт не должен упасть.

```python
# deals/tests/tests_form.py
from django.core.files.uploadedfile import SimpleUploadedFile
from django.test import Client, TestCase
from django.urls import reverse

from deals.forms import TaskCreateForm
from deals.models import Task


class TaskCreateFormTests(TestCase):
    @classmethod
    def setUpClass(cls):
        super().setUpClass()
        # Создаем запись в базе данных
        Task.objects.create(
            title='Тестовый заголовок',
            text='Тестовый текст',
            slug='first'
        )

    def setUp(self):
        # Создаем неавторизованный клиент
        self.guest_client = Client()

    def test_cant_create_existing_slug(self):
        tasks_count = Task.objects.count() # Подсчитаем количество записей в Task
        form_data = {
            'title': 'Заголовок из формы',
            'text': 'Текст из формы',
            'slug': 'first', # отправим в форму slug, который уже есть в БД
        }
        response = self.guest_client.post(
            reverse('deals:home'),
            data=form_data,
            follow=True
        )
        # Убедимся, что запись в базе данных не создалась: 
        # сравним количество записей в Task до и после отправки формы
        self.assertEqual(Task.objects.count(), tasks_count)
        # Проверим, что форма вернула ошибку с ожидаемым текстом:
        # из объекта responce берём словарь 'form', 
        # указываем ожидаемую ошибку для поля 'slug' этого словаря
        self.assertFormError(
            response, 'form', 'slug', 'first уже существует'
        )
        # Проверим, что ничего не упало и страница отдаёт код 200
        self.assertEqual(response.status_code, 200)

```
В тесте появился незнакомый метод assertFormError(). Его назначение — проверить, 
возвращают ли поля формы ожидаемые ошибки. В аргументах метода, кроме объекта response, указывается:
 - имя формы (как оно указано в словаре context),
 - имя поля, ошибку которого нужно протестировать,
 - ожидаемый текст ошибки.
[Официальное описание метода assertFormError()](https://docs.djangoproject.com/en/3.1/topics/testing/tools/#django.test.SimpleTestCase.assertFormError)
   
### Тестирование паджинатора
Для тестирования паджинатора в фикстурах можно создать объекты Post и в словаре 
context проверить количество переданных на страницу записей. Записей в фикстурах 
должно быть больше, чем выводится на одну страницу паджинатора.
```python
# Здесь импорт необходимых библиотек для тестов.
...
class PaginatorViewsTest(TestCase):
    # Здесь создаются фикстуры: клиент и 13 тестовых записей.
    ...
    def test_first_page_containse_ten_records(self):
        response = self.client.get(reverse('index'))
        # Проверка: количество постов на первой странице равно 10.
       
        self.assertEqual(len(response.context.get('page').object_list), 10)

    def test_second_page_containse_three_records(self):
        # Проверка: на второй странице должно быть три поста.
        response = self.client.get(reverse('index') + '?page=2')
        self.assertEqual(len(response.context.get('page').object_list), 3)
```
Дополнительно можно проверить, что содержимое постов на странице соответствует 
ожиданиям — подобную проверку вы проводили, тестируя views. Получить содержимое 
страницы поможет запрос ```response.context.get('page').object_list```



## Paginator

Список ссылок для постраничного перехода — это стандартный элемент интерфейса

Написать постраничное разбиение материалов можно самостоятельно:
 - при постраничном делении передать в GET-запросе переменную page, значением которой 
   будет номер запрошенной страницы, например ```/group/cats?page=8``` (восьмая страница
   с постами сообщества, посвящённого котикам);
 - во view-функции проверить, есть ли переменная page в GET-параметрах;
 - если в параметрах нет переменной page — отдавать первую страницу, с постами с 
   первого по одиннадцатый;
 - если переменная page есть:
   - посчитать количество записей в базе,
   - через OFFSET и LIMIT получить нужный диапазон записей и отобразить их на 
     странице. Для ```/group/cats?page=8``` нужно будет получить записи с 78-ой по 
     88-ую включительно (по одиннадцать постов на страницу).

Но писать такой код для каждого списка элементов было бы нерационально, и в Django решили 
эту задачу: стандартный модуль Paginator раскладывает списки объектов по отдельным страницам 
и создаёт множество дополнительных инструментов для управления такими страницами.

Объект класса Paginator получает на вход список объектов, разбивает его на отдельные 
страницы и позволяет обратиться к ним индивидуально или получить полный список получившихся страниц.

Задача разработчика — создать объект Paginator(), передать в него список объектов и число 
элементов, которое требуется выводить на одну страницу. Всё остальное модуль сделает сам, 
остаётся только обращаться к свойствам и методам созданного объекта:
```python
>>> from django.core.paginator import Paginator
# Создаём тестовый список объектов
>>> items = ['Антон Чехов', 'Владимир Набоков', 'Лев Толстой', 'Марина Цветаева']

# Cоздаём объект Paginator(object_list, per_page),
# он принимает на вход список объектов 
# и число объектов, которое должно отображаться на одной странице.
# Передаём список items и задаём постраничное деление: по два объекта на страницу
>>> p = Paginator(items, 2)

# Свойство count показывает, сколько объектов в последовательности
>>> p.count
4

# Свойство num_pages показывает сколько страниц получится из списка
# num_pages рассчитывается как len(items)/per_page
>>> p.num_pages
2

# Получаем объект с элементами для первой страницы
>>> page1 = p.get_page(1)
>>> page1
<Page 1 of 2>

# Получаем элементы для отображения на первой странице
>>> page1.object_list
['Антон Чехов', 'Владимир Набоков']

# Проверяем, есть ли страницы после текущей
# и надо ли отображать кнопку "Следующая страница"
>>> page1.has_next()
True
# Проверяем, есть ли страницы перед текущей
# и надо ли отображать кнопку "Предыдущая страница"
>>> page1.has_previous()
False

>>> page2 = p.get_page(2)
>>> page2.object_list
['Лев Толстой', 'Марина Цветаева']

>>> page2.has_next()
False
>>> page2.has_previous()
True

# Чтобы отобразить список с номерами доступных страниц,
# получим значение свойства page_range:
# в нём хранятся данные типа range
>>> type(p.page_range)
<class 'range'>
# выведем в консоль линейку с перечнем страниц
>>> for n in p.page_range:
...     print(f"<{n}> ", end="")
... 
<1> <2>
```
При запросе данных из базы тоже возвращается список объектов, и работать с ним можно 
точно так же, как со списком писателей из приведённого примера.
```python
>>> from posts.models import Post
>>> posts = Paginator(Post.objects.order_by('-pub_date'), 2)
# В переменную post_page передадим объект второй страницы паджинатора
>>> post_page = posts.get_page(2)
>>> post_page.object_list
<QuerySet [<Post: 36>, <Post: 35>]>
```
Свойства объекта страницы post_page, их тип данных и значения в приведённом примере:
 - post_page — значение ```<Page 2 of 19>```, тип ```django.core.paginator.Page```
 - post_page.has_next() — значение True, тип bool
 - post_page.has_previous() — значение True, тип bool
 - post_page.has_other_pages() — значение True, тип bool
 - post_page.next_page_number() — значение 3, тип int
 - post_page.previous_page_number() — значение 1, тип int
 - post_page.start_index() — номер первого элемента на текущей странице. Отсчёт идёт от начала списка, начиная с 1. Значение: 3, тип: int
 - post_page.end_index() — номер последнего элемента на текущей странице. Отсчёт идёт от начала списка, начиная с 1. Значение: 4, тип: int 
   
Методы ```start_index()``` и ```end_index()``` будут полезны, если нужно нумеровать элементы, выведенные на страницу.

### Паджинатор в Yatube

[Документация Paginator](https://docs.djangoproject.com/en/3.1/ref/paginator/)

Обновите view-функцию главной страницы: пусть она отдаёт по десять постов на страницу. 
Они будут передаваться в переменной page. Для перехода по страницам паджинатора к 
обычному URL будет добавляться GET-параметр page с указанием нужной страницы: ```page=n```, 
где n — это номер страницы. Например, URL второй страницы паджинатора для главной 
страницы проекта будет таким: ```http://127.0.0.1:8000/?page=2```
```python
from django.core.paginator import Paginator
from django.shortcuts import render
from .models import Post


def index(request):
    post_list = Post.objects.all().order_by('-pub_date')
    # Если порядок сортировки определен в классе Meta модели,
    # запрос будет выглядить так:
    # post_list = Post.objects.all()
    # Показывать по 10 записей на странице.
    paginator = Paginator(post_list, 10) 

    # Из URL извлекаем номер запрошенной страницы - это значение параметра page
    page_number = request.GET.get('page') 

    # Получаем набор записей для страницы с запрошенным номером
    page = paginator.get_page(page_number) 
    return render(
         request,
         'index.html',
         {'page': page,}
     )
```
### Настройка HTML-шаблонов
Измените шаблон index.html: список постов будет передаваться в элементе с ключом page.
```html
{% extends "base.html" %} 
{% block title %}Последние обновления на сайте{% endblock %}
{% block content %}

  <h1> Последние обновления на сайте<h1>

  {% for post in page %}
    ...Тут вывод списка записей...
  {% endfor %}

{% endblock %}
```
Теперь нужно написать HTML-код для навигации по страницам.
В директории templates создайте файл paginator.html и добавьте в него такой код:
```html
{# Отрисовываем навигацию паджинатора только если есть и другие страницы #}
{% if page.has_other_pages %}
<nav>
  <ul class="pagination">
    {% if page.has_previous %}
    <li class="page-item">
      <a class="page-link" href="?page={{ page.previous_page_number }}">&laquo; Предыдущая</a>
    </li>
    {% else %}
    <li class="page-item disabled">
      <span class="page-link">&laquo; Предыдущая</span>
    </li>
    {% endif %}
    {% for i in page.paginator.page_range %}
    {% if page.number == i %}
    <li class="page-item active">
      <span class="page-link">{{ i }}
        <span class="sr-only">(текущая)</span>
      </span>
    </li>
    {% else %}
    <li class="page-item">
      <a class="page-link" href="?page={{ i }}">{{ i }}</a>
    </li>
    {% endif %}
    {% endfor %}
    {% if page.has_next %}
    <li class="page-item">
      <a class="page-link" href="?page={{ page.next_page_number }}">Следующая &raquo;</a>
    </li>
    {% else %}
    <li class="page-item disabled">
      <span class="page-link">Следующая &raquo;</span>
    </li>
    {% endif %}
  </ul>
</nav>
{% endif %}
```
Осталось встроить виджет паджинатора в код шаблона главной страницы:
```html
{% extends "base.html" %}
{% block title %}Последние обновления на сайте{% endblock %}

{% block content %}

  <h1>Последние обновления на сайте</h1>

  {% for post in page %}
    ...Тут вывод списка записей...
  {% endfor %}

  {% include "paginator.html" %}

{% endblock %}
```

## Статичные страницы и класс TemplateView

[Документация TemplateView](https://docs.djangoproject.com/en/3.1/ref/class-based-views/base/#django.views.generic.base.TemplateView)

Вы уже создали несколько страниц и view-функций в проекте Yatube. Но помимо страниц 
с динамическим содержимым на сайте могут понадобиться и простые статичные страницы

В Django есть view-класс TemplateView, который создан для таких случаев. Этот простой 
класс по умолчанию обрабатывает только GET-запросы и возвращает страницу, сформированную 
на основе указанного шаблона и словаря контекста (словарь не обязателен: содержимое 
страницы может быть описано прямо в шаблоне).

### Раз: view-класс
```python
# views.py
# Импорт класса TemplateView, чтобы унаследоваться от него
from django.views.generic.base import TemplateView


class JustStaticPage(TemplateView):
    # В переменной template_name обязательно указывается имя шаблона,
    # на основе которого будет создана возвращаемая страница
    template_name = 'app_name/just_page.html'

```
### Два: шаблон
```html
<!-- any_dir/app_name/just_page.html -->
<html>
  <head>
    <title>Очень простая страница</title>
  </head>
    
  <body>
    <div class="header">JUST SITE</div>
    <h1>Очень простая страница</h1>
    <p>На создание этой страницы у меня ушло пять минут! Ай да я.</p>
    <div class="footer">© JUST SITE, все права </div>
  </body>
</html>
```
### Три: путь
```python
# urls.py
...
urlpatterns = [
    ...
    path('justpage/', views.JustStaticPage.as_view())
]
```
По ссылке /justpage/ откроется страница с похвалой самому себе.

### Можно и с контекстом
Класс ```TemplateView``` может передавать в шаблон словарь context, для этого нужно дописать 
метод класса ```get_context_data()```:
```python
# views.py
from django.views.generic.base import TemplateView


class JustStaticPage(TemplateView):
    template_name = 'any_dir/app_name/just_page.html'

    def get_context_data(self, **kwargs):
        context = super().get_context_data(**kwargs)
        # Здесь можно произвести какие-то действия для создания контекста.
        # Для примера в словарь просто передаются две строки
        context['just_title'] = 'Очень простая страница'
        context['just_text'] = 'На создание этой страницы у меня ушло пять минут! Ай да я.'
        return context
```
А шаблон, как и всегда, может рендериться на основе нескольких других шаблонов и словаря context:
```html
<!-- just_page.html -->
<html>
  <head>
    <title>{{ just_title }}</title>
  </head>

  <body>
  {% include 'header.html' %}

    <h1>{{ just_title }}</h1>
    <p>{{ just_text }}</p>

  {% include 'footer.html' %}
  </body>
</html>
```
Класс TemplateView отлично подходит
 - для отображения простых статичных страниц, например «Об авторе» или «О компании»;
 - для отображения страниц с простым контекстом;
 - для отображения страниц, всё содержимое которых описано в HTML-шаблоне.
Класс TemplateView не стоит применять
 - для работы с любыми HTTP-запросами, кроме GET;
 - для операций CRUD. Не имеет смысла расширять класс TemplateView, для CRUD есть специальные классы — FormView, CreateView и UpdateView.
Особенности класса TemplateView:
 - По умолчанию класс TemplateView ответит только на GET-запрос. На запросы других типов класс вернёт код 405: HttpResponseNotAllowed.
 - Класс не поддерживает формы.
 - Переменная ```template_name``` (путь к файлу шаблона) обязательно должна быть объявлена в классе.

## Страницы с ошибками

Если отключить режим отладки (его ещё называют «режим разработки» или «режим разработчика»), 
то часть страниц вы увидите в совершенно ином виде. Страницы ошибок (error 404, 
«страница не найдена» или error 500, «ошибка сервера») предустановлены в Django, 
но выглядят так, как будто разработчику сайта не было до них дела.

Если запрошенная страница не найдена, сервер возвращает код 404. Django видит этот 
ответ и автоматически вызывает собственную предустановленную view-функцию. Адрес 
этой view-функции хранится в переменной ```handler404``` (по умолчанию это view-функция 
```django.views.defaults.page_not_found```).

Но можно создать view-функцию самостоятельно и вызвать её при ошибке 404. Для этого 
надо лишь перезаписать содержимое переменной ```handler404```: передать в эту переменную 
имя нашей view-функции.

Точно так же дело обстоит и с обработкой прочих ошибок: для них заготовлены переменные 
```handler400```, ```handler403``` и несколько других, в [документации есть их перечень](https://docs.djangoproject.com/en/3.0/ref/urls/#handler400).

Импортируем переменные из модуля ```django.conf.urls```, переопределим дефолтные переменные — и сможем 
вызвать собственные view-функции и шаблоны для страниц ошибок. Указывать view-функции 
для таких страниц можно [только в головном](https://docs.djangoproject.com/en/3.0/topics/http/views/#customizing-error-views) ```urls.py```. Добавьте в него следующие строки:
```python
from django.conf.urls import handler404, handler500

handler404 = "posts.views.page_not_found"
handler500 = "posts.views.server_error"
```
Если в вашем редакторе кода включён анализ синтаксиса, возможно, вы получите предупреждение 
о том, что переменные созданы, но не используются. Но мы-то знаем, что это не так.
Чтобы редактор не приставал к вам по пустякам, выполните трюк, который отключит проверку 
текущей строки — добавьте в неё директиву-комментарий # noqa (от NO Quality Assurance):
```python
from django.conf.urls import handler404, handler500 # noqa

handler404 = "posts.views.page_not_found"  # noqa
handler500 = "posts.views.server_error"  # noqa
```
View-функции можно положить в любое удобное место, мы сохраним их в файле ```posts/views.py```:
```python
def page_not_found(request, exception):
    # Переменная exception содержит отладочную информацию, 
    # выводить её в шаблон пользователской страницы 404 мы не станем
    return render(
        request, 
        "misc/404.html", 
        {"path": request.path}, 
        status=404
    )


def server_error(request):
    return render(request, "misc/500.html", status=500)
```
Создайте файл шаблона ```templates/misc/404.html``` и добавьте в него код:
```html
{% extends "base.html" %} 
{% block title %} Ошибка 404 {% endblock %}
{% block content %}

<main role="main" class="container">
<div class="row">
    <div class="col-md-12">
        <h1>Ошибка 404</h1>
        <p class="lead">Страница <code>{{ path }}</code> не найдена</p>
        <p class="lead"><a href="{% url  'index' %}">Вернуться на главную</a></p>
    </div>
</div>
</main>

{% endblock %}
```
Теперь надо создать шаблон для ошибки 500, ```templates/misc/500.html```
```html
{% extends "base.html" %} 
{% block title %} Ошибка 500 {% endblock %}
{% block content %}

<main role="main" class="container">
<div class="row">
    <div class="col-md-12">
        <h1>Ошибка 500</h1>
        <p class="lead">Ошибка на сервере, попробуйте обновить страницу или обратиться позже</p>
        <p class="lead"><a href="{% url 'index' %}">Вернуться на главную</a></p>
    </div>
</div>
</main>

{% endblock %}
```
Директорию templates/misc создавать не обязательно, но с ней будет удобнее: там можно 
спрятать файлы, которые практически никогда не изменяются.

При разработке реальных проектов вы будете публиковать их на сервере, и режим отладки 
нужно будет отключать. Чтобы это сделать — измените в файле settings.py значение ключа 
DEBUG на False

## Добавление картинок к постам

Django — это огромная экосистема из всевозможных модулей, расширяющих возможности 
базового фреймворка. На сайте PyPI.org размещены десятки тысяч расширений, в названии 
которых есть слово django, а неопубликованных модулей или тех, что названы как-то 
иначе — ещё больше.

Подключим к нашему проекту управление изображениями.

### sorl-thumbnail

В стандартную установку Django встроен инструмент для работы с картинками, но задачи 
вроде изменения размера изображений ему не по силам. Django умеет только загружать файлы 
и отдавать их как есть. Для настоящей соцсети этого мало.

Дадим пользователям возможность иллюстрировать посты и сделаем так, чтобы загруженные 
изображения выглядели более-менее одинаково. Одно из первых по популярности и удобству 
приложений для работы с графикой — sorl-thumbnail. Для его работы нужна графическая 
библиотека, sorl-thumbnail умеет работать со многими, мы возьмём библиотеку Pillow.
```bash
(venv) $ pip install Pillow 
```
Теперь установите приложение sorl-thumbnail:
```bash
(venv) $ pip install sorl-thumbnail
```
Добавьте приложение в список ```INSTALLED_APPS```, в конец списка:
```python
INSTALLED_APPS = [
    # ... 
    'sorl.thumbnail',
]
```
> Выполните миграцию, и после этого приложение будет готово к работе.
Теперь вам станут доступны специальные теги в шаблонах:
```html
<!-- Загрузка тегов библиотеки в шаблон -->
{% load thumbnail %}

<!-- Пример использования тега для пропорционального уменьшения и обрезки картинки до размера 100x100px с центрированием -->
<!-- и вставляет в код изображение которое отобразится пользователю. -->
{% thumbnail item.image "100x100" crop="center" as im %}
        <img src="{{ im.url }}" width="{{ im.width }}" height="{{ im.height }}">
{% endthumbnail %}
```
Настроим модель Post так, чтобы к посту можно было добавить заглавную картинку:
```python
class Post(models.Model):
    text = models.TextField()
    pub_date = models.DateTimeField('Дата публикации', auto_now_add=True)
    author = models.ForeignKey(User, on_delete=models.CASCADE, related_name='author_posts')
    group = models.ForeignKey(
    Group, on_delete=models.CASCADE, related_name='group_posts', blank=True, null=True
    )
    # поле для картинки
    image = models.ImageField(upload_to='posts/', blank=True, null=True) 
```
Аргумент ```upload_to``` указывает, куда должны загружаться пользовательские файлы.
Теперь добавьте новое поле в форму, связанную с моделью:
```python
from django import forms
from .models import Post

class PostForm(forms.ModelForm):
    class Meta:
        model = Post
        fields = ['group', 'text', 'image']
```
Путь к директории для загрузки изображений указывается относительно адреса в параметре 
конфигурации ```MEDIA_ROOT```, который должен содержать полный путь к директории и не должен 
совпадать с директорией ```STATIC_ROOT```. Добавьте следующие строки в файл ```settings.py```:
```python
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/2.2/howto/static-files/

STATIC_URL = '/static/'
STATIC_ROOT = os.path.join(BASE_DIR, 'static')

MEDIA_URL = '/media/'
MEDIA_ROOT = os.path.join(BASE_DIR, 'media')
```
Есть еще один нюанс настройки сервера. Мы добавляем возможность загрузки файлов 
пользователями, а значит, эти файлы должны быть доступны для просмотра в режиме 
разработки. Поэтому добавьте в файл ```yatube/urls.py``` следующий код:
```python
# эти строки — в начало файла, рядом с импортом других модулей
from django.conf import settings
from django.conf.urls.static import static

# эти строки — в самый конец файла

if settings.DEBUG:
    urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
    urlpatterns += static(settings.STATIC_URL, document_root=settings.STATIC_ROOT)
```
Этот код будет работать, когда ваш сайт в режиме отладки. Он позволяет обращаться 
файлам в директории, указанной в **MEDIA_ROOT** по имени, через префикс **MEDIA_URL**.

Чтобы изображение показывалось на странице сайта, измените шаблон страницы записи. 
Добавьте вывод картинок в ```post.html```:
```html
<div class="card mb-3 mt-1 shadow-sm">
    {% load thumbnail %}
    {% thumbnail post.image "960x339" crop="center" upscale=True as im %}
        <img class="card-img" src="{{ im.url }}">
    {% endthumbnail %}
        <div class="card-body">
                ...
```
Если в посте нет картинки, то содержимое тега thumbnail будет проигнорировано, так 
что проверку ```{% if post.image %}...{% endif %}``` делать не надо.

В HTML-форме создания и редактирования поста появится поле для загрузки изображения. 
Форма должна понимать, что из неё на сервер будут передаваться файлы. Обновите шаблон 
с формой — в тег <form> добавьте атрибут enctype:
```html
<form method="post" enctype="multipart/form-data">
```
Осталось подправить функцию редактирования записи. Django-формы умеют работать с файлами, 
так что нужно лишь передать дополнительный параметр ```files=request.FILES or None```, и больше ничего!
```python
@login_required
def post_edit(request, username, post_id):
    profile = get_object_or_404(User, username=username)
    post = get_object_or_404(Post, pk=post_id, author=profile)
    if request.user != profile:
        return redirect('post', username=username, post_id=post_id)
    # добавим в form свойство files
    form = PostForm(request.POST or None, files=request.FILES or None, instance=post)
    
    if request.method == 'POST':
        if form.is_valid():
            form.save()
            return redirect("post", username=request.user.username, post_id=post_id)

    return render(
        request, 'post_edit.html', {'form': form, 'post': post},
    )
```
У вас должна получиться страница просмотра записи с картинкой.

## Полезные функции

В Django есть место, где можно найти наиболее востребованные функции: ```django.shortcuts```

### render()

```render(request, template_name, context=None, content_type=None, status=None, using=None)```

Вы уже не раз применяли эту функцию для генерации страниц на основе шаблона и списка 
переменных ```context```. В ```render()``` можно указать MIME-тип отдаваемого документа ```content_type```, 
по умолчанию это ```text/html```. Параметр ```status``` — это код HTTP-ответа сервера; чаще всего 
используются коды 200 и 404. В параметре ```using``` можно указать имя движка языка шаблонов, 
это нужно на сайтах, где применяется несколько разных движков.
```python
from django.shortcuts import render

def my_index(request):
    # какой-то код
    return render(request, 'index.html', {'elki': 'palki'}, content_type='text/html', status=200)
```

### redirect()

```redirect(to, *args, permanent=False, **kwargs)```

Чтобы view-функция ответила переадресацией на другую страницу сайта, применяют ```redirect()```. 
Аргумент ```permanent=True``` сообщит браузеру и поисковым системам, что редирект постоянный 
и это надо запомнить. Редирект может быть полезен при попытке неавторизованного доступа 
к определённой странице или в случае, если структура адресов сайта была изменена, 
а пользователь запросил устаревший адрес.

```python
# models.py

from django.db import models

class MyModel():
    # тут свойства модели
    def get_absolute_url(self):
        return f"/item/{self.id}/"


# views.py
from django.shortcuts import redirect

def my_obj_view(request):
    # ...
    # редирект на объект работает, если в модели есть 
    # метод get_absolute_url(), который возвращает путь
    obj = MyModel.objects.get(...)
    return redirect(obj)

def my_name_view(request):
    # ...
    # редирект на страницу по имени, с указанием переменной 
    # path("<var>/", views.other, name="path-name"),
    return redirect('path-name', var='any-value')

def my_str_view(request):
    # ...
    # редирект на относительный путь на сайте
    return redirect('/some/url/')

def my_url_view(request):
    # ...
    # редирект на любой другой ресурс в сети
    return redirect('https://example.com/')
```

### get_list_or_404()

```get_list_or_404(klass, *args, **kwargs)```

Функция ищет список объектов в базе. Если не находит — прерывает работу view-функции 
и возвращает страницу с ошибкой 404. Аргументы и принцип работы те же, что и у get_object_or_404(), 
но при получении нескольких объектов не вызывается исключение.
```python
from django.shortcuts import get_list_or_404

def group_posts(request, slug):
    group = get_object_or_404(Group, slug=slug)        
    posts = get_list_or_404(Post, group=group)
    # ...
```

### reverse()

```reverse(viewname, urlconf=None, args=None, kwargs=None, current_app=None)```

Эта функция позволяет обратиться к view-функции по её имени, указанному в ```path()```
В коде эта функция делает то же самое, что и тег ```{% url %}``` в шаблонах.
```python
from django.urls import reverse

def myview(request):
    # для пути 
    # path("<username>/<int:post_id>/", views.post_view, name="post"),
    
    path = reverse('post', kwargs={'username': 'leo', 'post_id': 42})        
    # или 
    path = reverse('post', args=('leo', 42))

    return HttpResponseRedirect(path)
```

### django-debug-toolbar

В Django супероружие — это django-debug-toolbar (сокращенно DjDT). [Документация](https://github.com/jazzband/django-debug-toolbar)

```bash
(venv) $ pip install django-debug-toolbar 
```

Зарегистрируйте в ```settings.py``` новое приложение:
```python
# Инструмент будет работать только в режиме разработки:
DEBUG = True

# Добавьте новое приложение в 
INSTALLED_APPS = [
    # Это приложение необходимо для работы
    "django.contrib.staticfiles",
    # ...
    "debug_toolbar",
]

# Добавьте новое приложения для обработки запросов

MIDDLEWARE = [
    # ...
    "debug_toolbar.middleware.DebugToolbarMiddleware",
]

# Добавьте IP адреса при обращении с которых будет доступен инструмент

INTERNAL_IPS = [
    "127.0.0.1",
]
```
В головной файл urls.py добавьте новое правило для режима отладки:
```python
from django.conf import settings

# У вас уже есть это условие
if settings.DEBUG:
    import debug_toolbar
    
    urlpatterns += (path("__debug__/", include(debug_toolbar.urls)),)

```
Теперь вам доступна груда информации о том, как шла отрисовка текущей страницы. 

### ngrok

[Документация](https://ngrok.com/download)

```BASH 
$ choco install ngrok
```
Добавьте в список ALLOWED_HOSTS разрешение для просмотра сайта под любыми именами:
```python
ALLOWED_HOSTS = [
        "*",
    ]
```
Убедитесь, что ваш сайт работает локально по адресу http://127.0.0.1:8000/
В отдельном окне терминала выполните команду:
```bash
$ ngrok http 8000
```
У вас появится окно, в нём через пару секунд вы увидите доменное имя вашего сайта



-------------------------------------------------------------------------------
# API 

В качестве примера хорошего и несложного API, созданного по принципам REST, 
рассмотрим сервис [SWAPI — Star Wars API](https://swapi.dev/).


























# Шпаргалка SQL

# Шпаргалка Git / GitHub

## Комманды Bash 

```bash
pwd # текущая директория
ls -laSt # список папок 
    # -l Допинформация 
    # -t сортировать по времени изменения
    # -a показать скрытые 
    # -S сортировать от больших к меньшим
cd c:  # сменить диск директорию 
сd /d/Project/ # сменить сразу и диск и директорию
сd ~/Desktop # перейти на рабочий стол текущего пользователя
cd / # Перейти в корневую директорию
rm -r -f # Удалить папку ы
    # -r рекурсивно удалять все вложения
    # -f удалять без вопросов
     
```



## Работа с Git 
 - [Скачать Git для Windows](https://gitforwindows.org/)
 - [Отличная шпаргалка по Git](https://githowto.com/ru/setup)
 - [Официальный верифицированный перевод руководства по Git на русский язык](https://git-scm.com/book/ru/v2)
 - [Ролик по Git](https://www.youtube.com/watch?v=SEvR78OhGtw&t=4215)
 - [Тренажер по Git](https://learngitbranching.js.org/?locale=ru_RU)

![картинка тренажера](https://habrastorage.org/storage2/8e7/132/076/8e7132076f76bc1c65eb1f41d15e1aa8.png)
s

### Команды Git 

```bash
###  базовые настройки Git.
git config --global user.name "Aleksandr Evstushkin"
git config --global user.email "evstushkin@gmail.com" 
### Клонирование себе репозитория с GitHub
git clone https://github.com/ваш-аккаунт-на-гитхабе/backend_test_homework

###
git add  название_файла # добавить новые файлы в индекс
git add .  # или (git add --all) добавить все неотслеживаемые файлы в индекс 
git commit -m  'New edit' # сохранить версию проекта с комментарием
git commit --amend -m "Текст вашего комментария" # Обновить последний commit и комментарий
git push # Отправить данные на сервер

### просмотр данных о коммитах
git status # Проверка статуса файлов 
git log # Информация о коммитах [Q] для выхода из просмотра  
git show # Подробная информация об изменениях 
git show HEAD # Подробная информация об изменениях в самом свежем коммите 
git show 1234567 # где вместо 1234567 нужно указать первые 7 символов контрольной суммы нужного коммита

### Сброс изменений
git reset 97a25f7 ### Сброс изменений и возврат всего проекта к определенному коммиту 
git reset HEAD program.py # откатиться на один коммит назад в определённом файле
git reset HEAD  # Сброс всего проекта до последнего коммита


```
Для игнорироания файлов Git-ом добавить файл .gitignore: 
```properties
# Пример файла (Комментарии поддерживаются):
README.md       # игнорировать файл README.md
build/side.txt  # игнорировать файл side.txt в директории build
*.doc           # игнорировать все файлы с расширением .doc
``` 

### Работа с GitHub  

 - Для копирования себе чужого репозитория нажать FORK. После этого он будет доступен по адресу https://github.com/ваш-аккаунт-на-гитхабе/backend_test_homework  



# Прочее 

## Оформление кода PEP8 

[Стандарт оформления кода PEP8](https://www.python.org/dev/peps/pep-0008/)

### Основные правила PEP8:
 - Длина строки — не более 79 символов.
 - Отступы — 4 пробела.
 - Стили имён должны соответствовать PEP8: Naming Conventions.
 - Переносы строк делаются с правильными отступами.
 - Бэкслеши \ для переносов не применяются.
 - В коде нет неиспользуемых импортов.
 - Импорты отсортированы в таком порядке:
    - импорты стандартной библиотеки,
    - импорты сторонних библиотек,
    - импорты модулей текущего проекта.
 - Функции верхнего уровня (не вложенные) и определения классов отделены друг от друга двумя пустыми строчками.
 - Определения методов внутри класса отделены одной пустой строкой.
 - Консистентность (одинаковые кавычки, одинаковые методы решения одинаковых проблем и так далее).
 - Отсутствие закомментированного кода и стандартных комментариев Django ( # Create your views here. etc.)
 - Комментарии к функциям оформлены в виде Docstrings, в соответствии с Docstring Conventions: начинаются с большой 
   буквы, заканчиваются точкой и содержат описание того, что делает функция. 
 -  Комментарии к коду лаконичны и содержательны.
 - Длинные куски кода логически разделены пустыми строками, как абзацы в тексте.
 - Отсутствуют лишние операции.
 - Нет лишних else там, где они не нужны (если в if происходит return / raise ); используется Guard Block.
 - В репозитории нет лишних файлов: никаких __pycache__ , .vscode и
прочего
 - Исполняемый код в .py-файлах должен быть закрыт конструкцией if__name__ == ‘__main__’
 - Для неизменяемых последовательностей данных предпочтительнее применяются кортежи, а не списки.
 - В f-строках применяется только подстановка переменных и нет логических или арифметических операций, вызовов функций и 
   подобной динамики.
 - Переменные названы в соответствии с их смыслом, по-английски, нет однобуквенных названий и транслита. В названии 
   переменной не должен содержаться её тип.
 - При необходимости применяются type annotations.

### Про HTML шаблоны:
 - {{ переменные }} и % теги % в шаблонах отформатированы согласно ощепринятым рекомендациям.
 - HTMLтеги в шаблонах отбиты отступами в соответствии со вложенностью. Размер отступа — 2 или 4 пробела, постоянный в
пределах проекта.
 - В приложениях указаны правильные пути к шаблонам
    - Допустимый путь: app/templates/app/index.html .
    - Недопустимый путь: app/templates/index.html .
    - Возможен вариант с project level templates: общая директория templates в корне проекта со всеми шаблонами внутри.

### Про Django в целом:
      
 - В urls.py в конце роутов стоит слеш /
 - Для URL применяются соответствующие Path converters.
 - Соблюдается официальный [код-стайл Django](https://docs.djangoproject.com/en/dev/internals/contributing/writing-code/coding-style/)


## Шпаргалка Markdown

 - [Краткая справка Markdown](https://paulradzkov.com/2014/markdown_cheatsheet/)
 - [PlantUML для рисования схем в двух словах](https://plantuml.com/ru/)

Пример диаграммы PlantUML из текста
```puml
start
:Вывалить мысли в текст;
if (Бред?) then (Возможно)
    :Дать посмотреть коллеге;
    if (Сойдет?) then (Да)
    else (Нет)
        :Помедитировать над текстом;
    endif
    :Разместить в проекте;
else (Точно)
    stop
endif
stop
```

## Сервисы для самообучения:

[Freecodecsmp](https://www.freecodecamp.org/) 

### Путевая карта Backend разработчика

![Путевая карта Backend разработчика](https://roadmap.sh/roadmaps/backend.png)
