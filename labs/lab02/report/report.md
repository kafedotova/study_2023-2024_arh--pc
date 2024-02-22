---
## Front matter
title: "Лабараторная работа 2"
subtitle: "Простейший вариант"
author: "Федотова Кения Алексеевна"

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

Целью работы является изучить идеологию и применение средств контроля версий. Приобрести практические навыки по работе с системой git.


# Выполнение лабораторной работы

1.Сначала сделала предварительную конфигурацию git. Открыла терминал и ввела
следующие команды, указав имя и email (рис. 1).
git config --global user.name "<Name Surname>"
git config --global user.email "<work@mail>"

2.Настроила utf-8 в выводе сообщений git:
git config --global core.quotepath false

Задала имя начальной ветки (будем называть её master):
git config --global init.defaultBranch master
 Параметр autocrlf:
git config --global core.autocrlf input
 Параметр safecrlf:
git config --global core.safecrlf warn (@fig:001)

3.Генерируем пару ключей Для последующей идентификации(приватный и открытый):
ssh-keygen -C "Имя Фамилия <work@mail>" (@fig:002)
4.Далее загрузила сгенерированный открытый ключ (@fig:003)

5.Открыла терминал и создала каталог для предмета «Архитектура компьютера»:
mkdir -p ~/work/study/2023-2024/"Архитектура компьютера"

6. Перешла на станицу репозитория с шаблоном курса https://github.com/yamadharma/cour
se-directory-student-template(какой-то рисуонк)

7.Откроыла терминал и перешла в каталог курса:
cd ~/work/study/2023–2024/"Архитектура компьютера"

8.Клонировала созданный репозиторий:
git clone --recursive git@github.com:<user_name>/study_2023–2024_arh-pc.git
↪ arch-pc

9.Настройка каталога курса
Перешла в каталог курса:
cd ~/work/study/2023-2024/"Архитектура компьютера"/arch-pc
Настройка каталога курса

Удалила лишние файлы:
rm package.json

Создала необходимые каталоги:
echo arch-pc > COURSE
make
Отправивила файлы на сервер:
git add .
git commit -am 'feat(main): make course structure'
git push


@fig:004
@fig:005

![рисунок 1](image/Снимок экрана от 2023-10-05 19-03-18){#fig:001 width=70%}
![рисунок 2](image/Снимок экрана от 2023-10-05 20-46-26){#fig:002 width=70%}
![рисунка 3](image/Снимок экрана от 2023-10-05 20-46-33){#fig:003 width=70%}
![рисунок 4](image/Снимок экрана от 2023-10-05 20-46-36){#fig:004 width=70%}
![рисунок 5](image/Снимок экрана от 2023-10-19 19-32-26){#fig:005 width=70%}

# Выводы

Я изучила идеологию и применение средств контроля версий. Приобрести практические навыки по работе с системой git.


