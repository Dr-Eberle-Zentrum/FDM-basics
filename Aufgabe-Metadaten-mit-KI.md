---
title: 'Aufgabe "Strukturcheck von Dateien"'
---

:::::::::::::::: instructor
## Aufgabe zu "Metadaten"
:::::::::::::::::::::::::::

Metadaten sind Daten, die Informationen über andere Daten enthalten. 
Sie beschreiben die Struktur, den Inhalt und die Eigenschaften von Datensätzen.

Es gibt verschiedene Standards und Formate für Metadaten, die je nach Anwendungsfall variieren können.
In dieser Aufgabe werden wir verschiedene Metadatenformate betrachten und diese mit Hilfe von KI ineinander umformen.

## Citation File Format (CFF)

Das [Citation File Format (CFF)](https://citation-file-format.github.io/) ist ein Standard, der es ermöglicht, bibliografische Informationen über Softwareprojekte oder Datenarchive in einer einfachen menschen- und maschinenlesbaren Form zu speichern.
Die explizite Spezifikation solcher Informationen ist für Software und Daten extrem wichtig, da sie sich i.d.R. nicht vom Endprodukt oder dem Inhalt der Resource ableiten lassen.
Softwarerepositorien wie GitHub oder Datenrepositorien wie ZENODO unterstützen dieses Format, um die Metadaten zu den Projekten zu speichern und nutzerfreundlich Zitationsinformationen in unterschiedlichen Formaten bereitzustellen.

### Aufgabe 1 - CFF Metadaten untersuchen

Die Datenbasis dieses Selbstlernmaterials ist ein GitHub Repository, in welchem auch Zitationsinformationen im `CFF` Format hinterlegt sind.

- Besuchen sie das Repository [https://github.com/Dr-Eberle-Zentrum/FDM-basics](https://github.com/Dr-Eberle-Zentrum/FDM-basics)
- Finden sie in der GitHub Oberfläche die von GitHub bereitgestellte Zitationsinformation (Menü im rechten Rand)
- Erstellen sie eine Markdown-Datei 
  - `FDM-basics-Metadaten.md` in ihrem Abgabeordner 
  - und dokumentieren sie dort den aktuellen Stand:
    - die Zitationsinformationen im CFF Format (nutzen sie einen Codeblock in Markdown)
    - die Zitationsinformation im BibTeX Format


### Aufgabe 1 - CFF Metadaten überarbeiten

CFF Dateien können auch von Menschen gelesen werden, da sie in einem YAML ähnlichen Format geschrieben sind.
Sie können die Datei also auch in einem Texteditor öffnen und bearbeiten.
Allerdings bietet es sich an, einen speziellen Editor zu verwenden, der die Syntaxprüfung und Validierung übernimmt.
Im Folgenden sollen sie solch einen verwenden, um die Metadaten zu überarbeiten.

- Öffnen sie die den [Online CFF Editor](https://citation-file-format.github.io/cff-initializer-javascript/#/)
- Laden sie die CFF Datei aus dem Repositorium zum Editieren hoch
- Prüfen und Überarbeiten sie die Metadaten, indem sie u.a. prüfen
  - Titel des Projekts
  - Autorenliste (check)
  - Artifact repository (URL der erzeugten Selbstlernseite wie in diesem Dokument)
  - Veröffentlichungsdatum auf das aktuelle Datum setzen
  - Keyword Liste ergänzen bzw. überarbeiten
  - Version auf das aktuelle Semester setzen
  - .. *falls sie nicht wissen, was gewisse Punkte bedeuten, schlagen sie kurz in der [CFF Spezifikation](https://github.com/citation-file-format/citation-file-format/blob/main/schema-guide.md#index) nach*.
- Speichern sie die überarbeiteten CFF Metadaten in der Datei `FDM-basics-Metadaten.md` in einem neuen Abschnitt ab.


### Aufgabe 2 - CFF Metadaten in andere Formate umwandeln

Es gibt verschiedene Formate, in denen Zitationsinformationen bereitgestellt werden können.
Die gängigsten sind `BibTeX`, `RIS` und `JSON` und hierfür gibt es auch Konverter, die die CFF Metadaten in diese Formate umwandeln können.

Allerdings möchten wir die Daten im allgemeinen [Dublin Core Format](https://www.glomas.de/glossar/dublin-core) bereitstellen, da dieses Format von vielen Repositorien und Bibliotheken unterstützt wird.

Um uns die Suche nach einem geeigneten Konverter zu ersparen, beschliessen wir, die Umwandlung mit Hilfe von KI Tools wie [ChatGPT](https://chat.openai.com/), [Claude](https://claude.ai/) oder Microsoft [Copilot](https://www.microsoft.com/en-us/microsoft-365/copilot) durchzuführen.

*ACHTUNG: Hierbei verschiebt sich jedoch ihre Rolle als Datenmanager:in von der manuellen Umwandlung hin zu einer Überprüfung der Ergebnisse, die die KI generiert.
Also prüfen sie die Ergebnisse auf Vollständigkeit und Richtigkeit (und schlagen sie ggf. vorher nochmal kurz in der [Dublin Core Format](https://www.glomas.de/glossar/dublin-core) Zusammenfassung nach).*

- Verwenden sie einen KI Dienst ihrer Wahl, um die CFF Metadaten in Dublin Core Metadaten im XML Format umzuwandeln.
- Standardmäßig unterstützt Dublin Core 15 unterschiedliche Metadaten-Elemente, welche teilweise auch mehrfach vorkommen dürfen
  - Prüfen sie, ob alle 15 Elemente in den Metadaten enthalten sind oder ob ggf. zusätzliche Elemente hinzugefügt werden könnten
  - Überprüfen sie, ob Mehrfachverwendungen von Elementen sinnvoll sind und ob diese korrekt umgesetzt wurden
  - Stellen sie sicher, dass die Datei in einem validen XML Format vorliegt
- Speichern sie die Metadaten in der Datei `FDM-basics-Metadaten.md` in einem neuen Abschnitt ab.
  - Dokumentieren sie auch die verwendete KI und was sie händisch nachgearbeitet haben.
  - Beschreiben sie (halbe Seite), wo sie an welche Grenzen gestoßen sind und welches Metadatenformat sie für mächtiger halten und warum.





