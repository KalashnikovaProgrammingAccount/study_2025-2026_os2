---
## Front matter
title: "Отчёт о лабораторной работе"
subtitle: "Лабораторная работа № 1"
author: "Калашникова Дарья Викторовна"

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
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:
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

Установить Linux Rocky и ознакомиться с его возможностями

# Задание

Установить ОС и выполнить домашнее задание

# Выполнение лабораторной работы

Для начала назовем нашу виртуальную машину и выберем место установки (рис. [-@fig:001]).

![Выбор диска](image/1.png){#fig:001 width=70%}

Выделяем основную память и процессоры (рис. [-@fig:002]).

![Выделение памяти и процессоров](image/2.png){#fig:002 width=70%} 

Выделяем 40 ГБ для виртуального жесткого диска (рис. [-@fig:003]).

![Выделение памяти для диска](image/3.png){#fig:003 width=70%}

Выбираем английский язык для интерфейса (рис. [-@fig:004]).

![Установка английского языка интерфейса ОС](image/4.png){#fig:004 width=70%}

Отключаем KDUMP (рис. [-@fig:005]).

![Отключение KDUMP](image/6.png){#fig:005 width=70%}

Далее мы устанавливаем настройки: выбор программ (рис. [-@fig:006]).

![Окно настройки установки](image/10.png){#fig:006 width=70%}

Теперь мы выбираем место установки диска (рис. [-@fig:007]).

![Окно с местом установки](image/5.png){#fig:007 width=70%}

Включаем сетевое соединение с именем узла dvkalashnikova.localdomain (рис. [-@fig:008]).

![Окно настройки установки сети и имени узла](image/7.png){#fig:008 width=70%}

Устанавливаем пароль для root и разрешение на ввод пароля root при использовании SSH (рис. [-@fig:009]).

![Установка пароля для root](image/8.png){#fig:009 width=70%}

Задаем локального пользователя с правами администратора (рис. [-@fig:010]).

![Установка пароля для пользователя с правами администратора](image/9.png){#fig:010 width=70%}

Далее нажимаем Begin Installation для установки (рис. [-@fig:011]).

![Установка](image/11.png){#fig:011 width=70%}

Завершение установки ОС (рис. [-@fig:012]).

![Завершение установки](image/12.png){#fig:012 width=70%}

Дальше нужно подключить образ диска дополнительной гостевой ОС (рис. [-@fig:013]).

![Подключение дополнительного образа диска гостевой ОС](image/13.png){#fig:013 width=70%}

Тепрь мы запускаем образ этого диска (рис. [-@fig:014]).

![Запуск дополнительного образа диска гостевой ОС](image/14.png){#fig:014 width=70%}

Далее приступаем к выполнению домашнего задания

Получаем информацию о версии ядра Linux (Linux version) (рис. [-@fig:015]).

![Версия ядра Linux](image/15.png){#fig:015 width=70%}

Получаем информацию о частоте процессора (Detected Mhz processor) (рис. [-@fig:016]).

![Частота процессора](image/16.png){#fig:016 width=70%}

Получаем информацию о моделе процессора (CPU0) (рис. [-@fig:017]). 

![Модель процессора](image/17.png){#fig:017 width=70%}

Получаем информацию об бъеме доступной оперативной памяти (Memory available) (рис. [-@fig:018]).

![Объем доступной оперативной памяти](image/18.png){#fig:018 width=70%}

Получаем информацию о типе обнаруженного гипервизора (Hypervisor detected) (рис. [-@fig:019]).

![Тип обнаруженного гипервизора](image/19.png){#fig:019 width=70%}

Получаем информацию о типе файловой системы корневого раздела (XFS) и последовательность монтирования файловых систем (рис. [-@fig:020]).

![Тип файловой системы корневого раздела и последовательсть монтирования файловых систем](image/20.png){#fig:020 width=70%}

# Выводы

В результате выполнения работы была установлена система

# Список литературы{.unnumbered}

::: {#refs}
:::
