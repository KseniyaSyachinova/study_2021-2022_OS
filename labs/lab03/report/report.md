---
## Front matter
title: "Отчёт по лабораторной работе №3"
subtitle: "Операционные системы"
author: "Сячинова Ксения Ивановна"

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

Цель работы:научиться оформлять отчёты с помощью легковесного языка разметки Markdown, а также познакомиться с основными возможностями разметки Markdown.

# Задание

Сделайте отчёт по предыдущей лабораторной работе в формате Markdown.
В качестве отчёта просьба предоставить отчёты в 3 форматах: pdf, docx и md (в архиве,
поскольку он должен содержать скриншоты, Makefile и т.д.)

# Выполнение лабораторной работы


1) Создаём учётную запись на github.(рис. [-@fig:001])

![Создание учётной записи](image/1.png){ #fig:001 width=70% }

2) Сделаем предварительную конфигурацию, указав имя и email владельца
репозитория с помощью git config —global user.name"Имя Фамилия", git
config —global user.email"work@mail". (рис. [-@fig:002])

![Делаем конфигурацию](image/2.png){ #fig:002 width=70% }

3) После этого создаём новый ключ на github (команда ssh-keygen -
C"KseniyaSyachinova <KseniyaZ.ru@yandex.ru> и привязываем его к
копьютеру через консоль. После этого, скопировав из локальной
консоли ключ в буфер обмена, вставляем ключ в появившееся на сайте
поле. (рис. [-@fig:003])

![Делаем конфигурацию](image/3.png){ #fig:003 width=70% }

4) Приступаем к базовой настройке git.Зададим имя и email владельца репозитория:  git config --globaluser.name "Name Surname" ,git config --global user.email "work@mail". Настроим utf-8 в выводе сообщений git: git config --global core.quotepath false.Настроим верификацию и подписание коммитов git. Зададим имя начальной ветки: git config --global init.defaultBranch master.Параметр autocrlf:  git config --global core.autocrlf input. Параметр safecrlf: git config --global core.safecrlf warn.(рис. [-@fig:004]) 

![Настройка git](image/4.png){ #fig:004 width=70% }

5) Затем создаём свой ключ по алгоритму:  ssh-keygen -t rsa-b 4096 иssh-keygen -t ed25519.(рис. [-@fig:005])

![Создание ssh ключа ](image/5.png){ #fig:005 width=70% }

6) Создаёмключgpg: gpg --full-generate-key. 
Затем настраиваем:
Тип RSA and RSA
Размер 4096
Срок действия,значение по умолчанию — 0 (срок действия не истекает никогда). 
Имя 
Адрес электронной почты (рис. [-@fig:006])

![Создание gpg ключа](image/6.png){ #fig:006 width=70% }

7) Добавлем PGP ключ в GitHub.  Используем gpg --list-secret-keys --keyid-format LONG. По образцу видим отпечаток моего ключа, вставляем его в следующую конструкцию: `gpg--armor--export<pgpFingerprint> | xclip-selclip`.Затем перешли в настройки github и вставили полученный ключ. (рис. [-@fig:007])

![Добавление ключей ](image/7.png){ #fig:007 width=70% }

8) Таким образом, у нас получились следующие ssh и gpg ключи: (рис. [-@fig:008])

![Полученные ключи](image/8.png){ #fig:008 width=70% }

9)Затем настраиваем автоматические подписи коммитов git: git config --global user.signingkey, git config --global commit.gpgsign truel, git config --global gpg.program $(which gpg2) (рис. [-@fig:009])

![Настройка коммитов](image/9.png){ #fig:009 width=70% }

10)После этого создаём репозиторий курса на основе шаблона. (рис. [-@fig:010])

![Содание репозитория](image/10.png){ #fig:010 width=70% }

11) Копируем ссылку и с помощью git clone –recursiveдобавляем наши лабораторные работы на github. Впоследствии удаляем лишние файлы:  rm package.json, создаём необходимые каталоги: make COURSE=os-intro, и отправляем файлы на сервер: git add .,  git commit -am 'feat(main): make course structure' , git push. (рис. [-@fig:011])

![Итог](image/11.png){ #fig:011 width=70% }

# Выводы

Я научилась офомлять отчёты в Markdown, познакомилась с основными его возможностями.
