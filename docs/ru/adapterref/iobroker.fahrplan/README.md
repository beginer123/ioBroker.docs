---
translatedFrom: en
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/adapterref/iobroker.fahrplan/README.md
title: ioBroker.fahrplan
hash: /Y+XydeKv9XJuVr50Bb1grwEQi7nB/GoVK8L7wkTUeg=
---
![Логотип](../../../en/adapterref/iobroker.fahrplan/admin/fahrplan.png)

![Версия NPM](http://img.shields.io/npm/v/iobroker.fahrplan.svg)
![Загрузки](https://img.shields.io/npm/dm/iobroker.fahrplan.svg)
![Количество установок (последнее)](http://iobroker.live/badges/fahrplan-installed.svg)
![Количество установок (стабильно)](http://iobroker.live/badges/fahrplan-stable.svg)
![Статус зависимости](https://img.shields.io/david/gaudes/iobroker.fahrplan.svg)
![НПМ](https://nodei.co/npm/iobroker.fahrplan.png?downloads=true)

# IoBroker.fahrplan
![Тестирование и выпуск](https://github.com/gaudes/ioBroker.fahrplan/workflows/Test%20and%20Release/badge.svg)

## Адаптер Fahrplan для ioBroker
### Deutsch
Адаптер Dieser для работы с мобильным API от HAFAS. HAFAS steht für HaCon Fahrplan-Auskunfts-System und wird von vielen europäischen Verkehrsunternehmen verwendet, unter anderem auch von der Deutschen Bahn.
Der Zugriff auf HAFAS erfolgt hierbei über [HAFAS-Клиент](https://github.com/public-transport/hafas-client).

Der Adapter bietet hierbei drei Funktionen:

#### Fahrplan für Verbindungen (Routen)
Die gewünschten Routen müssen in der Adapterkonfiguration eingerichtet und aktiviert werden.
Über einen konfigurierbaren Intervall ruft der Adapter dann regelmäßig die Verbindungsinformationen ab.
Неизвестно, какие вербиндунги вердены на HTML и дополнительные детали, как на объекты в ioBroker dargestellt.
Das HTML-Objekt kann einfach in VIS eingebunden werden.

#### Benachrichtigung bei Verspätungen der Routen
Für die konfigurierten Routen kann ein Verspätungsalarm aktiviert werden. Таким образом, kann beispielsweise eine Benachrichtigung через Telegram или Alexa erfolgen, попадает во все, что связано с Verbindung verspätet ist.

#### Abfahrtstafeln für Stationen
Zusätzlich bietet der Adapter eine Abfahrtstafel für konfigurierte Stationen.
Hierbei werden die nächsten drei Abfahrten einer Station abgerufen und als Objekte und HTML dargestellt.

** Адаптер Dieser доступен для Sentry Bibliotheken um automatisch Abstürze und Programmfehler an die Entwickler zu übermitteln. ** Подробная информация и информация о Deaktivierung der Fehlerberichterstattung в [Документация Sentry-Plugin](https://github.com/ioBroker/plugin-sentry#plugin-sentry)! Sentry Reporting сообщает о версии JS-Controller 3.0.

### Английский
Этот адаптер для ioBroker использует мобильный API HAFAS. HAFAS - это система управления общественным транспортом, используемая поставщиками общественного транспорта по всей Европе, например Deutsche Bahn.
[HAFAS-Клиент](https://github.com/public-transport/hafas-client) используется для доступа к HAFAS.

Адаптер выполняет три функции:

#### Расписание пересадок (маршрутов)
Желаемые маршруты должны быть настроены и включены в конфигурации адаптера.
Адаптер автоматически получает информацию о соединении с заданным интервалом.
Следующие три соединения сохраняются в ioBroker как HTML и необязательно как подробные объекты.
HTML-объект может быть легко использован в VIS.

#### Уведомление о задержках на маршрутах
Уведомление о задержке может быть активировано для настроенных маршрутов. Например, Telegram или Alexa может получать уведомление, когда все или одно конкретное соединение задерживается.

#### Расписание отправлений по станциям
Кроме того, адаптер предоставляет расписание отправлений для настроенных станций.
Здесь следующие три соединения обнаруживаются и создаются как объекты и HTML.

** Этот адаптер использует библиотеки Sentry для автоматического сообщения разработчикам об исключениях и ошибках кода. ** Дополнительные сведения и информацию о том, как отключить отчет об ошибках, см. В [Документация по Sentry-Plugin](https://github.com/ioBroker/plugin-sentry#plugin-sentry)! Сторожевые отчеты используются начиная с js-controller 3.0.

## Конфигурация
### Deutsch
Die Start- und Zielorte sowie Zwischenziele müssen mit ihrer numerischen ID angegeben werden.
Eine suchfunktion ist im Tab Einstellungen integriert.

#### Tab Einstellungen
![](../../../en/adapterref/iobroker.fahrplan/docs/de/img/settings.png)

| Einstellung | Beschreibung | ------------------------------ | --- | Анбитер | Auswahl des zu verwendenden Anbieters, aktuell DB und ÖBB | Aktualisierungsintervall | Intervall in dem die Route aktualisiert werden, Ангабе в Минутене | Verspätet markieren ab | Verspätung в Minuten ab der die Verbindung als verspätet markiert wird. Standardmäßig werden nur Verspätungen ab zwei Minuten markiert | HTML-Ansicht erzeugen | Erzeugt pro Route eine konfigurierbare HTML-tabelle in einem Objekt | Детальерте специальные объекты | Konfiguration der auszugebenden Objekte | JSON-Elemente speichern | Die Rückgabe von HAFAS erfolgt als JSON, diese sollten zur Fehlerbehebung gespeichert werden

Auf der rechten Seite ist die suchfunktion integriert. Zuerst muss ein Anbieter ausgewählt werden.
Данах канн über das Сучфельд и Drücken des Knopfs "Suche" nach einer Station gesucht werden.
Die Suchergebnisse der aktuellen Suche werden in der Tabelle angezeigt.

#### Вкладка Routen
![](../../../en/adapterref/iobroker.fahrplan/docs/de/img/settings_routes.png)

Mit dem + -Button können neue Einträge zur Tabelle hinzugefügt werden.

| Einstellung | Beschreibung | ----------------------------- | --- | № | Die Nummer entspricht dem Unterknoten in den Objekten und wird automatisch vergeben.
| Актив | Wenn die Route aktiviert ist werden die Verbindungsinfos aktualisiert | Фон | Numerische ID von Startbahnhof или Starthaltestelle (Ermittlung über Suche) | Фон (имя Эйгенера) | Benutzerdefinierter Name von Startbahnhof или Starthaltestelle, für HTML- и Verspätungstext verwendet | Нач | Numerische ID von Zielbahnhof oder Zielhaltestelle (Ermittlung über Suche) | Нах (имя Айгенер) | Benutzerdefinierter Name von Zielbahnhof oder Zielhaltestelle, für HTML- и Verspätungstext verwendet | Via 1 | Fahrt über bestimmten Ort angegeben als numerische ID (необязательно, sonst leer) | Via 2 | Fahrt über bestimmten Ort angegeben als numerische ID (необязательно, sonst leer) | Verkehrsmittel | Auswahl des Verkehrsmittels, z.B. Автобус, S-Bahn, usw. Standardmäßig werden all Verkehrsmittel ausgewählt | Максимум. Umstiege | Maximale Anzahl an Umstiegen. 0 für nur direkte Verbindungen.
| Абфахртен | Анзал абзуруфендер Фартен | Fahrradmitnahme | Nur Verbindungen mit Fahrradmitnahme auswählen

#### Вкладка Verspätungsalarm
![](../../../en/adapterref/iobroker.fahrplan/docs/de/img/settings_delaynotification.png)

Mit dem + -Button können neue Einträge zur Tabelle hinzugefügt werden.

| Einstellung | Beschreibung | ----------------------------- | --- | № | Die Nummer entspricht dem Unterknoten in den Objekten und wird automatisch vergeben.
| Актив | Wenn der Verspätungsalarm aktiviert ist wird dieser geprüft | Маршрут | Route auf die sich der Alarm beziehen soll | Geplante Abfahrt | Geplante Abfahrtszeit der zu prüfenden Route (Leer = Alle Verbindungen) | Wochentag | Wochentage an denen die Prüfung erfolgen soll | Benachrichtigung в Минутене | Anzahl der Minuten vor der Abfahrt, in denen benachrichtigt werden soll | Objekt für Ausgabetext | Angabe eines vorhandenen Objekts

Hinweis zum Ausgabetext: Hier kann neben einfachen Objekten für VIS z.B. auch das "Speak" -Objekt des Alexa-Adapters или das "reponse" -Objekt des Telegram-Adapters verwendet werden.

#### Tab Abfahrtstafeln
![](../../../en/adapterref/iobroker.fahrplan/docs/de/img/settings_departuretimetables.png)

Mit dem + -Button können neue Einträge zur Tabelle hinzugefügt werden.

| Einstellung | Beschreibung | ----------------------------- | --- | № | Die Nummer entspricht dem Unterknoten in den Objekten und wird automatisch vergeben.
| Актив | Венн дер Эйнтраг активный активист вирд dieser abgerufen | Фон | Numerische ID von Startbahnhof или Starthaltestelle (Ermittlung über Suche) | Фон (имя Эйгенера) | Benutzerdefinierter Name von Startbahnhof или Starthaltestelle, für HTML-Ausgabe verwendet | Абфахртен | Анзал абзуруфендер Абфахртен

### Английский
Начало, пункт назначения и остановки должны быть обозначены числовым идентификатором.
Функция поиска по этим идентификаторам встроена в настройки вкладок.

#### Настройки вкладки
![](../../../en/adapterref/iobroker.fahrplan/docs/en/img/settings.png)

| Настройка | Описание | ----------------------------- | --- | Провайдер | Выбор поставщика общественного транспорта, в настоящее время DB und ÖBB | Интервал обновления | Интервал обновления маршрутов в минутах | Марк задерживается после задержки в | Определить минуты после того, как задержка должна быть помечена как задержка, по умолчанию задержка отмечается, когда задержка превышает одну минуту | Создать представление HTML | Создает для каждого маршрута настраиваемую таблицу HTML в объекте | Сохранить подробные объекты | Конфигурация объектов вывода | Сохранить элементы JSON | Возврат из HAFAS - это JSON, следует сохранить для устранения неполадок.

#### Вкладка Маршруты
![](../../../en/adapterref/iobroker.fahrplan/docs/en/img/settings_routes.png)

С помощью + -Button новые записи могут быть добавлены в таблицу.

| Настройка | Описание | ----------------------------- | --- | № | Номер соответствует подузлу в объектах и присваивается автоматически | Activ | Информация о подключении обновляется, когда активен маршрут | От | Числовой идентификатор начальной станции или начальной остановки | От (Пользовательское имя) | Пользовательское имя для начальной станции или начальной остановки, используется в выводе HTML-уведомлений и уведомлений о задержках | К | Числовой идентификатор станции назначения или остановки назначения | От (Пользовательское имя) | Пользовательское имя для станции назначения или остановки назначения, используемое в выводе HTML-уведомлений и уведомлений о задержке | Via 1 | Проехать через специальную станцию в виде числового идентификатора (необязательно, по умолчанию пусто) | Via 2 | Проехать через специальную станцию в виде числового идентификатора (необязательно, по умолчанию пусто) | Автомобиль | Выбор автомобиля, например Автобус, S-Bahn и т. Д. По умолчанию выбраны все автомобили | Максимум. трансферы | Максимальное количество пересадок по маршруту, 0 только для прямых пересадок | Отправления | Количество отправлений для приема | Bycicle | Выбирайте только те соединения, где разрешены велосипеды

#### Тревога задержки табуляции
![](../../../en/adapterref/iobroker.fahrplan/docs/en/img/settings_delaynotification.png)

С помощью + -Button новые записи могут быть добавлены в таблицу.

| Einstellung | Beschreibung | ----------------------------- | --- | № | Номер соответствует подузлу в объектах и присваивается автоматически | Activ | Активирована проверка задержки сигнала тревоги | Маршрут | Маршрут относительно этого сигнала задержки | Планируемый отъезд | Планируемое отправление соединения подлежит проверке (Пусто = Все маршруты) | Будни | Будни, когда нужно проверять соединение | Уведомление за считанные минуты | Минуты до отправления при активном сигнале задержки | Объект для вывода текста | Состояние ioBroker для вывода текста

Подсказка для «Объект для вывода текста»: могут использоваться простые состояния для использования в VIS, но также «говорить» -состояние адаптера Alexa или «ответ» -состояние адаптера Telegram.

#### Вкладка "Расписание отправлений"
![](../../../en/adapterref/iobroker.fahrplan/docs/en/img/settings_departuretimetables.png)

С помощью + -Button новые записи могут быть добавлены в таблицу.

| Настройка | Описание | ----------------------------- | --- | № | Номер соответствует подузлу в объектах и присваивается автоматически | Activ | Информация о подключении обновляется, когда элемент активен | От | Числовой идентификатор начальной станции или начальной остановки | От (Пользовательское имя) | Пользовательское имя для начальной станции или начальной остановки, используется в выводе HTML-уведомлений и уведомлений о задержках | Отправления | Количество отправлений для приема

## Changelog

<!--
	Placeholder for the next version (at the beginning of the line):
	### __WORK IN PROGRESS__
-->

### 0.2.1 (2020-11-09)
* (Gaudes) Configurable number of journeys in routes
* (Gaudes) Configurable number of departures in departure timetable
* (Gaudes) Show product in departure timetable
* (Gaudes) Fix platform handling in departure timetable
* (Gaudes) Include Sentry error reporting
* (Gaudes) Update Adapter template from 1.27.0 to 1.29.0
* (Gaudes) Include Dependabot updates

### 0.2.0 (2020-09-23)
* (Gaudes) Include Departure Timetable for configured stations
* (Gaudes) Security fix for serialize-javascript
* (Gaudes) Enhanced error handling and preparation for Sentry
* (Gaudes) setObject replaced with setObjectNotExists
* (Gaudes) Update Adapter template from 1.25.0 to 1.27.0
* (Gaudes) Include Dependabot with auto-merge
* (Gaudes) Include Dependabot updates
* (Gaudes) Fix ESLINT errors
* (Gaudes) Integrate Integration and Unit Tests
* (Gaudes) Remove Travis & Snyk

### 0.1.12 (29.08.2020)
* (Gaudes) Fix station search

### 0.1.11 (28.08.2020)
* (Gaudes) Fix error with timeout

### 0.1.10 (28.08.2020)
* (Gaudes) Fix structure of classes and files
* (Gaudes) Fix language in io-package.json
* (Gaudes) Futher cleanups in code

### 0.1.9 (07.08.2020)
* (Gaudes) Fix object type for datetime objects

### 0.1.8 (05.08.2020)
* (Gaudes) Fix creation of channels

### 0.1.7 (31.07.2020)
* (Gaudes) Translations for foreign languages
* (Gaudes) Fix adapter checker E502
* (Gaudes) Configurable delay time
* (Gaudes) HTML output for journeys with section information
* (Gaudes) Fix product selection

### 0.1.6 (28.07.2020)
* (Gaudes) Fix of delay output text with custom names of stations

### 0.1.5 (27.07.2020)
* (Gaudes) Custom names for departure and arrival stations, fix of delay output text

### 0.1.4 (25.07.2020)
* (Gaudes) fix deletion of unused states and channels

### 0.1.3 (24.07.2020)
* (Gaudes) correct object types, delay notification

### 0.1.2 (19.07.2020)
* (Gaudes) quickfix ontime

### 0.1.1 (19.07.2020)
* (Gaudes) code refactoring to classes, more config options for objects and HTML

### 0.1.0 (14.07.2020)
* (Gaudes) First public alpha release

### 0.0.2 (09.07.2020)
* (Gaudes) code enhancements (refactoring, correct names for variables)

### 0.0.1 (06.07.2020)
* (Gaudes) initial release

## License
MIT License

Copyright (c) 2020 Ralf Gaudes <ralf@gaudes.net>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.