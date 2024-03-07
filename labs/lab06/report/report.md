---
## Front matter
title: "Отчёта по лабораторной работе №6"
subtitle: "Простейший вариант"
author: "Федоотова Ксения Алексеевна"

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

Освоение арифметических инструкций языка ассемблера NASM.

# Задание

. Создайте каталог для программам лабораторной работы № 6, перейдите в него и
создайте файл lab6-1.asm:
mkdir ~/work/arch-pc/lab06
cd ~/work/arch-pc/lab06
touch lab6-1.asm
Демидова А. В. 63
Архитектура ЭВМ
2. Рассмотрим примеры программ вывода символьных и численных значений. Программы будут выводить значения записанные в регистр eax.
Введите в файл lab6-1.asm текст программы из листинга 6.1. В данной программе в регистр eax записывается символ 6 (mov eax,'6'), в регистр ebx символ 4 (mov ebx,'4').
Далее к значению в регистре eax прибавляем значение регистра ebx (add eax,ebx, результат сложения запишется в регистр eax). Далее выводим результат. Так как для работы
функции sprintLF в регистр eax должен быть записан адрес, необходимо использовать дополнительную переменную. Для этого запишем значение регистра eax в переменную buf1
(mov [buf1],eax), а затем запишем адрес переменной buf1 в регистр eax (mov eax,buf1) и
вызовем функцию sprintLF.
Листинг 6.1. Программа вывода значения регистра eax
%include 'in_out.asm'
SECTION .bss
buf1: RESB 80
SECTION .text
GLOBAL _start
_start:
mov eax,'6'
mov ebx,'4'
add eax,ebx
mov [buf1],eax
mov eax,buf1
call sprintLF
call quit
Создайте исполняемый файл и запустите его.
nasm -f elf lab6-1.asm
ld -m elf_i386 -o lab6-1 lab6-1.o
./lab6-1
ВАЖНО! Для корректной работы программы подключаемый файл in_out.asm должен
лежать в том же каталоге, что и файл с текстом программы. Перед созданием исполняемого файла создайте копию файла in_out.asm в каталоге ~/work/arch-pc/lab06.
В данном случае при выводе значения регистра eax мы ожидаем увидеть число 10. Однако
результатом будет символ j. Это происходит потому, что код символа 6 равен 00110110 в
двоичном представлении (или 54 в десятичном представлении), а код символа 4 – 00110100
64 Демидова А. В.
Архитектура ЭВМ
(52). Команда add eax,ebx запишет в регистр eax сумму кодов – 01101010 (106), что в свою
очередь является кодом символа j (см. таблицу ASCII в приложении).
3. Далее изменим текст программы и вместо символов, запишем в регистры числа. Исправьте текст программы (Листинг 6.1) следующим образом: замените строки
mov eax,'6'
mov ebx,'4'
на строки
mov eax,6
mov ebx,4
Создайте исполняемый файл и запустите его.
Как и в предыдущем случае при исполнении программы мы не получим число 10. В данном
случае выводится символ с кодом 10. Пользуясь таблицей ASCII определите какому символу
соответствует код 10. Отображается ли этот символ при выводе на экран?
4. Как отмечалось выше, для работы с числами в файле in_out.asm реализованы подпрограммы для преобразования ASCII символов в числа и обратно. Преобразуем текст
программы из Листинга 6.1 с использованием этих функций.
Создайте файл lab6-2.asm в каталоге ~/work/arch-pc/lab06 и введите в него текст программы из листинга 6.2.
touch ~/work/arch-pc/lab06/lab6-2.asm
Листинг 6.2. Программа вывода значения регистра eax
%include 'in_out.asm'
SECTION .text
GLOBAL _start
_start:
mov eax,'6'
mov ebx,'4'
add eax,ebx
call iprintLF
call quit
Создайте исполняемый файл и запустите его.
Демидова А. В. 65
Архитектура ЭВМ
nasm -f elf lab6-2.asm
ld -m elf_i386 -o lab6-2 lab6-2.o
./lab6-2
В результате работы программы мы получим число 106. В данном случае, как и в первом,
команда add складывает коды символов ‘6’ и ‘4’ (54+52=106). Однако, в отличии от программы
из листинга 6.1, функция iprintLF позволяет вывести число, а не символ, кодом которого
является это число.
5. Аналогично предыдущему примеру изменим символы на числа. Замените строки
mov eax,'6'
mov ebx,'4'
на строки
mov eax,6
mov ebx,4
Создайте исполняемый файл и запустите его. Какой результат будет получен при исполнении программы?
Замените функцию iprintLF на iprint. Создай файл lab6-2.asm в каталоге ~/work/arch-pc/lab06 и введите в него текст программы из листинга 6.2.
touch ~/work/arch-pc/lab06/lab6-2.asm
Листинг 6.2. Программа вывода значения регистра eax
%include 'in_out.asm'
SECTION .text
GLOBAL _start
_start:
mov eax,'6'
mov ebx,'4'
add eax,ebx
call iprintLF
call quit
Создайте исполняемый файл и запустите его.
Демидова А. В. 65
Архитектура ЭВМ
nasm -f elf lab6-2.asm
ld -m elf_i386 -o lab6-2 lab6-2.o
./lab6-2
В результате работы программы мы получим число 106. В данном случае, как и в первом,
команда add складывает коды символов ‘6’ и ‘4’ (54+52=106). Однако, в отличии от программы
из листинга 6.1, функция iprintLF позволяет вывести число, а не символ, кодом которого
является это число.
5. Аналогично предыдущему примеру изменим символы на числа. Замените строки
mov eax,'6'
mov ebx,'4'
на строки
mov eax,6
mov ebx,4
Создайте исполняемый файл и запустите его. Какой результат будет получен при исполнении программы?
Замените функцию iprintLF на iprint. Создайте исполняемый файл и запустите его. Чем
отличается вывод функций iprintLF и iprint

# Выполнение лабораторной работы

1. Создала каталог для программам лабораторной работы № 6, перешда в него и создала файл lab6-1.asm:


2. Рассмотрела примеры программ вывода символьных и численных значений. Программы будут выводить значения, записанные в регистр eax.

3. Как отмечалось выше, для работы с числами в файле in_out.asm реализованы подпрограммы для преобразования ASCII символов в числа и обратно. Преобразуем текст программы с использованием этих функций.



В результате работы программы мы получим число 106. В данном случае, как и в первом, команда add складывает коды символов 6 и 4 (54+52=106). Однако, в отличии от прошлой программы, функция iprintLF позволяет вывести число, а не символ, кодом которого является это число.

4. Аналогично предыдущему примеру изменила символы на числа.
Создайте исполняемый файл и запустите его. Какой результат будет получен при исполнении программы? – получили число 10

![Название рисунка](image/placeimg_800_600_tech.jpg){#fig:001 width=70%}
![Название рисунка](image/placeimg_800_600_tech.jpg){#fig:002 width=70%}
![Название рисунка](image/placeimg_800_600_tech.jpg){#fig:003 width=70%}
![Название рисунка](image/placeimg_800_600_tech.jpg){#fig:004 width=70%}
![Название рисунка](image/placeimg_800_600_tech.jpg){#fig:005 width=70%}
![Название рисунка](image/placeimg_800_600_tech.jpg){#fig:006 width=70%}


# Выводы

Я освоила арифметических инструкций языка ассемблера NASM.

# Список литературы{.unnumbered}

::: {#refs}
:::
