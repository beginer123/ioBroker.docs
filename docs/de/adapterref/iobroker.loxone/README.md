---
translatedFrom: en
translatedWarning: Wenn Sie dieses Dokument bearbeiten möchten, löschen Sie bitte das Feld "translationsFrom". Andernfalls wird dieses Dokument automatisch erneut übersetzt
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/de/adapterref/iobroker.loxone/README.md
title: ioBroker.loxone
hash: RFvcOtNLZbcOXe0S3hodNtHZFAwGDPpE6jg8KW0TplQ=
---
![Logo](../../../en/adapterref/iobroker.loxone/admin/loxone.png)

![NPM-Version](http://img.shields.io/npm/v/iobroker.loxone.svg)
![Downloads](https://img.shields.io/npm/dm/iobroker.loxone.svg)
![Anzahl der Installationen (aktuell)](http://iobroker.live/badges/loxone-installed.svg)
![Anzahl der Installationen (stabil)](http://iobroker.live/badges/loxone-stable.svg)
![Abhängigkeitsstatus](https://img.shields.io/david/UncleSamSwiss/iobroker.loxone.svg)
![NPM](https://nodei.co/npm/iobroker.loxone.png?downloads=true)

# IoBroker.loxone
[![Übersetzungsstatus] (https://weblate.iobroker.net/widgets/adapters/-/loxone/svg-badge.svg)](https://weblate.iobroker.net/engage/adapters/?utm_source=widget)

** Tests: ** ![Testen und freigeben](https://github.com/UncleSamSwiss/ioBroker.loxone/workflows/Test%20and%20Release/badge.svg)

## Loxone-Adapter für ioBroker
** _ Dieser Adapter benötigt mindestens nodejs 10.x! _ **

Ruft alle in Loxone Miniserver (und Loxone Miniserver Go) verfügbaren Informationen ab und bietet Änderungen in Echtzeit.

## Installieren
Installieren Sie diesen Adapter über ioBroker Admin:

1. Öffnen Sie den Instanzkonfigurationsdialog
2. Geben Sie die IP-Adresse oder den Hostnamen und den HTTP-Port (standardmäßig 80) Ihres Loxone Miniservers ein
3. Erstellen Sie im Loxone Miniserver einen neuen Benutzer (mit der Anwendung Loxone Config), dem Sie nur Lese- und Schreibrechte für alle erforderlichen Variablen erteilen.
4. Geben Sie den Namen und das Passwort dieses Benutzers in den Konfigurationsdialog ein
5. Speichern Sie die Konfiguration
6. Starten Sie den Adapter

## Aufbau
### Miniserver Hostname / IP
Dies ist die IP-Adresse oder der Hostname Ihres Loxone Miniserver oder Miniserver Go.

### Miniserver Port
Dies ist der HTTP-Port Ihres Loxone Miniserver.

Standardmäßig ist der Miniserver so konfiguriert, dass er Port 80 überwacht. Möglicherweise haben Sie ihn jedoch geändert.

### Miniserver Benutzername
Geben Sie einen gültigen Benutzernamen an, um auf den Loxone Miniserver zuzugreifen.

Aus Sicherheitsgründen wird dringend empfohlen, einen anderen Benutzer als "admin" zu verwenden.

Der Benutzer benötigt nur Lesezugriff auf die Variablen, die Sie von ioBroker verwenden möchten.

### Miniserver-Passwort
Geben Sie das Passwort für den angegebenen Benutzernamen ein (siehe oben).

### Namen synchronisieren
Dadurch werden die Namen in ioBroker aktualisiert, wenn sie sich in der Loxone-Konfiguration ändern.
Wenn dies deaktiviert ist, werden Namen nur synchronisiert, wenn ein Steuerelement zum ersten Mal erkannt wird.

### Räume synchronisieren
Dadurch wird die Aufzählung enum.rooms mit allen vom Loxone Miniserver bereitgestellten Räumen gefüllt und alle Steuerelemente verknüpft.

### Funktionen synchronisieren
Dadurch wird die Aufzählung enum.functions mit allen vom Loxone Miniserver bereitgestellten Kategorien gefüllt und alle Steuerelemente verknüpft.

## Zustände
Der Adapter stellt automatisch eine Verbindung zum konfigurierten Loxone Miniserver her und erstellt Status für jeden gefundenen Steuerstatus.

Die IDs der Staaten sind wie folgt formatiert: `loxone.<instance>.<control>.<state>`

- `<Instanz>` ist der ioBroker-Adapterinstanzindex (normalerweise "0")
- `<control>` ist die UUID des Steuerelements
- `<Status>` ist der Status innerhalb des Steuerelements (weitere Informationen finden Sie unter [Unterstützte Steuerelementtypen] (# Unterstützte Steuerelementtypen)).

Der Name, der beim Konfigurieren eines Steuerelements in Loxone Config angegeben wird, wird nur als Anzeigename in ioBroker verwendet.
Dies liegt daran, dass ein Benutzer möglicherweise denselben Namen für mehrere Steuerelemente wählt.

Weitere Informationen zu Steuerelementen und ihren Status finden Sie auch in der Loxone-API (insbesondere in der Strukturdatei): https://www.loxone.com/enen/kb/api/

## Sichtbarkeit steuern
Standardmäßig verbirgt Loxone Miniserver viele Steuerelemente (und damit deren Status) vor der Weboberfläche.

Das heißt, sie sind auch vor diesem ioBroker-Adapter verborgen.

Um sicherzustellen, dass alle Ihre Status ordnungsgemäß an ioBroker gemeldet werden, stellen Sie sicher, dass "In Visualisierung verwenden" aktiviert ist:

![Verwendung in den Visualisierungseinstellungen](../../../en/adapterref/iobroker.loxone/doc/loxone-config-use-in-visualization.png)

## Globale Staaten
Die folgenden globalen Zustände werden derzeit von diesem Adapter bereitgestellt:

- `OperatingMode`: Die aktuelle Betriebsmodusnummer des Loxone Miniserver
- "OperatingMode-Text": Der aktuelle Betriebsmodus des Loxone Miniserver als Text
- "Sonnenaufgang": Die Anzahl der Minuten nach Mitternacht, in denen die Sonne heute aufgeht
- "Sonnenuntergang": Die Anzahl der Minuten nach Mitternacht, in denen die Sonne heute untergeht
- "Benachrichtigungen": Die Anzahl der Benachrichtigungen
- "Änderungen": Die Anzahl der Änderungen
- Alle anderen globalen Staaten werden einfach als Texte gemeldet

## Unterstützte Steuerungstypen
Die folgenden Steuerelementtypen werden derzeit von diesem Adapter unterstützt.

Hinter dem Namen des Staates sehen Sie den Typ des Staates:

- `(rw)`: lesbar und beschreibbar: Dieser Status kann von ioBroker aus geändert werden
- `(ro)`: schreibgeschützt: Dieser Status kann nicht von ioBroker geändert werden
- `(wo)`: Nur Schreiben: Der Wert dieses Status wird von diesem Adapter nicht gemeldet, kann jedoch geändert werden, wodurch eine Aktion auf dem Loxone Miniserver ausgelöst wird

### Alarm
Bereitgestellt von Burgler Alarm Control.

- "bewaffneter" (rw) boolescher Zustand (wahr / falsch) des Alarms; Wenn Sie "true" auf diesen Wert schreiben, wird der Alarm sofort eingeschaltet (ohne die vordefinierte Verzögerung).
- `nextLevel` (ro) die ID der nächsten Alarmstufe
    - 1 = Lautlos
    - 2 = akustisch
    - 3 = optisch
    - 4 = intern
    - 5 = extern
    - 6 = Fernbedienung
- `nextLevelDelay` (ro) die Verzögerung des nächsten Levels in Sekunden
- `nextLevelDelayTotal` (ro) die Gesamtverzögerung des nächsten Levels in Sekunden
- `level` (ro) die ID der aktuellen Alarmstufe
    - 1 = Lautlos
    - 2 = akustisch
    - 3 = optisch
    - 4 = intern
    - 5 = extern
    - 6 = Fernbedienung
- `startTime` (ro) der Zeitstempel beim Start des Alarms
- `armedDelay` (ro) die Verzögerung der Alarmierung der Alarmsteuerung
- `armedDelayTotal` (ro) die Gesamtverzögerung der Alarmsteuerung, die aktiviert wird
- "Sensoren" (ro) die Liste der Sensoren
- `disabledMove` (rw) die Bewegung ist deaktiviert (true) oder nicht (false)
- `delayOn` (wo), wenn ein Wert in diesen Zustand geschrieben wird, aktiviert den Alarm mit der konfigurierten Verzögerung
- `quit` (wo) das Schreiben eines Wertes in diesen Zustand bestätigt den Alarm

### Zentraler Alarm
Wird von der zentralen Burger-Alarmsteuerung bereitgestellt.

- "bewaffneter" (rw) boolescher Zustand (wahr / falsch) des Alarms; Wenn Sie "true" auf diesen Wert schreiben, wird der Alarm sofort eingeschaltet (ohne die vordefinierte Verzögerung).
- `delayOn` (wo), wenn ein Wert in diesen Zustand geschrieben wird, aktiviert den Alarm mit der konfigurierten Verzögerung
- `quit` (wo) das Schreiben eines Wertes in diesen Zustand bestätigt den Alarm

### Wecker
Wird durch Weckersteuerung bereitgestellt.

- "isEnabled" (rw) boolescher Zustand (wahr / falsch) des Weckers
- "isAlarmActive" (ro) boolesch (wahr / falsch), ob der Alarm gerade klingelt
- `assertNeeded` (ro) boolescher Wert (true / false), ob der Benutzer den Alarm bestätigen muss
- `ringingTime` (ro) Countdown in Sekunden, wie lange der Wecker klingelt, bis er wieder schlummert
- `ringDuration` (rw) Dauer in Sekunden, in der der Wecker klingelt
- `prepareDuration` (rw) Vorbereitungszeit in Sekunden
- `snoozeTime` (ro) Sekunden bis das Schlummern endet
- `snoozeDuration` (rw) Dauer in Sekunden nach dem Schlafengehen
- `snooze` (wo), wenn ein Wert in diesen Zustand geschrieben wird, schaltet den aktuellen Alarm aus
- Wenn Sie einen Wert in diesen Zustand schreiben, wird der aktuelle Alarm gelöscht

### AudioZone
Bereitgestellt von Music Server Zone.

- `serverState` (ro) Status des Musikservers:
    - -3 = unbekannte / ungültige Zone
    - -2 = nicht erreichbar
    - -1 = unbekannt
    - 0 = offline
    - 1 = Initialisieren (Booten, versuchen es zu erreichen)
    - 2 = online
- `playState` (rw) der Wiedergabestatus:
    - -1 = unbekannt (dieser Wert kann nicht eingestellt werden)
    - 0 = gestoppt (durch Einstellen dieses Werts wird die Wiedergabe angehalten)
    - 1 = angehalten (durch Einstellen dieses Werts wird die Wiedergabe angehalten)
    - 2 = Wiedergabe (durch Einstellen dieses Werts wird die Wiedergabe gestartet / fortgesetzt)
- `clientState` (ro) Status des Clients:
    - 0 = offline
    - 1 = Initialisieren (Booten, versuchen es zu erreichen)
    - 2 = online
- `power` (rw), ob die Client-Leistung aktiv ist oder nicht
- `Lautstärke` (rw) aktuelle Lautstärke
- `maxVolume` (ro) Zonen können eine maximale Lautstärke zugewiesen werden
- `shuffle` (rw), ob das Shuffle der Wiedergabeliste aktiviert ist oder nicht
- `sourceList` (ro) Liste mit allen Zonenfavoriten
- Wiederholungsmodus "Wiederholen" (rw):
    - -1 = unbekannt
    - 0 = aus
    - 1 = alles wiederholen
    - 2 = -nicht verwendet-
    - 3 = aktuelles Element wiederholen
- `songName` (ro) Songname
- `Dauer` (ro) wie lang der gesamte Track ist, -1 wenn nicht bekannt (Stream)
- `progress` (rw) aktuelle Position in der Spur
- Albumalbum (ro)
- "Künstler" (ro) Künstlername
- Name der Station (ro)
- Genre-Name (ro)
- `Cover` (ro) Song / Album Cover Bild URL
- `source` (rw) aktuell ausgewählte Quellenkennung (siehe` sourceList` oben)
- `prev` (wo) das Schreiben eines Wertes in diesen Zustand wechselt zum vorherigen Titel
- `next` (wo), wenn ein Wert in diesen Zustand geschrieben wird, wechselt zum nächsten Titel

### Zentrales Audio
Wird vom zentralen Musikserver bereitgestellt.

- `control` (wo) legt den Spielstatus aller Spieler fest (` true` = play, `false` = pause)

### Farbwähler
Dieses Gerät wird nur in einem LightController angezeigt.

- `red` (rw) Rotwert des Farbwählers
- `Grün` (rw) Grünwert des Farbwählers
- `blue` (rw) blue Wert des Farbwählers

Wenn Sie einen oder mehrere der oben genannten Zustände von ioBroker aus festlegen, wird erst nach ca. 100 ms ein Befehl an den Miniserver gesendet.
Dies soll verhindern, dass sich die Farbe für eine einzelne Benutzereingabe mehrmals ändert.

### Colorpicker V2
Dieses Gerät wird nur in einem Light Controller V2 in Loxone-Softwareversion 9 und höher angezeigt.

- `red` (rw) Rotwert des Farbwählers
- `Grün` (rw) Grünwert des Farbwählers
- `blue` (rw) blue Wert des Farbwählers

Wenn Sie einen oder mehrere der oben genannten Zustände von ioBroker aus festlegen, wird erst nach ca. 100 ms ein Befehl an den Miniserver gesendet.
Dies soll verhindern, dass sich die Farbe für eine einzelne Benutzereingabe mehrmals ändert.

### Dimmer
Zur Verfügung gestellt von Dimmern.

- `Position` (rw) aktuelle Position für den Dimmer
- `min` (ro) aktueller Mindestwert
- `max` (ro) aktueller Maximalwert
- `step` (ro) aktueller Schrittwert
- Wenn Sie einen Wert in diesen Zustand schreiben, wird der Dimmer auf die letzte bekannte Position gesetzt
- ʻoff` (wo), wenn ein Wert in diesen Zustand geschrieben wird, deaktiviert den Dimmer, setzt die Position auf 0, merkt sich aber die letzte Position

### Tor
Bereitgestellt durch Torsteuerungen.

- `position` (ro) die Position von 1 = bis 0 = unten
- "aktive" (rw) Stromrichtung der Torbewegung
    - -1 = schließen
    - 0 = bewegt sich nicht
    - 1 = offen
- `verhindernOpen` (ro) ob das Öffnen der Tür verhindert wird
- `PreventClose` (ro), ob das Schließen der Tür verhindert wird

### Zentrales Tor
Wird von der zentralen Torsteuerung bereitgestellt.

- "Öffnen" (wo) öffnet alle Tore
- `close` (wo) schließt alle Tore
- `stop` (wo) stoppt alle Torantriebe

### InfoOnlyDigital
Bereitgestellt durch virtuelle Zustände sowie den Loxone Touch-Schalter.

- "aktiver" (ro) boolescher Zustand (wahr / falsch) der Kontrolle
- "Active-Text" (ro), falls konfiguriert, das Textäquivalent des Status
- "Active-Image" (ro), falls konfiguriert, das Image-Äquivalent des Status
- "Active-Color" (ro), falls konfiguriert, das Farbäquivalent des Status

![InfoOnlyDigital Einstellungen](../../../en/adapterref/iobroker.loxone/doc/loxone-config-info-only-digital.png)

### InfoOnlyAnalog
Bereitgestellt durch virtuelle Zustände sowie den Loxone Touch-Schalter.

- `value` (ro) der Zustandswert (Nummer) der Steuerung
- `value-formatated` (ro) falls konfiguriert, der formatierte Wert des Status (unter Verwendung des" Unit "-Formats von Loxone Config)

### Gegensprechanlage
Wird von Türsteuerungen bereitgestellt.

- `bell` (ro) ob die Glocke läutet
- `lastBellEvents` (ro) Array mit den Zeitstempeln für jede Glockenaktivität, die nicht beantwortet wurde
- `version` (ro) Nur Loxone Intercoms - Text, der die aktuell installierte Firmware enthält

    Versionen

- Wenn Sie einen Wert in diesen Zustand schreiben, wird die Glocke deaktiviert

Diese Art von Kanal kann andere Geräte enthalten. Weitere Informationen finden Sie im jeweiligen Kapitel.

### Jalousie
Bereitgestellt durch verschiedene Arten von Jalousien (automatisch und manuell).

- "up" (rw), ob Jalousie aufsteigt
- `down` (rw) ob Jalousie sich nach unten bewegt
- `Position` (ro) Position des Jalousie, eine Zahl von 0 bis 1
    - Jalousie obere Position = 0
    - Jalousie untere Position = 1
- `shadowPosition` (ro) Schattenposition der Jalousie (Jalousien), eine Zahl von 0 bis 1
    - Jalousien sind nicht schattiert = 0
    - Jalousien sind schattiert = 1
- `securityActive` (ro) wird nur von Personen mit Autopilot verwendet. Dies stellt die Sicherheitsabschaltung dar
- `autoAllowed` (ro) wird nur von Personen mit Autopilot verwendet
- "autoActive" (rw) wird nur von Personen mit Autopilot verwendet
- `gesperrt` (ro) nur von Personen mit Autopilot, dies repräsentiert die Ausgabe-QI in Loxone Config
- "infoText" (ro) informiert z.B. darüber, was den gesperrten Zustand verursacht hat oder was dazu geführt hat, dass die Sicherheit aktiv wurde.
- `fullUp` (wo) das Schreiben eines Wertes in diesen Zustand löst eine vollständige Aufwärtsbewegung aus
- `fullDown` (wo) das Schreiben eines Wertes in diesen Zustand löst eine vollständige Abwärtsbewegung aus
- `shadow` (wo) Wenn Sie einen Wert in diesen Zustand schreiben, wird der Jalousie in die perfekte Position gebracht

### Central Jalousie
Bereitgestellt von der Zentraljalousiensteuerung.

- "autoActive" (rw) wird nur von Personen mit Autopilot verwendet
- `fullUp` (wo) das Schreiben eines Wertes in diesen Zustand löst eine vollständige Aufwärtsbewegung aus
- `fullDown` (wo) das Schreiben eines Wertes in diesen Zustand löst eine vollständige Abwärtsbewegung aus
- `Schatten` (wo) schreibt einen beliebigen Wert in diesen Zustand Schatten aller Jalousien in die perfekte Position

### Lichtsteuerung
Bereitgestellt von (Hotel-) Lichtsteuerungen.
Szenen können nur in den Loxone-Anwendungen geändert, aber in ioBroker ausgewählt werden.

- "ActiveScene" (rw) aktuelle Nummer der aktiven Szene
    - 0: alles aus
    - 1..8: Benutzerdefinierte Szene (Definition / Lernen von Szenen muss mit den Loxone-Werkzeugen erfolgen)
    - 9: alles an
- `sceneList` (ro) Liste aller Szenen
- `plus` (wo) wechselt zur nächsten Szene
- `minus` (wo) wechselt zur vorherigen Szene

Diese Art von Kanal kann andere Geräte enthalten. Weitere Informationen finden Sie im jeweiligen Kapitel.

### Lichtsteuerung V2
Bereitgestellt von (Hotel-) Lichtsteuerungen in Loxone Software Version 9 und höher.
Stimmungen können nur in den Loxone-Anwendungen geändert, aber in ioBroker ausgewählt und kombiniert werden.

- `MoodList` (ro) Liste aller konfigurierten Stimmungsnamen
- "ActiveMoods" (rw) derzeit aktive Liste der Stimmungsnamen
- `favorMoods` (ro) Liste der bevorzugten Stimmungsnamen
- "AdditionalMoods" (ro) Liste der nicht bevorzugten Stimmungsnamen
- `plus` (wo) wechselt zur nächsten Stimmung
- `minus` (wo) wechselt zur vorherigen Stimmung

Diese Art von Kanal kann andere Geräte enthalten. Weitere Informationen finden Sie im jeweiligen Kapitel.

### Zentrale Lichtsteuerung
Wird von einer zentralen Lichtsteuerung bereitgestellt.

- `control` (wo) schaltet alle Lichter ein oder aus

### Meter
Bereitgestellt von Stromzählern.

- "Ist" (ro) der tatsächliche Wert (Anzahl)
- "tatsächlich formatiert" (ro), falls konfiguriert, der formatierte tatsächliche Wert des Status (unter Verwendung des "Unit" -Formats von Loxone Config)
- `total` (ro) der Gesamtwert (Anzahl)
- `total-formatated` (ro) falls konfiguriert, der formatierte Gesamtwert des Status (unter Verwendung des" Unit "-Formats von Loxone Config)
- `reset` (wo) Schreiben eines Wertes in diesen Zustand setzt den Gesamtwert zurück

### Druckknopf
Bereitgestellt durch virtuelle Drucktasteneingaben.

- "Aktiv" (rw) der aktuelle Status der Drucktaste
- Wenn Sie einen Wert in diesen Zustand schreiben, wird simuliert, dass die Taste nur für eine sehr kurze Zeit gedrückt wird

### Schieberegler
Bereitgestellt durch analoge virtuelle Eingänge.

- `value` (rw) der aktuelle Wert des Schiebereglers
- `value-formatated` (ro) falls konfiguriert, der formatierte Wert des Status (unter Verwendung des" Unit "-Formats von Loxone Config)
- "Fehler" (ro) zeigt einen ungültigen Wert des Schiebereglers an

### Rauchmelder
Bereitgestellt von Stromzählern.

- `nextLevel` (ro) die ID der nächsten Alarmstufe
    - 1 = Lautlos
    - 2 = akustisch
    - 3 = optisch
    - 4 = intern
    - 5 = extern
    - 6 = Fernbedienung
- `nextLevelDelay` (ro) Verzögerung des nächsten Levels in Sekunden
- `nextLevelDelayTotal` (ro) Gesamtverzögerung des nächsten Levels in Sekunden
- `level` (ro) die ID der aktuellen Alarmstufe
    - 1 = Lautlos
    - 2 = akustisch
    - 3 = optisch
    - 4 = intern
    - 5 = extern
    - 6 = Fernbedienung
- "Sensoren" (ro) die Liste der Sensoren
- "Akustischer Alarm" (ro) -Zustand des akustischen Alarms falsch für nicht aktiv und wahr für aktiv
- `testAlarm` (ro) ob testalarm aktiv ist
- "AlarmCause" (ro) die Ursache des Alarms:
    - 1 = nur Rauchmelder
    - 2 = nur Wasser
    - 3 = Rauch und Wasser
    - 4 = nur Temperatur
    - 5 = Feuer und Temperatur
    - 6 = Temperatur und Wasser
    - 7 = Feuer, Temperatur und Wasser
- `startTime` (ro) Zeitstempel beim Start des Alarms
- `timeServiceMode` (rw) Verzögerung bis der Servicemodus deaktiviert ist
- `stumm` (wo) Wenn Sie einen Wert in diesen Zustand schreiben, wird die Sirene stummgeschaltet
- `quit` (wo) Schreiben eines Wertes in diesen Zustand bestätigt den Rauchmelder

### Schalter
Wird von virtuellen Eingangsschaltern bereitgestellt.

- "Aktiv" (rw) der aktuelle Status des Schalters

### TimedSwitch
Zur Verfügung gestellt von Treppenhaus und Multifunktionsschaltern.

- `deactivationDelayTotal` (ro) Sekunden, wie lange der Ausgang aktiv ist, wenn der Timer verwendet wird
- Countdown "Deaktivierung Verzögerung" (ro), bis der Ausgang deaktiviert wird
    - 0 = der Ausgang ist ausgeschaltet
    - -1 = der Ausgang ist permanent eingeschaltet
    - Andernfalls wird von deactivationDelayTotal heruntergezählt
- Wenn Sie einen Wert in diesen Zustand schreiben, wird der Schalter dauerhaft ohne Deaktivierungsverzögerung aktiviert
- Wenn Sie einen Wert in diesen Zustand schreiben, wird der Schalter deaktiviert
- `puls` (wo) pulsiert den Schalter:
    - Deaktivierungsverzögerung = 0
        - Startet den Countdown von deactivationDelayTotal bis 0
    - Wenn dies ein Treppenhausschalter ist:
        - Deaktivierungsverzögerung = -1
            - Keine Wirkung, bleibt dauerhaft eingeschaltet.
        - Deaktivierungsverzögerung> 0
            - Startet den Countdown neu
    - wenn dies ein Multifunktionsschalter ist
        - schaltet es aus (vom Countdown oder permanent eingeschaltet)

### Tracker
Zur Verfügung gestellt von Treppenhaus und Multifunktionsschaltern.

- Liste "Einträge" (ro) der vom Miniserver zurückgegebenen Einträge

### WindowMonitor
Bereitgestellt von Stromzählern.

- `numOpen` (ro) Anzahl offener Fenster und Türen
- `numClosed` (ro) Anzahl geschlossener Fenster und Türen
- `numTilted` (ro) Anzahl der gekippten Fenster und Türen
- `numOffline` (ro) Anzahl der Fenster und Türen, die nicht verfügbar sind
- `numLocked` (ro) Anzahl der verschlossenen Fenster und Türen
- `numUnlocked` (ro) Anzahl der entsperrten Fenster und Türen

Die Summe der Werte aus all diesen Zuständen entspricht der Anzahl der überwachten Fenster und Türen. Die Fenster / Türen mit zwei Zuständen werden immer zum "schlechtesten" Zustand gezählt.

Für jedes überwachte Fenster / jede überwachte Tür gibt es ein Gerät mit einem Index als ID und dem angegebenen Namen. Sie haben die folgenden Zustände:

- `geschlossen` (ro) das Fenster / die Tür ist geschlossen
- "gekippt" (ro) das Fenster / die Tür ist gekippt
- "Öffnen" (ro) das Fenster / die Tür ist offen
- `verriegelt` (ro) das Fenster / die Tür ist verschlossen
- "entriegelt" (ro) das Fenster / die Tür ist entriegelt

## Wetterserver
Die Wetterserverinformationen werden als Gerät mit mehreren Kanälen bereitgestellt.
Das Gerät heißt `WeatherServer`.
Es beinhaltet:

- der Kanal "Ist" mit den aktuellen Wetterwerten
- ein Kanal für jede Prognosestunde namens "HourXX", wobei "XX" die Anzahl der Stunden in der Zukunft ist

Jeder Kanal enthält die folgenden Zustände:

- `barometricPressure`: numerischer Luftdruckwert
- `barometricPressure-formatiert`: formatierter Luftdruckwert mit Einheit
- `dewPoint`: numerischer Taupunktwert
- `dewPoint-formatiert`: formatierter Taupunktwert mit Einheit
- "wahrgenommene Temperatur": numerischer wahrgenommener Temperaturwert
- "wahrgenommene Temperatur formatiert": formatierter wahrgenommener Temperaturwert mit Einheit
- "Niederschlag": numerischer Niederschlagswert
- "niederschlagsformatiert": formatierter Niederschlagswert mit Einheit
- "relative Luftfeuchtigkeit": numerischer Wert für die relative Luftfeuchtigkeit
- `relativeHumidity-formatiert`: formatierter relativer Feuchtigkeitswert mit Einheit
- `solarRadiation`: Sonnenstrahlungswert
- `Temperatur`: numerischer Temperaturwert
- `temperaturformatiert`: formatierter Temperaturwert mit Einheit
- `timestamp`: Zeitstempel der Daten als` value.time` (JavaScript-Zeit)
- `weatherType`: numerischer Aufzählungswert für den Wettertyp
- `weatherType-text`: Textdarstellung des Wettertyps
- `windDirection`: Windrichtungswert
- `windSpeed`: Windgeschwindigkeitswert
- `windSpeed-formatiert`: formatierter Windgeschwindigkeitswert mit Einheit

## Kompatibilität
Die Kompatibilität wurde mit Loxone Miniserver Go 9.0.9.26 unter Verwendung von Loxone Config 9.0.9.26 getestet.

## Fehlerberichte und Funktionsanforderungen
Verwenden Sie das GitHub-Repository, um Fehler zu melden oder neue Funktionen anzufordern.

Wenn Sie einen fehlenden Steuerelementtyp benötigen, geben Sie den Namen an, wie er im Fehlerprotokoll von ioBroker angegeben ist, sowie den gesamten Rohinhalt des Geräts im ioBroker-Objektbaum:

Beispiel für eine Protokolldatei für "LightController":

![Protokoll der fehlenden LightController-Steuerung](../../../en/adapterref/iobroker.loxone/doc/log-missing-control-type.png)

Nativer Wert von ioBroker &gt; Objekte

![Details zur fehlenden LightController-Steuerung](../../../en/adapterref/iobroker.loxone/doc/details-missing-control-type.png)

## Legal
Dieses Projekt ist weder direkt noch indirekt mit der Firma Loxone Electronics GmbH verbunden.

Loxone und Miniserver sind eingetragene Marken der Loxone Electronics GmbH.

## Changelog

### 2.0.2 (2020-10-26)

-   (UncleSamSwiss) Fixed color picker updates (#52)
-   (UncleSamSwiss) TimedSwitch to have `on`/`off` instead of `active` (#53)
-   (UncleSamSwiss) Cleaning illegal characters for room and function names (#54)

### 2.0.1 (2020-09-24)

-   (UncleSamSwiss) Fixed percentage states always showing 0% (#49)
-   (UncleSamSwiss) Fixed analog virtual inputs wouldn't set the value 0 from ioBroker (#47)
-   (UncleSamSwiss) Added translations to package information.

### 2.0.0

- **BREAKING:** Since the password is now encrypted, you will need to enter the password again after an update to this version!
-   (UncleSamSwiss) Updated to the latest development tools and changed to the TypeScript language

### 1.1.0

-   (UncleSamSwiss) Added support for Miniserver Gen 2
-   (sstroot) RGB for LightControllerV2
-   (Apollon77) Updated CI Testing

### 1.0.0

-   (UncleSamSwiss) Fixed issue that was resetting the custom settings and cloud smartName
-   (alladdin) Fixed connection issues with Loxone Miniserver 10
-   (UncleSamSwiss) Changed all write-only "switch"es to "button"s
-   (UncleSamSwiss) Added support for AlarmClock control
-   (Apollon77) Updated CI Testing

### 0.4.0

-   (UncleSamSwiss) Improved support for Loxone Config 9
-   (UncleSamSwiss) Changed all color choosers (i.e. color lights) to use RGB (previously HSV/HSL was completely wrong)

### 0.3.0

-   (UncleSamSwiss) Control names only synchronized on the first time by default (configurable); users can change control names the way they want

### 0.2.1

-   (UncleSamSwiss) Added support for Slider control

### 0.2.0

-   (UncleSamSwiss) Added proper support for Alexa for the following controls: Alarm, AudioZone, Gate, Jalousie and LightController

### 0.1.1

-   (UncleSamSwiss) Added support for synchronizing rooms and functions (categories) from Loxone Miniserver

### 0.1.0

-   (UncleSamSwiss) Added support for many more controls including commands from ioBroker to Loxone Miniserver

### 0.0.3

-   (Bluefox) Formatting, refactoring and Russian translations

### 0.0.2

-   (UncleSamSwiss) Added creation of an empty device for all unsupported controls (helps figure out its configuration)

### 0.0.1

-   (UncleSamSwiss) Initial version

## License

Copyright 2020 UncleSamSwiss

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.