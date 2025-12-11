---
title: 'Aufgabe zu "Manuelle Datenbereinigung"'
---

## Manuelle Datenbereinigung

Im Folgendenen soll eine manuelle Datenbereinigung durchgeführt und dokumentiert werden.
Manuelle Bearbeitung bietet sich an, wenn die Daten in einem Format vorliegen, das nicht automatisiert bereinigt werden kann, oder wenn die Datenqualität so schlecht ist, dass eine automatisierte Bereinigung nicht sinnvoll ist.
Ausserdem ist man manchmal bei kleinen Datensätzen manuell schneller als mit einem automatisierten Prozess.

**ABER**: *Manuelle Datenbereinigung ist ...*

- ... fehleranfällig und sollte nur in Ausnahmefällen durchgeführt werden.
- ... nicht reproduzierbar und sollte deshalb detailliert dokumentiert werden.
- ... zeitaufwändig und nicht skalierbar und sollte nur bei kleinen Datensätzen durchgeführt werden.


### Ziel

Konkret wollen wir die Daten für die Mietpreisentwicklung in Baden-Württemberg extrahieren vom Statistischen Landesamt Baden-Württemberg extrahieren und bereinigen.
Die Daten wurden 2024 vom destatis Server heruntergeladen, liegen jedoch in einem Format vor, das nicht direkt weiterverwendet werden kann.

- [`mietpreisindex-bw.komplett.csv`](data/mietpreisindex-bw.komplett.csv) (Quelle: [Statistisches Landesamt Baden-Württemberg](https://www.statistik-bw.de/GesamtwBranchen/KonjunktPreise/VPI-LR.jsp?i=h) - Zugriff 13.09.2024; Aktuelle Daten via [Tabelle 61111_0003 in Genesis-Online](https://daten.statistik-bw.de/genesisonline/online?operation=table&code=61111_0003))

Wir sind allerdings nur an Teilen der Daten interessiert, konkret:

- Verbraucherpreisindex für Baden-Württemberg (Spalte 2)
- nur die Jahresdurchschnitswerte (Zeilen mit "JD XXXX")
- nur die Werte für die Jahre 2000 bis 2023


### Aufgabe 1 - Reguläre Ausdrücke

- Speichern sie die oben verlinkte Datei `mietpreisindex-bw.komplett.csv` in ihrem Abgabeordner

Zum Erstellen und Testen von Regulären Ausdrücken empfehlen wir einen der folgenden Schritte:

:::::: tab

### Texteditor oder IDE

- Öffnen sie die Datei in einem TEXTEDITOR (nicht Excel oder ähnliches) oder einer Programmierumgebung (IDE) welche in der Suche *REGULÄRE AUSDRÜCKE* unterstützt.
- Falls sie Notepad++ verwenden, können sie in der Suchmaske auf den Reiter "Hervorheben" wechseln, um Treffer leichter zu sehen.

### Online-Tool

- Öffnen sie ein Online-Tool für Reguläre Ausdrücke, z.B. [regex101.com](https://regex101.com/)
  - Wählen sie links oben als Flavor "Python" aus
- Öffnen sie die Datei in einem Texteditor und kopieren sie den Inhalt in den unteren Bereich "TEST STRING" des Online-Tools

::::::::

Ersinnen sie REGULÄRE AUSDRÜCKE für die folgenden Aufgaben und dokumentieren sie diese in ihrem Abgabeordner.

- Dateiname: `mietpreisindex-bw.komplett.regex.md`

1. Ausdruck selektiert ausschliesslich die Überschrift `Jahr/Monat;Verbraucherpreisindex`
2. Ausdruck selektiert alle Datenzeilen für Einzelmonate
    - erster Treffer sollte `Januar;117,4;109,3;+3,0;108,9;+2,7;109,8;+2,8` sein
    - letzter Treffer is `Dezember;27,3;23,8;–;-;–;-;–`
    - Versuchen sie den Ausdruck möglichst klein zu halten. 
    - *Finden sie mindestens 2 unterschiedliche Ausdrücke für diese Aufgabe*
3. Ausdruck selektiert AUSSCHLIESSLICH die gewünschten Daten (siehe Ziel)
    - sollten 24 Treffer/Zeilen sein
    - der erste Match sollte `JD 2023;116,4` sein
4. Erweiterung von 3., sodass nur die Jahreszahl und der Wert selektiert werden
    - der erste Match sollte `2023;116,4` sein
    - Tipp: lookaround assertions verwenden
5. Kombination aus 1. und 4. um die gewünschten Daten inklusive Überschrift zu selektieren

Nun wollen wir den Regulären Ausdruck aus 5. verwenden, um die Daten zu extrahieren.
In der Linux/Unix Kommandozeile gibt es hierfür das Tool `grep`, welches reguläre Ausdrücke unterstützt.
Im Folgenden wollen wir eine Online-Version von `grep` verwenden.

6. Öffnen sie die Webseite [Grep Online](https://www.online-utility.org/text/grep.jsp)
   - Kopieren sie ihren Regulären Ausdruck aus 5. in das Feld "Input Regular Expression"
   - Kopieren sie den Inhalt der Datei `mietpreisindex-bw.komplett.csv` in das Feld "Enter Text"
   - Klicken "Only Matching"
   - Starten sie die Extraktion via "Process text"
7. Kopieren sie das Ergebnis in ihre Markdowndatei
   - Verwenden sie einen Codeblock im Markdown, um das Ergebnis einzufügen


### Aufgabe 2 - Copy-Paste-Edit

- Speichern sie die Datei [`mietpreisindex-bw.jahresdurchschnitt.csv`](data/mietpreisindex-bw.jahresdurchschnitt.csv) in ihrem Abgabeordner
  - Diese Datei enthält die Jahresdurchschnittszeilen aus der kompletten Datei von oben
  
Nun wollen wir die Daten manuell bereinigen, um nur die zwei Zielspalten zu behalten und die Jahreszahlen zu extrahieren.
Ausserdem soll die Datei am Ende im amerikanischen CSV Format (Punkt als Dezimaltrenner, Komma als Spaltentrenner) vorliegen.
  
- Öffnen sie die Datei in einem TEXTEDITOR (nicht Excel oder ähnliches)
- Bereinigen sie die Daten manuell (ohne reguläre Ausdrücke etc.)
  - Verwenden sie [vertikale Markierung](https://www.pctipp.ch/praxis/zubehoer/kleines-maus-trickli-fuer-word-writer-2012970.html) ([MacOs](https://www.macwelt.de/article/934976/textedit-beliebig-markieren.html)), um spaltenweise zu markieren und zu löschen
  - Verwenden sie "Suchen und Ersetzen", um die Spaltentrenner und Dezimaltrennzeichen zu korrigieren
  - Reduzieren sie die erste Spalte auf die Jahreszahlen (vertikale Markierung oder Suchen-und-Ersetzen)
  - Fügen sie eine Überschriftszeile `Jahr,Verbraucherpreisindex` ein
  - Reduzieren sie den Datensatz auf die Jahre 2000-2023
- Speichern sie die Datei in ihrem Ablageordner

Und damit das auch nachvollziehbar bleibt:

- Dokumentieren sie die Herkunft und den Inhalt der Datei in einer Markdown-Datei
  - Dateiname: `mietpreisindex-bw.jahresdurchschnitt.README.md`
  - Denken sie an eine komplette Onlinequellen- und Editierbeschreibung!
