---
title: 'Aufgabe "Versionschaos"'
---

:::::::::::::::: instructor
## Aufgabe zu "Dateiverwaltung"
:::::::::::::::::::::::::::

Im Folgenden wollen wir das Sprichwort "Viele Köche verderben den Brei" auf seine Anwendbarkeit bzgl. der gemeinsamen Dateibearbeitung überprüfen. 
Hierfür sollen verschiedene Kollaborationsszenarien verglichen und eingeschätzt werden.

Diskutieren sie in Kleingruppen Vor- und Nachteile der nachfolgend skizzierten Szenarien.

Fokussieren sie dabei auf folgende Aspekte

- Was kann schief gehen? (möglichst viele Punkte aufzählen!)
- Zeit(verbrauch)
- Nötige Kenntnisse?
- Wer hat die Hauptarbeit?
- Wie "gemeinsam" ist das Ergebnis?
- Skalierbarkeit? Ab wieviel wirds kritisch?
- Nachvollziehbarkeit?
- ... ?

Fassen sie ihre Ergebnisse in einer von ihrer Kleingruppe geteilten Datei *stichpunktartig* zusammen.

Speichern sie die Datei im **PDF Format** in ihrem Ablageordner:

- Dateiname: `Versionschaos.pdf`
- ACHTUNG: nennen sie in der ersten Zeile ihre Gruppenmitglieder!

## Szenarien

### Szenario "Kettenbriefe"

- A schickt die aktuelle Datei an X (via Email, WhatsApp, ...)
- X überarbeitet die Datei und schickt sie weiter an Y
- Y ....
- der/die Letzte sendet wieder an A
- A prüft und finalisiert
    
### Szenario "Broadcast"

- A schickt die aktuelle Datei gleichzeitig einmalig an X, Y, Z, ...
- jeder schickt seine Überarbeitung direkt zurück an A (in welcher Form auch immer)
- A integriert die Änderungen und finalisiert die Datei

### Szenario "Cloud"

- A teilt Dokument in Onlineeditor zur direkten Bearbeitung mit X, Y, Z, ...


### Szenario "Git"

- A teilt Dokument über Versionsverwaltungsplatform mit X, Y, Z
  - jeder ändert direkt im Dokument
  - Änderungen werden über branches und pull requests bereitgestellt und von A eingepflegt (gemerged)

