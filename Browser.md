---
title: "Browser"
teaching: 30
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions 

- Browser?
- Cookies?
- JavaScript?
- Suchmaschinen?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Aufgaben und Funktionsweise von Browsern
- Einsatz und Ziele von Cookies
- Möglichkeiten und Grenzen von JavaScript
- Gedanken zu Suchmaschinen und GPTs/LLMs

::::::::::::::::::::::::::::::::::::::::::::::::

Browser sind Programme, die es ermöglichen, Webseiten oder Dokumente anzuzeigen und mit diesen zu interagieren.
Sie sind die Schnittstelle zwischen dem Nutzer und dem World Wide Web. 
Beispiele sind Google Chrome, Mozilla Firefox, Microsoft Edge und Safari (Apple).

## Historie

Die ersten Browser waren textbasiert und konnten nur einfache HTML-Dokumente (Webseiten) darstellen.
Derartige Browser sind heute noch im Einsatz, z.B. `lynx` oder `w3m`, und werden oft in der Kommandozeile verwendet.
Diese Browser sind sehr schnell und ressourcenschonend, da sie keine Grafiken oder JavaScript ausführen können, und können daher auch bei sehr langsamen Internetverbindungen eingesetzt werden.
Im Folgenden ist das Darstellen der Google-Startseite in `w3m` dargestellt:

![Google Startseite im `w3m` Textbrowser](fig/w3m-google.png){width=80% alt="w3m-google"}

Seit den 1990er Jahren sind Browser in der Lage, auch Grafiken und andere Medien anzuzeigen.
Die ersten Browser, die dies ermöglichten, waren Netscape Navigator und Microsoft Internet Explorer.
Die "Browserkriege" der 1990er Jahre führten zu einer Vielzahl von proprietären Technologien, die die Entwicklung von Webseiten erschwerten.
Gegen Ende der 1990er Jahre hatte Microsoft eine marktbeherrschende Stellung erreicht, die erst in den 2000er Jahren durch den Aufstieg von Mozilla Firefox und später Google Chrome gebrochen wurde.
Die Entwicklung ist in der folgenden Grarik dargestellt.

![Marktanteile von Browsern. Quellen [csmonitor.com](https://www.csmonitor.com/Technology/Tech/2008/0131/p25s01-stct.html) und [statcounter.com](https://gs.statcounter.com/browser-market-share) (Dez. 2024)](fig/browser-timeline.png){width=80% alt="Browser-Marktanteile"}

Mit der Einführung von Google Chrome im Jahr 2008 begann eine neue Ära der Browserentwicklung.
Chrome war der erste Browser, der auf der JavaScript-Engine V8 basierte, die deutlich schneller war als die Konkurrenz.
Chrome führte auch eine Sandbox-Technologie ein, die es ermöglichte, Webseiten in isolierten Prozessen auszuführen, um die Sicherheit zu erhöhen.
Seitdem haben sich die Browser stark weiterentwickelt und sind heute in der Lage, komplexe Webanwendungen auszuführen, die früher nur als Desktop-Anwendungen (eigenständige Programme) möglich waren.
Mittlerweile basieren fast alle Browser auf der Open-Source-Engine Chromium (dem Herzstück von Chrome), die von Google entwickelt wurde, und sind daher sehr ähnlich in ihrer Funktionsweise.


:::::::::: challenge

# Aufgabe

Microsoft Internet Explorer war lange Zeit der dominierende Browser, da er mit Windows gebündelt war.

Welche Gründe könnten für den Aufstieg von Google Chrome verantwortlich sein?

::: solution

# Antwort

- Chrome war (wirklich) besser:
  - schneller und ressourcenschonender
  - Unterstützung für moderne Webstandards
  - ...
- ABER: Chrome ist mittlerweile der Standardbrowser auf Android-Geräten, was auch zu einer hohen Verbreitung beiträgt

:::

::::::::::::::::::::

## Aufgaben und Funktionsweise von Browsern

Browser haben verschiedene Aufgaben, darunter:

- Anzeigen von Webseiten
- Ausführen von JavaScript
- Verwalten von Cookies
- Anzeigen von Medien (Bilder, Videos, Audio)
- Ausführen von Webanwendungen (z.B. Google Docs, Facebook)
- Unterstützung von Webstandards (HTML, CSS, JavaScript)
- Sicherheit (Sandboxing, HTTPS, Passwörter, Content Security Policy)
- Barrierefreiheit (Screenreader, Tastaturnavigation)
- Datenschutz (Verschlüsselung, Do Not Track, Cookie-Verwaltung)
- Erweiterbarkeit (Plugins, Addons)
- ...

Browser sind also weit mehr als nur ein "Fenster" ins Internet, sondern eine komplexe Software, die viele verschiedene Technologien und Standards unterstützt und bündelt.
Im Folgenden werden einige dieser Aufgaben näher beleuchtet.

:::::::::::::::: testimonial

# Browser vs. Suchmaschine

Wichtig: **Browser sind keine Suchmaschinen!**

- Suchmaschinen = Webseiten, die es ermöglichen, Inhalte im Internet zu finden.
- Browser = Programme/Werkzeuge, die Webseiten anzeigen und mit ihnen interagieren.

*Das heisst, man benötigt einen Browser, um eine Suchmaschine zu benutzen, aber nicht umgekehrt.*

::::::::::::::::::::::::::::



## Webseiten anzeigen

Bevor wir uns damit beschäftigen, was alles geschehen muss, damit eine Webseite angezeigt wird, schauen wir uns an, wie eine Webseite aufgebaut ist.

Im Folgenden werden die wichtigsten **Bestandteile einer Webseite** zergliedert dargestellt.

![Bestandteile einer Webseite. Um eine Webseite anzuzeigen (oben mittig), müssen verschiedene Ressourcen geladen werden: HTML, CSS, JavaScript, Bilder, Schriftarten, etc., die i.d.R. in verschiedenen Dateien vorliegen.](fig/webpage-Bestandteile.png){width=80% alt="Bestandteile einer Webseite"}

Zentral für eine Webseite ist die **HTML**-Datei, die den strukturellen Aufbau der Seite definiert.
In dieser Datei werden die verschiedenen Elemente der Seite (Überschriften, Absätze, Links, Bilder, etc.) definiert und miteinander verknüpft bzw. deren Anordnung festgelegt.

Hierbei werden in der HTML-Datei auch Verweise auf andere Ressourcen gemacht, die für die Darstellung der Seite notwendig sind.
So werden z.B. **Bilddateien** referenziert und deren Position auf der Seite festgelegt.
Auch **Schriftarten** und **CSS-Dateien** (Cascading Style Sheets) werden in der HTML-Datei referenziert, um das Aussehen der Seite zu definieren.

Interaktivität und dynamische Inhalte werden durch **JavaScript** ermöglicht, das ebenfalls in der HTML-Datei eingebettet oder referenziert wird.
JavaScript ermöglicht es, auf Benutzereingaben zu reagieren, Daten zu verarbeiten und zu speichern, und die Seite dynamisch zu verändern.

Alle diese Ressourcen müssen vom Browser zuerst geladen und verarbeitet werden, um die Seite anzuzeigen zu können.
Das Laden und Verarbeiten dieser Ressourcen wird als **Fetching** bezeichnet und kann je nach Grösse und Anzahl der Ressourcen einige Zeit in Anspruch nehmen, was sich auf die Ladezeit der Seite auswirkt und stark von der Internetverbindung abhängt.
Das anschliessende **Rendering** der Seite, also das Anzeigen der Seite im Browserfenster, kann ebenfalls einige Zeit in Anspruch nehmen, insbesondere wenn die Seite viele Elemente und komplexe Layouts enthält.
Hierbei müssen die verschiedenen Elemente der Seite anhand des HTML-Codes und der CSS-Definitionen positioniert und formatiert werden, Bilder und Schriftarten geladen und dargestellt werden, und ggf. JavaScript-Code ausgeführt werden, um finale Anpassungen vorzunehmen.
Dieser Prozess wird als **Rendering Pipeline** bezeichnet und ist ein komplexer Vorgang, der viele Schritte umfasst und von der Leistungsfähigkeit des Browsers und des Endgeräts abhängt.


## JavaScript

Heutzutage sind Webseiten oft interaktiv und dynamisch, d.h. sie reagieren auf Benutzereingaben, laden Daten nach, und passen sich an die Umgebung (z.B. den Browser oder das Endgerät) an.
Hierfür wird **JavaScript** verwendet, eine Programmiersprache, die im Browser ausgeführt wird.

Ein zentraler Fokus der Verwendung von JavaScript in Browsern ist die **Sicherheit**, da JavaScript potenziell gefährliche Aktionen ausführen kann, wie z.B. das Lesen von Dateien auf dem Computer des Benutzers oder das Senden von Daten an einen Server.
Aus diesem Grund sind Browser so konzipiert, dass sie JavaScript in einer **Sandbox** ausführen, d.h. in einer isolierten Umgebung, die den Zugriff auf bestimmte Funktionen und Ressourcen des Endgeräts einschränkt.
So kann JavaScript z.B. nicht auf das Dateisystem des Benutzers zugreifen oder auf andere Browser-Tabs oder -Fenster zugreifen.
Dies dient dazu, die Sicherheit des Benutzers und seiner Daten zu gewährleisten und die Integrität des Browsers zu schützen.

### Was geht (nicht) mit JavaScript im Browser?

| Möglich | Verhindert |
|---------|---------|
| Änderung der angezeigten Seite (HTML, CSS, Inhalte, ...) | Kein Zugriff auf andere Browser-Tabs oder -Fenster |
| Interaktion mit dem Benutzer (Klicks, Tastatureingaben, ...) | Kein (unauthorisierter) Zugriff auf Hardware (Kamera, Microfon, ...) |
| Laden von Daten vom Webseitenserver (AJAX, Fetch, ...) | Keine direkte Kommunikation mit anderen Webseiten |
| Speichern von Daten im Browser (Cookies, LocalStorage, ...) | Kein Zugriff auf das Dateisystem des Benutzers |
| Komplexe Visualisierungen und Animationen | Keine Ausführen von Programmen auf dem Endgerät |
 


:::::::::: challenge

# Aufgabe

Die Folgende Grafik von [javacript.info](https://javascript.info) fasst die verschiedenen Möglichkeiten und Einschränkungen von JavaScript im Browser zusammen.

![Möglichkeiten und Einschränkungen von JavaScript im Browser](https://raw.githubusercontent.com/javascript-tutorial/en.javascript.info/refs/heads/master/1-js/01-getting-started/1-intro/limitations.svg){width=40% alt="Möglichkeiten und Einschränkungen von JavaScript im Browser"}

*Gleichen sie die Punkte aus der obigen Tabelle mit den Elementen der Grafik ab.*

::: solution

## Antwort

- **Möglichkeiten**: 
  - Serverkommunikation (grüner Smiley)
  - (stark beschränkter) Endgerätezugriff (roter Smiley nach unten)
- **Verhindert**:
  - Zugriff auf Hardware (roter Smiley nach unten)
  - Zugriff auf andere Webseiten/Server (roter Smiley nach oben rechts)
  - Zugriff auf andere Browser-Tabs/Fenster (roter Smiley nach rechts)
  - Zugriff auf Dateisystem (roter Smiley nach unten)
  - Ausführen von Programmen (roter Smiley nach unten)

:::

::::::::::::::::::::::


::::::::::: testimonial

Weiterführende Informationen zu JavaScript und seinen Möglichkeiten und Einschränkungen finden Sie auf der Webseite [javascript.info](https://javascript.info).

:::::::::::::::::::::::


## Cookies

Cookies sind kleine Textdateien, die vom Browser auf dem Endgerät des Benutzers gespeichert werden und **Informationen über die Interaktion des Benutzers mit der Webseite** enthalten.
Cookies werden verwendet, um den Benutzer zu identifizieren, seine Einstellungen und Präferenzen zu speichern, und das Verhalten des Benutzers auf der Webseite zu verfolgen.
Sie sind daher ein wichtiges Instrument *für die Personalisierung von Webseiten und die Verbesserung der Benutzererfahrung*. Mögliche Anwendungen von Cookies sind z.B.:

- **Authentifizierung**: Cookies werden verwendet, um den Benutzer zu identifizieren und seine Anmeldung auf der Webseite zu speichern.
- **Sitzungsverwaltung**: Cookies werden verwendet, um Informationen über die aktuelle Sitzung des Benutzers zu speichern, z.B. den Warenkorb in einem Online-Shop.
- **Präferenzen**: Cookies werden verwendet, um die Einstellungen und Präferenzen des Benutzers zu speichern, z.B. die Sprache oder das Design der Webseite.

Diese sogenannten **Erstanbieter-Cookies** (First-Party-Cookies) werden beim Wiederbesuch der Webseite vom Browser an den Server gesendet, um dem Server Informationen über den Benutzer und seine bisherige Interaktion mit der Webseite zur Verfügung zu stellen.
Hierbei werden dem Server nur die Informationen übermittelt, die im Webseiten-zugehörigen Cookie gespeichert sind. Ein Zugriff auf Cookies anderer Webseiten ist nicht möglich.

### ABER...

Cookies können auch von Drittanbietern (z.B. Werbenetzwerken) verwendet werden, um das Verhalten des Benutzers über verschiedene Webseiten hinweg zu verfolgen und personalisierte Werbung anzuzeigen.

- **Tracking**: Cookies werden verwendet, um das Verhalten des Benutzers auf der Webseite zu verfolgen und personalisierte Inhalte oder Werbung anzuzeigen.

Hierfür werden **Drittanbieter-Cookies** (Third-Party-Cookies) verwendet, die beim Laden von Teilen der Webseite (z.B. Werbung) von einem anderen Server als dem Webseiten-Server gesetzt werden.
Hierdurch können Drittanbieter Informationen über das Verhalten des Benutzers auf verschiedenen Webseiten sammeln und personalisierte Werbung webseitenübergreifend anzeigen.
Die Idee ist in folgender Grafik dargestellt.

![Tracking mit Drittanbieter-Cookies](fig/third-party-cookie.png){width=80% alt="Tracking mit Drittanbieter-Cookies"}


### Datenschutz und Sicherheit

Daher sind Cookies auch ein umstrittenes Thema im Hinblick auf **Datenschutz und Sicherheit**.
Einerseits ermöglichen sie die Personalisierung von Webseiten und die Verbesserung der Benutzererfahrung, andererseits können sie auch zur **Überwachung und Profilbildung** der Benutzer verwendet werden, was Datenschutzbedenken aufwirft.
Deshalb gibt es in der EU die **Cookie-Richtlinie**, die die Verwendung von Cookies regelt und den Benutzern die Kontrolle über die Verwendung von Cookies gibt.
Aufgrund dieser Richtlinie müssen Webseiten den Benutzern die Möglichkeit geben, der Verwendung von Cookies zuzustimmen oder sie abzulehnen.


### Löschen von Cookies

Benutzer können Cookies in ihrem Browser löschen, um ihre Spuren im Internet zu entfernen und ihre Privatsphäre zu schützen.
Die meisten Browser bieten die Möglichkeit, Cookies selektiv oder alle auf einmal zu löschen.
Dies kann in den Einstellungen des Browsers oder über spezielle Erweiterungen oder Add-Ons erfolgen.


:::::::: challenge

# Aufgabe

Im Folgenden sollen sie sich ein Bild machen, wieviele Cookies und welche Informationen darin gespeichert sind.

- Öffnen sie die Google Startseite in ihrem Browser [https://www.google.de/](https://www.google.de/)
- Öffnen sie die Cookie-Informationen ihres Browsers
  - Google Chrome: Tastenkombination `F12` und dann `Speicher` >> `Cookies`
  - Mozilla Firefox: Tastenkombination `UMSCHALT`+`F9`
  - Microsoft Edge: Tastenkombination `F12` und dann `Speicher` -> `Cookies`
- Öffnen sie die Cookie-Details von `www.google.de` an

*Bis wann sind die Cookies gültig?*

::: solution

# Antwort

Die Gültigkeit der Cookies ist unterschiedlich und hängt von den Einstellungen des Servers und des Browsers ab.
Zum Zeitpunkt der Erstellung dieses Dokuments (Dez 2024) haben die Cookies auf der Google-Startseite eine Gültigkeit von einem halben Jahr.

Dies zeigt, dass **Cookies eine lange Lebensdauer haben** können, da mit ihrer Hilfe i.d.R. über einen längeren Zeitraum Informationen über den Webseitennutzer gespeichert werden.

:::

::::::::::::::::::


## Best Practices für Browsernutzung

- **Aktualisieren Sie Ihren Browser regelmäßig**: Halten Sie Ihren Browser auf dem neuesten Stand, um die neuesten Sicherheitsupdates und Funktionen zu erhalten.
- **Verwenden Sie sichere Passwörter**: Verwenden Sie sichere Passwörter, um Ihr Konto und Ihre Daten zu schützen.
- **Verwenden Sie HTTPS**: Verwenden Sie HTTPS, um die Sicherheit Ihrer Verbindung zu gewährleisten und die Übertragung sensibler Daten zu schützen.
- **Verwenden Sie sichere Verbindungen**: Vermeiden Sie unsichere WLAN-Verbindungen und verwenden Sie VPNs, um Ihre Verbindung zu schützen.
- **Verwenden Sie sichere Erweiterungen**: Verwenden Sie nur vertrauenswürdige Erweiterungen und Add-Ons, um die Sicherheit Ihres Browsers zu gewährleisten.
- **Verwenden Sie sichere Einstellungen**: Überprüfen Sie die Sicherheitseinstellungen Ihres Browsers und passen Sie sie an Ihre Bedürfnisse an.
- **Verwenden Sie sichere Cookies**: Verwenden Sie nur sichere Cookies und löschen Sie regelmäßig alte Cookies, um Ihre Privatsphäre zu schützen.
- **Schließen Sie nicht benötigte Tabs**: Schließen Sie nicht benötigte Tabs und Fenster, um die Leistung Ihres Browsers zu verbessern und Speicherplatz freizugeben.
- **Löschung von Verlaufsdaten**: Löschen Sie regelmäßig Ihren Browserverlauf, um Ihre Privatsphäre zu schützen und Speicherplatz freizugeben.
- **Ausloggen aus Konten**: Melden Sie sich immer aus Ihren Konten ab, wenn Sie den Browser verlassen, um Ihre Daten zu schützen und personalisiertes Profiling zu reduzieren.

:::::::::: testimonial

**AUCH AUF DEM HANDY !!!**

:::::::::::::::::::::::



## Zusammenfassung

:::::: keypoints

- 

::::::::::::::::::::

:::::::::: challenge

# Einordnung im Datenlebenszyklus

![*In welchen Phasen im Datenlebenszyklus sehen sie obige Punkte als besonders wichtig an?*](https://uni-tuebingen.de/fileadmin/_processed_/6/b/csm_FDM_Lebenszyklus_d1353825c4.png){width=40% alt="Datenlebenszyklus"}


::: solution

## Antwort

TODO


:::

::::::::::::::::::::



:::::::::::::::: instructor


:::::::::::::::::::::::::::
