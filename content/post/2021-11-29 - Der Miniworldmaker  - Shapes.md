---
title: "Miniworldmaker - Version 2"
date: "2021-02-16"

type: post
author: asbl
image: /images/shapes.png
categories:
  - Informatik
  - Miniworldmaker
tags:
  - miniworldmaker
  - python
  - Informatik
---

Ich habe dem Miniworldmaker eine neue Major-Versionsnummer spendiert. da ich in den letzten Monaten wirklich sehr viel daran gearbeitet habe, halte ich dies für angemessen.

Mit der neuen Versionsnummer kommen ein paar kleinere und größere Änderungen

  * Ich habe Shapes umfangreich überarbeitet, damit diese ähnlich wie in Processing genutzt werden können, ohne dabei aber die Processing-Syntax zu kopieren (darüber habe ich lange nachgedacht, habe mich dann aber aus verschiedenen Gründen dagegen entschieden). In den nächsten Wochen/Monaten will ich dazu das ein- oder andere Tutorial schreiben. Geometrische Objekte haben jedenfalls nun eine innere und eine äußere Fläche, welche unabhängig voneinander gestaltet werden können.

  ![shapes](/images/shapes.png)

  * Auch Tokens können nun wie andere Shapes auch einen Rahmen haben.

  ![Border and fill](/images/border_and_fill.png)

  * Konstruktoren wurden generell alle auf das nötigste reduziert. Veränderungen werden durch Attributsänderungen erzeugt. So wird z.B. kein Bild, Rahmen o.ä. mehr dem Konstruktor hinzugefügt.

  * Ich habe die Dokumentation nochmal umfangreich überarbeitet und von einigen Fehlern beseitigt. 

  ![Docs](/images/docs.png)


Wie geht es weiter?

  * Zunächst mal wird der an Processing angelehente Grafikteil einige Tutorials bekommen.

  * Ich halte weiter die Augen offen, ob es Möglichkeiten gibt, die Engine ins Web zu bekommen. Bisher geht dies nur mit Umweg über repl.it, vielleicht könnte ich aber auf einen der Python-Web-Ansätze aufbauen und/oder ggf. das Backend Pygame durch etwas anderes ersetzen, um die SDL-Abhängigkeiten aufzulösen. Hier habe ich aber noch keinen konkreten Fahrplan, sondern beobachte, welcher Weg mit geringstem Aufwand möglich wäre.



