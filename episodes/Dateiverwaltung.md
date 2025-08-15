---
title: 'Dateiverwaltung'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions 

- Windows, MacOS, Linux?
- Was wenn ganz viele Dateien?
- 

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Unterschiede der Dateisysteme gängiger Betriebssysteme
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

:::::::::::::::  challenge

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

| Betriebssystem | Beispielpfad             | Besonderheiten                  |
|----------------|--------------------------|---------------------------------|
| Windows        | `C:\Benutzer\Max\Dokumente` | Backslashes `\` als Trenner     |
| macOS/Linux    | `/home/max/Dokumente`      | Slashes `/` als Trenner         |

**Windows** verwendet Laufwerksbuchstaben für einzelne Datenträger oder (Teil)festplatten (z. B. `C:`), während **Linux/macOS** ein einheitliches Wurzelverzeichnis (`/`) nutzen.
Das heißt in letzterem sind alle Dateien und Ordner Teil eines einzigen "Zugriffsbaumes", während in Windows jeder Datenträger ein eigenes "Laufwerk" mit eigener Orderhierarchie darstellt.
Dies ist im Folgenden dargestellt.

![Hierarchische Dateiorganisation in verschiedenen Betriebssystemen[^1]](fig/linux-struktur.png){alt='Dateiorganisation'}

[^1]: Quelle - [Franz Fiala](https://clubcomputer.at/2017/04/30/linux/) - 15.08.2025

Zudem sind Pfade unter **Linux/macOS case-sensitive**, d. h. `Datei.txt` ≠ `datei.txt`. Unter **Windows** ist dies meist nicht der Fall.


:::::::::::::::  challenge

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


:::::::  instructor

TODO QUIZ ERSTELLEN


1. Welches Dateisystem ist standardmäßig unter Windows im Einsatz?
2. Was bedeutet „case-sensitive“?
3. Warum ist exFAT für den Datenaustausch geeignet?

::::::::::::::::::





::::::::::::::::::::::::::::::::::::: keypoints 

- 

::::::::::::::::::::::::::::::::::::::::::::::::

