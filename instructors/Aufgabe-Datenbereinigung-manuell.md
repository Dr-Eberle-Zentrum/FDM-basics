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

Konkret wollen wir die Daten für die [Mietpreisentwicklung in Baden-Württemberg extrahieren vom Statistischen Landesamt Baden-Württemberg](https://www.statistik-bw.de/GesamtwBranchen/KonjunktPreise/VPI-LR.jsp?i=h) extrahieren und bereinigen (siehe Link).

- Die Gesamttabelle ist als CSV Download auf der oben gelinkten Seite verfügbar.

Wir sind allerdings nur an Teilen der Daten interessiert, konkret:

- Verbraucherpreisindex für Baden-Württemberg (Spalte 2)
- nur die Jahresdurchschnitswerte (Zeilen mit "JD XXXX")
- nur die Werte für die Jahre 2000 bis 2023


### Aufgabe 1 - Reguläre Ausdrücke

- Downloaden sie die CSV Datei von der oben verlinkten Seite und
  - Speichern sie diese in ihrem Abgabeordner
  - Dateiname: `mietpreisindex-bw.komplett.csv`

- Öffnen sie die Datei in einem TEXTEDITOR (nicht Excel oder ähnliches) der in der Suche REGULÄRE AUSDRÜCKE unterstützt.
- Falls sie Notepad++ verwenden, können sie in der Suchmaske auf den Reiter "Hervorheben" wechseln, um Treffer leichter zu sehen.

Ersinnen sie REGULÄRE AUSDRÜCKE für die folgenden Aufgaben und dokumentieren sie diese in ihrem Abgabeordner.

- Dateiname: `mietpreisindex-bw.komplett.regex.md`

1. Ausdruck selektiert ausschliesslich die Überschrift `Jahr/Monat;Verbraucherpreisindex`
2. Ausdruck selektiert alle Datenzeilen für Einzelmonate
    - erster Treffer sollte `Januar;117,4;109,3;+3,0;108,9;+2,7;109,8;+2,8` sein
    - letzter Treffer is `Dezember;27,3;23,8;–;-;–;-;–`
    - Versuchen sie den Ausdruck möglichst klein zu halten. Sie können auch gern mehrere Varianten vorschlagen!
3. Ausdruck selektiert AUSSCHLIESSLICH die gewünschten Daten (siehe Ziel)
    - sollten 24 Treffer/Zeilen sein
    - der erste Match sollte `JD 2023;116,4` sein
4. Erweiterung von 3., sodass nur die Jahreszahl und der Wert selektiert werden
    - der erste Match sollte `2023;116,4` sein
    - Tipp: lookaround assertions verwenden
5. Kombination aus 1. und 4. um die gewünschten Daten inklusive Überschrift zu selektieren


### Aufgabe 2 - Copy-Paste-Edit

- Öffnen sie die Webseite von oben
- Markieren sie die gewünschten Daten (siehe Ziel)
- Kopieren sie die Daten in die Zwischenablage
- Öffnen sie einen TEXTEDITOR und fügen sie die Daten ein
- Bereinigen sie die Daten manuell
  - Verwenden sie [vertikale Markierung](https://www.pctipp.ch/praxis/zubehoer/kleines-maus-trickli-fuer-word-writer-2012970.html) ([MacOs](https://www.macwelt.de/article/934976/textedit-beliebig-markieren.html)), um spaltenweise zu markieren und zu löschen
  - Verwenden sie "Suchen und Ersetzen", um ein Semikolon als Spaltentrenner zwischen den zwei Zielspalten einzufügen
  - Reduzieren sie die erste Spalte auf die Jahreszahlen (vertikale Markierung oder Suchen-und-Ersetzen)
  - Fügen sie eine Überschriftszeile `Jahr;Verbraucherpreisindex` ein
- Speichern sie die Daten als CSV Datei
  - Dateiname: `mietpreisindex-bw.jahresdurchschnitt.csv`
  
- Dokumentieren sie die Schritte in einer Markdown-Datei
  - Dateiname: `mietpreisindex-bw.jahresdurchschnitt.README.md`
  - Denken sie an eine komplette Quellen- und Editierbeschreibung!
