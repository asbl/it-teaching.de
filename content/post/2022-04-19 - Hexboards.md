---
title: "Hexboards"
date: "2022-04-19"

type: post
author: asbl
image: /images/hexboard.png
categories:
  - Informatik
  - miniworldmaker
tags:
  - miniworldmaker
  - python
  - Informatik
---

Neu im miniworldmaker sind seit heute Hexboards.

Ich muss das neue Feature noch etwas dokumentieren und in die Dokumentation auf miniworldmaker.de einpflegen und dann mal Tutorials schreiben... - Die ersten Beispiele und Tests laufen aber bereits, so dass ich den nächsten Schritten optmistisch entgegenblicke. 

Die Implementation von Hexboards hat mich vor einige Herausforderungen gestellt, die mir viel Mühe aber gleichzeitig auch viel Spaß bereitet haben. Zu, Glück hat Amit Patel [hier](https://www.redblobgames.com/grids/hexagons/) schon fast alles zusammengetragen, was man zu Hexboards wissen muss.

Was ich besonders spannend finde ist, dass man die Kacheln eines Hexgrids als Würfelkoordinaten auffassen kann:

![Cube coordinates](/images/hexcubes.png)

Darüber lassen sich viele Algorithmen -z.B. Abstandsberechnungen- sehr elegant durchführen.

Das erste Beispiel, bei dem man die API ansehen kann, findet man im [miniworldmaker-Kochbuch](https://codeberg.org/a_siebel/miniworldmaker_cookbook/src/branch/main/objects_first/boardgame)

Gleichzeitig habe ich eine kleine Änderung an der Physik-Engine vorgenommen -auch diese erhält bald mehr Dokumentation und ein eigenes Tutorial-. Man kann nun über einen Joint Elemente verbinden und so z.B. ein Pendel realisieren.

![Joints](/images/joints1.png)

Der Code findet sich ebenfalls im [miniworldmaker-Kochbuch](https://codeberg.org/a_siebel/miniworldmaker_cookbook/src/branch/main/snippets/4%20Physics/405_pin_joint.py)