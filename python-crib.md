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
for iterator not in list: # перебор значений коллекций: списков, словарей, сетов
range(a, b) # генератор чисел для итерации с a до b-1. Запомнить принцип легко: если на месте a стоит ноль, range(0, N) вернёт ровно N значений
reversed(range(1, 13)) # Обратный отсчет с 12 до 1 
reversed(list) # развернуть список с конца
for i in range(-1, 10): # Перебрать все числа в диапазоне от -1 до 9
    conteny 

### while
while a==b: 
else: 
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
> 
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

### Модуль pytest

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

## Создание пользователей

```bash
python manage.py createsuperuser 
http://127.0.0.1:8000/admin/ # админка
```

```python
# Регистрация модели в админке 
# в файле posts/admin.py
from django.contrib import admin
from .models import Post
admin.site.register(Post)
```


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
