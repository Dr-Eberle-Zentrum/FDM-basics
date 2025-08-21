---
title: 'Aufgabe "Metadaten mit KI"'
---

:::::::::::::::: instructor
## Aufgabe zu "Metadaten"
:::::::::::::::::::::::::::

Das Erstellen von Metadaten ist eine wichtige Aufgabe, um die Auffindbarkeit und Nachnutzbarkeit von Daten und Software zu gewährleisten.
Allerdings kann das Erstellen und Pflegen von Metadaten auch zeitaufwändig sein.
Um diesen Prozess zu vereinfachen, können KI-gestützte Tools eingesetzt werden, die bei der Erstellung und Überarbeitung von Metadaten helfen.
In dieser Aufgabe werden wir KI-gestützte Tools verwenden, um relevante Metadatenschlagworte aus bestehenden Einträgen eines Repositoriums zu extrahieren und diese mit Informationen einer neuen Ressource zu füllen.
Hierbei steht wieder einmal die Überprüfung der Ergebnisse im Vordergrund, da KI-gestützte Tools nicht immer die gewünschten Ergebnisse liefern und menschliche Expertise erforderlich ist, um die Qualität der Metadaten sicherzustellen.

Konkret wollen wir

- Wichtige Metadatenschlagworte aus einen Eintrag im [Zentralen Open Educational Resource Repositorium (ZOERR)](https://www.zoerr.de/) extrahieren
- Entsprechende Metadaten für die Selbstlernmaterialien "[FDM-basics](https://dr-eberle-zentrum.github.io/FDM-basics/)" des Dr. Eberle Zentrums erstellen


## Aufgabe 1 - AI for the rescue

- Besuchen sie die Seite des [ZOERR](https://www.zoerr.de/) und öffnen sie verschiedene Materialien
  - (mindestens 3)
  - Klicken sie jeweils auf den "(I) Infos" Button im oberen grauen Rand, um die hinterlegten Metadaten zu sehen
  - Kopieren sie sich die **umfangreichsten Metadaten** (bzw. halten sie diese im Browser offen für den nächsten Schritt)
- Öffnen sie eine neue Prompting Session im LLM Tool ihrer Wahl (z.B. MS Copilot, ChatGPT, ...)
  - **BEACHTEN:** *Wenn das Ergebnis nach etwa 10 (konkreten und expliziten) Prompts noch nicht ihren Wünschen entspricht, brechen sie ab und machen mit dem nächsten Punkt weiter*
  - Informieren sie die KI über ihre Absichten und was sie von ihr wollen (Kontext und Aufgabe definieren!)
  - Liefern sie die Metadaten aus Schritt eins
  - Sorgen sie dafür, dass diese auf ein leeres Formular reduziert werden
    - Prüfen sie das leere Formular auf Vollständigkeit und Richtigkeit! (und lassen sie entsprechend korrigieren wenn nötig)
  - Lassen sie das leere Formular für unser [Onlinelehrmaterial "FDM-basic"](https://dr-eberle-zentrum.github.io/FDM-basics/) füllen.
  - Lassen sie sich eine Kurzbeschreibung in 10 Sätzen und 10 Schlagworte erstellen und einfügen
    -  Verwenden sie hierfür die ["All-in-one"-Seitenansicht](https://dr-eberle-zentrum.github.io/FDM-basics/aio.html)
  - Prüfen sie kritisch den Vorschlag
    - Autoreninformation finden sie auf der GitHub Seite des Projektes
    - Lassen sie den Vorschlag entsprechend korrigieren.
- Lassen sie sich den letzten Vorschlag im Markdown Format ausgeben und speichern sie diesen in ihrem Abgabeordner:
  - Dateiname: `FDM-basics.ZOERR.KI.md`
  - Fügen sie der Datei einen neuen (letzten) Abschnitt "KI" hinzu
    - Dokumentieren sie die verwendete KI (Name, URL, Version)
    - Speichern sie ihre komplette LLM Prompthistorie (sollten max. 10 Prompts sein, s.o.) für diese Aufgabe ab Schritt 2 (einfach komplett mit Zwischenantworten) zur Dokumentation via Copy-And-Paste
- Laden sie die Datei in ihrem Abgabeordner hoch


## Aufgabe 2 - Manuelle Überarbeitung und Reflexion

- Kopieren sie die erzeugte Markdown Datei und nehmen sie finale händische Überarbeitungen vor
  - Dateiname: `FDM-basics.ZOERR.md`
  - Entfernen sie den "KI" Abschnitt der Prompthistorie
  - Prüfen sie Metadaten, insbesondere
    - Autoren, Lizenz, Schlagwörter, Fachbereich, ... korrekt?
    - "Alte" Informationen aus Vorlage entfernt?
    - Erweiterte Kurzbeschreibung und Schlagworte von oben integriert und korrekt?
    - Kann man noch was ergänzen?
- Ergänzen sie einen neuen Abschnitt "Reflexion":
  - Dokumentieren sie ihre Erfahrungen und Beurteilen sie den Workflow. Beantworten sie dazu einige Fragen:
    - Was musste noch final angepasst werden? Wo hat generatives Erstellen nicht funktioniert?
    - Wie schätzen sie den Zeitbedarf ein? Wären sie händisch schneller gewesen? Was ging so schneller?
    - Wo sehen sie Grenzen in der Anwendung ihres LLM Tools für derartige Aufgaben? Wie beurteilen sie die Zuverlässigkeit?
    - Gibt es aus ihrer Sicht rechtliche Bedenken und wenn ja welche?
    - Wie sicher sind sie, dass die finalen, händisch überarbeiteten Metadaten stimmen?
- Laden sie die finale Datei in ihrem Abgabeordner hoch


