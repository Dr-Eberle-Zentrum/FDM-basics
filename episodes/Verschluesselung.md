---
title: 'Verschlüsselung'
teaching: 15
exercises: 5
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

::::::::::::: challenge

## Was kann schief gehen?

Gehen wir davon aus, dass sie mittels HTTPS eine Webseite besuchen und der oben beschriebene Ablauf funktioniert hat.
Allerdings stellen sie kurz darauf fest, dass der angezeigte Inhalt gar nichts mit dem erwarteten Inhalt zu tun hat.
Was könnte hier passiert sein?

:::: solution

## Antwort

Sie haben zwar eine verschlüsselte Verbindung zu einem Webserver aufgebaut, aber dieser Webserver ist nicht der, den sie erwartet haben.
Dies kann z.B. passieren, wenn sie auf einen Phishing-Link geklickt haben, der sie zu einer gefälschten Webseite geleitet hat, die vorgibt, die echte Webseite zu sein.
In diesem Fall ist die Verbindung zwar verschlüsselt, aber der Inhalt stammt nicht von der erwarteten Quelle.

Dies ist ein Beispiel dafür, dass Verschlüsselung allein nicht ausreicht, um die Sicherheit zu gewährleisten.
Es ist auch wichtig, die Identität des Kommunikationspartners zu überprüfen, z.B. durch die Verwendung von Zertifikaten, die von vertrauenswürdigen Zertifizierungsstellen ausgestellt wurden.
Diese Zertifikate bestätigen die Identität des Webservers und stellen sicher, dass sie tatsächlich mit dem richtigen Server kommunizieren.
Wenn das Zertifikat nicht gültig ist oder nicht von einer vertrauenswürdigen Zertifizierungsstelle ausgestellt wurde, wird ihr Browser sie warnen und die Verbindung abbrechen.
Dies ist ein wichtiger Sicherheitsmechanismus, um sicherzustellen, dass sie nicht Opfer von Phishing-Angriffen oder anderen Betrugsversuchen werden.

::::::::::::::::

:::::::::::::::::::::::::::::::


Asymmetrische public-key Verschlüsselung ist also ein zentrales Konzept, um eine sichere Kommunikation im Internet zu ermöglichen.
Sie kommt neben der Webseitenkommunikation auch bei anderen Anwendungen zum Einsatz, wie z.B. bei

- E-Mail-Verschlüsselung (PGP) 
- Digitale Signaturen (z.B. für Software-Downloads)
- Sicheren Dateiübertragungen (z.B. SFTP)
- SSH-Zugriff auf Server
- VPN-Verbindungen
- ... und vielen anderen Anwendungen, bei denen eine sichere Kommunikation erforderlich ist.

### Hashing

Hashing ist ein Verfahren, bei dem eine beliebige Datenmenge (z.B. eine Datei oder ein Text) in einen festen, eindeutigen Hash-Wert fester Länge umgewandelt wird.
Dieser Hash-Wert dient als Fingerabdruck der Daten und kann verwendet werden, um die Integrität der Daten zu überprüfen.
Dies ist deshalb möglich, da schon minimale Abweichungen einen anderen Hash-Wert erzeugen, so dass eine Manipulation der Daten oder Fehler sofort erkannt werden können.

Hierbei ist der zentrale Trick, dass die Hash-Funktion nicht umkehrbar ist, d.h. es ist nicht möglich, aus dem Hash-Wert die ursprünglichen Daten wiederherzustellen.
Als einfachste Analogie kann man die Modulo-Operation verwenden, die den Rest bei einer Ganzzahldivision berechnet.
Bei Modulo 10 würde z.B. 12 zu 2, 22 zu 2 und 32 zu 2 werden.
Alle Hash-Werte sind einstellige Ziffern, aber ob diese aus einer 13- oder zwei-stelligen Zahl stammen, ist nicht mehr erkennbar.
Ausserdem zeigt das Beispiel, dass es mehrere Zahlen geben kann, die den gleichen Hash-Wert ergeben (Kollisionssicherheit).

So können z.B. Passwörter in Datenbanken nicht im Klartext gespeichert werden, sondern nur deren Hash-Wert.
Damit kann bei der Anmeldung eines Nutzers das eingegebene Passwort ebenfalls gehasht und mit dem gespeicherten Hash-Wert verglichen werden, ohne dass das Passwort selbst gespeichert werden muss.
Hierbei ist es theoretisch möglich, dass zwei verschiedene Passwörter den gleichen Hash-Wert erzeugen (Kollision), aber dies ist bei modernen Hash-Funktionen extrem unwahrscheinlich.

Somit sind Hash-Funktionen ein wichtiges Werkzeug zur Sicherstellung der Datenintegrität und werden in vielen Anwendungen eingesetzt, wie z.B. bei der Überprüfung von Software-Downloads, der Speicherung von Passwörtern oder der digitalen Signatur von Dokumenten.

Bei der oben beschriebenen HTTPS-Kommunikation kommen u.a. auch Hash-Funktion zum Tragen, um die Integrität der übertragenen Daten zu überprüfen, d.h. um sicherzustellen, dass der Empfänger tatsächlich die Daten erhalten hat und korrekt entschlüsseln konnte.

Für häufig verwendete Hash-Funktionen, wie z.B. SHA-256 oder SHA-512, bieten die meisten Programmiersprachen und Betriebssysteme ([Anleitungen](https://www.dell.com/support/kbdoc/de-de/000130826/identifizieren-des-sha-256-hash-einer-datei-f%C3%BCr-sicherheitsanwendungen)) bereits fertige Implementierungen an, die einfach verwendet werden können, um z.B. schnell die Integrität eines wichtigen Dateidownloads zu überprüfen.
Außerdem gibt es viele Online-Tools, die Hash-Werte für beliebige Daten oder kleinere Dateien berechnen können.


## Dateiverschlüsselung

Neben den beschriebenen Einsatzgebiet der Kommunikationsverschlüsselung, werden häufig auch einzelne Dateien verschlüsselt.
Dies kann z.B. notwendig sein, um sensible Daten zu schützen, die auf einem Computer oder einem Datenträger gespeichert sind oder um Daten zu übertragen, die nicht für jedermann zugänglich sein sollen.
Hierbei kommen in der Regel symmetrische Verschlüsselungsverfahren zum Einsatz, bei denen ein Passwort oder ein Schlüssel verwendet wird, um die Daten zu verschlüsseln und zu entschlüsseln.

Die Verschlüsselung von Dateien kann auf verschiedene Arten erfolgen, z.B. durch die Verwendung von speziellen Software-Tools oder durch die Nutzung von Betriebssystemfunktionen.
Einige gängige Tools und Methoden zur Dateiverschlüsselung sind:

- **GnuPG**: Ein Open-Source-Tool zur Verschlüsselung von Dateien und E-Mails, das auf dem OpenPGP-Standard basiert.
- **VeraCrypt**: Ein Open-Source-Tool zur Verschlüsselung von Festplatten, USB-Sticks und anderen Datenträgern, das auf dem TrueCrypt-Projekt basiert.
- **7-Zip**: Ein Open-Source-Dateikomprimierungstool, das auch die Möglichkeit bietet, Dateien mit AES-256-Verschlüsselung zu verschlüsseln.

Auch bieten manche Dateiformate wie `PDF` oder `ZIP` die Möglichkeit, Dateien direkt beim Erstellen zu verschlüsseln.
Hierbei wird in der Regel ein Passwort abgefragt, das zum Entschlüsseln der Datei benötigt wird.


### Cloudspeichernutzung

Gerade beim **Speichern von sensiblen Daten in der Cloud**, bietet es sich an, die Daten vor dem Hochladen zu verschlüsseln, um sicherzustellen, dass nur autorisierte Personen Zugriff auf die Daten haben.
Denn je nach Cloud-Anbieter und dessen Sicherheitsvorkehrungen und AGBs, können unbefugte Dritte möglicherweise auf die Daten zugreifen, wenn sie nicht verschlüsselt sind.

Hierbei können die oben genannten Tools verwendet werden, um die Daten vor dem Hochladen zu verschlüsseln.
Es ist jedoch wichtig, sicherzustellen, dass das Passwort oder der Schlüssel für die Verschlüsselung sicher aufbewahrt wird, da sonst der Zugriff auf die Daten verloren gehen kann.

## Verschlüsselung von Datenträgern

Neben der Verschlüsselung einzelner Dateien kann auch der gesamte Datenträger verschlüsselt werden, um alle darauf gespeicherten Daten zu schützen.
Dies ist besonders wichtig, wenn sensible Daten auf einem Laptop oder einem USB-Stick gespeichert sind, der verloren gehen oder gestohlen werden könnte.
Die Verschlüsselung des gesamten Datenträgers kann verhindern, dass unbefugte Personen auf die Daten zugreifen können, selbst wenn sie physisch Zugriff auf den Datenträger haben.
Hierbei kommen in der Regel symmetrische Verschlüsselungsverfahren zum Einsatz, bei denen ein Passwort oder ein Schlüssel verwendet wird, um die Daten zu verschlüsseln und zu entschlüsseln.

## Worst Case

### Unverschlüsselte Daten

Wenn sie sensible Daten auf einem Computer oder einem Datenträger speichern, der nicht verschlüsselt ist, besteht das Risiko, dass unbefugte Personen auf diese Daten zugreifen können.
Dies kann zu Datenverlust, Identitätsdiebstahl oder anderen schwerwiegenden Konsequenzen führen.

### Unzureichende Verschlüsselung

Wenn sie eine unzureichende Verschlüsselung verwenden, z.B. ein schwaches Passwort oder einen veralteten Verschlüsselungsalgorithmus, können unbefugte Personen möglicherweise auf die Daten zugreifen.
Es ist wichtig, starke Passwörter zu verwenden und aktuelle Verschlüsselungsalgorithmen zu verwenden, um die Sicherheit der Daten zu gewährleisten.
Ein schwaches Passwort kann leicht erraten oder durch Brute-Force-Angriffe geknackt werden, was die Sicherheit der verschlüsselten Daten gefährdet.

### Verschlüsselung als Angriff

Es gibt auch Angriffe, bei denen die Verschlüsselung selbst als Waffe eingesetzt wird.
Ein Beispiel hierfür ist die sogenannte "Ransomware", bei der Angreifer die Daten eines Opfers verschlüsseln und dann ein Lösegeld verlangen, um den Schlüssel zur Entschlüsselung bereitzustellen.
In solchen Fällen ist es wichtig, regelmäßige Sicherungskopien der Daten zu erstellen, um im Falle eines Angriffs die Daten wiederherstellen zu können.
Derartige Angriffe können verheerende Auswirkungen sowohl auf Unternehmen als auch auf Einzelpersonen haben, da sie den Zugriff auf wichtige Daten und Systeme blockieren und erhebliche finanzielle Verluste verursachen können.

### Verschlüsselung vergessen

Wenn sie eine Datei oder einen Datenträger verschlüsseln, aber das Passwort oder den Schlüssel vergessen, können sie möglicherweise nicht mehr auf die Daten zugreifen.
Dies kann zu einem dauerhaften Datenverlust führen, insbesondere wenn keine Sicherungskopien der Daten vorhanden sind.
Es ist daher wichtig, Passwörter und Schlüssel sicher zu speichern und regelmäßig Sicherungskopien der verschlüsselten Daten zu erstellen.

Gerade bei der Verschlüsselung von Datenträgern ist es wichtig, dass sie sich das Passwort gut merken oder es an einem sicheren Ort aufbewahren.
Hierbei kann ein Passwortmanager helfen, der Passwörter sicher speichert und verwaltet.

### Quantencomputer

Die Sicherheit der meisten aktuellen Verschlüsselungsverfahren basiert auf der Annahme, dass bestimmte mathematische Probleme für klassische Computer schwer zu lösen sind.
Allerdings könnte die Entwicklung von Quantencomputern diese Annahme in Frage stellen.
Quantencomputer können bestimmte mathematische Probleme viel schneller lösen als klassische Computer, was bedeutet, dass sie in der Lage sein könnten, viele der derzeit verwendeten Verschlüsselungsalgorithmen zu knacken.
Dies könnte zu einem Paradigmenwechsel in der Kryptographie führen, da neue, quantensichere Verschlüsselungsalgorithmen entwickelt werden müssen, um die Sicherheit der Daten zu gewährleisten.
Es ist jedoch wichtig zu beachten, dass Quantencomputer noch in der Entwicklungsphase sind und es noch einige Jahre dauern könnte, bis sie in der Lage sind, aktuelle Verschlüsselungsverfahren zu gefährden.
In der Zwischenzeit ist es wichtig, weiterhin starke Verschlüsselungsalgorithmen zu verwenden und regelmäßig Sicherheitsupdates durchzuführen, um die Sicherheit der Daten zu gewährleisten.

Die Wissenschaftliche Arbeitsgruppe Nationaler Cyber-Sicherheitrat schätzt in ihrem [Impulspapier "Quantencomputer und ihr Einfluß auf die Cybersicherheit"](https://www.forschung-it-sicherheit-kommunikationssysteme.de/dateien/forschung/2024-03-impulspapier-quanten-cybersicherheit.pdf) (März 2024) symmetrische Verschlüsselungsverfahren wie AES-256 als "quantensicher" ein, da sie auch von Quantencomputern nicht in akzeptabler Zeit geknackt werden können.
Allerdings liefert sie auch dringende Empfehlungen, dass asymmetrische Verschlüsselungsverfahren wie RSA und ECC in den nächsten Jahren auf quantensichere Verfahren umgestellt werden sollten.


## Passwortmanager

Ein Passwortmanager ist ein Tool, das hilft, Passwörter sicher zu speichern und zu verwalten.
Er kann auch dabei helfen, starke Passwörter zu generieren und automatisch in (Web)Anwendungen einzufügen.
Dies ist besonders nützlich, um die Sicherheit der Passwörter zu erhöhen und das Risiko von Passwortdiebstahl zu verringern, da so deutlich komplexere Passwörter verwendet werdeb können, die schwer zu erraten sind.


In Webbrowsern gibt es mittlerweile viele integrierte Passwortmanager, die Passwörter für Websites speichern und automatisch ausfüllen können.
Es gibt aber auch eigenständige Passwortmanager, die zusätzliche Funktionen bieten, wie z.B.

- die Möglichkeit, Passwörter für verschiedene Anwendungen und Dienste zu speichern,
- die Synchronisierung von Passwörtern über verschiedene Geräte hinweg,
- die Generierung von starken Passwörtern,
- die Möglichkeit, Passwörter zu teilen oder gemeinsam zu nutzen,
- die Überprüfung der Sicherheit von Passwörtern und
- die Möglichkeit, Passwörter zu kategorisieren und zu organisieren.

Einige beliebte Passwortmanager sind:

- **Bitwarden**: Ein Open-Source-Passwortmanager, der eine kostenlose Version mit vielen Funktionen anbietet.
Er bietet eine benutzerfreundliche Oberfläche und die Möglichkeit, Passwörter zu generieren, zu speichern und automatisch auszufüllen.
- **KeePass**: Ein Open-Source-Passwortmanager, der lokal auf dem Computer installiert wird und eine sichere Speicherung von Passwörtern ermöglicht.
Er bietet viele Funktionen, wie z.B. die Möglichkeit, Passwörter zu generieren, zu speichern und zu organisieren.
KeePass ist besonders beliebt bei Nutzern, die Wert auf Datenschutz und Sicherheit legen, da die Passwörter lokal gespeichert werden und nicht in der Cloud.
- **1Password**: Ein kostenpflichtiger Passwortmanager, der eine benutzerfreundliche Oberfläche und viele Funktionen bietet, wie z.B. die Möglichkeit, Passwörter zu teilen und gemeinsam zu nutzen.
- **LastPass**: Ein beliebter Passwortmanager, der sowohl eine kostenlose als auch eine kostenpflichtige Version anbietet.
Er bietet viele Funktionen, wie z.B. die Möglichkeit, Passwörter zu generieren, zu speichern und automatisch auszufüllen.
- **Passbolt**: Ein Open-Source-Passwortmanager, der speziell für Teams und Unternehmen entwickelt wurde. 
Er bietet Funktionen wie die gemeinsame Nutzung von Passwörtern, die Verwaltung von Benutzerrechten und die Integration in verschiedene Anwendungen.


::::::::::: testimonial

Allerdings muss der Passwortmanager selbst sicher sein, da er die sensibelsten Informationen über sie enthält.
Daher ist es wichtig, einen vertrauenswürdigen Passwortmanager zu wählen und sicherzustellen, dass er starke Verschlüsselungstechniken verwendet, um die gespeicherten Passwörter zu schützen
und dass er regelmäßig aktualisiert wird, um Sicherheitslücken zu schließen.

Es ist auch wichtig, ein starkes Master-Passwort für den Passwortmanager zu wählen, da dieses Passwort der Schlüssel zu allen anderen Passwörtern ist.
Ein schwaches Master-Passwort kann dazu führen, dass unbefugte Personen Zugriff auf den Passwortmanager und damit auf alle gespeicherten Passwörter erhalten.
Daher sollte das Master-Passwort lang, komplex und einzigartig sein, um die Sicherheit des Passwortmanagers zu gewährleisten und das Risiko von Passwortdiebstahl zu minimieren.
Ggf. bietet es sich an, das Master-Passwort ebenfalls in einem Passwortmanager einer Person ihres Vertrauens zu speichern, um es nicht zu vergessen (und vice versa).

:::::::::::::::::::::::::

## Zusammenfassung

::::::::::::::::::::::::::::::::::::: keypoints 

- Verschlüsselung ist ein zentrales Konzept zum Schutz sensibler Daten.
- Symmetrische und asymmetrische Verschlüsselung sind die beiden Hauptarten der Datenverschlüsselung.
- Public-Key-Verschlüsselung ermöglicht eine sichere Kommunikation, ohne dass ein geheimer Schlüssel vorher ausgetauscht werden muss.
- Hash-Funktionen sind wichtig für die Integrität von Daten.
- Die Verschlüsselung von Dateien und Datenträgern ist wichtig, um sensible Daten zu schützen.
- Quantencomputer könnten die Sicherheit aktueller Verschlüsselungsverfahren in Frage stellen, aber symmetrische Verfahren wie AES-256 gelten als quantensicher.
- Passwortmanager helfen, Passwörter sicher zu speichern und zu verwalten und vor allem **starke Passwörter zu verwenden**.


::::::::::::::::::::::::::::::::::::::::::::::::




:::::::::: challenge

# Einordnung im Datenlebenszyklus

![*In welchen Phasen im Datenlebenszyklus sehen sie obige Punkte als besonders wichtig an?*](https://uni-tuebingen.de/fileadmin/_processed_/6/b/csm_FDM_Lebenszyklus_d1353825c4.png){width=40% alt="Datenlebenszyklus"}

::: solution

## Antwort

Das Wissen um **Verschlüsselung** ist immer dann zentral, 
wenn Daten verschickt oder auf unsicheren Datenträgern gespeichert werden.
Auch strenge Datenschutzbestimmungen können Verschlüsselung notwendig machen.

- **Erhebung**: Sensible Daten müssen verschlüsselt werden
- **Analyse**: Falls Daten geteilt werden, müssen Schlüssel sicher ausgetauscht werden
- **Nachnutzung**: Bereitstellung von sensiblen, verschlüsselten Daten nach Absprache

:::

::::::::::::::::::::



:::::::::::::::: instructor

## Aufgaben


### Sitzungsfragen

- 

### Anwendungsaufgaben



:::::::::::::::::::::::::::
