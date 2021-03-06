---
title: пользователь
lastChanged: 27.03.2019
translatedFrom: de
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/admin/users.md
hash: 8jYWtumjWGf3hSM81yXLYzlD4MxMtGBFLljKoySqw5U=
---
# Пользователь страницы
На этой странице можно создавать пользователей и группы, а также назначать права для групп.

![Пользователи страницы](../../de/admin/media/ADMIN_Benutzer_numbers.png)

С левой стороны находятся существующие группы, с правой стороны - пользователи.

Пользователи могут быть перетащены в группы простым перетаскиванием.

## 1.) новая группа
После нажатия на этот значок открывается другое окно:

![Создать новую группу](../../de/admin/media/ADMIN_Benutzer_newgroup_allgemein.png)

Это окно состоит из двух подразделений.

### Общие
Вот основные введенные вещи:

** Имя **

Название группы. Это имя можно выбрать произвольно, но оно должно быть уникальным.

** ID ** Идентификатор заполняется автоматически

** Описание **

В этом поле можно ввести объяснение задач этой группы.

** ** Предварительный просмотр

Появляется автоматически и содержит полный идентификатор sytem.group.group name.

Значок можно добавить с помощью кнопки [+], но его также можно перетащить в окно.

** Цвет **

При установленном цвете плитка группы выделяется.

### Права доступа
Права назначаются группам. Чтобы пользователи имели определенные права, они должны быть отнесены к соответствующей группе.

![Права доступа группы](../../de/admin/media/ADMIN_Benutzer_newgroup_rechte.png)

Здесь права доступа для различных задач назначены.

## 2.) новый пользователь
После нажатия на этот значок открывается другое окно:

![Создать нового пользователя](../../de/admin/media/ADMIN_Benutzer_newuser.png)

** Имя **

Имя пользователя. Это имя можно выбрать произвольно, но оно должно быть уникальным.

** ID **

Идентификатор будет заполнен автоматически

** Описание **

В этом поле может быть введено объявление для пользователя.

** ** Предварительный просмотр

Появляется автоматически и содержит полный идентификатор sytem.group.Username.

** Пароль **

Пароль пользователя

**Повторить пароль**

Для защиты от ошибок при вводе, пароль должен быть введен здесь во второй раз