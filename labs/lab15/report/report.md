---
## Front matter
title: "Лабораторная работа № 15"
subtitle: "Управление логическими томами"
author: "Калашникова Д. В."

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

Получить навыки управления логическими томами.

# Задание

1. Продемонстрировать навыки создания физических томов на LVM 
2. Продемонстрировать навыки создания группы томов и логических томов на LVM 
3. Продемонстрировать навыки изменения размера логических томов на LVM 
4. Выполнить задание для самостоятельной работы 

# Выполнение лабораторной работы

Для начала мы отмонтируем /mnt/data и /mnt/data-ext(рис. [-@fig:001]).

![Отмонтируем](image/1.png){#fig:001 width=70%}

Затем с помощью команды mount мы убедимся что диски /dev/sdb и /dev/sdc не подключены (рис. [-@fig:002]).

![Диски не подключены](image/2.png){#fig:002 width=70%}

Далее сделаем новую разметку для  sdb и  sdc, введем p  для просмотра текущей разметки затем создадим пустую таблицу o для того чтобы удалить все имеющиеся партиции, проверяем что партиции удалены введя p и сохраняем w (рис. [-@fig:003]).

![Создание](image/3.png){#fig:003 width=70%}

Запишем изменения (рис. [-@fig:004]).

![Запись](image/4.png){#fig:004 width=70%}

После чего просматриваем информацию о разделах (рис. [-@fig:005]).

![Просмотр](image/5.png){#fig:005 width=70%}

Теперь создадим новый раздел с типом LVM, введем  n чтобы создать новый раздел выберем основной p и в последнем секторе введем +100М, после чего вернувшись в приглашение fdisk введем t чтобы изменить тип раздела, при запросе о выборе раздела выбераем 8e, после чего записываем изменения w (рис. [-@fig:006]).

![Создание](image/6.png){#fig:006 width=70%}

Затем обновлим страницу разделов (рис. [-@fig:007]).

![Обновление](image/7.png){#fig:007 width=70%}

После того как раздел был создан, укажем его как физический том LVM (рис. [-@fig:008]).

![Физический том](image/8.png){#fig:008 width=70%}

Чтобы убедиться,что физический том создан успешно введем pvs (рис. [-@fig:009]).

![Проверка](image/9.png){#fig:009 width=70%}

Далее открываем новый терминал и переходим в супер пользователя (рис. [-@fig:010]).

![Открытие](image/10.png){#fig:010 width=70%}

Проверяем доступность физических томов в нашей системе (рис. [-@fig:011]).

![Проверка](image/11.png){#fig:011 width=70%}

Далее создаем группу томов с присвоенным ей физическим томом (рис. [-@fig:012]).

![Создание](image/12.png){#fig:012 width=70%}

Проверим, что группа томов была  создана успешно (рис. [-@fig:013]).

![Проверка](image/13.png){#fig:013 width=70%}

После чего создадим логический том LVM с именем lvdata, который будет использовать  только 50% (рис. [-@fig:014]).

![Создание](image/14.png){#fig:014 width=70%}

Для проверки успешного добавления введем lvs (рис. [-@fig:015]).

![Проверка](image/15.png){#fig:015 width=70%}

Далее создадим файловую систему поверх логического тома (рис. [-@fig:016]).

![Создание](image/16.png){#fig:016 width=70%}

Затем создаем папку и в файл /etc/fstab, записываем следующую строку /dev/vgdata/lvdata /mnt/data ext4 defaults 1 2 и проверяем, монтируется ли файловая система (рис. [-@fig:017]).

![Проверка](image/17.png){#fig:017 width=70%}

Затем добавляем новый раздел /dev/sdb2 размером 100 М и тип раздела 8е (рис. [-@fig:019]).

![Добавление](image/19.png){#fig:019 width=70%}

После чего создаем физический том, расширяем его и проверяем, что размер доступных групп томов увеличен и проверяем размер логического тома lvdata (рис. [-@fig:020]).

![Создание](image/20.png){#fig:020 width=70%}

Затем проверяем текущий размер фаловой системы на lvdata (рис. [-@fig:021]).

![Проверка](image/21.png){#fig:021 width=70%}

И увеличиваем lvdata на 50% (рис. [-@fig:022]).

![Увеличение](image/22.png){#fig:022 width=70%}

После чего убеждаемся что добавленное дисковое пространство стало доступным (рис. [-@fig:023]).

![проверка](image/23.png){#fig:023 width=70%}

Затем уменьшаем размер lvdata на 50МБ (рис. [-@fig:024]).

![Уменьшение](image/24.png){#fig:024 width=70%}

И проверяем успешное изменение дискового пространства (рис. [-@fig:025]).

![Проверка](image/25.png){#fig:025 width=70%}

# Контрольные вопросы 

1. Какой тип раздела используется в разделе GUID для работы с LVM?

Ответ: тип раздела 8e00

2. Какой командой можно создать группу томов с именем vggroup, которая содержит физическое устройство /dev/sdb3 и использует физический экстент 4 MiB?

Ответ: командой vgcreate -s 4M vggroup /dev/sdb3

3. Какая команда показывает краткую сводку физических томов в вашей системе, а также группу томов, к которой они принадлежат?

Ответ:  команда  pvs

4. Что вам нужно сделать, чтобы добавить весь жёсткий диск /dev/sdd в группу томов группы?

Ответ: сначало надо создать lVM раздел  pvcreate /dev/sdd и  vgextend "vgname" /dev/sdd

5. Какая команда позволяет вам создать логический том lvvol1 с размером 6 MiB?

Ответ: команда  lvcreate -n lvvol1 -L 6M "vgname"

6. Какая команда позволяет вам добавить 100 МБ в логический том lvvol1, если предположить, что дисковое пространство доступно в группе томов?

Ответ: команда  lvextend -L +100M /dev/"vgname"/lvvol1

7. Каков первый шаг, чтобы добавить ещё 200 МБ дискового пространства в логический том, если требуемое дисковое пространство недоступно в группе томов?

Ответ: добавляем новый физический том pvcreate "device"  и  vgextend "vgname" "device"

8. Какую опцию нужно использовать с командой lvextend, чтобы также изменить размер файловой системы?

Ответ: -r

9. Как посмотреть, какие логические тома доступны?

Ответ: lvs

10. Какую команду нужно использовать для проверки целостности файловой системы на /dev/vgdata/lvdata?

Ответ: команда  fsck /dev/vgdata/lvdata

# Выводы 

В ходе выполнения лабораторной работы я получила навыки управления логическими томами.



# Список литературы{.unnumbered}

::: {#refs}
:::
