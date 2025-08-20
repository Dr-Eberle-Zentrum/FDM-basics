---
title: 'Aufgabe "Strukturcheck von Dateien"'
---

:::::::::::::::: instructor
## Aufgabe zu "Dateiformate"
:::::::::::::::::::::::::::


## Datenimportvorbereitung

Sie haben zur Verarbeitung die folgende Datei erhalten.

- [turkish.tsv](data/turkish.tsv)

Bevor sie diese weiterverarbeiten können, müssen sie erst prüfen, ob das Dateiformat korrekt ist, und ob sie irgendwelche Dinge für den Import beachten müssen.

### Aufgabe 1 - Dateninspektion

Die Datei hat die Endung `.tsv`, was auf text-basierte, tabulator-getrennte tabellarische Daten schließen läßt.
Das einfachste Mittel zur Überprüfung, ob dies tatsächlich stimmt, besteht im Öffnen der Datei in einem Texteditor.

1. Speichern sie die Datei `turkish.tsv` in ihrem Abgabeordner
2. Öffnen sie die Datei in einem Texteditor ihrer Wahl (z.B. Notepad++)
3. Prüfen sie die folgenden Punkte:
   - Stimmt die Dateistruktur, d.h. Dateiendung und erwarteter Aufbau der Daten passen zusammen?
   - Welche Textkodierung wird verwendet? Überlegen sie, wie sie prüfen könnten, ob die Textanzeige stimmt... (und halten sie auch ihre Überlegungen textuell fest)
   - Welche Zahlenkodierung wird verwendet?
   
### Aufgabe 2 - Dokumentation

Um ihre Entdeckungen zu einem späteren Zeitpunkt festzuhalten, möchten/sollen sie diese in Form einer Dokumentationsdatei festhalten.

- Verwenden sie dazu ein neues **Markdown**-Dokument in ihrem Abgabeordner
  - dieses können sie z.B. mit dem [dillinger.io Editor](https://dillinger.io/) online erstellen und testen
- **Dateiname:** `turkish.md` (im Abgabeordner)
- Verwenden sie in ihrem Markdowndokument
  - Überschriften
  - Links
  - Listen
  - ggf. Fett- oder Kursivschrift
- Dokumentieren sie
  - Name der Datei um die es geht
  - Quelle (GitHub Link) und Zugriffszeitpunkt
  - Eigenschaften (siehe Aufgabe 1)
  - Aufbau (Welche Spalten gibt es und welcher Datentyp ist dort jeweils erwartet)

### Aufgabe 3 - Textbasierte Zahlenkodierung

Bei der vorliegenden Datei handelt es sich um ein textbasiertes Dateiformat.
Das heisst, Zahlen sind nicht in ihrer computerinternen binären Darstellung gespeichert, sondern als Text kodiert.

Überlegen sie, welche Probleme oder Konsequenzen hieraus entstehen und welche Vorteile dies haben könnte.

Welche Überlegungen sollte man immer anstellen, bevor man Zahlendaten in textbasierten Dateiformaten abspeichert?

Ergänzen sie ihre Überlegungen in einem gesonderten Abschnitt in der Markdown-Datei aus Aufgabe 2.

Laden sie die Markdown-Datei in ihrem Abgabeordner hoch.



:::: instructor

## Musterlösung

- [turkish.md](data/turkish.md.txt)

::::::::::



