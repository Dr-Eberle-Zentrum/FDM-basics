---
title: 'Datenimport'
teaching: 10
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- Häufige Probleme?
- Pfade?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Was geht oft schief beim Datenimport?
- Wie kann eine gute Dateiorganisation helfen?

::::::::::::::::::::::::::::::::::::::::::::::::

Der Import von Daten ist oft der erste Schritt in einem Datenprojekt.
Hierbei stammen die Daten häufig aus verschiedenen Quellen und liegen in unterschiedlichen Formaten vor.

Mögliche Quellen sind hierbei:

- Rohdaten aus Messgeräten
- Exportierte Daten aus Datenbanken
- Daten von Webservices (APIs)
- Daten von Webseiten (Webscraping)
- Daten von Kolleg:innen oder aus anderen (alten) Projekten
- Daten aus anderen Analyseschritten

## Was kann schiefgehen?

Beim Import von Daten treten häufig Probleme auf, die den weiteren Arbeitsprozess erschweren können.
Dies ist **insbesondere beim Import fremder oder alter Daten** der Fall, wenn die ursprünglichen Rahmenbedingungen oder Programme nicht mehr bekannt sind.

Im Folgenden gehen wir davon aus, dass sie es mit *textbasierten Dateiformaten* zu tun haben (z.B. CSV, TSV, JSON, XML, etc.), da diese am häufigsten zum Teilen und Archivieren von Daten verwendet werden.

Häufige Probleme beim Import solcher Dateien haben ihren Grund in der **textuellen Repräsentation von Daten**, die teilweise im [Kapitel "Digitale Daten"](Digitale-Daten.md) besprochen wurden:

- **Textkodierung**: Sonderzeichen (z.B. Umlaute) werden nicht korrekt dargestellt, da eine falsche Textkodierung verwendet wird (z.B. UTF-8 statt ISO-8859-1)
- **Zeilenumbrüche**: Daten werden nicht korrekt in Zeilen aufgeteilt (z.B. `\r\n` statt `\n`)
- **Dezimaltrennzeichen**: Zahlen werden nicht korrekt interpretiert (z.B. `1,23` statt `1.23`)
- **Feldtrennzeichen**: Daten werden nicht korrekt in Spalten aufgeteilt (z.B. `;` statt `,`)
- **Datumsformat**: Datumskodierung nicht korrekt erkannt/interpretiert (z.B. `DD.MM.YYYY` statt `YYYY-MM-DD`), gerade bei unterschiedlichen Ländern
- **Fehlende Werte**: Fehlende Daten werden nicht korrekt erkannt (z.B. `NA` statt `""`)
- **Datentypen**: Daten werden nicht korrekt als numerisch, kategorisch oder logisch erkannt (z.B. `1` statt `TRUE`)
- **Spaltennamen**: Spaltennamen sind nicht aussagekräftig oder enthalten Sonderzeichen (z.B. Leerzeichen, Umlaute)


Dadurch sollte man immer vor dem Datenimport einen Blick in die Rohdaten werfen (z.B. mit einem Texteditor), um solche Probleme frühzeitig zu erkennen und zu beheben.

Auch empfiehlt es sich, gerade bei fremden Daten, das Ergebnis des Datenimports sehr genau zu überprüfen, damit keine Fehler in die weitere Analyse eingeschleust werden.

### Hilfreiche Fragen

- *Aus welchem Land stammt die Datei?*
  - Hinweis auf Textkodierung, Dezimaltrennzeichen, Datumsformat, da diese häufig vom Betriebssystem und der eingestellten Sprache abhängen
- *Wann wurde die Datei erstellt?*
  - Hinweis auf Textkodierung, da ältere Dateien häufig in anderen Kodierungen vorliegen
- *Gibt es eine Dokumentation der Datei?*
  - Hinweis auf Datentypen, Spaltennamen, Fehlende Werte, da diese häufig in einer begleitenden Dokumentation beschrieben sind
- *Wie wurden fehlende Werte kodiert?*
  - Wichtig, da diese häufig unterschiedlich kodiert werden (z.B. `NA`, `NULL`, `-9999`, `-`, `unbekannt`, etc.), gerade bei manuell erhobenen Daten

Auch wenn ein Dokumentation vorliegt oder der Datenimport scheinbar direkt funktioniert, empfiehlt es sich, die **Datei immer mit einem Texteditor oder dergleichen zu untersuchen**, um alle Fragen zu klären.


## Dateiorganisation und Pfade

Ein weiteres häufiges Problem beim Datenimport betrifft die Wiederverwendbarkeit von Skripten.
Häufig werden Skripte so geschrieben, dass der Datenimport die genaue Position der Datei auf dem eigenen Rechner (z.B. `C:/Users/Name/Documents/Projekt/data/datei.csv`) referenziert.
Derartige Pfadangaben werden als **absolute Pfade** bezeichnet.
Während dies eine intuitive und einfache Lösung ist, kann die Wiederverwendbarkeit des Skripts stark eingeschränkt sein.

Mögliche Szenarien die dazu führen können, dass ein Skript mit absoluten Pfaden nicht mehr funktioniert, sind z.B.:

- Das Skript wird weitergegeben und soll auf einem anderen Rechner ausgeführt werden.
- Die zu importierende Zieldatei und/oder das Skript werden in einen anderen Ordner verschoben.
- Das Skript soll auf ähnliche Zieldateien in anderen Ordnern angewandt werden.

In alle diesen Fällen muss der absolute Pfad im Skript angepasst werden, was zu Fehlern führen kann und den Aufwand erhöht.


Daher empfiehlt es sich, stattdessen **relative Pfade** zu verwenden (z.B. `data/datei.csv`).
Diese beziehen sich i.d.R. auf den **Arbeitsordner** (working directory) der aktuellen Sitzung der Skriptumgebung (z.B. RStudio, Jupyter, etc.).
Konkret bedeutet dies, das beim Ausführen eines Skriptes die Skriptumgebung einen Ordner als Arbeitsordner festlegt.
Dies ist häufig der Ordner, aus dem heraus das Skript ausgeführt wird.
Der Arbeitsordner kann aber auch explizit gesetzt werden.

Alle relativen Pfadangaben innerhalb des Skriptes beziehen sich dann auf diesen Arbeitsordner.

### Beispiel

Nehmen wir an, wir hätten folgende Ordnerstruktur die Messdaten aus einer Experimentreihe in Datumsordnern (mit gleichem Dateinamen) ablegt und die Analyseskripte in einem eigenen Skripteordner gesammelt werden:

```
projekt/
├── daten
│   └── 20250901/
│       └── messdaten.csv
│   └── 20250902/
│       └── messdaten.csv
└── skripte/
    └── analyse.py
```

Nehmen wir weiter an, dass das Skript `analyse.py` die Messdaten mit einem relativen Pfad ohne Ordnerangabe, z.B. mit `pandas.read_csv("messdaten.csv")`, importieren würde.

Wenn wir nun in der Skriptumgebung den Arbeitsordner auf `projekt/daten/20250901/` setzen und das Skript ausführen, würde die Datei `projekt/daten/20250901/messdaten.csv` importiert werden.
Würden wir hingegen den Arbeitsordner auf `projekt/daten/20250902/` setzen, würde die dortige Datei `messdaten.csv` importiert werden.
Dadurch könnten wir das gleiche Skript für die Analyse der Daten aus beiden Tagen verwenden, ohne den Pfad im Skript anpassen zu müssen.

Zudem könnte das Skript auch problemlos auf einem anderen Rechner ausgeführt werden, solange die Ordnerstruktur beibehalten wird.

Ausserdem ermöglicht diese Ordnerstruktur eine Automatisierung der Analysen, z.B. mit einem Makefile oder einem Bash-Skript, um die Analysen für alle Datumsordner durchzuführen.
Dies ist beispielhaft in folgendem Bash-Skript dargestellt:

```bash
# Wechsle ins Projektverzeichnis (ggf. via absoluten Pfad)
cd projekt
# Schleife über alle Datumsordner (relative Pfade bzgl. Projektordner)
for dir in daten/*/; do
  # Ausgabe des aktuellen Datenordners
  echo "Analysiere Daten in $dir"
  # In Datenordner wechseln (via relativen Pfad)
  # und Skript ausführen (Arbeitsverzeichnis = Aufrufordner = Datenordner)
  # (relativer Pfad im Skript funktioniert, da Arbeitsverzeichnis auf 
  #  aktuellen Datenordner gesetzt)
  (cd "$dir" && python ../../skripte/analyse.py)
done
```

Hierbei ist zu bemerken, dass auch das Bash-Skript zur Automatisierung wiederum mit relativen Pfaden arbeitet, u.a. um das Skript `analyse.py` auszuführen.
Das `..` verweist hierbei auf den übergeordneten Ordner, sodass der Pfad `../../skripte/analyse.py` vom aktuellen Datenordner aus auf das Skript im `skripte` Ordner zeigt ("Zwei Ordner hoch und dann ins `skripte` Verzeichnis", siehe Verzeichnisstruktur oben).

Dadurch ist das gesamte Projekt sehr flexibel und wiederverwendbar gestaltet.
Es kann auf beliebig viele Daten (z.B. weitere Datumsordner) angewandt werden, ohne dass Pfade im Skript oder im Automatisierungsskript angepasst werden müssen.
Ausserdem kann das gesamte Projekt problemlos auf einen anderen Rechner verschoben werden, solange die projektinterne Ordnerstruktur beibehalten wird.

Die obigen Bash-Kommandos könnten hierfür als eigenes Skript (z.B. `run_analysen.sh`) im `skripte` Ordner gespeichert und ausgeführt werden.

### `\` vs. `/`

In Windows werden Pfade häufig mit dem Backslash `\` angegeben (z.B. `C:\Users\Name\Documents\Projekt\data\datei.csv`), während in Unix-basierten Systemen (Linux, macOS) der Forwardslash `/` verwendet wird (z.B. `/home/name/dokumente/projekt/data/datei.csv`).
Dies kann zu Problemen führen, wenn Skripte auf verschiedenen Betriebssystemen ausgeführt werden sollen.

Daher empfiehlt es sich, in **Skripten immer den Forwardslash `/`** zu verwenden, da dieser in den meisten Programmiersprachen und Skriptumgebungen (z.B. Python, R, Bash) auch unter Windows unterstützt wird.



### Best Practices

- Organisieren sie ihre Projektdaten in einer **logischen Ordnerstruktur**, um die Übersicht zu behalten und den Grundstein für relative Pfade zu legen.
- Legen sie **Rohdaten, Zwischenergebnisse und Endergebnisse** in separaten Ordnern ab, um Verwechslungen zu vermeiden.
- Verwenden sie in Skripten und Dokumentationen **relative Pfade** anstelle von absoluten Pfaden, um die Wiederverwendbarkeit zu erhöhen.
- Automatisieren sie wiederkehrende Aufgaben (z.B. Datenimport, Datenverarbeitung) mit Skripten, um Fehler zu vermeiden und Zeit zu sparen.  
- **Vermeiden sie Kopien** von Skripten und Daten
  - Nutzen sie stattdessen Verlinkungen (z.B. symbolische Links) oder Automatisierungsskripte, um Redundanzen zu vermeiden.
- Verwenden sie Versionskontrolle (z.B. Git), um Änderungen an Skripten und Daten nachvollziehbar zu machen.



## Zusammenfassung

:::::: keypoints

- Text-basierte Datenrepräsentation kann zu Problemen beim Import führen
  - Häufige Probleme: Zeichenkodierung, Zeilenumbrüche, Trennzeichen
- Vor dem Import immer Rohdaten inspizieren (Texteditor!)
- Relative Pfade in Skripten erhöhen Wiederverwendbarkeit
- Logische Ordnerstruktur erleichtert Datenorganisation und Automatisierung

::::::::::::::::


:::::::::: challenge

# Einordnung im Datenlebenszyklus

![*In welchen Phasen im Datenlebenszyklus sehen sie obige Punkte als besonders wichtig an?*](https://uni-tuebingen.de/fileadmin/_processed_/6/b/csm_FDM_Lebenszyklus_d1353825c4.png){width=40% alt="Datenlebenszyklus"}

::: solution

## Antwort

Das Wissen um die **digitale Repräsentation von Informationen** ist immer dann zentral, wenn Daten importiert oder exportiert werden, um sicherzustellen, dass die Daten korrekt übertragen und gespeichert werden.

- **Verarbeitung**: Import von Rohdaten
- **Analyse**: Import von Zwischenergebnissen
- **Nachnutzung**: Import von (alten) Daten

:::

::::::::::::::::::::



:::::::::::::::: instructor

## Aufgaben

### Sitzungsaufgaben

- 


### Sitzungsfragen

- An was muss ich beim Datenimport denken?
- Warum sind relative Pfade besser?


:::::::::::::::::::::::::::
