---
title: 'Aufgabe zu "Digitale Daten"'
---


## Datenimport in MS Excel

In dieser Aufgabe soll der Import von Daten in Microsoft Excel geübt werden, wenn die Zahlendaten in der falschen Trennzeichennotation vorliegen.
Wir haben hierfür eine Datei mit einem Mietpreisindex für Deutschland vom Bundesamt für Statistik in zwei Varianten vorbereitet.

- [mietindex.destatis.de.txt](https://raw.githubusercontent.com/Dr-Eberle-Zentrum/FDM-basics/main/instructors/data/mietindex.destatis.de.txt) - mit deutschen Dezimaltrennzeichen 
  - für Import in englischsprachigem MS Excel
- [mietindex.destatis.us.txt](https://raw.githubusercontent.com/Dr-Eberle-Zentrum/FDM-basics/main/instructors/data/mietindex.destatis.us.txt) - mit amerikanischem Dezimaltrennzeichen
  - für Import in deutschsprachigem MS Excel (bzw. einer westeuropäischen Sprache)
  
Die Tabellen enthalten die Nettokaltmieten-Indexwerte (Referenzjahr 2020) für Baden-Württemberg aus der Tabelle 61111-0020 der GENESIS-Online Datenbank des Statistischen Bundesamtes.

Für die folgende Aufgabe verwenden sie bitte die Datei, die *NICHT* der in ihrem Microsoft Excel eingestellten Sprache (bzw. dem entsprechenden Zahlentrennzeichensystem) entspricht, um die Probleme zu simulieren, die durch unterschiedliche Dezimaltrennzeichen entstehen können.

### Aufgabe 1 - Datenimport

- Öffnen sie eine neue Arbeitsmappe in **Microsoft Excel** (entweder lokal oder online in MS365)
- Wechseln sie auf das Register "Daten"
- Links oben finden sie die Schaltfläche "Daten abrufen" bzw. "Aus Text/CSV"
- Verwenden sie in der Dateiauswahl einen der beiden Links von oben für die für sie passende Datei
  - d.h. verwenden sie die Datei mit dem *falschen* Dezimaltrennzeichen
  - importieren sie die Daten direkt aus dem Internet OHNE die Datei vorher lokal zu speichern
  - Stimmen sie im Webimport-Assistenten dem Import von github zu
- Im Vorschaudialog sollte das meiste passen, ABER:
  - *WICHTIG*: setzen sie "Datentyperkennung" auf "Datentypen nicht ermitteln", um die Fehlinterpretation der Zahlen zu verhindern
  - Bestätigen sie mit "Laden"
- Nun sollten sie ein neues Arbeitsblatt "mietindex.destatis.de" oder "mietindex.destatis.us" haben
  - korrigieren sie die Spaltennamen zu "Jahr" und "Mietpreisindex"
  - korrigieren sie die Zahlenformate der Mietpreisindex-Spalte
    - Spalte markieren
    - Reiter "Daten" -> "Text in Spalten"
      - "Getrennt" passt (irrelevant, weil nur eine Spalte)
      - Trennzeichen "Tabstopp" ist ok und egal, solange nicht ihr Dezimaltrennzeichen
      - Datenformat "Standard" und *WICHTIG* auf "Erweitert.." klicken
        - Dezimaltrennzeichen auf "." bzw. "," setzen (je nach Datei) und 1000er-Trennzeichen auf " " setzen
      - "Fertigstellen"
- Benennen sie das Arbeitsblatt in "Mietpreisindex.destatis" um
- Speichern sie die Arbeitsmappe in ihrem Abgabeordner ab
  - **Dateiname:** `mietpreisindex.destatis.xlsx`

Nun sollten die Daten korrekt importiert sein und die Mietpreisindex-Spalte als Zahlen erkannt sein.

### Aufgabe 2 - Dokumentation mit Markdown

- Dokumentieren sie Herkunft und Import der Daten in einem kurzen Text
- Verwenden sie dazu ein neues **Markdown**-Dokument in ihrem Abgabeordner
  - dieses können sie z.B. mit dem [dillinger.io Editor](https://dillinger.io/) online erstellen und testen
  - **Dateiname:** `mietpreisindex.destatis.README.md`
  - Verwenden sie in ihrem Markdowndokument
    - Überschriften
    - Links
    - Listen
    - ggf. Fett- oder Kursivschrift
- Verwenden sie die folgenden Abschnitte:
  - **Herkunft der Daten** (Datenzitation)
    - Beschreibung der Datenquelle
    - Link zur Datenquelle
    - Linzenz? Überlegen sie, ob und in welchem Rahmen sie die Daten verwenden dürfen. Begründen sie ihre Aussagen.
  - **Import in MS Excel**
    - Beschreibung der Importschritte (in eigenen Stichpunkten)
    - Verwendete Datei
    - Verwendete Einstellungen
  - **Speicherung**
    - Dateiname der gespeicherten Arbeitsmappe
    - Name des Arbeitsblattes

### Aufgabe 3 - Dokumentation überarbeiten und vereinheitlichen

In der letzten Woche haben sie bereites eine Dokumentationsdatei namens `strompreise.destatis.README.[???]` erstellt.
Um die Dokumentation in ihrem Projekt einheitlich zu halten, sollen sie nun eine überarbeitete Version dieser Datei erstellen.
Konkret:

- Erstellen sie eine Markdown-Datei mit dem Namen `strompreise.destatis.README.md`
- Kopieren sie den Inhalt der alten Datei hinein (*Die alte Datei soll im Ablageordner verbleiben!*)
- Überarbeiten sie den Inhalt so, dass er zu den neuen Anforderungen aus Aufgabe 2 passt (*fügen sie ggf. neue Abschnitte hinzu, die sie für ihre Dokumentation benötigen.*)
- Speichern sie die Datei in ihrem Abgabeordner ab

