---
title: 'Aufgabe "Automatisierung"'
---

:::::::::::::::: instructor
## Aufgabe zu "Dateiverwaltung"
:::::::::::::::::::::::::::

Diese Aufgabe führt sie in die Automatisierung von Dateiverwaltung ein.

Sie sollen hierfür verschiedene Herangehensweisen an die gleiche Aufgabe testen und praktisch ausprobieren.
Hierfür haben wir ihnen eine Archivdatei mit 60 leeren Dateien vorbereitet, die sie unter folgendem Link herunterladen können:

- [Dateien-fuer-Automatisierung.zip](data/Dateien-fuer-Automatisierung.zip)

Das Ziel dieser Aufgabe ist es, die enthaltenen Dateien in verschiedene Ordner zu verschieben, die nach den Dateiendungen benannt sind.
D.h. alle `.txt`-Dateien sollen in den Ordner `txt`, alle `.md`-Dateien in den Ordner `md` usw. verschoben werden.

Sie sollen diese Aufgabe auf verschiedene Arten lösen und die Vor- und Nachteile der jeweiligen Herangehensweise dokumentieren.

### Variante 1 - Manuelle Verschiebung via Dateimanager

1. Entpacken sie die Archivdatei in einen Ordner ihrer Wahl.
2. Öffnen sie den Ordner in ihrem Dateimanager.
3. Erstellen sie die Ordner `txt`, `md`, für alle Dateiendungen, die in den Dateien vorkommen. (Achtung: nur für diese und keine darüber hinaus!)
4. Verschieben sie die Dateien in die entsprechenden Ordner.
5. Dokumentieren sie in einem Markdown-Dokument `Automatisierung.md` in einem Abschnitt `Variante 1 - manuell` in ihrem Abgabeordner:
   - Welche Schritte sie unternommen haben.
   - Welche Vor- und Nachteile diese Herangehensweise hat.
   - Wie sie die Skalierbarkeit dieses Ansatzes einschätzen.
   - Wie sieht die Reproduizierbarkeit dieses Ansatzes aus?
   
### Variante 2 - Automatisierung via Shell Skript

Erstellen sie ein Skript, das die Dateien automatisch in die entsprechenden Ordner verschiebt.

Wählen sie hierfür **eine Skriptsprache, die sie noch nicht beherrschen**!
Finden sie sich hierfür zu Kleingruppen mit anderen Kursteilnehmenden zusammen, die die gleiche Sprache gewählt haben.

Lassen sie sich (getrennt voneinander) von einem LLM (z.B. ChatGPT) ein entsprechendes Skript generieren.
Versuchen sie, die Skripte gemeinsam nachzuvollziehen.

Erstellen sie als Gruppe ein gemeinsames Shell-Skript, dass die Kernfunktionalität enthält, die sie benötigen, um die Dateien in die entsprechenden Ordner zu verschieben.
Hierfür sollte ihnen das Vergleichen der verschiedenen Skripte helfen, um die besten Ansätze zu finden.

Speichern sie das Skript in ihrem Abgabeordner unter dem Namen `Automatisierung.[SHELLNAME].txt`.

Beschreiben sie in ihrem Markdown-Dokument `Automatisierung.md` in einem Abschnitt `Variante 2 - Shell-Skript`:

- Namen der Gruppenmitglieder
- Welche LLMs etc. wurden verwendet?
- Wie sicher sind sie, dass das Skript funktioniert?
- Wie sicher sind sie, dass das Skript *nur genau das* tut, was sie wollen?


