---
title: "Datenverarbeitung"
teaching: 30
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions 

- Reproduzierbar?
- Dokumentiert?
- Skalierbar?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Gründe für den Einsatz von Workflow-Systemen und Skriptsprachen
- Verständnis von Pipelines und deren Aufbau
- Was, wenn der eigene Rechner nicht mehr reicht?


::::::::::::::::::::::::::::::::::::::::::::::::


Datenverarbeitung ist der Kernpunkt jedes Forschungsprozesses. 
In dieser Sitzung werden wir uns mit grundlegenden Aspekten der Datenverarbeitung im Kontext des Forschungsdatenmanagements (FDM) beschäftigen. 
Hierbei liegt der Fokus auf der Bedeutung von Workflow-Systemen, Skriptsprachen und Pipelines für die effiziente und reproduzierbare Arbeitsabläufe.


Bevor wir starten, hier ein kleines fiktives Beispiel, um die Relevanz der Themen zu verdeutlichen:

::: tab

### Was bisher geschah ...

Sie verspüren heute einen unbändigen Tatendrang und möchten Daten zu Blütenformen analysieren.

Nach kurzer Recherche finden sie den [Iris-Datensatz](https://en.wikipedia.org/wiki/Iris_flower_data_set), der Informationen zu verschiedenen Iris-Arten und deren Blütenmerkmalen enthält.
Dieser Datensatz ist in einer [CSV-Datei](https://zenodo.org/record/1319069/files/iris.csv) im [Zenodo Datenrepositorium](https://zenodo.org/records/1319069) verfügbar, und sie laden ihn sofort herunter.

![Iris Blüten verschiedener Arten (Autoren v.l.n.r: D. Langlois , C. Johansson, S. Keohane, [Lizenzinfos](https://training.galaxyproject.org/training-material/topics/introduction/tutorials/galaxy-intro-101-everyone/tutorial.html#analysis-how-to-differentiate-the-different-iris-species))](https://training.galaxyproject.org/training-material/topics/introduction/images/iris_flowers.png){width=70% alt="Three species of Iris flowers"}

Da sie lieber im TSV-Format arbeiten, konvertieren sie die Datei mit einem Texteditor mit Hilfe der "Finden und Ersetzen"-Funktion in das gewünschte Format.
Ausserdem löschen sie die Kopfzeile mit den Spaltennamen, da sie diese nicht benötigen.

Nun möchten sie die Daten analysieren.
Die erste Frage, die sich aufdrängt, ist, wieviele verschiedene Iris-Arten im Datensatz enthalten sind.
Hierfür erinnern sie sich an die "Spaltenselektion"-Funktion ihres Texteditors (Alt-Taste (Windows/Linux) bzw. Befehlstaste (Mac) gedrückt halten und dann die Maus ziehen) und extrahieren die Spalte mit den Artennamen.
Diese kopieren sie in eine neue Datei und verwenden die "Duplikate entfernen"-Funktion ihres Texteditors, um die einzigartigen Arten zu identifizieren.
Wunderbar, es sind genau drei Arten, wie erwartet.

Danach bearbeiten sie die Daten weiter mit einer Kombination aus Texteditor und Tabellenkalkulationsprogramm, um herauszufinden,

- Wieviele Datensätze gibt es pro Art?
- Wie sind die durchschnittlichen Blütenmaße pro Art?
- Wie verteilen sich die [Datenpunkte der Sepalblätter in einem Streudiagramm](https://training.galaxyproject.org/training-material/topics/introduction/images/101_foreveryone_scatter.png) coloriert nach Art?

Am Ende ihres Arbeitstages sind sie zufrieden mit den Ergebnissen, aber auch etwas erschöpft.
Sie haben sich auf einem Blatt Papier die Ergebniszahlen notiert und die Grafik ausgedruckt.

:::


:::::::::: challenge

## Und nun?

Ein paar Tage später sprechen sie mit Freunden über ihre Analyse und holen ihre Notizen und den Ausdruck.

Was könnte nun das Problem sein?

::: solution

## Mögliche Probleme

- **Nicht nachvollziehbar**: Leider sind sie sich nicht mehr sicher, welche Zahl auf ihren Notizen welche Art repräsentiert.
- **Nicht reproduzierbar**: Der Hamster hat den halben Ausdruck gefressen, aber sie wissen nicht mehr genau, wie sie die Grafik erstellt haben.
- **Fehleranfällig**: Beim Kopieren der Daten in den Texteditor haben sie versehentlich eine Zeile gelöscht, was die Ergebnisse verfälscht. Bzw. beim Notieren der Ergebniszahlen hatten sie einen Zahlendreher.
- **Zeitaufwand**: Die manuelle Bearbeitung der Daten hat viel Zeit in Anspruch genommen, die sie lieber in die Interpretation der Ergebnisse investiert hätten.
- **Fehlende Skalierbarkeit**: Sie möchten die Analyse auf einen größeren Datensatz anwenden, aber die manuelle Methode ist nicht praktikabel für größere Datenmengen.

::::::::::::

::::::::::::::::::::


## Ziele guter Datenverarbeitung

Gute Datenverarbeitung sollte folgende Ziele verfolgen:


- **Reproduzierbarkeit**: Andere (oder sie selbst zu einem späteren Zeitpunkt) sollten die Analyse mit den gleichen Daten und Methoden wiederholen können und zu den gleichen Ergebnissen kommen.
- **Nachvollziehbarkeit**: Jede Entscheidung und jeder Schritt in der Datenverarbeitung sollte dokumentiert sein, um die Analyse transparent zu machen.
- **Automatisierung**: Wiederkehrende Aufgaben sollten automatisiert werden, um menschliche Fehler zu minimieren und Zeit zu sparen.
- **Skalierbarkeit**: Die Methoden sollten auf größere Datensätze anwendbar sein, ohne dass der Aufwand exponentiell steigt.
- **Portabilität**: Die Analyse sollte auf verschiedenen Systemen und Umgebungen durchführbar sein, ohne dass umfangreiche Anpassungen erforderlich sind.

Reproduzierbarkeit und Nachvollziehbarkeit sind hierbei zwei zentrale Prinzipien in der wissenschaftlichen Forschung, die sicherstellen, dass Forschungsergebnisse verlässlich und überprüfbar sind.

Damit diese erreicht werden können, bedarf es entweder einer extrem umfangreichen Dokumentation oder - und das ist der bessere Weg - die Datenverarbeitung sollte mit Hilfe von Skriptsprachen und/oder Workflow-Systemen erfolgen.




## Skriptsprachen

Skriptsprachen sind Programmiersprachen, die speziell für die Automatisierung von Aufgaben und die Verarbeitung von Daten entwickelt wurden. 
Sie ermöglichen es Forschenden, komplexe Datenverarbeitungsaufgaben durch das Schreiben von Code zu automatisieren ohne dabei spezifische Kenntnisse über computerinterne Abläufe und Strukturen haben zu müssen.
Das heißt, Skriptsprachen abstrahieren viele technische Details und bieten eine benutzerfreundliche Syntax, die es auch Nicht-Programmierern ermöglicht, effektive Datenverarbeitungsprozesse zu erstellen.
Zudem sind Skriptsprachen oft plattformunabhängig, was bedeutet, dass Skripte auf verschiedenen Betriebssystemen ausgeführt werden können, ohne dass sie angepasst werden müssen.

Verbreitete Skriptsprachen im Forschungsdatenmanagement sind:

- **Python**: Bekannt für seine Lesbarkeit und Vielseitigkeit, mit umfangreichen Bibliotheken für Datenanalyse (z.B. Pandas, NumPy).
- **R**: Speziell für statistische Analysen und Datenvisualisierung entwickelt, mit einer großen Community und vielen Paketen (z.B. ggplot2, dplyr).
- **Bash**: Eine Unix-Shell und Skriptsprache, die häufig für Systemadministration und Automatisierung von Aufgaben in Linux-Umgebungen verwendet wird.

Auch die mit der Webentwicklung verbundene Sprache *JavaScript* kann für Datenverarbeitungsaufgaben genutzt werden.

Wenngleich Skriptsprachen viele technische Details abstrahieren, ist es dennoch wichtig, ein grundlegendes Verständnis der zugrunde liegenden Konzepte zu haben, um effektiv und effizient arbeiten zu können.

Bei der Verwendung von Skriptsprachen muss unterschieden werden zwischen 

- **Interaktive Verarbeitung**, bei der einzelne Befehle oder Code-Snippets in einer interaktiven, chatartigen Eingabe ausgeführt werden, um Daten zu analysieren und zu visualisieren.
- **Automatisierte Verarbeitung**, bei der komplette Skripte geschrieben werden, die eine Reihe von Befehlen enthalten, die nacheinander ausgeführt werden, um eine vollständige Datenverarbeitungsaufgabe zu erledigen.

Die interaktive Verarbeitung eignet sich gut für explorative Datenanalyse und schnelle Tests, hat aber die gleichen Nachteile wie die manuelle Verarbeitung.
**Die automatisierte Verarbeitung ist daher zu bevorzugen und eigenet sich für wiederholbare und skalierbare Aufgaben.**

Einer der größten Vorteile von Skriptsprachen (im Rahmen der automatisieren Verarbeitung) ist es, dass sie direkt Dokumentation und Automatisierung verbinden und i.d.R. auch Skalierbarkeit und Portabilität unterstützen.
Das heißt, ein einmal geschriebenes Skript kann immer wieder ausgeführt werden, ohne dass manuelle Schritte erforderlich sind.
Zudem erlaubt das Skript einzelne Schritte und Entscheidungen zu dokumentieren, was die Nachvollziehbarkeit erhöht.

Im Folgenden haben wir das Datenverarbeitungsbeispiel von oben in einfache Python- und R-Skripte übersetzt, welche die gleichen Schritte automatisiert durchführt:

::::::::::::: tab


### R-Skript

Hier als R-Skript:

```R
library(tidyverse)  
# (1) Daten einlesen (ersetzt Umformatierung und Kopfzeilenentfernung)
data <- read_csv('https://zenodo.org/record/1319069/files/iris.csv')
# (2) Enthaltene Arten extrahieren
distinct(data, Species)
# (3) Anzahl der Datensätze pro Art bestimmen
count(data, Species)
# (4) Gruppieren pro Art und Mittelwerte der Spalten berechnen
data %>% 
  group_by(Species) %>% 
  summarise(across(everything(), mean))
# (5) Visualisierung als Streudiagram
ggplot(data, aes(x=Sepal.Length, y=Sepal.Width, color=Species)) +
  geom_point() +
  labs(title='Sepal length as a function of sepal width', 
       x='Sepal length', y='Sepal width')
```

### R online interaktiv

Und hier als interaktives R-Skript (kann direkt im Browser ausgeführt werden):

<iframe width='100%' height='300' src='https://rdrr.io/snippets/embed/?code=library(tidyverse)%20%20%0A%23%20(1)%20Daten%20direkt%20laden%20(ersetzt%20Import%2C%20Umformatierung%20und%20Kopfzeilenentfernung)%0Adata%20%3C-%20iris%0A%23%20(2)%20Enthaltene%20Arten%20extrahieren%0Adistinct(data%2C%20Species)%0A%23%20(3)%20Anzahl%20der%20Datens%C3%A4tze%20pro%20Art%20bestimmen%0Acount(data%2C%20Species)%0A%23%20(4)%20Gruppieren%20pro%20Art%20und%20Mittelwerte%20der%20Spalten%20berechnen%0Adata%20%25%3E%25%20%0A%20%20group_by(Species)%20%25%3E%25%20%0A%20%20summarise(across(everything()%2C%20mean))%0A%23%20(5)%20Visualisierung%20als%20Streudiagram%0Aggplot(data%2C%20aes(x%3DSepal.Length%2C%20y%3DSepal.Width%2C%20color%3DSpecies))%20%2B%0A%20%20geom_point()%20%2B%0A%20%20labs(title%3D'Sepal%20length%20as%20a%20function%20of%20sepal%20width'%2C%20%0A%20%20%20%20%20%20%20x%3D'Sepal%20length'%2C%20y%3D'Sepal%20width')' frameborder='0'></iframe>


### Python-Skript

Und das Gleiche als Python-Skript:

```python
import pandas as pd
import matplotlib.pyplot as plt
# (1) Daten einlesen (ersetzt Umformatierung und Kopfzeilenentfernung)
data = pd.read_csv('https://zenodo.org/record/1319069/files/iris.csv')
# (2) Enthaltene Arten extrahieren
print(data['Species'].unique())
# (3) Anzahl der Datensätze pro Art bestimmen
print(data['Species'].value_counts())
# (4) Gruppieren pro Art und Mittelwerte der Spalten berechnen
grouped_data = data.groupby('Species').mean()
print(grouped_data)
# (5) Visualisierung als Streudiagramm
plt.scatter(x=data['Sepal.Length'], y=data['Sepal.Width'], c=data['Species'].astype('category').cat.codes)
plt.title('Sepal length as a function of sepal width')
plt.xlabel('Sepal Length')
plt.ylabel('Sepal Width')
plt.show()
# PS: Legende für die Farben fehlt noch...
```

:::::::::::::::


Nicht alle Schritte der Datenverarbeitung lassen sich immer einfach in Skripte übersetzen.
Häufig sind mehrere Schritte notwendig, um eine vollständige Analyse durchzuführen, welche ggf. dann in verschiedenen Skriptdateien organisiert werden müssen.
Allerdings ist nun die übergeordnete Ausführteihenfolge der Einzelskripte entscheidend, um die gesamte Analyse durchzuführen.
Das heißt, es entsteht eine **Abhängigkeit** zwischen den einzelnen Skripten und die Organisations- und Dokumentationsprobleme verschieben sich nun auf die Ebene der **Verwaltung und Ausführung von Skript-Abfolgen**.

An dieser Stelle kommen **Workflow-Systeme** und **Pipelines** ins Spiel, die genau diese Probleme adressieren.


## Workflow-Systeme und Pipelines

*Workflow-Systeme* sind spezialisierte Softwarelösungen, die entwickelt wurden, um komplexe Datenverarbeitungsprozesse zu automatisieren, zu verwalten und zu dokumentieren.
Sie ermöglichen es Forschenden, verschiedene Schritte der Datenverarbeitung zu definieren, zu verknüpfen und auszuführen, ohne dass sie sich um die technischen Details der Ausführung kümmern müssen.
Workflows bestehen aus einer Reihe von **Schritten** oder **Tasks**, die nacheinander oder parallel ausgeführt werden können.
Jeder Schritt kann ein Skript, ein Programm oder ein Tool sein, das eine spezifische Aufgabe erfüllt.

*Pipelines* sind eine spezielle Art von Workflows, die sich auf die Verarbeitung von Daten in einer sequenziellen Abfolge von Schritten konzentrieren.
Pipelines sind besonders nützlich, wenn Daten durch mehrere Verarbeitungsschritte transformiert werden müssen, bevor sie analysiert oder visualisiert werden können.


Beide Konzepte, Workflows und Pipelines, bieten mehrere Vorteile:

- **Automatisierung**: Einmal definierte Workflows können automatisch ausgeführt werden, was den manuellen Aufwand reduziert und die Effizienz erhöht.
- **Dokumentation**: Workflows dokumentieren die Abfolge der Verarbeitungsschritte, was die Nachvollziehbarkeit und Reproduzierbarkeit der Analyse verbessert.
- **Wiederverwendbarkeit**: Einmal erstellte Workflows können leicht angepasst und für ähnliche Analysen wiederverwendet werden.
- **Fehlerbehandlung**: Viele Workflow-Systeme bieten Mechanismen zur Fehlererkennung und -behandlung, was die Robustheit der Datenverarbeitung erhöht.
- **Skalierbarkeit**: Workflows können auf verschiedenen Systemen ausgeführt werden, von lokalen Rechnern bis hin zu Hochleistungsrechnern und Cloud-Umgebungen.

Hier sind einige verbreitete Workflow-Systeme und Tools zur Erstellung von Pipelines: 

- **Snakemake**: Ein Workflow-Management-System, das auf Python basiert und sich besonders für bioinformatische Analysen eignet.
- **Nextflow**: Ein weiteres beliebtes Workflow-Tool, das die Ausführung von verschiedenen Umgebungen unterstützt, einschließlich Cloud-Computing.
- **Galaxy**: Eine webbasierte Plattform, die es ermöglicht, Datenanalysen über eine grafische Benutzeroberfläche durchzuführen und Workflows zu erstellen, ohne dass Programmierkenntnisse erforderlich sind.

Es gibt aber auch einfache Workflow-Systeme für spezielle Anwendungsfälle, wie z.B. **OpenRefine** für die Datenbereinigung und -transformation.

Im Folgenden werden wir uns beispielhaft zwei dieser Tools genauer anschauen: Galaxy und OpenRefine.


### Galaxy

Die [Galaxy](https://galaxyproject.org/)-Plattform ist ein webbasiertes Workflow-System, das speziell für die Analyse von wissenschaftlichen Daten entwickelt wurde, primär im Bereich der Life-Sciences.
Galaxy bietet eine benutzerfreundliche grafische Oberfläche, die es Forschenden ermöglicht, komplexe Datenanalysen durchzuführen, ohne dass sie Programmierkenntnisse benötigen.
Die Plattform unterstützt eine Vielzahl von Datenformaten und Analysewerkzeugen, die in sogenannten "Tools" organisiert sind.

Galaxy ermöglicht es Nutzern, Workflows zu erstellen, indem sie verschiedene Tools miteinander verknüpfen.
Diese Workflows können gespeichert, geteilt und wiederverwendet werden, was die Zusammenarbeit und Reproduzierbarkeit von Analysen fördert.
Ein weiterer Vorteil von Galaxy ist die Möglichkeit, Analysen in einer Cloud-Umgebung durchzuführen, was die Skalierbarkeit und den Zugriff auf leistungsfähige Rechenressourcen erleichtert.

Es gibt ein einführendes [Tutorial für einen Workflow in Galaxy](https://training.galaxyproject.org/training-material/topics/introduction/tutorials/galaxy-intro-101-everyone/tutorial.html), der die Schritte aus unserem Iris-Datensatz-Beispiel automatisiert.
Die darin enthaltenen Arbeitsschritte und ihre Verknüpfung zu einem Workflow können in Galaxy direkt nachvollzogen und visualisiert werden:

![Galaxy Workflow](https://training.galaxyproject.org/training-material/topics/introduction/images/101_foreveryone_workflow_editor.png){width=70% alt="Galaxy Workflow"}

[Der Workflow selbst](https://training.galaxyproject.org/training-material/topics/introduction/tutorials/galaxy-intro-101-everyone/workflows/main_workflow.html), ist dabei exportierbar und kann in anderen Galaxy-Instanzen importiert und ausgeführt werden.

Da Galaxy webbasiert ist, ist keine Installation auf dem eigenen Rechner notwendig.
Daten können direkt im Browser hochgeladen und analysiert werden.
Allerdings benötigt das System einen Server, auf dem es läuft und einiges an Rechenleistung und Administration.
Daher werden Galaxy-Instanzen häufig von Institutionen für ihre Nutzer bereitgestellt.
Es gibt aber auch öffentliche Galaxy-Server, die von jedem genutzt werden können, z.B. [usegalaxy.org](https://usegalaxy.org/).


### OpenRefine

[OpenRefine](https://openrefine.org/) (früher Google Refine) ist ein Open-Source-Tool zur Datenbereinigung und -transformation.
Es bietet eine grafische Benutzeroberfläche, in der man große Datensätze importieren, bereinigen und untersuchen kann.
OpenRefine ist besonders nützlich für die Arbeit mit unstrukturierten oder semi-strukturierten Daten, wie z.B. CSV-Dateien, Excel-Tabellen oder JSON-Daten.
OpenRefine ermöglicht es Nutzern, Daten zu filtern, zu sortieren, zu gruppieren und zu transformieren.
Es unterstützt auch die Anwendung von regulären Ausdrücken und bietet eine Vielzahl von Erweiterungen, die zusätzliche Funktionalitäten bereitstellen.
Ein weiterer Vorteil von OpenRefine ist die Möglichkeit, Daten aus verschiedenen Quellen zu importieren und zu exportieren, was die Integration in bestehende Datenverarbeitungsprozesse erleichtert.



## Portierbarkeit



## Skalierbarkeit



Das klingt nach einer spannenden und wichtigen Einführung! Für eine erste Sitzung zur Datenverarbeitung im Rahmen eines FDM-Hochschulkurses (Forschungsdatenmanagement) könntest du die Inhalte so strukturieren, dass sie sowohl konzeptionell als auch praxisnah sind. Hier sind relevante Themenbereiche und Inhalte, die du abdecken könntest:

🧭 1. Überblick über Datenverarbeitung im FDM-Kontext
  - Was bedeutet Datenverarbeitung im Forschungsdatenmanagement?
  - Lebenszyklus von Forschungsdaten: Erhebung, Verarbeitung, Analyse, Archivierung, Publikation
  - Bedeutung von Reproduzierbarkeit und Nachvollziehbarkeit
🔄 2. Workflow-Systeme
  - Was sind Workflows und warum sind sie wichtig?
  - Beispiele: Snakemake, Nextflow, Apache Airflow
  - Vorteile: Automatisierung, Dokumentation, Wiederverwendbarkeit
  - Kurze Demo oder Visualisierung eines einfachen Workflows
    - bsp. galaxy
    - openrefine (für begrenzte anwendungen)

🧬 4. Pipelines
  - Was ist eine Datenpipeline?
  - Aufbau: Input → Verarbeitungsschritte → Output
  - Beispiel: Pipeline zur Genomdatenanalyse oder Bildverarbeitung
  - Tools: Snakemake, Luigi, DVC (Data Version Control)
🖥️ 5. Systemunabhängigkeit und Portabilität
  - Containerisierung: Docker, Singularity
  - Vorteile: Reproduzierbarkeit, einfache Weitergabe
  - Beispiel: Ein Dockerfile für eine Datenanalyseumgebung
📦 6. Datenformate und Standards
  - Offene Formate: CSV, JSON, HDF5, NetCDF
  - Metadatenstandards: Dublin Core, DataCite, schema.org
  - Bedeutung für Langzeitarchivierung und Interoperabilität
🧠 7. Best Practices & Tools
  - Versionskontrolle mit Git
  - Dokumentation mit Markdown, Jupyter Notebooks
  - Datenvalidierung und Qualitätssicherung
💬 8. Diskussion & Ausblick
  - Welche Tools nutzen die Studierenden bereits?
  - Welche Herausforderungen sehen sie in der Datenverarbeitung?
  - Ausblick auf weiterführende Themen: Datenbanken, Big Data, Machine Learning

9. Clustercomputing etc...






https://training.galaxyproject.org/training-material/topics/introduction/tutorials/galaxy-intro-101-everyone/tutorial.html
https://training.galaxyproject.org/training-material/topics/introduction/tutorials/galaxy-intro-101-everyone/workflows/main_workflow.html



# Galaxy 101 Workflow – Zusammenfassung

## 🎯 Ziel
Demonstration eines einfachen, reproduzierbaren Datenanalyse-Workflows mit Galaxy anhand des Iris-Datensatzes.

---

## 🧰 Workflow-Schritte

### 1. Datenimport
- **Tool**: `Upload Data`
- **Datei**: `iris.csv`
- **Ziel**: Laden des Iris-Datensatzes in Galaxy

### 2. CSV in tabellarisches Format umwandeln
- **Tool**: `csv_to_tabular`
- **Ziel**: Konvertierung der CSV-Datei in ein tabellarisches Format für weitere Verarbeitung

### 3. Entfernen der Kopfzeile
- **Tool**: `Remove beginning`
- **Parameter**: Entferne die erste Zeile
- **Ziel**: Entfernen der Spaltenüberschriften

### 4. Spalten extrahieren
- **Tool**: `Cut columns from a table`
- **Parameter**: Auswahl relevanter Spalten (z. B. Sepal Length, Petal Length, Species)
- **Ziel**: Reduktion auf relevante Daten

### 5. Gruppierung und Aggregation
- **Tool**: `Datamash`
- **Parameter**: Gruppieren nach Spezies, Berechnung von Mittelwerten
- **Ziel**: Statistische Analyse der Daten

### 6. Sortieren und Duplikate entfernen
- **Tool**: `Sort`, `Unique`
- **Ziel**: Aufbereitung der Daten für Visualisierung

### 7. Visualisierung
- **Tool**: `ggplot2`
- **Parameter**: Erstellen eines Scatterplots (z. B. Sepal vs. Petal Länge, farblich nach Spezies)
- **Ziel**: Grafische Darstellung der Daten

---

## 📦 Outputs
- Bereinigte und aggregierte Datentabellen
- Interaktive Visualisierungen (ggplot2-Plots)

---

## 🧠 Lernziele
- Nutzung von Galaxy als grafisches Workflow-System
- Verarbeitung tabellarischer Daten ohne Programmierung
- Erstellung und Wiederverwendung von Workflows
- Visualisierung von Daten direkt im Browser












## Zusammenfassung

:::::: keypoints

- 
  
::::::::::::::::


:::::::::: challenge

# Einordnung im Datenlebenszyklus

![*In welchen Phasen im Datenlebenszyklus sehen sie obige Punkte als besonders wichtig an?*](https://uni-tuebingen.de/fileadmin/_processed_/6/b/csm_FDM_Lebenszyklus_d1353825c4.png){width=40% alt="Datenlebenszyklus"}

::: solution

## Antwort

Das Wissen um die **digitale Repräsentation von Informationen** ist immer dann zentral, wenn Daten importiert oder exportiert werden, um sicherzustellen, dass die Daten korrekt übertragen und gespeichert werden.

- **Planung**: Festlegung von Datenformaten und -strukturen
- **Erhebung**: Korrekte Interpretation von Daten
- **Archivierung**: Export von Daten in geeigneten Formaten
- **Nachnutzung**: korrekter Datenimport und -export

:::

::::::::::::::::::::



:::::::::::::::: instructor

## Aufgaben

### Sitzungsaufgaben

- 

### Sitzungsfragen

- 

:::::::::::::::::::::::::::

