---
title: "Crazy Machines"
date: "2022-08-11"
published: true
type: post
author: asbl
image: /images/crazy_machines1.png
categories:
  - Informatik
  - miniworldmaker
tags:
  - miniworldmaker
  - python
  - Informatik
---

In den Ferien habe ich mal wieder etwas Zeit zum Programmieren gefunden und im miniworldmaker ein Programmierprojekt vorangetrieben, was *nicht* in erster Linie eine Vorlage für meinen Informatikunterricht oder eine Projektwoche ist (in der letzten Woche haben die Schüler den miniworldmaker sehr erfolgreich verwendet).

Ich wollte ausprobieren, wie gut ich ein Spiel aus meiner Kindheit "Crazy Machines" umsetzen kann. Der momentane Status ist natürlich noch weit von diesem Meisterwerk meiner Kindheit entfernt, aber schon so weit, dass er enorme Faszination auf meinen Sohn und gleichaltrige Kinder ausgeübt hat - Mir wurden schon zig verschiedene "Murmelbahnen" gemahlt, die ich umsetzen sollte.

Das Spiel funktioniert so:

* Es gibt einen Start- und einen Endpunkt. 
* Es gibt verschiedene Hindernisse
* Der Spieler kann selbst bestimmte geometrische Objekte setzen (mit begrenzter Anzahl und Größe)
* Wenn man Space drückt, wird die Kugel losgelassen und hat nun 10 Sekunden Zeit das Ziel zu erreichen.

So sieht der aktuelle Status in Bewegung aus:

 <video controls loop>
  <source src="/videos/crazy_machines1.mp4" type="video/webm">
  Your browser does not support the video tag.
</video>

...und so werden zur Zeit Levels erstellt (Das Level wurde nach Vorlage für ein Kind namens *Bruno* erstellt:

``` python
class LevelBruno1(LevelBase):
    def on_setup(self):
        super().on_setup()
        self.start_marker.center = (50,50)
        # Obstacles
        Base((40,60),(100,100))
        Base((100,100),(140,100))
        Base((160,120),(190,145))
        Base((200,200),(240,155))
        Base((160,240),(200,240))
        Base((160,365),(320,350))
        r = Rectangle((120,80),20,20)
        r.physics.density = 0.9
        r.physics.elasticity = 0.1
        c = Circle((120,5))
        c.physics.simulation = None
        # Objects        
        pinjoin_obj = PinJointObject(75, c)
        pinjoin_obj.add_to_level(self, 1)
        rect_obj = RectObject(50)
        rect_obj.add_to_level(self, 2)
        w = Wheel((240, 280), 70, 3)
        self.end_marker.center = (200,350)
```
