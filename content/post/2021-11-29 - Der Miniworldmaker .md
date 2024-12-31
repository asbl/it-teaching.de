---
title: "Miniworldmaker"
date: "2021-12-19"

type: post
author: asbl
image: /images/mwm_kara.png
categories:
  - Informatik
  - Miniworldmaker
tags:
  - miniworldmaker
  - python
  - Informatik
---

In den letzten Wochen habe ich den miniworldmaker stark überarbeitet. Nach außen fällt dies kaum auf, weil die meisten Änderungen hinter den Kulissen stattgefunden haben:

  * Ich habe die Architektur an vielen Stellen überarbeitet und Klassen aufgesplittet, damit einzelne Programmteile unabhängig voneinander laufen. Dabei einige Entwurfsmuster zur Hilfe genommen um diese Strukturierung möglichst sauber zu unterstützen. Dieser Prozess ist noch nicht 100% abgeschlossen, greift aber sehr weit; Im Prinzip habe ich dafür 3/4 des Codes nochmal angepasst und wirklich sehr viel herumgeschoben und verändert.

  * Ich habe viele Tests ergänzt, mit denen ich in Zukunft hoffentlich früher Bugs entdecke.

  * Der Miniworldmaker basiert nun auf der neuesten Version von Pymunk. In der Physikengine habe ich in dem Zuge stärkere Änderungen durchgeführt, die das Arbeiten meiner Meinung nach deutlich vereinfachen.

  * Es wurden einige neue Exceptions ergänzt, damit Fehler klarer zurückgegeben werden.

  * Kleine Ergänzungen habe ich umgesetzt (z.B.  Layer oder andere Bequemlichkeiten) - Darauf lag aber wirklich kein Schwerpunkt. An der Funktionalität hat sich im wesentlichen nichts verändert.

![Kara im Miniworldmaker](/images/mwm_kara.png)

Leider hat das auch dazugeführt, dass in diesem Übergangsprozess der Miniworldmaker instabiler lief und einzelne Releases nicht lauffähig waren. Ich gehe aber davon aus, dass jetzt wieder ein Status erreicht, wo alles wieder stabil läuft. Durch die vielen Tests vermutlich sogar stabiler als vorher.

Jetzt kann ich mich daran machen die Dokumentation zu überarbeiten und demnächst vielleicht auch wieder das ein- oder andere Feature hinzuzufügen. Wenn ihr Wünsche habt, oder euch etwas auffällt, dann fügt einen Issue im Codeberg-Repository hinzu.

{{< chat miniworldmaker >}}