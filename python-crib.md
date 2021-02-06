# Установка

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
### Работа
c:\>c:\Python38\python -m venv c:\path\to\<name_venv>  # Создаем новое окружение
### Активируем окружение 
cd /path/to/new/<name_venv>/Scripts/
activate.bat 

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
$ pip install flake8 # Устаовка flake8 
$ flake8 my_project # Запустить для проверки ошибок в папке проекта

# Дополнения для линтера Flake8 
pep8-naming # проверяет имена классов, функций и переменных на соответствие PEP8;  
flake8-broken-line # отслеживает применение устаревших переносов (через обратный слеш \);
flake8-return # проверяет значения, возвращаемые функциями;
flake8-isort # проверяет правильность порядка импортов.

# Контроль линтером в момент коммита 
$ flake8 --install-hook git # Установить хук для Git
$ git config --bool flake8.strict true И настроить сам гит, чтобы учитывать правила Flake8
```

# Шпаргалка Python

## Простые объекты

### --- Числа

```py
None # не определена, не имеет никакого значения

### элементарные операции + - * / идентичны
x = a//b # целое от деления
x = a%b  # остаток от деления
x = a**b # а в степени b 

### булевые операции. порядок выполнения: 
not # смена значения
and # булево умножение
or  # булево сложение
== <= >= != # равно, меньше+равно, больше+равно, не равно 

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

``
### --- Строки 

```py
' sdf  sdf '.split() # разбить строку по пробелам 
blok_string.split('. ') # разделить строку по разделителю. получить список
'.sdf  sdf.'.strip() # Убирает лишние символы в начале и в конце  
', '.join(iterator) # Сборка строки из значений любой коллекции через запятую 
'sdfdf "sd" sad' # если нужно вывести кавычки в тексте они должны отличатся от обрамляющих
### f-строки
print(f'На улице сейчас {weather}.') 


```

### --- Преобразования

Между системами счисления - схема Горнера
```python
str() # к строке
int() # к целому
float() # к дробному числу
```

### --- Списки list
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
```

### --- Словари dict
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

### --- Множества (сеты) set

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

### --- Условия 

```py
if beaufort == 0: 
elif:
else:
```

### --- Циклы

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

### --- Функции

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

### --- Файлы

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

### --- Библиотеки. Полезные  модули

```py
### Подключение модулей
import random # Подключение всего модуля. 
random.random()
import random as r # Подключение модуля под определенным именем
r.random() 
from random import choice, randint # Подключение отдельных функций
randint(0, 23) # Можно вызывать не указывая модуль
from random import * # Подлключение всех функций
random() # Можно вызывать любую функцию не указывая модул

### Полезные библиотеки
import random 
random.randint(0, 23) # функция randint() генерирует случайное целое число  
random.random() # случайное дробное число
random.choice(list) # случайный элмент списка

import math 
math.sqrt(16) # квадратный корень

import datetime as dt
dt.datetime(1961, 4, 12, 9, 7, 0) # 1961-04-12 09:07:00 
landing_time - start_time # Можно вычитать даты. Результат: 1:48:00 -> тип timedelta
dt.utcnow() #  текущий момент времени
dt.datetime.utcnow() # прямой вызов текущего времени
timedelta(days, hours, minutes, seconds, microseconds) # тип. хранение промежутков времени
period = dt.timedelta(hours=3) # промежуток времени в три часа. 3:00:00 
moscow_moment = dt.datetime.utcnow() + dt.timedelta(hours=3) # московское время
dt.strftime('%H:%M') # форматированный вывод времени. 10:31 Параметры: %B — месяц, %Y — год и %S — секунды, %A — название дня недели по-английски, %U — номер недели в году

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

### --- Обработка исключений

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

# Алгоритмы

## == Однопроходные алгоритмы

```py
flag = flag or (x==find) # Проверк наличия значения find 
 
```

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

 - [Официальный верифицированный перевод руководства по Git на русский язык](https://git-scm.com/book/ru/v2)
 - [Описание команд Хабр]([https://gist.github.com/rdnvndr/cb21a06c5a71fd71213aed1619380b8e]()
)

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


## Дополнительные материалы:

 - Тренажер по Git https://learngitbranching.js.org/?locale=ru_RU

![картинка тренажера](https://habrastorage.org/storage2/8e7/132/076/8e7132076f76bc1c65eb1f41d15e1aa8.png)

 - Ролик по Git https://www.youtube.com/watch?v=SEvR78OhGtw&t=4215s



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

