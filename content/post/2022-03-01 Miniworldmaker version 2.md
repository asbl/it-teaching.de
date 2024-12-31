---
title: "Miniworldmaker - Version 2"
date: "2022-02-28"

type: post
author: asbl
image: /images/mouse2.png
categories:
  - Informatik
  - miniworldmaker
tags:
  - miniworldmaker
  - python
  - Informatik
---

Der miniworldmaker trägt nun eine neue Major-Versionummer.

In den leztzten Wochen und Monaten habe ich nochmal intensiv an der Engine gearbeitet und zahlreiche Veränderungen vorgenommen. Die Änderungen sind insgesamt so umfangreich, dass ich die Version 2 vorangestellt habe.

Am entscheidensten aus Nutzersicht ist, dass ich stark daran gearbeitet habe das Programmieren mit Shapes zu vereinfachen. 
Dies ermöglicht mit noch weniger Zeilen Code Programme zu schreiben - Im Unterricht kann man den miniworldmaker daher ähnlich wie die Bibliothek processing verwenden. Ich habe dabei allerdings bemüht wo möglich Ansätze aus processing in Ansätze zu verändern, die besser zu python-Codingstandards passen.

![draw with mouse](/images/mouse2.png)

* Ich habe [hier](https://miniworldmaker.de/processing_german/01_first_steps_drawing.html) ein Tutorial begonnen, 
dass erläutert, wie man mit dem processing-Zugang starten kann.

* Das reguläre ["Objects First"-Tutorial](https://miniworldmaker.de/objectsfirst_german/index.html) hat ebenfalls eine massive Überarbeitung erfahren:

Mit den Tutorials sind ca. 100 neue Tests und Miniwelten entstanden, mit denen ich auch die Stabilität der verschiedenen Komponenten getestet habe - Dadurch sollte 
sich insgesamt auch die Stabilität der Engine erhöht haben.

Vorstellen kann man sich dies z.B. an einem einfachen Flappy-Bird-Beispiel:

``` python
from miniworldmaker import *

board = Board(300, 200)

rect = Rectangle((280,120), 20, 80)
ball = Circle((20,50),20)
velocity = 1
@rect.register
def act(self):
    rect.x -= 1
    if rect.x == 0:
        rect.x = 280

@ball.register
def act(self):
    global velocity
    self.y += velocity
    if board.frame % 10 == 0:
        velocity += 1
    token = self.sensing_token()
    if token == rect:
       self.board.stop()

@ball.register
def on_key_down(self, key):
    global velocity
    velocity = -2
board.run()
```

 <video controls loop width=300px>
  <source src="/videos/flappy2.webm" type="video/webm">
  <source src="/videos/flappy2.mp4" type="video/
  Your browser does not support the video tag.
</video>