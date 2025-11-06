---
## Front matter
title: "Лабораторная работа № 10"
subtitle: "Основы работы с модулями ядра операционной системы"
author: "Калашникова Дарья"

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
Платформа plvideo все также не работает, все видео выложены на две другие платформы (рис. [-@fig:001]).

![Технические работы](image/11.png){#fig:011 width=70%}

# Цель работы

Получить навыки работы с утилитами управления модулями ядра операционной системы

# Задание

Продемонстрировать навыки работы по управлению модулями ядра, а также по загрузке модулей ядра с параметрами 

# Выполнение лабораторной работы

Запускаем полномочия администратора. Смотрим, какие устройства имеются в вашей системе и какие модули ядра с ними связаны: lspci -k (рис. [-@fig:001]).

![Запуск](image/1.png){#fig:001 width=70%}

Команда lspci -k отображает список всех PCI-устройств в системе, а также информацию о том, какие драйверы ядра и модули с ними связаны. Это позволяет роанализировать как операционная система взаимодействует с “железом”.

Посмотрим, какие модули ядра загружены:lsmod | sort (рис. [-@fig:002]).

![Просмотр](image/2.png){#fig:002 width=70%}

Посмотрим, загружен ли модуль ext4: lsmod | grep ext4. Загрузим модуль ядра ext4: modprobe ext4. Убедимся, что модуль загружен, посмотрев список загруженных модулей: lsmod | grep ext4 (рис. [-@fig:003]).

![Просмотр](image/3.png){#fig:003 width=70%}

Команда modinfo отображает информацию о модуле ядра Linux. В данном случае мы исследуем модуль ext4, который отвечает за поддержку одноименной файловой системы (рис. [-@fig:004]).

![Просмотр](image/4.png){#fig:004 width=70%}

После пробуем выгрузить модуль ядра ext4, мы увидим что нам система сообщает что не может выгрузить ext4 потому что от него зависит другой модуль cr32c_intel который в данный момент используется. Ядро Linux не позволяет выгрузить модуль от которого зависят другие активные модули,чтобы избежать сбоев.Затем пробуем выгрузить модуль ядра xfs (рис. [-@fig:005]).

![Выгрузка](image/5.png){#fig:005 width=70%}

Посмотрим, загружен ли модуль bluetooth: lsmod | grep bluetooth. Загрузим модуль ядра bluetooth: modprobe bluetooth. Также посмотрим список модулей ядра, отвечающих за работу Bluetooth:lsmod | grep bluetooth. И посмотрите информацию о модуле bluetooth: modinfo bluetooth, а также выгрузим модуль ядра bluetooth: modprobe -r bluetooth (рис. [-@fig:006]).

![Выгрузка](image/6.png){#fig:006 width=70%}

Команда отображает информацию о модуле ядра,отвечающем за работу
Bluetooth-стека в системе. В выводе команды содержатся параметры, которые могут быть установлены для настройки работы этого модуля

Посмотрим версию ядра, используемую в операционной системе:uname -r. Выведем на экран список пакетов, относящихся к ядру операционной системы: dnf list kernel (рис. [-@fig:007]).

![Просмотр](image/7.png){#fig:007 width=70%}

Обновиим систему, чтобы убедиться, что все существующие пакеты обновлены, так как это важно при установке/обновлении ядер Linux и избежания конфликтов:dnf upgrade --refresh (рис. [-@fig:008]).

![Обновление](image/8.png){#fig:008 width=70%}

Обновите ядро операционной системы, а затем саму операционную систему: dnf update kernel, dnf update, dnf upgrade --refresh (рис. [-@fig:009]).

![Обновление](image/9.png){#fig:009 width=70%}

Перегрузите систему и посмотрим версию ядра, используемую в операционной системы: uname -r, hostnamectl (рис. [-@fig:010]).

![Версия](image/10.png){#fig:010 width=70%}

# Контрольные вопросы

1. Какая команда показывает текущую версию ядра, которая используется на вашей системе?

Ответ: команда uname -r

2. Как можно посмотреть более подробную информацию о текущей версии ядра операционной системы?

Ответ: чтобы просмотреть более подробную информацию о текущей версии ядра операционной системы командой uname -a

3. Какая команда показывает список загруженных модулей ядра?

Ответ: команда lsmod

4. Какая команда позволяет вам определять параметры модуля ядра?

Ответ: команда modinfo “имя_модуля”

5. Как выгрузить модуль ядра?

Ответ: с помощью команды modprobe -r “имя_модуля”

6. Что вы можете сделать, если получите сообщение об ошибке при попытке выгрузить модуль ядра?

Ответ: при ошибки выгрузки модуля надо проверить зависимость lsmod | grep “модуль”,размонтировать связанные файловые системы, остановить используеющие сервисы и выгрузить зависимые модули

7. Как определить, какие параметры модуля ядра поддерживаются?

Ответ: определение поддерживаемых параметров командой modinfo “имя_модуль”

8. Как установить новую версию ядра?

Ответ: установка новой версии ядра через пакетный менеджер или обновление дистрибутива, после чего перезагружаем систему

# Выводы

После выполнения лабораторной работы я получила навыки работы с утилитами управления модулями ядра операционной системы

# Список литературы{.unnumbered}

::: {#refs}
:::
