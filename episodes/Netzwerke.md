---
title: "Netzwerke"
teaching: 30
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions 

- Router?
- Ports?
- Firewall?
- Logging?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Wie funktioniert das Internet?
- Wie finden die Daten ihr Ziel?
- Wie kann ich mich schützen?
- Wer sieht was ich im Internet mache?

::::::::::::::::::::::::::::::::::::::::::::::::


Die Verwendung des Internets ist heute allgegenwärtig. 
Doch wie funktioniert das Internet eigentlich? 
Wie finden die Daten ihren Weg? 
Und wie kann ich mich schützen?
Auf diese und ähnliche Fragen wollen wir im Folgenden eingehen.


## Computernetzwerke und das Internet

Ein Computernetzwerk ist eine Ansammlung von Rechnern, die miteinander verbunden sind und Informationen austauschen können.
Hierbei ist die Art der Verbindung entscheidend und diese kann sowohl kabelgebunden (z.B. via elektrischem oder Glasfaserleiter) als auch drahtlos (z.B. via Funk, Satelit, Infrarot, ...) erfolgen.
Kabelgebundene Verbindungen sind in der Regel schneller und sicherer, während drahtlose Verbindungen flexibler sind und keine physische Verbindung benötigen.
Daher sind drahtlose Verbindungen insbesondere für mobile Geräte wie Smartphones und Tablets von Bedeutung wohingegen kabelgebundene Verbindungen in Büroumgebungen oder Rechenzentren vorherrschen bzw. Knotenpunkte im Internet miteinander verbinden.

Das Internet selbst ist ein weltweites Netzwerk von Computernetzwerken, das auf dem Internetprotokoll (IP) basiert.
Das Internetprotokoll ist ein Regelwerk, das den Datenaustausch zwischen Rechnern regelt und dabei die Daten in Pakete aufteilt, die über das Netzwerk verschickt werden.
Die Pakete enthalten neben den eigentlichen Daten auch Informationen über den Absender und Empfänger, sodass die Pakete ihren Weg durch das Netzwerk finden können.
Die Pakete werden dabei von Routern weitergeleitet, die die Pakete anhand der Empfängeradresse an den nächsten Knotenpunkt im Netzwerk weiterleiten.
Die Knotenpunkte sind dabei die Verbindungen zwischen den einzelnen Netzwerken und können sowohl kabelgebunden als auch drahtlos sein.
Da Satelit, Funk und andere drahtlose Verbindungen eine (relativ) geringere Bandbreite und "Transportgeschwindigkeit" haben, werden diese in der Regel nur für die letzte Meile verwendet, also die Verbindung zwischen dem Endgerät und dem nächsten Knotenpunkt.
Zwischen den Knotenpunkten werden in der Regel Glasfaserleitungen verwendet, die eine hohe Bandbreite und Geschwindigkeit haben.
Um die Kommunikation zwischen Kontinenten und Ländern zu ermöglichen, werden unterseeische Kabel verwendet, welche im Folgenden visualisiert sind.

[![Unterseeische Kabel verbinden Kontinente und Inseln (Quelle: [TeleGeography](https://www.submarinecablemap.com/))](fig/submarinecablemap.png){width=100%, alt="Unterseeische Kabel"}](https://www.submarinecablemap.com/)

::::: testimonial

# Lebensadern des Internets

Unterseeische Kabel sind die Lebensadern des Internets.
Das diese dennoch anfällig sind, zeigt der Schiffsankerschaden 2019 und der Vulkansausbruch 2022 in Tonga, welche die Kommunikation des Inselstaates mit der Außenwelt unterbrachen.

Die folgenden beiden Artikel geben exemplarisch einen kurzen Einblick in die Bedeutung und Funktionsweise von Unterseekabeln:

- [Tonga surft nicht mehr - Süddeutsche](https://www.sueddeutsche.de/wirtschaft/tonga-internet-kabel-glasfaser-blackout-ausfall-1.4302776)
- [So werden Unterseekabel repariert - Süddeutsche](https://www.sueddeutsche.de/panorama/vulkanausbruch-tonga-unterseekabel-internetverbindung-1.5511500)

:::::::::::::::::


Damit die Datenpakete ihren Weg durch das Netzwerk finden, benötigen sie eine Adresse, die den Weg durch das Netzwerk beschreibt.
Diese Adresse ist die IP-Adresse, die aus einer Kombination von Zahlen und Punkten besteht.
Zum Beispiel hat der Server (Computer), der die Webseite der Universität Tübingen bereitstellt, die IP-Adresse `134.2.5.1`.
Allerdings gibt es mehr Geräte im Internet als es IP-Adressen gibt, sodass die IP-Adressen in der Regel dynamisch vergeben werden (sich also immer wieder ändern) bzw. innerhalb eines Netzwerkes lokal sind.

Um sich den Kommunikationsprozess und die IP-Lokalität vorzustellen, hier eine kleine Analogie:

- Sie machen Urlaub in einem Hotel im Zimmer Nummer 5.
- Wenn Sie eine Postkarte verschicken möchten, schreiben Sie die Zieladresse auf die Postkarte.
- Diese geben sie beim Portier in Zimmer Nummer 1 ab, der die Postkarte an den Empfänger weiterleitet.
- Hierzu verlässt der Portier das Hotel und gibt die Postkarte an den Briefträger, der diese ins Briefzentrum bringt.
- Im Briefzentrum wird die Postkarte an ein Verteilzentrum weitergeleitet, welches die Postkarte an ein Verteilzentrum in der Nähe des Empfängers weiterleitet.
- Von dort gehts ins entsprechende Briefzentrum und von dort zum Empfänger.

Das bedeutet, dass für die Weiterleitung der Postkarte mehrere Personen und Einrichtungen beteiligt sind, die die Postkarte anhand der Adresse weiterleiten, obwohl die meisten von ihnen den Zielort bzw. dessen Lokalisierung gar nicht kennen (Sie selbst, der Portier, der lokale Briefträger, ...).

Wenn sie nun Post empfangen möchten, sehen sie an obiger Analogie, dass es nicht reicht, dass die Antwort an sie an Zimmer Nummer 5 adressiert wird.
Ohne die Hoteladresse wird sie die Antwort nicht erreichen.
Je nach Distanz bedarf es auch noch der Information über die Stadt oder sogar das Land, in dem das Hotel liegt.
Zudem bedarf es des lokalen Portiers, der die Postkarte in Zimmer 1 entgegennimmt und an sie ins Zimmer 5 weiterleitet.

Ähnliches gilt auch für das Internet:

- Ihr Computer, an dem sie eine Nachricht verschicken, hat eine IP-Adresse (Zimmernummer) innerhalb ihres lokalen Netzwerkes (Hotel).
- Um eine Nachricht ins Internet zu senden, benötigen sie einen Router (Portier), der die Nachricht an den nächsten Knotenpunkt weiterleitet.
- Hierzu muss der Router sich mit dem Internet verbinden (Hotel verlassen).
Diese Verbindung wird durch einen Internet Service Provider (ISP) bereitgestellt, der ihrem Router eine IP-Adresse zuweist (Hoteladresse).
- Diese ist eine andere als die IP-Adresse des Routers innerhalb ihres lokalen Netzwerkes!
Der Portier lebt also in zwei Welten und hat zwei Adressen: eine innerhalb des Hotels, um für Gäste erreichbar zu sein (Zimmer 1), und eine außerhalb des Hotels (Hoteladresse), um die Post des Hotels zentral entgegen nehmen zu können.

::::::::::: testimonial

# Wie funktioniert das Internet?

Die Idee ist in folgender Grafik dargestellt, die in Blogbeitrag [Wie funktioniert das Internet?](https://www.dr-datenschutz.de/wie-funktioniert-das-internet/) näher beschrieben wird.

![Routing und IP-Adressen im Internet (Quelle: [Dr. Datenschutz](https://www.dr-datenschutz.de/wie-funktioniert-das-internet/))](fig/internet-funktionsweise.jpg){width=50%, alt="Routing und IP-Adressen im Internet"}

:::::::::::::::::::::::


Was sie an der obigen Analogie aber auch erkennen können: jeder der Beteiligten könnte die Postkarte lesen, wenn er wollte!

Das gleiche trifft auch auf das Internet zu: die Datenpakete werden von verschiedenen Knotenpunkten weitergeleitet, die die Pakete anhand der IP-Adresse an den nächsten Knotenpunkt weiterleiten.
Wenn die Datenpakete unverschlüsselt sind, können die Knotenpunkte die Datenpakete lesen und ggf. manipulieren.
Daher ist es i.d.R. wichtig, die Datenpakete zu verschlüsseln, um die Daten vor unbefugtem Zugriff zu schützen.

## HTTPS-Verschlüsselung

Die meisten Webseiten verwenden das HTTPS-Protokoll, um die Datenpakete zu verschlüsseln.
Das heisst, bevor irgendwelche Informationen/Daten zwischen ihrem Computer und dem Zielcomputer (Webserver) ausgetauscht werden, tauschen beide Computer "Schlüssel" aus, mit denen der nachfolgende Datenaustausch verschlüsselt werden.

Um das "Henne-Ei-Problem" zu lösen, da die Schlüssel ja auch übertragen werden müssen, wird ein sogenanntes Public-Key-Verfahren verwendet.
Hierbei gibt ein Rechner einen öffentlichen Schlüssel aus, mit dem jeder Nachrichten an diesen verschlüsseln kann. 
Allerdings hat nur der Rechner selbst den geheimen privaten Schlüssel, mit dem die Nachricht auch wieder entschlüsselt werden kann.
Auf diese Weise kann man ein Geheimnis an jemanden übermitteln, mit dem dann nur dieser etwas anfangen kann.

Im Falle des HTTPS-Protokolls wird der öffentliche Schlüssel des Webservers genutzt, um die Daten zu verschlüsseln, die dann nur der Webserver entschlüsseln kann.

Der Ablauf ist in folgender Grafik illustriert.

![Ablauf des Aufbaus einer HTTPS Verschlüsselung. Hierbei wird mittles public-key-Verschlüsselung ein geheimer Schlüssel an den Webserver gesendet, der eine anschliessende schnelle "symmetrische" Verschlüsselung ermöglicht. (Quelle: [tiptopsecurity.com](https://tiptopsecurity.com/how-does-https-work-rsa-encryption-explained/))](fig/https-dialog.png){width=50%, alt="Ablauf der HTTPS-Verschlüsselung"}

### ABER ...

Aber wie stellen wir sicher, dass wir überhaupt mit dem richtigen Webserver kommunizieren?
Hierzu gibt es sogenannte Zertifikate, die von Zertifizierungsstellen (Certification Authorities, CAs) ausgestellt werden.
Diese Zertifikate enthalten den öffentlichen Schlüssel des Webservers und sind von der Zertifizierungsstelle signiert.
Das bedeutet, dass die Zertifizierungsstelle bestätigt, dass der öffentliche Schlüssel tatsächlich zum Webserver gehört.
Die Zertifikate werden von den Webbrowsern genutzt, um die Identität des Webservers zu überprüfen.
Da die Zertifikate zeitlich begrenzt sind, müssen sie regelmäßig erneuert werden.


## Wer sieht was?

Trotz Verschlüsselung können alle beteiligten Computer die Metadaten der Datenpakete lesen.
Diese Metadaten enthalten Informationen über den Absender, den Empfänger, die Größe des Datenpakets, den Zeitpunkt des Versands, ...
Dies umfasst u.a. auch die Adresse (URL/IP) der Zielwebseite.

Somit kann z.B. der lokale Router (Portier) sehen, welche Webseiten besucht wurden.
Jeder der Zugriff auf diesen (also z.B. ihre lokale FritzBox oder dergleichen) hat (entweder von aussen oder direkt von innerhalb ihres lokalen Netzwerkes), kann diese Metadaten einsehen.

::::::: challenge

# Metadaten Kommunikation

Denken sie kurz über die folgende Frage nach:

*Was könnte man aus der Historie ihrer besuchten Webseiten etc. ablesen?*

::: solution

# Möglichkeiten ...

- Was ist ihre Bank?
- Wo kaufen sie ein?
- Welche Nachrichtenseiten lesen sie?
- ...

:::

::::::::::::::::::

Diese Informationen werden z.T. auch in Logfiles im Router gespeichert.

Auch der Internet Service Provider (ISP) kann sehen, welche Webseiten besucht wurden, welche Apps genutzt wurden, ...
Dieser ist sogar, aufgrund der Vorratsdatenspeicherung, verpflichtet, diese Daten für eine bestimmte Zeit zu speichern, um diese ggf. zur Aufklärung von Straftaten zur Verfügung zu stellen.
Wenn also jemand Zugriff auf diese Daten erhält, kann er ein ziemlich genaues Bild über ihre Aktivitäten im Internet erstellen.

Das gleiche gilt auch für frei verfügbare WLAN-Anbieter (Cafe, Bahnhof, ...), die die Datenpakete ihrer Nutzer mitlesen können.

Auch der Webserver, mit dem sie kommunizieren, kann die Metadaten der Datenpakete sehen und auswerten.
Und wenn sie sich auf einer Webseite registrieren und eingeloggt sind, dann kann der Webseitenbetreiber auch noch weitere Informationen über sie sammeln.


## VPN

Eine VPN-Verbindung (Virtual Private Network) kann helfen, ihre Daten vor neugierigen Blicken zu schützen.
Hierbei wird eine verschlüsselte Verbindung zu einem VPN-Server aufgebaut, der dann die Datenpakete weiterleitet.

![Kommuniation mit und ohne VPN-Verbindung (Quelle: [top10vpn.com](https://www.top10vpn.com/what-is-a-vpn/does-vpn-use-data/))](fig/vpn.png){width=70%, alt="VPN-Verbindung"}

Der Datenverkehr zwischen ihrem Computer und dem VPN-Server ist verschlüsselt, so dass niemand die Datenpakete lesen kann.
Erst der VPN-Server entschlüsselt die Datenpakete und stellt die Verbindung zum Zielserver her.
Dadurch kann der Zielserver nur die IP-Adresse des VPN-Servers sehen, nicht aber ihre eigene IP-Adresse.
Der VPN-Server kann zwar die Metadaten der Datenpakete sehen, aber er kennt nicht den Inhalt der Datenpakete, wenn diese (z.B. via HTTPS) verschlüsselt sind.

Somit können lokale Router, ISPs, WLAN-Anbieter, ... nicht mehr sehen, welche Webseiten besucht werden.

### ABER ...

Aber der VPN-Anbieter kann die Metadaten der Datenpakete sehen und auswertenm, da er diese ja für sie weiterleitet und entgegennimmt.
Auch der Internetprovider des VPN-Anbieters kann die Metadaten der Datenpakete sehen und auswerten, auch wenn diesem die Zuordnung zu ihnen nicht bekannt ist.

VPN schützt also vor lokalen Schnüfflern, aber nicht vor dem VPN-Anbieter und dessen Internetprovider.
Somit sollten sie sich gut überlegen, welchem VPN-Anbieter sie vertrauen.

Ein weiterer Nachteil von VPN ist, dass die Datenpakete über den VPN-Server geleitet werden, was zu einer Verlangsamung der Verbindung führen kann.
Allerdings bieten VPN-Anbieter auch Server in verschiedenen Ländern an, so dass sie z.B. über eine IP-Adresse aus einem anderen Land (die des VPN Servers) mit dem Internet kommunizieren, um z.B.  [Geoblocking](https://de.wikipedia.org/wiki/Geoblocking) oder lokalisierte Werbung zu umgehen.


## Zusammenfassung

:::::: keypoints

- Jeder Computer ist über seine IP-Adresse (im Internet) identifizierbar.
- Zertifikate bestätigen die Identität von Webservern.
- Datenpakete zwischen Computern werden "von Knoten zu Knoten" weitergeleitet.
- HTTPS verschlüsselt die Datenpakete.
- Metadaten der Datenpakete können von lokalen Routern, ISPs, WLAN-Anbietern, ... eingesehen werden.
- VPN schützt vor lokalen Schnüfflern, aber nicht vor dem VPN-Anbieter.


::::::::::::::::::::

:::::::::: challenge

# Einordnung im Datenlebenszyklus

![*In welchen Phasen im Datenlebenszyklus sehen sie obige Punkte als besonders wichtig an?*](https://uni-tuebingen.de/fileadmin/_processed_/6/b/csm_FDM_Lebenszyklus_d1353825c4.png){width=40% alt="Datenlebenszyklus"}


::: solution

## Antwort

Das Wissen um Netzwerkkommunikation und Verschlüsselung ist in allen Phasen des Datenlebenszyklus wichtig.
Kenntnisse darum erleichtern uns, Probleme und Ursachen zu erkennen und zu lösen, die im Zusammenhang mit der Kommunikation von Daten auftreten können.

Immer dann, wenn wir auf fremde Rechner zugreifen oder mit diesen interagieren, sollte uns bewusst sein, dass wir dabei Spuren hinterlassen und dass diese Spuren auch von anderen eingesehen werden können.


:::

::::::::::::::::::::



:::::::::::::::: instructor


:::::::::::::::::::::::::::
