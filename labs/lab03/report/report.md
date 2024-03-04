---
## Front matter
title: "Лабораторноя работа №3"
subtitle: "Наисложнейший вариант"
author: "Федотова Ксения Алексеевна"

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

Целью работы является освоение процедуры оформления отчетов с помощью легковесного
языка разметки Markdown.


# Выполнение лабораторной работы

1. Открыла терминал
2. Перешла в каталог курса сформированный при выполнении лабораторной работы:

cd ~/work/study/2023-2024/"Архитектура компьютера"/arch-pc/

Обновите локальный репозиторий, скачав изменения из удаленного репозитория с помощью команды
git pull

3. Перешла в каталог с шаблоном отчета по лабораторной работе № 3

cd ~/work/study/2023-2024/"Архитектура компьютера"/arch-pc/labs/lab03/report

4. Провела компиляцию шаблона с использованием Makefile. Для этого ввела команду:

make

Сгенерировалтсь файлы report.pdf и report.docx.

Открыла и провертла корректность полученных файлов.

5. Удалила полученный файлы с использованием Makefile. Для этого ввела команду:

make clean

Провертла, что после этой команды файлы report.pdf и report.docx были удалены.

6. Откройте файл report.md c помощью текстового редактора gedit:
gedit report.md

Внимательно изучила структуру этого файла.

7. Заполнила отчет и скомпилировала его с использованием Makefile.

8. Загрузила файлы на Github используя команды:

cd ~/work/study/2023-2024/"Архитектура компьютера"/arch-pc
git add .
git commit -am 'feat(main): add files lab-3'
git push


![Общий скриншон со всеми шагами(и ошибками)](image/блаблабла2023-10-1920-02-54.png){#fig:001 width=70%}

9. 1. В соответствующем каталоге сделала отчёт по лабораторной работе № 2 в формате
Markdown.

2. Загрузила файл на github.


# Вывод
Я освоила процедуры оформления отчетов с помощью легковесного
языка разметки Markdown.

:::
