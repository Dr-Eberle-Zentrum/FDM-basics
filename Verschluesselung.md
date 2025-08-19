---
title: 'Verschlüsselung'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions 

- Wofür wichtig?
- Wie gehts?
- Wann einsetzen?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Einsatzgebiete von Verschlüsselung
- Grundprinzipien der Datenverschlüsselung
- Verschlüsselung von Daten in der Praxis

::::::::::::::::::::::::::::::::::::::::::::::::


Verschlüsselung ist ein zentrales Thema beim Arbeiten mit und Versenden/Speichern von Daten, insbesondere wenn es um den Schutz sensibler Informationen geht. 
Im Folgenden werden wir uns mit den Grundlagen der Datenverschlüsselung befassen und deren Anwendung in verschiedenen Phasen des Datenlebenszyklus untersuchen.

## Allgegenwärtig

Schon in unserem alltäglichen Leben begegnen uns Verschlüsselungstechniken, oftmals ohne dass wir es bewusst wahrnehmen.
Hier ein paar Beispiele:

- *`https://` in URLs*: Das "s" steht für "secure" und zeigt an, dass die Datenübertragung zwischen dem Browser und der Website verschlüsselt stattfindet.
- *Ende-zu-Ende-Verschlüsselung* in Messaging-Apps wie WhatsApp oder Signal: Hierbei werden Nachrichten so verschlüsselt, dass nur der Absender und der Empfänger sie lesen können.
- *Verschlüsselung von E-Mails*: Viele E-Mail-Dienste bieten die Möglichkeit, E-Mails zu verschlüsseln, um den Inhalt vor unbefugtem Zugriff zu schützen. Ansonsten werden diese im Klartext übertragen, analog zu einer Postkarte.
- *Verschlüsselung von Dateien*: Betriebssysteme wie Windows und macOS bieten integrierte Funktionen zur Verschlüsselung von Dateien und Ordnern, um sensible Daten zu schützen.
- *Passwortmanager*: Diese speichern Passwörter verschlüsselt, sodass sie sicher aufbewahrt werden können.
- ...

## Grundlagen der Datenverschlüsselung

Datenverschlüsselung ist ein Prozess, bei dem Informationen in eine Form umgewandelt werden, die für unbefugte Personen unlesbar ist.
Die Verschlüsselung erfolgt in der Regel durch mathematische Algorithmen, die einen sogenannten "Schlüssel" (i.d.R. eine Zahl; ggf. basierend auf einem Passwort) verwenden, um die Daten zu verschlüsseln und zu entschlüsseln.
Die Verschlüsselung kann auf verschiedene Arten erfolgen, abhängig von den Anforderungen an Sicherheit und Leistung.

Die wichtigsten Konzepte sind:

- **Symmetrische Verschlüsselung**: Hierbei wird derselbe Schlüssel zum Verschlüsseln und Entschlüsseln der Daten verwendet. 
Diese Art der Verschlüsselung ist in der Regel schneller und effizienter, erfordert jedoch, dass der Schlüssel sicher zwischen den Parteien ausgetauscht wird.
Dies ist jedoch problematisch, wenn die Parteien sich zuvor nicht kennen, wie das z.B. beim Webseitenzugriff der Fall ist.
- **Asymmetrische Verschlüsselung**: Hierbei gibt es zwei Schlüssel: einen öffentlichen Schlüssel, der zum Verschlüsseln der Daten verwendet wird, und einen privaten (geheimen) Schlüssel, der zum Entschlüsseln dient.
Diese Methode ermöglicht es, Daten sicher zu übertragen, denn der öffentliche Schlüssel kann frei verteilt werden, während der private Schlüssel geheim bleibt.
Dies wird z.B. beim Aufbei einer verschlüsselten Webseitenkommunikation verwendet.
- **Hash-Funktionen**: Diese erzeugen aus den Daten einen eindeutigen Hash-Wert, der nicht umkehrbar ist. 
Hash-Funktionen werden häufig zur Überprüfung der Integrität von Daten verwendet (z.B. SHA-256).
Da der Hash-Wert i.d.R. viel kleiner ist als die ursprüngliche Information, können damit einige Validierungstricks ohne viel Datenvolumen vorgenommen werden.

Hier noch ein paar mehr Details.


### Symmetrische Verschlüsselung

Wenn sie z.B. eine Datei verschlüsseln oder eine verschlüsselte ZIP oder PDF Datei erhalten haben, müssen sie das korrekte Passwort eingeben, um die Daten wieder lesen zu können.
Hierbei kommt symmetrische Verschlüsselung zum Tragen, d.h. beim Verschlüsselungsprozess wurde ein Passwort X festgelegt, und beim Entschlüsseln muss das gleiche Passwort X wieder angeben werden.

Derartige Verschlüsselungstechniken wurden auch schon lange vor dem "Computerzeitalter" in mechanischer Form oder in einfachen Buchstabenverschiebesystemen verwendet.
Aktuelle komplexere mathematische Ansätze erhöhen die Schwierigkeit, mit der der Kodierungsansatz identifiziert und neutralisiert werden kann.
Das Grundkonzept bleibt jedoch das gleiche.

Und das Grundproblem auch, denn wenn ich symmetrische Verschlüsselung bei der *Übertragung* von Information verwenden will, müssen beide Kommunikationspartner den Schlüssel kennen!
Hierzu müssen sie sich i.d.R. treffen, um diesen persönlich auszutauschen oder ein anderer (sicherer, d.h. verschlüsselter) Kommunikationsweg muss hierfür verwendet werden.

Dies ist aber bei vielen Übertragungen nicht möglich.
So auch bei der allgegenwärtigen Kommunikation von ihrem Browser (Computer) mit einem Webserver, wenn sie sich z.B. diese Webseite hier anschauen.
Wenn die Datenübertragung verschlüsselt stattfinden soll, ist dies zunächst mit symmetrischen Verschlüsselungskonzepten nicht möglich.
Hier kommt die asymmetrische Verschlüsselung ins Spiel.

### Asymmetrische Verschlüsselung

Die asymmetrische Verschlüsselung beruht auf mathematischen Verfahren, die es ermöglichen, dass für das Verschlüsseln und das Entschlüsseln verschiedene "Passwörter", also Schlüssel, verwendet werden.

Vereinfacht gesagt funktioniert das ganze auf einem *"Empfängerprinzip"*, d.h. der Empfänger ermöglicht es, das ihm kodierte Nachrichten zugesendet werden, die nur er öffnen/lesen kann.

Hierfür gibt der Empfänger seinen "Kodierungsschlüssel" öffentlich und für jeden zugreifbar bekannt.
Wenn jemand diesem nun eine geheime Nachricht schicken will, dann kann diese Nachricht mit dem "Kodierungsschlüssel" unleserlich gemacht und versand werden.
Niemand im Versandweg (und auch nicht der Sender!) kann die Nachricht lesen.
Der Empfänger hat nun einen zweiten, geheimen Schlüssel, seinen "Dekodierungsschlüssel", mit Hilfe dessen er die unleserliche erhaltene Nachricht wieder in seine Ursprungsform zurückversetzen kann.
Solange der Empfänger seinen "Dekodierungsschlüssel" geheim hält, ist die Kommunikation sicher.
Daher wird diese Art Verschlüsselung auch *public-key-Verschlüsselung* genannt.


Bei der Webseitenkommunikation kommt nun genau soetwas zum Tragen. 
Wenn ihr Browser seine (unverschlüsselte) erste Anfrage an den Webserver (= Empfänger) schickt, sendet dieser erst einmal seinen öffentlichen "Kodierungsschlüssel" zurück.
Mit diesem kann ihr Browser nun dem Webserver eine geheime Nachricht schicken, die nur dieser lesen kann.
Und dies kann z.B. ein Schlüssel für eine (technisch einfachere) symmetrische Kommunikation sein, da wir ja nun über einen sicheren Kommunikationskanal verfügen.
Im Anschluß erfolgt die weitere verschlüsselte Kommunikation symmetrisch, da ja nun sowohl ihr Browser wie auch der Webserver den Schlüssel der symmetrischen Kommunikation kennen.


Der Ablauf ist nochmals in folgender Grafik illustriert.

![Ablauf des Aufbaus einer HTTPS Verschlüsselung. Hierbei wird mittles public-key-Verschlüsselung ein geheimer Schlüssel an den Webserver gesendet, der eine anschliessende schnelle "symmetrische" Verschlüsselung ermöglicht. (Quelle: [tiptopsecurity.com](https://tiptopsecurity.com/how-does-https-work-rsa-encryption-explained/))](fig/https-dialog.png){width=50%, alt="Ablauf der HTTPS-Verschlüsselung"}



## Zusammenfassung

::::::::::::::::::::::::::::::::::::: keypoints 

- 

::::::::::::::::::::::::::::::::::::::::::::::::




:::::::::: challenge

# Einordnung im Datenlebenszyklus

![*In welchen Phasen im Datenlebenszyklus sehen sie obige Punkte als besonders wichtig an?*](https://uni-tuebingen.de/fileadmin/_processed_/6/b/csm_FDM_Lebenszyklus_d1353825c4.png){width=40% alt="Datenlebenszyklus"}

::: solution

## Antwort

Das Wissen um **Verschlüsselung** ist immer dann zentral, 
wenn Daten verschickt oder auf unsicheren Datenträgern gespeichert werden.
Auch strenge Datenschutzbestimmungen können Verschlüsselung notwendig machen.

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


### Sitzungsfragen

- 

### Anwendungsaufgaben



:::::::::::::::::::::::::::
