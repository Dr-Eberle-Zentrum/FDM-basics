
# Aufgabe 1 - Datenextraktion

## Vorgehensweise:
1. Downloaden der Mietpreise Tübingen .png Datei
2. Hochladen der Datei in den __WebPlotDigitizer Version 4.8__
3. Choose Plot Type: __2D (X-Y) Plot__
4. Auswählen von vier bekannten Werten, um die Achsen zu kalibrieren
5. Eintragen der Werte in die Tabelle:

| - | Point 1 | Point 2 |
| ------ | ------ | ------ |
| X-Axis | 2013 | 2020 |
| Y-Axis | 9 | 16 |

6. Rename Dataset: __30qm__
7. Display Color -> __Dunkelrot__
8. Add point: Manuelles Hinzufügen der 13 Werte, der 30qm Kurve
9. Add Dataset: Erstellen der Datensätze für die Kurven __60qm__ (Gelb) und __100qm__ (Grün)
10. Automatische Detektion der Bildwerte des Datensatzes __100qm__:
    - Automatic Extraction -> Anklicken der Farbe, Color picker -> Anklicken der Kurvenfarbe (grün)
    - Algorithm: __X-Step__
    - Datenwerte:

| - | - |
| ------ | ------ |
| X_min | 2011 |
| ΔX Step | 0.1 |
| X_max	 | 2023 |
| Y_min | 8 |
| Y_max | 18 |
| Line width	 | 30 |  

11. Wiederholen des Schritts für __60qm__: Fehlerhafte Werte werden erkannt
12. Manuelle Setzung der Werte
13. Exportieren der Daten: “Datasets” -> “Export All Data” -> “Download .CSV”
14. Umbenennen der Datei in: mietpreise-tuebingen.csv

## Verwendete Tools:
- WebPlotDigitizer Version 4.8
- Zugriffszeit: 21.05.2025, 21:02
- Manuell gesetzte Datensätze: __30qm__ und __60qm__
- Automatisch extrahierte Datensätze: __100qm__
   
   
