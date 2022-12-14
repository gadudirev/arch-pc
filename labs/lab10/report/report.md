---
## Front matter
title: "Отчёта по лабораторной работе 10"
subtitle: "Понятие подпрограммы. Отладчик GDB."
author: "Дудырев Г. А.	НПИбд-01-22"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Целью работы является приобретение навыков написания программ с использованием подпрограмм.
Знакомство с методами отладки при помощи GDB и его основными возможностями.

# Задание

1. Изучите примеры реализации подпрограмм

2.  Изучите работу с отладчиком GDB

4. Выполните самостоятеьное задание

3. Загрузите файлы на GitHub.


# Выполнение лабораторной работы


1. Сначала создадим каталог для выполнения лабораторной работы № 10, далее перейдем в него и создадим файл lab10-1.asm:

2. Рассмотрим программу вычисления арифметического
выражения f(x) = 2x+7 с помощью подпрограммы calcul. В данном
примере x вводится с клавиатуры, а само выражение вычисляется в подпрограмме. 
(рис. [-@fig:001], [-@fig:002])

![Файл lab10-1.asm](image/01.png){ #fig:001 width=70%, height=70% }

![Работа программы lab10-1.asm](image/02.png){ #fig:002 width=70%, height=70% }

3. Теперь изменим текст программы, добавив подпрограмму subcalcul в подпрограмму calcul, 
для вычисления выражения f(g(x)), где x вводится с клавиатуры, 
f(x) = 2x + 7, g(x) = 3x − 1(рис. [-@fig:003], [-@fig:004])

![Файл lab10-1.asm](image/03.png){ #fig:003 width=70%, height=70% }

![Работа программы lab10-1.asm](image/04.png){ #fig:004 width=70%, height=70% }

4. Создаем файл lab10-2.asm с текстом программы из Листинга 10.2. (Программа печати сообщения Hello world!):
(рис. [-@fig:005])

![Файл lab10-2.asm](image/05.png){ #fig:005 width=70%, height=70% }

Получаем исполняемый файл. Для работы с GDB в исполняемый файл необходимо добавить отладочную информацию, 
для этого трансляцию программ необходимо проводить с ключом ‘-g’.
Загрузим исполняемый файл в отладчик gdb:
Проверим работу программы, запустив ее в оболочке GDB с помощью команды run :(рис. [-@fig:006])

![Работа программы lab10-2.asm в отладчике](image/06.png){ #fig:006 width=70%, height=70% }

Установим брейкпоинт на метку
start, с которой начинается выполнение любой ассемблерной программы, и запустим её.
Посмотрим дисассимилированный код программы  (рис. [-@fig:007], [-@fig:008])

![дисассимилированный код](image/07.png){ #fig:007 width=70%, height=70% }

![дисассимилированный код в режиме интел](image/08.png){ #fig:008 width=70%, height=70% }

На предыдущих шагах была установлена точка останова по имени метки (_start). 
Проверим это с помощью команды info breakpoints
Установим еще одну точку останова по адресу инструкции. 
Теперь определим адрес предпоследней инструкции (mov ebx,0x0) и установим точку.(рис. [-@fig:009])

![точка остановки](image/09.png){ #fig:009 width=70%, height=70% }

Выполним 5 инструкций с помощью команды stepi (или si) и проследии за
изменением значений регистров. (рис. [-@fig:011] [-@fig:012])

![изменение регистров](image/10.png){ #fig:010 width=70%, height=70% }

![изменение регистров](image/11.png){ #fig:011 width=70%, height=70% }

Посмотрим значение переменной msg1 по имени
Посмотрим значение переменной msg2 по адресу
Изменить значение для регистра или ячейки памяти можно с помощью команды set, 
задав ей в качестве аргумента имя регистра или адрес. 
Заменим первый символ переменной msg1 
Заменим любой символ во второй переменной msg2. (рис. [-@fig:012])

![замена значения переменной](image/12.png){ #fig:012 width=70%, height=70% }

Выведем в различных форматах (в шестнадцатеричном формате, в двоичном формате и в символьном виде) 
значение регистра edx.
С помощью команды set изменим значение регистра ebx:(рис. [-@fig:013])

![вывод значения регистра](image/13.png){ #fig:013 width=70%, height=70% }

С помощью команды set изменим значение регистра ebx:(рис. [-@fig:014])

![вывод значения регистра](image/14.png){ #fig:014 width=70%, height=70% }

5. Скопируем файл lab9-2.asm, созданный при выполнении лабораторной работы №9, 
с программой выводящей на экран аргументы командной строки. Создадим исполняемый файл.
Для загрузки в gdb программы с аргументами необходимо использовать ключ
--args. Таким образом загрузим исполняемый файл в отладчик, указав аргументы

Для начала установим точку останова перед первой инструкцией в программе
и запустим ее.

Адрес вершины стека храниться в регистре esp и по этому адресу располагается число равное количеству аргументов командной строки (включая имя
программы):
Заметим, что число аргументов равно 5: имя программы lab10-3 и аргумент1, аргумент2 и аргумент3.

Посмотрим остальные позиции стека – по адесу esp+4,
по адесу esp+8, по аресу esp+12, шаг равен размеру переменной, то есть 4 байтам. (рис. [-@fig:015])

![вывод значения регистра](image/15.png){ #fig:015 width=70%, height=70% }

6. Преобразуем программу из лабораторной работы №9, реализовав вычисление значения функции f(x)как подпрограмму. (рис. [-@fig:016] [-@fig:017])

![Файл lab10-4.asm](image/16.png){ #fig:016 width=70%, height=70% }

![Работа программы lab10-4.asm](image/17.png){ #fig:017 width=70%, height=70% }

7. В листинге приведена программа вычисления выражения (3+2)*4+5.
При запуске данная программа дает неверный результат. Необходимо это проверить.
С помощью отладчика GDB, найдем ошибку и исправим ее.(рис. [-@fig:018] [-@fig:019] [-@fig:020] [-@fig:021])

![код с ошибкой](image/18.png){ #fig:018 width=70%, height=70% }

![отладка](image/19.png){ #fig:019 width=70%, height=70% }

Важно заметить, что неправильный порядок аргументов у инструкции add и что по окончании работы в edi вместо eax отправляется ebx

![код исправлен](image/20.png){ #fig:020 width=70%, height=70% }

![проверка работы](image/21.png){ #fig:021 width=70%, height=70% }

# Выводы

Были получены и освоены навыки работы с подпрограммами и отладчиком.
