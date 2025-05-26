---
title: 'Aufgabe zu "Netzwerke"'
---

## Aufgabe - Netzwerkroute

Wir möchten wissen, über welche Netzwerkknoten wir die englische Wikpedia Webseite erreichen und in welchen Städten/Ländern die jeweiligen Server denn konkret stehen.

### Schritt 1

Als erstes möchten wir die IP-Adresse der englischen Wikipedia Webseite `en.wikipedia.org` herausfinden. 

Dazu können wir uns eines online DNS Tools bedienen. 
Ein solches Tool ist z.B. [https://www.digwebinterface.com/](https://www.digwebinterface.com/) oder
[https://dnschecker.org](https://dnschecker.org).

*Unter welcher IP-Adresse ist die Webseite erreichbar?*

- (!) Speichere deine Ergebnisse in der Datei **en.wikipedia.org.md** in einem entsprechenden Abschnitt mit Überschrift etc.


### Schritt 2

Nun möchten wir wissen, über welche Netzwerkknoten wir die Webseite erreichen.

*Hierzu müssen wir uns auf die Kommandozeile begeben.*

- Microsoft Windows:
  - Öffnen sie eine "PowerShell"
  - geben sie `tracert -4 en.wikipedia.org` ein
- Linux/MacOS:
  - Öffnen sie ein Terminal (Bash)
  - geben sie `traceroute en.wikipedia.org` ein


- (?) Auf welcher Server IP sind sie gelandet? Ist diese in ihrer Liste aus Schritt 1?
- (!) Kopieren sie sich die IP-Liste der besuchten Netzwerkknoten und speichern sie diese in der Datei **en.wikipedia.org.md** in einem entsprechenden Abschnitt.


### Schritt 3

Nun möchten wir die Ortsangaben für alle Knoten herausfinden.
Hierzu können wir uns eines anderen Geolocation online Tools bedienen, welches uns die Ortsangaben zu einer IP-Adresse anzeigt, konkret [https://www.iplocation.net/bulk-ip-lookup](https://www.iplocation.net/bulk-ip-lookup).

*Kopieren sie die IPs in 10er Blöcken (maximale Eingabelänge) in die Webseite und wählen sie als "Provider" `IP2Location` aus.*

- (!) Kopieren sie sich die Ortsangaben der besuchten Netzwerkknoten und speichern sie diese als Tabelle in der Datei **en.wikipedia.org.md.md**.
- (!) Wiederholen sie ggf. den Vorgang bis sie Angaben zu allen IPs haben.

### Ergebnis

- Datei **en.wikipedia.org.md** mit
  - IP-Adresse(n) des Webservers der englischen Wikipedia Seite
  - IP-Liste der Netzwerkknoten, die beim Aufruf der Webseite durchlaufen wurden
  - Tabelle mit Ortsangaben der Netzwerkknoten

