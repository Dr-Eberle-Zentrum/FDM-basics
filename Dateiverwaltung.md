---
title: 'Dateiverwaltung'
teaching: 15
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions 

- USB Stick nicht lesbar?
- Zugeschickte Datei nicht lesbar?
- Was wenn ganz viele Dateien?
- 

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Unterschiede der Dateisysteme gängiger Betriebssysteme
- Best Practices für Dateinamen und Pfade
- Automatisierung von Dateiverarbeitungsabläufen

::::::::::::::::::::::::::::::::::::::::::::::::

In den meisten Fällen arbeitet man heutzutage in einem sehr heterogenen Computerumfeld, d.h. es kommen verschiedene Betriebssysteme zum Einsatz, die jeweils ihre eigenen Dateisysteme verwenden.
Zum Beispiel arbeitet ein Mitarbeiter auf einem Windows-Rechner, ein anderer auf einem Mac und wieder ein anderer auf einem Linux-Rechner oder Daten werden auf einem Linux-basierten Server gespeichert.
Daher sollte man einen Überblick über die Unterschiede und Eigenheiten der Dateisysteme haben, um die Datenübertragung und -verarbeitung über Systemgrenzen hinweg zu erleichtern.



# Datei- vs. Betriebssystem



## Was ist ein Dateisystem?

Ein Dateisystem organisiert Daten auf Speichermedien wie Festplatten, SSDs oder USB-Sticks. Es legt fest:

- wie Dateien gespeichert und gelesen werden,
- wie Zugriffsrechte verwaltet werden,
- wie Daten strukturiert sind (z.B. Laufwerke, Ordner, Pfade, ..).

Gängige Dateisysteme sind im Folgenden aufgelistet und verglichen.

| Dateisystem | Betriebssystem(e) | Max. Dateigröße   | Kompatibilität |
|-------------|-------------------|-------------------|----------------|
| FAT32       | Windows, Linux, macOS | 4 GB          | Hoch (aber veraltet) |
| NTFS        | Windows             | >16 TB          | Eingeschränkt auf macOS/Linux |
| exFAT       | Windows, macOS, Linux | >16 EB        | Sehr hoch      |
| HFS+        | macOS               | >8 EB           | Nur macOS      |
| APFS        | macOS               | >8 EB           | Nur macOS      |
| ext4        | Linux               | >1 EB           | Eingeschränkt auf Windows/macOS |
| Btrfs/XFS   | Linux               | >16 EB          | Nur Linux      |

Man sieht hier deutlich, dass sich Dateisystem u.a. in der maximalen Dateigröße und der Kompatibilität unterscheiden.
Ein weiteres Unterscheidungsmerkmal ist ihre Unterstützung durch verbreitete Betriebssysteme.

:::::::::: challenge

## Was ist ein EB?

GB steht für "Gigabyte" und somit für $10^9$ Bytes.

Was ist dann ein EB und für welche 10-Potenz steht es?

:::: solution

## Antwort

- kB = Kilobyte = $10^3$ Bytes
- MB = Megabyte = $10^6$ Bytes
- GB = Gigabyte = $10^9$ Bytes
- TB = Terabyte = $10^{12}$ Bytes
- PB = Petabyte = $10^{15}$ Bytes
- **EB** = Exabyte = **$10^{18}$ Bytes** ... ganz schön viel! (derzeit...)


:::::::::::::

:::::::::::::::::::::


## Was ist ein Betriebssystem?

Ein Betriebssystem (OS) ist die Software, die die Hardware eines Computers verwaltet und eine Schnittstelle für Anwendungen bereitstellt.
Ein wichtiger Bestandteil eines Betriebssystems ist somit das Dateisystem, das die Organisation und Verwaltung von Dateien auf Speichermedien ermöglicht.
Dabei ist es möglich, das ein Betriebssystem mehrere Dateisysteme unterstützt, aber in der Regel wird ein primäres Dateisystem für Festplatten und neue Datenträger verwendet.

Im Folgenden sind die gängigsten Betriebssysteme und ihre bevorzugten Dateisysteme aufgeführt:

- **Windows** nutzt hauptsächlich **NTFS**, unterstützt aber auch **FAT32** und **exFAT**.
- **macOS** verwendet **APFS** (modern) und **HFS+** (älter).
- **Linux** setzt auf **ext4**, **Btrfs** oder **XFS**, je nach Distribution und Einsatzzweck.

## Kompatibilitätsaspekte

Um Daten zwischen verschiedenen Betriebssystemen auszutauschen, ist es wichtig, ein kompatibles Dateisystem zu wählen. Hier einige Hinweise:

- **exFAT** ist ideal für den Datenaustausch zwischen Windows, macOS und Linux.
- **NTFS** kann unter macOS und Linux oft nur gelesen werden, nicht geschrieben (außer mit Zusatzsoftware).
- **ext4** ist unter Windows nur mit Zusatztools nutzbar.

Falls ein (externer) Datenträger ein Dateisystem verwendet, welches vom genutzten Betriebssystem nicht unterstützt wird, dann kann man in den meisten Fällen auf die enthaltenen Daten nicht zugreifen.

::::::::::::::: challenge

## Welche Dateisysteme nutze ich?

Versuchen sie herauszufinden, welches Dateisystem auf folgenden Medien (je nach Verfügbarkeit) installiert ist.

- ihrer eingebauten (Haupt)festplatte
- einem USB-Stick
- einer externen Festplatte

*Falls sie in ihrem Betriebssystem nicht wissen, wie das geht, recherchieren sie kurz. Das ist wirklich wichtig!* 💪


:::::::::: solution

# Antwort

Das Betriebssystem der Hauptfestplatte eines Computers ist i.d.R. mit einem der oben gelisteten Betriebssysteme ausgestattet, wobei die konkrete Auswahl häufig vom Alter oder der Version des Betriebssystems abhängt.

Je nach Alter und Größe des USB Sticks, sind diese zumeist mit FAT32 oder exFAT formatiert.

:::::::::::::::::::

:::::::::::::::::::::::::::




# Dateinamen und Pfade

Beim Arbeiten mit Dateien in unterschiedlichen Betriebssystemen ist es wichtig, die Unterschiede in der Benennung und Pfadangabe zu kennen. 
Fehlerhafte Dateinamen oder falsche Pfadangaben können zu Problemen beim Zugriff, der Verarbeitung oder dem Austausch von Dateien führen.

## Pfadnotationen im Vergleich

Die Art und Weise, wie Pfade zu Dateien angegeben werden, variiert zwischen Betriebssystemen. Hier sind die wichtigsten Unterschiede:

| Betriebssystem | Beispielpfad innerhalb des Systems | Besonderheiten   |
|----------------|--------------------------|---------------------------------|
| Windows        | `C:\Benutzer\Max\Dokumente` | Backslashes `\` als Trenner     |
| macOS/Linux    | `/home/max/Dokumente`      | Slashes `/` als Trenner         |

**Windows** verwendet Laufwerksbuchstaben für einzelne Datenträger oder (Teil)festplatten (z.B. `C:`), während **Linux/macOS** ein einheitliches Wurzelverzeichnis (`/`) nutzen.
Das heißt in letzterem sind alle Dateien und Ordner Teil eines einzigen "Zugriffsbaumes", während in Windows jeder Datenträger ein eigenes "Laufwerk" mit eigener Orderhierarchie darstellt.
Dies ist im Folgenden dargestellt.

![Hierarchische Dateiorganisation in verschiedenen Betriebssystemen[^1].](fig/linux-struktur.png){alt='Dateiorganisation'}

[^1]: Quelle - [Franz Fiala](https://clubcomputer.at/2017/04/30/linux/) - 15.08.2025

Zudem sind Pfade unter **Linux/macOS case-sensitive**, d.h. `Datei.txt` ≠ `datei.txt`. Unter **Windows** ist dies meist nicht der Fall.


::::::::::::::: challenge

## Laufwerksbuchstaben

Welches Problem könnte sich aus der Verwendung von Buchstaben zur Bezeichnung von Laufwerken in Windows ergeben?


:::::::::: solution

# Antwort

Da das Alphabet nur 26 Buchstaben umfasst, können "nur" 26 Laufwerke eingebunden werden.

Allerdings sind die Laufwerksbuchstaben in neueren Windowsversionen nur noch in der Darstellungsebene für die Benutzer relevant; intern werden die Laufwerke anders verwaltet.

:::::::::::::::::::

:::::::::::::::::::::::::::



## Regeln für Dateinamen

Auch unterscheiden sich die Betriebssysteme in ihren Dateinamenskonventionen.

| Merkmal              | Windows                  | macOS/Linux              |
|----------------------|--------------------------|--------------------------|
| Sonderzeichen        | Verboten: `\ / : * ? " < > |` | Meist erlaubt, aber mit Vorsicht |
| Groß-/Kleinschreibung| Nicht relevant           | Relevant (case-sensitive)|
| Erweiterungen        | Wichtig (z.B. `.docx`)   | Optional, aber üblich    |

Diese haben häufig direkte Auswirkung auf den Dateiaustausch, auch wenn die Dateien über Cloudservices oder Dateitransfer ausgetauscht werden.

::::::::::: testimonial

## Typische Probleme beim Dateiaustausch

- **Ungültige Zeichen**: Eine Datei namens `Projekt:2025.docx` funktioniert unter Windows nicht.
- **Groß-/Kleinschreibung**: `Bericht.pdf` und `bericht.pdf` sind unter Linux zwei verschiedene Dateien.
- **Pfadlängen**: Windows hat Einschränkungen bei sehr langen Pfaden (>260 Zeichen).

:::::::::::::::::::::::::


::::::: instructor

TODO QUIZ ERSTELLEN


1. Welches Dateisystem ist standardmäßig unter Windows im Einsatz?
2. Was bedeutet „case-sensitive“?
3. Warum ist exFAT für den Datenaustausch geeignet?

::::::::::::::::::



# Automatisierte Dateiverarbeitung

Wenn man mit einigen wenigen Dateien arbeitet, führt man die nötigen Dateiverwaltungsschritte wie Umbenennen, Verschieben, Vergleichen, Löschen, etc. zumeist manuell aus.
Dies stößt schnell an seine Grenzen, wenn die Dateianzahl steigt.
Daher ist es sinnvoll, diese Schritte zu automatisieren, um Zeit zu sparen und Fehler zu vermeiden.

Alle Betriebssysteme bieten Möglichkeiten, Dateiverwaltungsschritte zu automatisieren, z.B. durch:

- **Shell Scripting**: Mit Shell-Skripten (z.B. Bash unter Linux/macOS oder PowerShell/Cmd unter Windows) können wiederkehrende Aufgaben automatisiert werden.
- **Programmiersprachen**: vor allem Skriptsprachen wie Python bieten umfangreiche Bibliotheken zur Dateiverwaltung.
- **Dateimanager**: Viele Dateimanager bieten Funktionen zum Batch-Umbenennen, Verschieben oder Löschen von Dateien.


::::::::::::::: challenge

## Automatisierung

Recherchieren sie eine Lösung für jeden der oben genannten Wege, um alle *.txt Textdateien in einem gewählten Verzeichnis umzubenennen, indem den Dateinamen ein `backup_` Präfix vorangestellt wird.

Finden sie Lösungen basierend auf

- einem Shellskript (Bash oder Powershell)
- einem Python-Skript
- einem Dateimanager (Windows Explorer oder Finder)

:::::::::: solution

## Antwort

Ein mögliches Bash Shellskript unter Linux oder macOS:

```bash
for file in *.txt; do
    mv "$file" "backup_$file"
done
```

PowerShell unter Windows:

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { "backup_" + $_.Name }
```

Ein einfaches Python-Skript:

```python
import os
for file in os.listdir('.'):
    if file.endswith('.txt'):
        os.rename(file, f'backup_{file}')
```

Im Windows Explorer lassen sich alle `.txt` Dateien auswählen, dann Rechtsklick -> "Umbenennen" und den neuen Namen `backup_` eingeben. Windows wird dann automatisch die Nummerierung hinzufügen (z.B. `backup_1.txt`, `backup_2.txt`, ...).

Analog ist dies im macOS Finder möglich: Alle `.txt` Dateien auswählen, dann Rechtsklick -> "Umbenennen" und den neuen Namen `backup_` eingeben. macOS wird ebenfalls die Nummerierung hinzufügen.

*Unbedingt beachten: In den beiden letzten Fällen gehen jedoch die Ursprungsnamen verloren!*

:::::::::::::::::::::

:::::::::::::::::::::::::

Skript- und Programmiersprachen bieten hier den Vorteil, dass sie komplexere Logik implementieren können, z.B. um nur bestimmte Dateien umzubenennen oder zusätzliche Bedingungen zu prüfen.

Zudem sichern Skripte und Programme die Reproduzierbarkeit der Dateiverwaltungsschritte, da sie jederzeit wiederholt werden können, ohne dass manuelle Eingriffe nötig sind.
Dies ist vor allem ein wichtiger Punkt bei der Prozessierung von Rohdaten.
Die verwendeten Skripte können (und sollten!) dokumentiert, versioniert und zusammen mit den Rohdaten archiviert werden, was die Nachvollziehbarkeit und Wartbarkeit erhöht.

Skriptsprachen sind hierbei häufig die erste Wahl, da sie eine einfache Syntax bieten und direkt auf das Dateisystem zugreifen können.
Zudem sind diese direkt in den meisten Betriebssystemen verfügbar und benötigen keine zusätzliche Installation.




## Zusammenfassung

::::::::::::::::::::::::::::::::::::: keypoints 

- Dateisysteme unterscheiden sich in ihrer Struktur, Kompatibilität und maximalen Dateigröße.
- Betriebssysteme nutzen/unterstützen unterschiedliche Dateisysteme und Pfadnotationen.
- Dateinamen und Pfade müssen betriebssystemkonform sein, um Probleme zu vermeiden.
- Automatisierung von Dateiverwaltungsschritten spart Zeit und reduziert Fehler.
- Skriptsprachen sind ideal für die Automatisierung von Dateiverwaltungsschritten.


::::::::::::::::::::::::::::::::::::::::::::::::



:::::::::: challenge

# Einordnung im Datenlebenszyklus

![*In welchen Phasen im Datenlebenszyklus sehen sie obige Punkte als besonders wichtig an?*](https://uni-tuebingen.de/fileadmin/_processed_/6/b/csm_FDM_Lebenszyklus_d1353825c4.png){width=40% alt="Datenlebenszyklus"}

::: solution

## Antwort

Das Wissen um die **Dateiverwaltung** ist immer dann zentral, 
wenn Dateien erzeugt, verarbeitet oder gespeichert werden.

- **Planung**: Festlegung von Dateisystemen und Dateinamenkonventionen
- **Erhebung**: Korrekte Dateinamen und Pfade, Automatisierung von Bearbeitungsabläufen
- **Analyse**: Automatisierung von Verwaltungsschritten
- **Publikation**: Dateiaustausch zwischen Projektpartnern
- **Archivierung**: Sicherung der Dateistruktur und -inhalte, Versionierung von Skripten
- **Nachnutzung**: Bereitstellung von Daten in kompatiblen Formaten, Namen, Organisationen

:::

::::::::::::::::::::



:::::::::::::::: instructor

## Aufgaben

### Vorbereitende Aufgaben

- [Aufgabe "Dateimanagementsysteme"](Aufgabe-Dateimanagementsysteme.md)

### Sitzungsfragen

- Wie sollte ich Dateien besser nicht benennen und warum?
- Worin unterscheiden sich die Dateiverwaltungen von Windows, Linux und macOS?
- Welche Dateisysteme sind für den Datenaustausch zwischen Betriebssystemen geeignet?
- Wie kann ich viele Dateien auf einmal verarbeiten?

### Anwendungsaufgaben

- [Sitzungsaufgabe "Versionschaos"](Aufgabe-Versionschaos.md)
- [Abgabeaufgabe "Dateiorganisation"](Aufgabe-Dateiorganisation.md)
- [Abgabeaufgabe "Backup"](Aufgabe-Backup.md)

:::::::::::::::::::::::::::

