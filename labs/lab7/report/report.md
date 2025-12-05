---
## Front matter
title: Лабораторная работа
subtitle: Номер 7
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

Целью данной работы является получение навыков настройки межсетевого экрана в Linux в части переадресации портов и настройки Masquerading.

# Выполнение лабораторной работы

На виртуальной машине server переходим в режим суперпользователя.
На основе существующего файла описания службы ssh создаем файл с собственным описанием.
Смотрим содержимое файла службы (Рис. 12.1).

![Создание пользовательской службы firewalld](image/1.png){height=60%}

Открываем файл описания службы на редактирование и заменяем порт 22 на новый порт (2022) (Рис. 12.2).

![Файл ssh-custom.xml](image/2.png){height=60%}

Смотрим список доступных FirewallD служб.
Перегружаем правила межсетевого экрана с сохранением информации о состоянии и вновь выводим на экран список служб, а также список активных служб (Рис. 12.3).

![FirewallD](image/3.png){height=60%}

Добавляем новую службу в FirewallD и выводим на экран список активных служб.
Перегружаем правила межсетевого экрана с сохранением информации о состоянии.
Организовываем на сервере переадресацию с порта 2022 на порт 22 (Рис. 12.4).

![Новая служба FirewallD](image/4.png){height=60%}

На клиенте пробуем получить доступ по SSH к серверу через порт 2022 (Рис. 12.5).

![Попытка получить доступ по SSH к серверу через порт 2022](image/5.png){height=60%}

На сервере смотрим, активирована ли в ядре системы возможность перенаправления IPv4-пакетов пакетов.
Включаем перенаправление IPv4-пакетов на сервере.
Включаем маскарадинг на сервере (Рис. 12.6).

![Настройка Port Forwarding и Masquerading](image/6.png){height=60%}

На виртуальной машине server переходим в каталог для внесения изменений в настройки внутреннего окружения /vagrant/provision/server/, создаем в нём каталог firewall, в который помещаем в соответствующие подкаталоги конфигурационные файлы FirewallD.
В каталоге /vagrant/provision/server создаем файл firewall.sh (Рис. 12.7).

![Внесение изменений в настройки внутреннего окружения виртуальной машины](image/7.png){height=60%}

Прописываем скрипт в firewall.sh (Рис. 12.8).

![Файл firewall.sh](image/8.png){height=60%}

Для отработки созданного скрипта во время загрузки виртуальной машины server в конфигурационном файле Vagrantfile добавляем в разделе конфигурации для сервер (Рис. 12.9).

![Vagrantfile](image/9.png){height=60%}

# Выводы

В результате выполнения лабораторной работы мною были получены навыки настройки межсетевого экрана в Linux в части переадресации портов и настройки Masquerading.

# Список литературы{.unnumbered}