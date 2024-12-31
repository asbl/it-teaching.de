---
title: "Objects First"
date: "2021-06-02"
published: true
type: post
author: asbl
image: images/objectsfirst.png
categories:
  - Informatik
  - Miniworldmaker

tags:
  - python
  - miniworldmaker
  - Informatik
---

Ich habe mal wieder ein altes Projekt ausgegraben, den [miniworldmaker](miniworldmaker.de). Beim Überarbeiten der Dokumentation und der Einführungsbeispiele ist mir wieder aufgefallen, dass ich erst mit Python gelernt habe, dass man zwischen "objects first" und "classes first"-Ansätzen unterscheiden muss.

Wenn man wirklich mit Objekten starten möchte, dann bieten sich dafür decorator an, man vergleiche die folgenden beiden Codes:

1: Mit Objekten
```
import miniworldmaker

board = miniworldmaker.PixelBoard(400,300)
board.add_background("images/stone.jpg")

robot = miniworldmaker.Token(position=(50, 50))
robot.add_costume("images/robo_green.png")
robot.costume.orientation = - 90
robot.size = (30,30)
@robot.register
def act(self):
    global board
    mouse_pos = board.get_mouse_position()
    if mouse_pos:
        self.point_towards_position(mouse_pos)
        self.move()
               
board.run()
```

So sieht das Ergebnis aus:

![Objects first](/images/mwm_objects_first.png)

Mit Klassen:
```
from miniworldmaker import *


class MyBoard(PixelBoard):

    def on_setup(self):
        self.add_background("images/stone.jpg")
        Robot(position=(50, 50))


class Robot(Actor):

    def on_setup(self):
        self.size = (30, 30)
        self.add_costume("images/robo_green.png")
        self.costume.orientation = - 90

    def act(self):
        mouse = self.board.get_mouse_position()
        if mouse:
            self.point_towards_position(mouse)
            self.move()


board = MyBoard(800, 600)
board.run()

```

Meiner Meinung nach ist Variante 2 für Anfänger deutlich intuitiver, einfach weil dies ein tatsächlicher "Objects First"-Ansatz ist und die Klassen erstmal nur eine untergeordnete Rolle spielen.