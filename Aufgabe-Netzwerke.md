---
title: 'Aufgabe zu "Netzwerke"'
---

## Aufgabe - Netzwerkroute

Wir möchten wissen, über welche Netzwerkknoten wir die Webseite der Vereinten Nationen (UNO) erreichen und in welchen Städten/Ländern die jeweiligen Server denn konkret stehen.

### Schritt 1

Als erstes möchten wir die IP-Adresse der Webseite der Vereinten Nationen herausfinden. 

Dazu können wir uns eines online DNS Tools bedienen. 
Ein solches Tool ist z.B. [https://www.digwebinterface.com/](https://www.digwebinterface.com/) oder
[https://dnschecker.org](https://dnschecker.org).

*Unter welchen IP-Adressen ist die Webseite der Vereinten Nationen erreichbar?*

Speichere deine Ergebnisse in der Datei **UNO.md** in einem entsprechenden Abschnitt mit Überschrift etc.


### Schritt 2

Nun möchten wir wissen, über welche Netzwerkknoten wir die Webseite der Vereinten Nationen erreichen.

Hierzu können wir uns eines online Tools bedienen, welches uns die Netzwerkroute anzeigt.
Ein solches Tool ist z.B. [https://gsuite.tools/de/traceroute](https://gsuite.tools/de/traceroute).

*Verwenden sie die obige Webseite und geben sie die URL (!) der Webseite ein!*

- (?) Auf welcher Server IP sind sie gelandet? Ist diese in ihrer Liste aus Schritt 1?
- (!) Kopieren sie sich die IP-Liste der besuchten Netzwerkknoten und speichern sie diese in der Datei **UNO.md** in einem entsprechenden Abschnitt.

### Schritt 3

Die Ortsangaben der obigen Webseite war nur für einige Knoten verfügbar.
Daher möchten wir nun die Ortsangaben für alle Knoten herausfinden.
Hierzu können wir uns eines anderen Geolocation online Tools bedienen, welches uns die Ortsangaben zu einer IP-Adresse anzeigt, konkret [https://www.iplocation.net/bulk-ip-lookup](https://www.iplocation.net/bulk-ip-lookup).

*Kopieren sie die IPs in 10er Blöcken (maximale Eingabelänge) in die Webseite und wählen sie als "Provider" `IP2Location` aus.*

- (!) Kopieren sie sich die Ortsangaben der besuchten Netzwerkknoten und speichern sie diese als Tabelle in der Datei **UNO.md**.
- (!) Wiederholen sie den Vorgang bis sie Angaben zu allen IPs haben.








https://www.iplocation.net/bulk-ip-lookup
 >> IP2Location Provider
