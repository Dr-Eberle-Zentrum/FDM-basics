
---
title: 'Aufgabe "OpenRefine in Action"'
---

:::::::::::::::: instructor
## Aufgabe zu "Datenverarbeitung"
:::::::::::::::::::::::::::

Diese Aufgabe soll ihnen einen ersten Einstieg in OpenRefine liefern.
Hierbei wollen wir direkt an einem Beispiel arbeiten, um die Reproduzierbarkeit von OpenRefine-Workflows zu verdeutlichen.

Konkret soll hierbei eine Lösung für die Verarbeitung der Iris-Daten aus dem Selbstlernkapitel "Datenverarbeitung" betrachtet werden.

Dazu müssen sie allerdings OpenRefine lokal auf ihrem Rechner installiert haben (Anleitung auf der [OpenRefine Webseite](https://openrefine.org/download.html)).

Im Anschluß können sie OpenRefine wie folgt testen:


## Aufgabe 1: Projektimport

Als ersten wollen wir erleben, wie eine komplette Datenverarbeitungspipeline inklusive Daten mit OpenRefine nachvollziehbar abgelegt werden kann.
Hierzu ist es möglich, das komplette OpenRefine Projekt (also Daten und Verarbeitungsschritte) als komprimiertes Dateiarchiv als `.tar.gz` Datei abzulegen.
Dies haben wir für den Iris-Datensatz bereits vorbereitet und entsprechende Dateien zum Download bereitgestellt.

Ihre Aufgabe ist es nun, dieses komplette Projekt in OpenRefine zu importieren, d.h. Daten und Arbeitsschritte in einem, und zu schauen welche Arbeitsschritte vorgenommen wurden.

- Speichern sie die [Iris OpenRefine Projektdatei](data/openrefine_example.projekt.tar.gz) in ihrem Ablageordner lokal auf ihrem Rechner
- Öffnen sie OpenRefine
- Klicken sie auf "Öffnen..." (oben rechts)
- Wählen sie links "Projekt importieren" und wählen sie die heruntergeladene Datei aus und bestätigen sie den Import
- Nun sollte das Ergebnis wie oben gezeigt erscheinen
- Wählen sie links oben "Rückgängig/Wiederholen", um die einzelnen Schritte des Workflows zu sehen
- Klicken sie auf verschiedene Schritte, um die Effekte der einzelnen Datentransformationen zu sehen.


   
### Aufgabe 2: Workflowimport

Nun wollen wir lediglich den Workflow (also die Arbeitsschritte) importieren, was nützlich ist, um einenen Workflow auf andere (aber gleich strukturierte) Datensätze anzuwenden.

- Erzeugen sie ein neues Projekt in OpenRefine via "Öffnen..."
- Verwenden sie "Webaddressen (URLs)" und geben sie die URL des Iris-Datensatzes ein: `https://zenodo.org/record/1319069/files/iris.csv`
- Prüfen sie die Datenvorschau und die verschiedenen Importoptionen und klicken sie am Ende auf "Projekt erstellen" (oben rechts)
  - **WICHTIG: Verwenden sie `IRIS-Beispiel` als Projektnamen**
- Nun sollten die rohen Daten des Iris-Datensatzes in OpenRefine erscheinen
- Speichern sie den [Iris OpenRefine Workflow](data/openrefine_example.workflow.json) in ihrem Ablageordner lokal auf ihrem Rechner
- Wechseln sie in OpenRefine links oben zu "Rückgängig/Wiederholen"
  - Klicken sie auf "Anwenden", um den heruntergeladenen Workflow zu importieren und auszuführen
- Nun sollte das Ergebnis wie oben gezeigt erscheinen

Wer möchte, kann auf die gleiche Art auch einen [Python-basierten Workflow](data/openrefine_example.workflow.python.json) austesten.


### Aufgabe 3: Workflowerweiterung

Nun wollen wir den Workflow erweitern, um die Daten noch weiter zu bereinigen und zu transformieren.

Aktuell sind die Zahlen noch mit vielen Nachkommastellen angegeben, was für die meisten Anwendungsfälle nicht notwendig ist.

Daher sollen wir die Zahlen auf zwei Nachkommastellen runden und das Ergebnis als CVS exportieren.

Konkret:

- Öffnen sie ihr Projekt `IRIS-Beispiel` in OpenRefine
- Erweitern sie die Datenverarbeitung um die Rundung der vier numerischen Spalten auf zwei Nachkommastellen
  - Verwenden sie hierzu die GREL Funktionen
    - Nutzen sie `toString()` für eine Spalte
      - Stellen sie sicher, dass der Ergebnistext "." (Punkt) als Dezimaltrenner verwendet
    - Nutzen sie `round()` für eine andere Spalte
      - Beachten sie: round rundet auf ganze Zahlen, sie brauchen also einen mathematischen Trick!
    - Sehen sie einen Unterschied in den Ergebnissen?
  - Verwenden sie den "Verlauf" in der GREL Eingabemaske, um die gleiche Transformation bei weiteren Spalten anzuwenden
- Sie sollten nun eine Tabelle mit 5 Spalten und 3 Zeilen mit gerundeten Werten haben
- Exportieren sie die **Daten als CSV** (Komma-getrennt) via "Exportieren" (oben rechts)
  - Dateiname: `openrefine.iris.mean.csv`
  - Prüfen sie den Inhalt (z.B. via Texteditor)
- Exportieren sie ihre *Workflow-Erweiterung* als JSON:
  - "Rückgängig/Wiederholen" -> "Exportieren"
  - Wählen sie **nur ihre neuen Schritte** aus (also die Rundungen)
  - Dateiname: `openrefine.iris.mean.rounding.json`

Laden sie **beide Dateien in ihrem Abgabeordner** hoch.




:::::::::::::::: instructor

## Musterlösung

- [`openrefine.iris.mean.csv`](data/openrefine.iris.mean.csv)
- [`openrefine.iris.mean.rounding.json`](data/openrefine.iris.mean.rounding.json)

:::::::::::::::::::::::::::



