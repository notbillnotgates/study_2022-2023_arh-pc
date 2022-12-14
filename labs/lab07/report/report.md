---
## Front matter
title: "Лабораторная работа №7"
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

Освоение арифметических инструкций языка ассемблера NASM.

# Теоретическое введение

## Адресация в NASM
Большинство инструкций на языке ассемблера требуют обработки операндов.
Адрес операнда предоставляет место, где хранятся данные, подлежащие обработке. Это могут быть данные хранящиеся в регистре или в ячейке памяти. Далее рассмотрены все существующие способы задания адреса хранения операндов – способы адресации.
Существует три основных способа адресации:

• Регистровая адресация – операнды хранятся в регистрах и в команде
используются имена этих регистров, например: mov ax,bx.

• Непосредственная адресация – значение операнда задается непосредственно в команде, Например: mov ax,2.

• Адресация памяти – операнд задает адрес в памяти. В команде указывается символическое обозначение ячейки памяти, над содержимым которой
требуется выполнить операцию.

# Выполнение лабораторной работы

1. Создадим каталог для программам лабораторной работы № 7, перейдем в
него и создадим файл **lab7-1.asm**:

![](https://sun9-44.userapi.com/impg/z21_HfE_AaCkvt1u20B_uVhQz0G6m-yJo1jk0A/ah-RxxZu-Kw.jpg?size=653x132&quality=96&sign=55998edcff1ec848e71dfc2de99907b2&type=album)

2. Рассмотрим примеры программ вывода символьных и численных значений. Программы будут выводить значения записанные в регистр eax.
Введем в файл lab7-1.asm текст программы:   
![](https://sun9-48.userapi.com/impg/gXGA85k-iTdQ_Z1KnpCi8oLVEuakbZJDzvjmlw/fsmCul4M9dU.jpg?size=690x460&quality=96&sign=3f6b4f430586ff88c54a9eae4f31d5ee&type=album)

Создадим исполняемый файл и запустим его:
![](https://sun9-23.userapi.com/impg/N5PkppddxgSVmEK0GV7JI8FjHbGpwFFrcaRTlg/nxjKD8rQjio.jpg?size=656x166&quality=96&sign=c14dfc447957386890b804c9e0cb3c82&type=album)

В данном случае при выводе значения регистра eax мы ожидаем увидеть число **10**. Однако результатом будет символ **j**. Это происходит потому, что код символа 6 равен 00110110 в двоичном представлении, а код символа 4 – 00110100. Команда add eax,ebx запишет
в регистр eax сумму кодов – 01101010, что в свою очередь является кодом символа **j**.

3. Далее изменим текст программы и вместо символов запишем в регистры числа. Исправим текст программы следующим образом:

заменим строки

mov eax,'6'

mov ebx,'4'

![](https://sun9-66.userapi.com/impg/gJu8PJLJKWe3QyINKDOFXSz-7mgB_MUEdc3Vvg/wWs6tv5sptI.jpg?size=197x379&quality=96&sign=cbe6f15c9e6eaaedc0ba88d27190582c&type=album)

на строки

mov eax,6

mov ebx,4

![](https://sun9-13.userapi.com/impg/np9Jlxhr6M4X7BCsx9sex2mTPJL60VnAQsSTig/IwMbF2Q-Jck.jpg?size=195x388&quality=96&sign=f6bfb9e548efb6b3dc8fbdacf82d9077&type=album)

Создадим исполняемый файл и запустим его.

![](https://sun1-54.userapi.com/impg/QbbTM5VUltYypcrZEr1gwgrbjleD_bdSrVH-Rw/7SN4_OIizPU.jpg?size=657x181&quality=96&sign=f5b2bac73c57e808663ddab9a7d3242c&type=album)

Как и в предыдущем случае при исполнении программы мы не получим число 10. В данном случае выводится символ с кодом 10.

4. Как отмечалось выше, для работы с числами в файле in_out.asm реализованы подпрограммы для преобразования ASCII символов в числа и обратно.
Преобразуем текст программы с использованием этих функций.
Создадим файл **lab7-2.asm** в каталоге ~/work/arch-pc/lab07 и введем в него
текст программы:
![](https://sun9-32.userapi.com/impg/xnZNlMSzI-9M9ji52nQJFaLaQINNjSGE29XTCg/Vc3mugyWjVw.jpg?size=694x344&quality=96&sign=f02cf562a152086344c44a7ea0406c95&type=album)

Создадим исполняемый файл и запустите его.
![](https://sun9-71.userapi.com/impg/7cd8Ytq6xqijCWdUkq_ktTAaHlEXkEegnXHIuw/eq35o1ApDG0.jpg?size=652x201&quality=96&sign=f806b4626e067189804430e4a3ac90e7&type=album)

В результате работы программы мы получим число 106. В данном случае, как и в первом, команда add складывает коды символов ‘6’ и ‘4’ (54+52=106). Однако, в отличии от прошлой программы, функция **iprintLF** позволяет вывести число, а не символ, кодом которого является это число.

5. Аналогично предыдущему примеру изменим символы на числа. Заменим строки

mov eax,'6'

mov ebx,'4'

на строки

mov eax,6

mov ebx,4

![](https://sun9-87.userapi.com/impg/dLKgdRw9QrQVprpfw-QrcE0W5iWBNIl4cYsYuA/hB7DmkTdJd4.jpg?size=197x313&quality=96&sign=d13beb07d37964b6a078a94b2d27f946&type=album)

Создадим исполняемый файл и запустим его.

![](https://sun1-87.userapi.com/impg/15rZXhpruiJgXQxkxs03UpXtlp_7dy0a8QEzWg/PEemLkFPLJc.jpg?size=654x181&quality=96&sign=ac4c5115a8eab91f1a1a03667b05ff43&type=album)

Далее заменим функцию iprintLF на iprint. Создадим исполняемый файл и запустим его.

![](https://sun1-97.userapi.com/impg/8B-PAMkH7Yu3IAGpHEa7yK6PTT7VtYPgSylYtA/MTnahYwAe6c.jpg?size=185x288&quality=96&sign=592fa0f523ac8ae45601fc051ad47226&type=album)

![](https://sun9-33.userapi.com/impg/_dWlzP9av-_m3pU7mi6j2AanNMeHeR8zKrWQLg/-yM03DTQukw.jpg?size=656x148&quality=96&sign=691f6fb075b42604eb6deef18d055d67&type=album)
наблюдается явное отличие двух программ в виде переноса строки результата вывода.

## Выполнение арифметических операций в NASM

В качестве примера выполнения арифметических операций в NASM приведем программу вычисления арифметического выражения 𝑓(𝑥) = (5 ∗ 2 + 3)/3

Создадим файл **lab7-3.asm** в каталоге ~/work/arch-pc/lab07 и запишем в него следующую программу:

![](https://sun9-3.userapi.com/impg/b_WokRAB_K5F5OW1hU_mdebypykQnJXL8aWlnA/xnpDOeyZjBA.jpg?size=690x846&quality=96&sign=1dfc600a13a95417b461085f1de15824&type=album)

После чего сгенерируем исполняемый файл и запустим его:

![](https://sun1-47.userapi.com/impg/21vI7s0Gjwicycr7kMuPUnnpV0fGyARh0eH1YQ/I8KbiW9RI3Q.jpg?size=653x202&quality=96&sign=35dd21aa9c51eec5a550791e871f524a&type=album)

Измениим текст программы для вычисления выражения 𝑓(𝑥) = (4 ∗ 6 + 2)/5.

![](https://sun9-23.userapi.com/impg/F-97OQWZG_j462GXvhWFbJzXbz03t8NAPDLLvQ/5HIsfUi570E.jpg?size=438x226&quality=96&sign=678af89407c33886d734a8df776cfaa0&type=album)

![](https://sun1-14.userapi.com/impg/KZGRGFRUegS3bGA9NhJznA6pjdO-avfjvSmzFw/9JqFlcxpV70.jpg?size=657x186&quality=96&sign=86de06895bd0be8421934fb1b3e30ffa&type=album)

7. В качестве другого примера рассмотрим программу вычисления варианта задания по номеру студенческого билета, работающую по следующему алгоритму:

• вывести запрос на введение № студенческого билета

• вычислить номер варианта по формуле: (𝑆𝑛 mod 20) + 1, где 𝑆𝑛 – номер студенческого билета (В данном случае 𝑎 mod 𝑏 – это остаток от деления 𝑎 на 𝑏).

• вывести на экран номер варианта.

Создадим файл **variant.asm** в каталоге ~/work/arch-pc/lab07 и запишем в него следующую программу для вычисления номера варианта: 

![](https://sun1-21.userapi.com/impg/EARo7Q9JrtUFyvt5zCsQdddC7O_K5eg8jqEY_A/rR1sBP8ocqc.jpg?size=692x843&quality=96&sign=d9b72f4e8c0fea3fdf6015651d30a481&type=album)

После мы создадим и запустим исполняемый файл, введя свой номер студенческого билета:

![](https://sun9-48.userapi.com/impg/q-d_Ulc12zlzzhyBynQWnVkwgzeXn6tkrtz8zQ/pXMdJJQvhjs.jpg?size=652x229&quality=96&sign=0c2a4276cd26d8f59bb60e9c4232db4d&type=album)
Путем вычислений программы я получил 8 вариант.

# Теоретические вопросы

1. #### Какие строки листинга 7.4 отвечают за вывод на экран сообщения ‘Ваш вариант:’?

rem: DB 'Ваш вариант: ',0
call sprintLF

2. #### Для чего используется следующие инструкции? nasm mov ecx, x
mov edx, 80 call sread

Функция nasm определяет язык исполняемого файла
Команда mov задает значение переменной
ecx - регистр, позволяющий обращаться к данным
mov edx, 80 - длина вводимой строки в байтах.

3. #### Для чего используется инструкция “call atoi”?

Команда call atoi позволяет преобразовать ASCII код в число и записать его в регистр eax, перед вызовом atoi в регистр eax необходимо записать число

4. #### Какие строки листинга 7.4 отвечают за вычисления варианта?

xor edx,edx
mov ebx,20
div ebx
inc edx

5. #### В какой регистр записывается остаток от деления при выполнении инструкции “div ebx”?

Остаток от деления при выполнении инструкции div ebx записывается в регистр edx.

6. #### Для чего используется инструкция “inc edx”?

Инструкция inc edx увеличивает значение регистра edx на единицу.

7. #### Какие строки листинга 7.4 отвечают за вывод на экран результата вычислений?

call sprint

call iprintLF


# Выводы

По итогам проделанной работы мы освоили некоторые инструкции языка ассемблера NASM.

# Список литературы

::: {#refs}
:::
https://esystem.rudn.ru/pluginfile.php/1584637/mod_resource/content/1/%D0%9B%D0%B0%D0%B1%D0%BE%D1%80%D0%B0%D1%82%D0%BE%D1%80%D0%BD%D0%B0%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%20%E2%84%967.pdf
