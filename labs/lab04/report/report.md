---
## Front matter
title: "Отчет по лабораторной работе №4"
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

Целью работы является освоение процедуры оформления отчетов с помощью
легковесного языка разметки Markdown.

# Задание

Здесь приводится описание задания в соответствии с рекомендациями
методического пособия и выданным вариантом.

# Выполнение лабораторной работы
Для начала работы заранее установим **Text Live** и пропишем в терминале **path**


![0](https://sun9-48.userapi.com/impg/WNQOF_LLsOoqNHP7KJnI4h1BoHtcRtdz28OzJg/5kI4BMChR0E.jpg?size=654x480&quality=96&sign=809000b1a1fbf8629d33fabc6e1d5b81&type=album)

А потом установим и распакуем **pandoc 2.18** и **pandoc-crossref**
![0](https://sun9-78.userapi.com/impg/2d5lJsz18ass-ZcEdy7P0Ov5AmIWJ6q2fqlnOA/FnO0kVp7lms.jpg?size=653x474&quality=96&sign=3da2f320b68add2599322bb35c81cb5e&type=album)

1. Теперь откроем терминал и перейдем в каталог курса лабораторной работы №3 и обновим локальный репозиторий, скачав изменения из удаленного репозитория с помощью команды ***git pull***:

![1](https://sun1-16.userapi.com/impg/WyGCDKX414iGaed6-hiaiHLR2aAD61LV2jO2DA/45GTkVS0nG4.jpg?size=648x142&quality=96&sign=8b98f9901be8eac6caa0c436ad4f6fa2&type=album)


2. Далее перейдем в каталог с шаблоном отчета по лабораторной работе №4 и проведем там компиляцию шаблона с использованием **Makefile**
![2](https://sun9-70.userapi.com/impg/H_ZjbbBXQDLou1drBa6iZU6xVHWrrYWPSb4y0g/Ir_DuV1ZtI0.jpg?size=653x394&quality=96&sign=43196949c9c9265d88f02ba1e5229d78&type=album)

У нас сгенерировались 2 файла: report.pdf и report.docx
После мы их удалили командой ***make clean***

*Отчет о выполненной лабораторной работе №3 также загружен на github.*



# Ответы на контрольные вопросы для самопроверки

**1**. Markdown - облегчённый язык разметки, созданный для форматирования в простом тексте, с максимальным сохранением его читаемости человеком, и пригодный для машинного преобразования в языки для продвинутых публикаций
**2**. Начертания шрифтов создаются несколькими способами: a) для создания заголовка используется символ # (чем их больше, тем меньше шрифт); b) для полужирного начертания - символ * с обеих сторон; c) курсивное начертание задается уже двумя символами **; d) также полужирное и курсивное начертание задается тремя ***.
	
**3**. Упорядоченный список форматируется цифрами:
1. First instruction
1. 		Sub-instruction
1. 		Sub-instruction
1. Second instruction

Вложенные списки форматируются с помощью отступа:
1. 		First instruction
1. 		Second instruction
1. 		Third instruction

Неупорядоченный список форматируется звездочками или тире:
* List 1
	- list a
- List 2
	+ list a

**4**. Изображения и ссылки на них оформляются 
следующим образом: 
! подпись в квадратных скобках и ( / путь / изображения)  или в скобках может быть URL-ссылка 

**5**. Математические формулы создаются с помощью символов, аналогично формулам LaTeX, например, 
$$
\sin^2 (x) + \cos^2 (x) = 1
$$ {#eq:eq1}

Со ссылкой на формулу (`[-@eq:eq1]`).

# Выводы

После проделанной работы мы познакомились с языком разметки **Markdown** и научились компилировать файлы .md в .pdf и .docx с помощью **makefile**.

