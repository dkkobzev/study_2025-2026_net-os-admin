---
## Front matter
title: Лабораторная работа
subtitle: Номер 12
author: "Кобзев Д. К."

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: /home/dkkobzev/pandoc/csl/gost-r-7-0-5-2008-numeric.csl

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
mainfont: Liberation Serif
romanfont: Liberation Serif
sansfont: Liberation Sans
monofont: Liberation Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9

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

Целью данной работы является получение навыков по управлению системным временем и настройке синхронизации времени.

# Выполнение лабораторной работы

На сервере смотрим параметры настройки даты и времени и текущее системное время (Рис. 12.1).

![Настройки даты и времени на сервере](image/1.png){height=60%}

На клиенте смотрим параметры настройки даты и времени и текущее системное время (Рис. 12.2).

![Настройки даты и времени на клиенте](image/2.png){height=60%}

Проверяем источники времени на клиенте и на сервере (Рис. 12.3), (Рис. 12.4).

![Источники времени на сервере](image/3.png){height=60%}

![Источники времени на клиенте](image/4.png){height=60%}

На сервере открываем на редактирование файл /etc/chrony.conf и добавляем строку:
allow 192.168.0.0/16 (Рис. 12.5).

![Файл /etc/chrony.conf](image/5.png){height=60%}

На сервере перезапускаем службу chronyd.

Настраиваем межсетевой экран на сервере (Рис. 12.6).

![Настройка межсетевого экрана](image/6.png){height=60%}

На клиенте открываем файл /etc/chrony.conf и добавляем строку: server server.user.net iburst (Рис. 12.7).

![Файл /etc/chrony.conf](image/7.png){height=60%}

На клиенте перезапускаем службу chronyd.

Проверяем источники времени на клиенте и на сервере (Рис. 12.8), (Рис. 12.9).

![Источники времени на клиенте](image/8.png){height=60%}

![Источники времени на сервере](image/9.png){height=60%}

На виртуальной машине server переходим в каталог для внесения изменений в настройки внутреннего окружения /vagrant/provision/server/, создаем в нём каталог ntp, в который помещаем в соответствующие подкаталоги конфигурационные файлы.

В каталоге /vagrant/provision/server создаем исполняемый файл ntp.sh (Рис. 12.10).

![/vagrant/provision/server/](image/10.png){height=60%}

Редактируем файл ntp.sh (Рис. 12.11).

![Файл ntp.sh](image/11.png){height=60%}

На виртуальной машине client переходим в каталог для внесения изменений в настройки внутреннего окружения /vagrant/provision/client/, создаем в нём каталог ntp, в который помещаем в соответствующие подкаталоги конфигурационные файлы.

В каталоге /vagrant/provision/client создаем исполняемый файл ntp.sh (Рис. 12.12).

![/vagrant/provision/client/](image/12.png){height=60%}

Редактируем файл ntp.sh (Рис. 12.13).

![Файл ntp.sh](image/13.png){height=60%}

Для отработки созданных скриптов во время загрузки виртуальных машин server
и client в конфигурационном файле Vagrantfile добавляем в соответствующих разделах конфигураций для сервера и клиента (Рис. 12.14), (Рис. 12.15).

![Конфигурации для сервера](image/14.png){height=60%}

![Конфигурации для клиента](image/15.png){height=60%}

# Выводы

В результате выполнения лабораторной работы мною были получены навыки по управлению системным временем и настройке синхронизации времени.

# Список литературы{.unnumbered}
