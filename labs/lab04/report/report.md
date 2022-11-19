---
## Front matter
title: "Отчёта по лабораторной работе 4"
subtitle: "Язык разметки Markdown"
author: "Дудырев Г. А. НПИбд-01-22"

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

Целью работы является освоение процедуры оформления отчетов с помощью легковесного языка разметки Markdown.

# Задание

1. В соответствующем каталоге сделайте отчёт по лабораторной работе № 3 в формате Markdown. 
В качестве отчёта необходимо предоставить отчёты в 3 форматах: pdf, docx и md.

2. Загрузите файлы на github.

# Теоретическое введение

Markdown — язык текстовой разметки, созданный писателем и блогером Джоном Грубером. 
Он предназначен для создания красиво оформленных текстов в обычных файлах формата TXT. 
Вам не нужны громоздкие процессоры вроде Word или Pages, чтобы создавать документы с 
жирным или курсивным начертанием, цитатами, ссылками и даже таблицами. 
Достаточно запомнить простые правила Markdown, и можно писать хоть в «Блокноте». 
Хотя специализированные Markdown-редакторы, конечно, намного удобнее.

# Выполнение лабораторной работы

Установили программы pandoc и TexLive по указаниям в лабораторной работе. 

1. Откройте терминал

2. Перейдите в каталог курса сформированный при выполнении лабораторной работы №3:
Обновите локальный репозиторий, скачав изменения из удаленного репозитория.

3. Перейдите в каталог с шаблоном отчета по лабораторной работе № 4

4. Проведите компиляцию шаблона с использованием Makefile. 
Для этого введите команду make.
При успешной компиляции должны сгенерироваться файлы report.pdf и
report.docx. Откройте и проверьте корректность полученных файлов. (рис. [-@fig:001], [-@fig:002], [-@fig:003])

![Команда компиляции](image/01.png){ #fig:001 width=70%, height=70% }

![Файл отчета в docx](image/02.png){ #fig:002 width=70%, height=70% }

![Файл отчета в pdf](image/03.png){ #fig:003 width=70%, height=70% }


5. Удалите полученный файлы с использованием Makefile. Для этого введитекоманду make clean
Проверьте, что после этой команды файлы report.pdf и report.docx были удалены. (рис. [-@fig:004])

![Удалены файлы шаблона](image/04.png){ #fig:004 width=70%, height=70% }

6. Откройте файл report.md c помощью любого текстового редактора, например gedit
Внимательно изучите структуру этого файла. (рис. [-@fig:005])

![Структура шаблона](image/05.png){ #fig:005 width=70%, height=70% }

7. Заполните отчет и скомпилируйте отчет с использованием Makefile. 
Проверьте корректность полученных файлов. (рис. [-@fig:006])
(Обратите внимание, для корректного отображения скриншотов они должны быть размещены в каталоге image)

![Заполняем шаблон](image/06.png){ #fig:006 width=70%, height=70% }

8. Загрузите файлы на Github.

# Выводы

Изучили как работать с языком Markdown и как создавать отчет из шаблона.

# Список литературы{.unnumbered}

1. [Что такое Markdown и как им пользоваться](https://lifehacker.ru/chto-takoe-markdown/)
