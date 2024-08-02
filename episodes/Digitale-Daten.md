---
title: "Digitale Daten"
teaching: 40
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions 

- Wie wird ... gespeichert?
- Was gibt es für Probleme?
- Worauf muss man achten?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Verständnis wie verschiedene Informationstypen digital repräsentiert sind
- Wissen um die Grenzen und Schwierigkeiten von Informationsspeicherung
- Lösungsstrategien für häufige Daten(import)probleme

::::::::::::::::::::::::::::::::::::::::::::::::

Grundlegende Formen von Information sind Text, Zahlen, Bilder, Audio und Video. 
Wenn wir an diese denken, haben wir meistens eine Vorstellung von einem physischen Medium wie einem Blatt Papier etc., auf dem diese gespeichert sind.
Eine solche Form der Informationsspeicherung wird als **analoge** Speicherung bezeichnet.

In Computern wird Information in Form von **digitalen Daten** gespeichert.
Digital bedeuted, vereinfacht gesagt, dass die Information in Form von Zahlen gespeichert wird, die wiederum in Form von elektrischen Signalen (z.B. "Strom an oder aus") repräsentiert werden.
Letzteres ist die Grundlage für die Funktionsweise von Computern.

Das bedeutet, dass alle Informationen, die wir in Computern speichern, in Form von Zahlen repräsentiert werden muss.
Eine weitere wichtige Eigenschaft von digitalen Daten ist, dass sie in **diskreten** Einheiten gespeichert werden, also i.d.R. in Form von ganzen Zahlen.

Im Folgenden werden wir uns mit den verschiedenen Arten von digitalen Daten und deren Speicherung beschäftigen.

## Text

Text ist die einfachste Form von digitalen Daten.
Text wird in Computern in Form von **Zeichenketten** gespeichert.
Jedes Zeichen wird dabei durch eine Zahl repräsentiert, wobei die Zuordnung von Zeichen zu Zahlen durch eine **Zeichencodierung** festgelegt wird.
Letztere ist eine Tabelle, die jedem Zeichen eine Zahl zuordnet.

Die bekannteste und eine der ersten ist die **ASCII**-Codierung (American Standard Code for Information Interchange), welche 128 Zeichen umfasst und im Folgenden dargestellt ist.

![ASCII](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/ASCII-Table-wide.svg/800px-ASCII-Table-wide.svg.png){alt='ASCII'}

Wenn wir die Tabelle betrachten, fällt uns auf, dass nicht nur Buchstaben oder Ziffern, sondern auch Sonderzeichen und Steuerzeichen (z.B. Zeilenumbruch) enthalten sind.
Zudem fehlen Umlaute und Sonderzeichen, die in anderen Sprachen verwendet werden.

Daher wurden im Laufe der Zeit weitere Zeichencodierungen entwickelt, die mehr Zeichen umfassen.
Hier ein paar Beispiele:

- **latin1** (ISO-8859-1): 256 Zeichen, enthält Umlaute und Sonderzeichen für westeuropäische Sprachen
- **latin2** (ISO-8859-2): 256 Zeichen, enthält Umlaute und Sonderzeichen für osteuropäische Sprachen
- **GB2312**: 6.763 Zeichen, enthält chinesische Schriftzeichen
- **UTF-8**: 1.112.064 Zeichen, enthält fast alle Schriftzeichen der Welt

Hierbei ist zu beachten, dass die erweiterten Zeichencodierungen rückwärtskompatibel sind, d.h. die Zahlen-Buchstaben-Kodierungen der ersten 128 Zahlen entsprechen i.d.R. der "alten" ASCII Codierungen.

Aktuell ist **UTF-8** die am weitesten verbreitete Zeichencodierung, da sie fast alle Schriftzeichen der Welt umfasst und daher für die meisten Anwendungsfälle geeignet ist.
Diese Kodierung wird auch von den meisten neueren Betriebssystemen und Anwendungen standardmäßig verwendet.

:::::::::::::::  challenge

# Kodierungsprobleme

*Was kann passieren, wenn ein Text mit **latin1**-Codierung abgespeichert wird (also in Zahlen umgewandelt wird) und anschliessend mit **latin2**-Codierung gelesen wird (also die Zahlen wieder mit Buchstaben ersetzt werden)?*

:::::::::: solution

Es werden falsche Zeichen angezeigt, da die Zahlen-Buchstaben-Zuordnung nicht übereinstimmt.

:::::::::::::::::::

:::::::::::::::::::::::::::

Das Problem mit den verschiedenen Zeichencodierungen ist, dass beim Öffnen einer Datei mit einer anderen Codierung als der, in der sie gespeichert wurde, die Zeichen falsch dargestellt werden.
Daher ist es wichtig, die Codierung einer Datei zu kennen, um sie korrekt lesen zu können.
Ein deutliches Zeichen, dass die falsche Codierung verwendet wird, ist, wenn anstelle von Umlauten oder Sonderzeichen nur Fragezeichen oder andere Zeichen angezeigt werden, wie in folgendem Bild.

![Kodierungsproblem](fig/encoding-problem.jpg){alt='Kodierungsproblem'}

Dies tritt häufig auf, wenn man mit *älteren Dateien* arbeitet, was gerade im wissenschaftlichen Bereich *in der Datennachnutzung von Daten* immer wieder vorkommt.


::::::::::: callout

# Hinweis

In diesem Fall, muss man händisch die Codierung ändern, um den Text korrekt darzustellen.
Hier bleibt häufig nichts weiter übrig, als die Codierung auszuprobieren, bis der Text korrekt dargestellt wird.
Dabei ist es hilfreich, über den Urheber der Datei Bescheid zu wissen.

Hier kommt wieder die Dokumentation von Daten ins Spiel!

::::::::::::::::::::

### Zeilenumbruch

Ein weiteres Problem, das beim Lesen von Textdateien auftreten kann, ist der **Zeilenumbruch**, also das Zeichen, das angibt, dass eine neue Zeile beginnt.
In verschiedenen Betriebssystemen wird der Zeilenumbruch unterschiedlich dargestellt:

- **Windows**: `\r\n` (zwei Zeichen: Carriage Return und Line Feed)
- **Linux**: `\n` (ein Zeichen: Line Feed)
- **MacOS**: `\r` oder `\n`, je nach Alter des Betriebssystems (Carriage Return oder Line Feed)

Dies kann dazu führen, dass Textdateien auf einem Betriebssystem, auf dem sie nicht erstellt wurden, nicht korrekt dargestellt oder verarbeitet werden können.

::::::::::: callout

# Hinweis

Texteditoren wie Notepad++ oder Visual Studio Code können automatisch die Zeilenumbrüche in Textdateien erkennen und korrekt darstellen.
Auch ist es dort möglich, die Zeilenumbrüche in einem Textdokument zu konvertieren, d.h. von einem Format in ein anderes zu ändern.

::::::::::::::::::::

## Zahlen





:::::: keypoints
- TODO
::::::::::::::::::::

