---
## Front matter
title: "Отчёт по лабораторной работе №6"
author: "Олег Россохин"

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

Приобретение практических навыков работы в Midnight Commander. Освоение
инструкций языка ассемблера mov и int.

# Теоретическое введение

## Основы работы с Midnight Commander

Midnight Commander — это программа, которая позволяет просматривать структуру каталогов и выполнять основные операции по управлению файловой системой, т.е. mc является файловым менеджером. Midnight
Commander позволяет сделать работу с файлами более удобной и наглядной по сравнению с терминалом.

# Выполнение лабораторной работы

1. Откроем Midnight Commander
![1](https://sun1-28.userapi.com/impg/MDvdgXoYQhJ_Y1qtbpkJPpjxEUKuEO0KdVAJfw/f6EVc8JCnIs.jpg?size=653x484&quality=96&sign=d3e965190b6d7ec044e562677da21b33&type=album)

2. Пользуясь клавишами ↑ , ↓ и Enter перейдем в каталог ~/work/arch-pc, созданный при выполнении лабораторной работы №5
![2](https://sun1-19.userapi.com/impg/vkf6-l9x1X8eE-5KReXNj0I5yxdbNvyMZT4now/PMhMPuk1UFE.jpg?size=654x482&quality=96&sign=b7476931dfea823e6594e39ac5bf8198&type=album)

3. С помощью клавиши F7 создадим папку lab06 и перейдем в созданный каталог
![3](https://sun9-55.userapi.com/impg/F9uqOmQT5SGUSD1MGMMk2Tr16S87WR7m-wQgkA/dogASHuKmek.jpg?size=654x485&quality=96&sign=36cf342250e85a44cba2bf167fa6cdff&type=album)

4. Пользуясь строкой ввода и командой touch создадим файл lab6-1.asm
![4](https://sun9-47.userapi.com/impg/JnOYgJlaxG7soZ7ltXbgv2pTpL7WLECFOh-LrQ/rIE7zGyeC-E.jpg?size=653x191&quality=96&sign=a0890330efbeb16b1fa810e904206332&type=album)

5. С помощью клавиши F4 откроем файл lab6-1.asm для редактирования
![5](https://sun9-2.userapi.com/impg/cusrKtI1o-HfmQoOIo5SBeyG_qRIeFWvPNOz0A/1BefOXwoPbQ.jpg?size=655x480&quality=96&sign=b173a7f7b3768d71c8e1de8be85d7653&type=album)

6. Введем текст программы вывода сообщения на экран, сохраним изменения и закроем файл
![6](https://sun9-60.userapi.com/impg/-j5RRe8q85Gg6aaawx5dVS6PetBYu6NugzvHGg/kpVD6Hv-c_s.jpg?size=659x676&quality=96&sign=4a055db057d7282452fa4ea3ec0d5674&type=album)

7. С помощью клавиши F3 откроем файл lab6-1.asm для просмотра и убедимся, что файл содержит текст программы
![7](https://sun9-60.userapi.com/impg/-j5RRe8q85Gg6aaawx5dVS6PetBYu6NugzvHGg/kpVD6Hv-c_s.jpg?size=659x676&quality=96&sign=4a055db057d7282452fa4ea3ec0d5674&type=album)

8. Оттранслируем текст программы lab6-1.asm в объектный файл. Далее выполним компоновку объектного файла и запустим получившийся исполняемый
файл. Программа напишет 'Введите строку:' и будет ожидать ввода текста с клавиатуры. На запрос введу свои ФИО.
![8](https://sun9-6.userapi.com/impg/z_uTk3nNCKSayHnIigKhZYnk7FTKhY1-32iyIA/jw6V0N2L5po.jpg?size=655x479&quality=96&sign=64517f3ea7d6bc9779ba2d85e811d6dc&type=album)

## Подключение внешнего файла in_out.asm

9-10. Скачаем файл in_out.asm и с помощью MC и клавиши F6 переместим его в каталог с программой lab6-1.asm.
![9-10](https://sun9-39.userapi.com/impg/TNOnvj_aT3jFLL59MjKlTrGEj3S3pPvpCckU1A/w2IBt1KbQGw.jpg?size=657x521&quality=96&sign=d26b14c9410d5876545a275fe767b304&type=album)

11. С помощью клавиши F5 создадим копию файла lab6-1.asm с именем lab6-2.asm.
![11](https://sun9-81.userapi.com/impg/NNDcL7b8tXLLIAoN6stxBGr1jtnrtXzn_oLByQ/3V48g2LceeU.jpg?size=655x480&quality=96&sign=41db284144e6147aab9142fa283bf40a&type=album)

12. Исправим текст программы в файле lab6-2.asm с использование подпрограмм из внешнего файла in_out.asm. Создадим исполняемый файл и проверим его работу.
![12](https://sun9-66.userapi.com/impg/kCrtVC0zIyfLgx-KK-Y_mZfMgg5Ndf2Ict7Rag/eFSG36tHRvw.jpg?size=655x481&quality=96&sign=d19a5cd324e05760d23071a238b8821c&type=album)
![12_1](https://sun9-78.userapi.com/impg/BKTl9z687IkolVCuQxn0QC1u-ETfPnvRi1WtJQ/_f_ef2leCmg.jpg?size=656x524&quality=96&sign=8bfe1b923637bc01a7088798268f2627&type=album)

13.В файле lab6-2.asm заменим подпрограмму sprintLF на sprint. Создадим исполняемый файл и проверим его работу. *В чем разница?*
![13](https://sun9-81.userapi.com/impg/KF-CX68J8LRqVSs9pqaxUiyp6kZWu2l84fZXuA/6uMSBstv4kM.jpg?size=657x520&quality=96&sign=23864c20895fbe9aec43abd14c139197&type=album)
![13_1](https://sun9-50.userapi.com/impg/4YR22OHPCluAcTroe0lHzqzteUtoU_O0T8dMug/C_rnnBJS1LQ.jpg?size=659x513&quality=96&sign=31a55341544d6b651e77b972e31ef087&type=album)

заметим, что разница двух команд sprint и sprintLF заключается в переносе строки.

# Самостоятельная работа

1-2. Создайте копию файла lab6-1.asm. Внесите изменения в программу (без
использования внешнего файла in_out.asm), так чтобы она работала по
следующему алгоритму:
• вывести приглашение типа “Введите строку:”;
• ввести строку с клавиатуры;
• вывести введённую строку на экран.
Затем получите исполняемый файл и проверьте его работу. На приглашение
ввести строку введите свою фамилию.
	![a](https://sun9-32.userapi.com/impg/hDMiVYrr-XcX2nzycstdPSbgBwLsoC6rLIrrUA/RUNlPoEJ72I.jpg?size=748x651&quality=96&sign=768aedf7258a6d56547af68437b7d2c1&type=album)
	![b](https://sun1-23.userapi.com/impg/XX5T65wYgwxcztIGbo7uRNZI4kR8RvBJqWCNDQ/drGvYviejng.jpg?size=656x372&quality=96&sign=d3857a6f6439bf02b528aab90e878755&type=album)	

3-4. Создайте копию файла lab6-2.asm. Исправьте текст программы с исполь-
зование подпрограмм из внешнего файла in_out.asm, так чтобы она ра-
ботала по следующему алгоритму:
• вывести приглашение типа “Введите строку:”;
• ввести строку с клавиатуры;
• вывести введённую строку на экран.
Создайте исполняемый файл и проверьте его работу.
	![a](https://sun9-71.userapi.com/impg/fpiOTXNIIieQ4AUZ5bepWu_kBTZ8hfPgogRkQw/lnZpHCylF3U.jpg?size=746x573&quality=96&sign=3ae20489f9cd92cbe6b18c6f20d83723&type=album)
	![b](https://sun9-88.userapi.com/impg/Z5ONszpnEssF1xOxgTRPdcXQ58unP7oCCp7TWA/sopGnHh1uOg.jpg?size=658x297&quality=96&sign=d7391e9a7634b01d7f9d63813d7465f7&type=album)

# Вопросы для самопроверки

1. Каково назначение mc?

	1. Midnight Commander - программа, позволяющая просмотреть структуру каталогов и выполнить основные операции по управлению файловой системой.

2. Какие операции с файлами можно выполнить как с помощью команд bash, так и с помощью меню (комбинаций клавиш) mc? Приведите несколько
примеров.
	1. Как с помощью команды cd в 		**bash** можно перейти в нужный каталог, так и в **mc** это можно сделать с помощью клавиш.  
	2. Копирование файла осуществляется как в **bash** командой cp, так и в **mc** клавишей F5 
	3. Перемещение файла в **bash** осуществляется командой mv, а в **mc** - клавишей F6.

3. Какова структура программы на языке ассемблера NASM?

	3. Программа на языке ассемблера NASM, как правило, состоит из трёх секций: SECTION .text(код программы); SECTION .data(секция инициализированных данных); SECTION .bss(секция неинициализированных данных).

4. Для описания каких данных используются секции bss и data в языке ассемблера NASM?
	1. SECTION .data содержит переменные, для которых задано начальное значение.
	2. SECTION .bss используется содержит переменные, для которых **не** задано начальное значение.

5. Для чего используются компоненты db, dw, dd, dq и dt языка ассемблера
NASM?
	1. db - определяет переменную размером в 1 байт;
	2. dw - определяет переменную размеров в 2 байта(слово);
	3. dd - определяет переменную размером в 4 байта(двойное слово);
	4. dq - определяет переменную размером в 8 байт;
	5. dt - определяет переменную размером в 10 байт.

6. Какое произойдёт действие при выполнении инструкции mov eax, esi?
	1. mov **eax**, **esi** перешлет значение регистра **esi** в регистр **eax**
7. Для чего используется инструкция int 80h?
	1. Инструкция int 80h используется для выполнения системного вызова какой-либо функции ядра Linux. 
При этом происходит передача управления ядру операционной системы. Чтобы узнать, какую именно системную функцию нужно выполнить, ядро извлекает номер системного вызова из регистра eax. Поэтому перед вызовом прерывания необходимо поместить в этот регистр нужный номер.
# Выводы

По итогам проделанной работы мы приобрели навыки работы с Midnight Commander, а также освоили некоторые инструкции языка ассемблер.

# Список литературы{.unnumbered}

::: {#refs}
:::	https://esystem.rudn.ru/pluginfile.php/1584633/mod_resource/content/1/%D0%9B%D0%B0%D0%B1%D0%BE%D1%80%D0%B0%D1%82%D0%BE%D1%80%D0%BD%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%20%E2%84%966.pdf
