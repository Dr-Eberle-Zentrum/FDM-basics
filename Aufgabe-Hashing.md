
---
title: 'Aufgabe "Hashing"'
---

:::::::::::::::: instructor
## Aufgabe zu "Verschlüsselung"
:::::::::::::::::::::::::::

Hashing dient häufig zur Überprüfung der Integrität von Daten. 
Wenn z.B. Dateien auf den eigenen Rechner gedownloaded werden, kann theoretisch eine Menge schief gehen.

- Die Datei kann während des Downloads beschädigt werden oder unvollständig ankommen.
- Die Datei kann während der Reise manipuliert oder ausgetauscht werden.

Daher werden häufig zusammen mit dem Download auch Hash-Werte der Dateien bereitgestellt, die nach dem Download überprüft werden können.


## Downloadcheck

In dieser Aufgabe soll solch ein Integritätscheck durchgeführt werden.
Dazu soll ein Hash-Wert für eine Datei berechnet werden, der dann mit dem bereitgestellten Hash-Wert verglichen wird.

- Lade die Datei [`hash-geheimnis.txt`](data/hash-geheimnis.txt) herunter.
- Berechne den Hash-Wert der Datei.
- Vergleiche den berechneten Hash-Wert mit dem folgenden bereitgestellten Hash-Wert.


```
# sha256 hash von "hash-geheimnis.txt"
829bcbd040dceae6d3c5cb5332fb3e3921cefe7e9eb5657b4e4ec661124db493
```

### Dokumentation

- Erstellen sie die Datei `hash-geheimnis.md` in ihrem Arbeitsverzeichnis.

- (1) Dokumentieren sie, welche Schritte sie unternommen haben, um den Hash-Wert zu berechnen. Welche Tools haben sie verwendet?
- (2) Dokumentieren sie, ob der Hash-Wert mit dem bereitgestellten Hash-Wert übereinstimmt.
- (3) Überlegen sie, welche Sicherheitsbedenken sich aus der Verwendung von Onlinetools ergeben können? Beschreiben sie stichpunktartig ihre Gedanken in der Datei.


## Leichte Änderung

Als nächstes sollen sie die Auswirkungen von kleinen Änderungen auf den Hash-Wert untersuchen.

- Suchen sie sich einen Online Hash-Generator für SHA256-Hashes von Texteingaben.
- Berechnen sie die Hash-Werte der folgenden Texteingaben:
  - `FDM360` = unser Ausgangstext für diese Aufgabe.
  - `FDM361` = quasi der gleiche Text, nur dass ein Zeichen verändert wurde.
  - `FDM362` = und noch ein ähnlicher Text.
- Dokumentieren sie beide Werte in ihrer Abgabedatei

## Was ist der Hash-Wert?

Der Hash-Wert ist eine Art Fingerabdruck für digitale Daten.
Allerdings sieht er erst einmal wie eine zufällige Zeichenkette von Buchstaben und Zahlen aus.

- Recherchieren sie, was genau ein Hash-Wert ist.
  - Dokumentieren sie ihre Ergebnisse in der Abgabedatei.
- Finden sie eine Möglichkeit, diesen in eine Ganzzahl umzuwandeln.
  - Dokumentieren sie die Ganzzahlumrechnungen beider Hash-Werte in der Abgabedatei.
- Welche Effekte sehen sie?

