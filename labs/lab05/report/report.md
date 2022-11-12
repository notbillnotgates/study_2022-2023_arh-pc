---
## Front matter
title: "Лабораторная работа №5"

subtitle: "Создание и
процесс обработки программ на языке
ассемблера NASM"

author: "Россохин Олег"

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

Освоение процедуры компиляции и сборки программ, написанных на ассемблере NASM.

# Теоретическое введение

Основными функциональными элементами любой электронно-вычислительной
машины (ЭВМ) являются центральный процессор, память и периферийные
устройства.
Взаимодействие этих устройств осуществляется через общую шину, к которой они подключены. Физически шина представляет собой большое количество проводников, соединяющих устройства друг с другом. В современных компьютерах проводники выполнены в виде электропроводящих дорожек на материнской (системной) плате.

Язык ассемблера (assembly language) — представление команд процессора в виде, доступном для чтения человеком. Язык ассемблера считается языком программирования низкого уровня, в противовес высокоуровневым языкам, не привязанным к конкретной реализации вычислительной системы. Программы, написанные на языке ассемблера однозначным образом переводятся в инструкции конкретного процессора и в большинстве случаев не могут быть перенесены без значительных изменений для запуска на машине с другой системой команд. Ассемблером называется программа, преобразующая код на языке ассемблера в машинный код; программа, выполняющая обратную задачу называется дизассемблером.

# Выполнение лабораторной работы

## Программа Hello world!
**1.** Создадим каталог для работы с программами на языке ассемблера NASM и перейдем в него:

![1](https://sun9-85.userapi.com/impg/EA_MynOyIPhzR_z8yy59xrgnoqto-Q9fqoRqXA/xsx02oFpI-4.jpg?size=651x180&quality=96&sign=eed8170cdafd0e3b471665f9779500fd&type=album)
я создал отдельный каталог nasm в директории lab05.

**2.** Создадим текстовый файл с именем hello.asm и пропишем в нем следующие команды:

![2](https://sun9-1.userapi.com/impg/4fiD4HMzxDPIQbctLeqbjRgPtHnHC9eot1dMCg/5UnC2oq49-E.jpg?size=654x516&quality=96&sign=3e9171a2d05b9cb25e6190b676ac1d42&type=album)

Далее для компиляции файла пропишем в терминале команду а также сразу проверим, создался ли в папке результат компиляции: 

![3](https://sun9-56.userapi.com/impg/CaGptaP9DrsrZoP--3jOMix4PI_BQz4RK_Dp6Q/zjoF3xnrXO8.jpg?size=652x155&quality=96&sign=735cf2c64b0563d4f538c555ff2bfe48&type=album)

Как мы видим, появился новый файл *hello.o*.

**3.** Далее выполним следующую команду для компиляции файла *hello.asm* в *obj.o* и проверим, что файлы были созданы:

![3](https://sun9-37.userapi.com/impg/klkXOSETvOVogMQMS_LVWVovBrA4fE2N12csfg/yO1VGY5a4nc.jpg?size=653x130&quality=96&sign=eb90ae6d11cf56b3d791440cd70cfea2&type=album)

Данна команда скомпилировала файл *hello.asm* в *obj.o* при помощи опции -о, при этом формат файла elf, в него включены символы для отладки с помощью опции -g, а также, создан файл листинга *list.lst* с помощью опции -l.

**4.** Чтобы получить исполняемую программу,
объектный файл необходимо передать на обработку компановщику:

![4](https://sun9-75.userapi.com/impg/1Tg7bZzgz5ge7PNxTRX-g75uikOAcHadh5njSw/zhtzybqHVWs.jpg?size=654x175&quality=96&sign=bec594ff3c61ee6d2f675f4a8ec25106&type=album)

Несмотря на ошибку, файл создался.

Далее выполним команду:

![4.1](https://sun9-14.userapi.com/impg/bLQQyQqpBVtGGkTuHckKvnPERxEaLl95ORtk4A/e_bjtC6Gs9E.jpg?size=651x179&quality=96&sign=122d50304af1403d5d5acf50fa35af07&type=album)

Видим, что имя исполняемого файла *obj.o*, а объектного файла *main*, потому что перед ним стоит опция -o.

**5.** *Позже обратил внимание на разрядность дистрибутива и проделал те же операции, но для 64-бит системы.*
**Запустим созданный исполняемый файл**

![5](https://sun1-47.userapi.com/impg/WM_VLn-LK-7FmN-2n5xovhfr8W-tu4Y5e3Jtaw/XP8WThORbCw.jpg?size=654x196&quality=96&sign=fdba8845c2db1c8e9665feba98c4a65d&type=album)

# Задание для самостоятельной работы

**1.**В каталоге ~/work/arch-pc/lab05 с помощью команды cp создайте копию
файла hello.asm с именем lab5.asm

![1](https://sun9-87.userapi.com/impg/yXmb8PKEvR3RNACBnoRGVhEs9J4XJRJwAMmoew/HDr_C_BemA4.jpg?size=653x139&quality=96&sign=29601d2b39f15b09f2b42d0a41fff245&type=album)

**2, 3** С помощью любого текстового редактора внесите изменения в текст программы в файле lab5.asm так, чтобы вместо Hello world! на экран выводилась строка с вашими фамилией и именем;
Оттранслируйте полученный текст программы lab5.asm в объектный
файл. Выполните компоновку объектного файла и запустите получивший-
ся исполняемый файл

![2](https://sun9-3.userapi.com/impg/oBfujEj9F88HEpi2OXJkAdFzAqw8KjVgRlTCeQ/5Aau-zSk62c.jpg?size=654x219&quality=96&sign=c1a94bb8da63d5cef442490ec6004962&type=album)

**4.** Скопируйте файлы hello.asm и lab5.asm в Ваш локальный репозиторий
в каталог ~/work/study/2022-2023/"Архитектура компьютера"/arch-
pc/labs/lab05/. Загрузите файлы на Github.

![4](https://sun9-80.userapi.com/impg/PpC3nEXqJkSqoNQrbys_OR3HtGq7v010Um-oHQ/78ZaiLdTC2c.jpg?size=654x159&quality=96&sign=8ccf4802842e8858936229e9358d9061&type=album) 

# Вопросы для самопроверки

**1.** *Какие основные отличия ассемблерных программ от программ на языках высокого уровня?*

Основные отличия заключаются в том, что ассемблерная программа обращается напрямую к ядру ОС и содержит только тот код, который ввел программист. 

2. *В чём состоит отличие инструкции от директивы на языке ассемблера?*

Отличие состоит в том, что директива -не переводящаяся в машинную команду инструкция, а управляющая работой транслятора. Она используется для определения данных и пишется большими буквами.



3. *Перечислите основные правила оформления программ на языке ассем-
блера.*

Чтобы писать программы на ассемблере, нужно знать, какие регистры процессора существуют и как их можно использовать.
Доступ к регистрам осуществляется не по адресам, как к основной памяти, а
по именам. Каждый регистр процессора архитектуры x86 имеет свое название,
состоящее из 2 или 3 букв латинского алфавита.

![пример](https://sun9-53.userapi.com/impg/uvJ82_PJrLVLKqxSjN5pzCpfKFsF_sXqzkO98g/9Ddnpbto3o0.jpg?size=689x418&quality=96&sign=f57d4a664c4892f922016a8f492ffacd&type=album)

4. *Каковы этапы получения исполняемого файла?*

*a)* Набор текста программы в текстовом редакторе и сохранение её в отдельном файле.

*b)* Трансляция — преобразование с помощью транслятора, например nasm,
текста программы в машинный код, называемый объектным

*c)* Компоновка — этап обработки объектного кода компоновщиком (ld), который принимает на вход объектные файлы и собирает по ним исполняемый файл.

*d)* Запуск программы.

5. *Каково назначение этапа трансляции?*

Трансляция нужна для преобразования текста программы в машинный код(объектный).

6. *Каково назначение этапа компоновки?*

Компоновка осуществляет обработку машинного кода компоновщиком, принимает на вход объектные файлы и собирает по ним исполняемый файл.

7. *Какие файлы могут создаваться при трансляции программы, какие из них создаются по умолчанию?*

На этапе трансляции генерируется листинг программы и объектный файл (по умолчанию)

8. *Каковы форматы файлов для nasm и ld?*

Для nasm - *.asm*
Для ld - *.o*


# Выводы

По итогам проделанной работы мы научились писать базовую программу вывода текста на языке ассемблера nasm, освоили её компиляцию и сборку.

# Список литературы{.unnumbered}

::: {#refs}
:::
https://esystem.rudn.ru/pluginfile.php/1584628/mod_resource/content/1/%D0%9B%D0%B0%D0%B1%D0%BE%D1%80%D0%B0%D1%82%D0%BE%D1%80%D0%BD%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%20%E2%84%965.pdf (author: Демидова А.В.)
