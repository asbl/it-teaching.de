---
title: "Random Rectangles with Transparency"
date: "2022-02-28"

type: post
author: asbl
image: /images/random_rectangles2.png
categories:
  - Informatik
  - miniworldmaker
tags:
  - miniworldmaker
  - python
  - Informatik
---

In bestimmten Kreisen ist der Spruch "Das kann man auch mit Moodle machen" ja sehr populär.

Mir geht es ähnlich mit dem miniworldmaker: Mich reizt es Sketches mit dem miniworldmaker umzusetzen, um zu vergleichen wie elegant (oder auch nicht) man Dinge dort umsetzen kann.

Auf dem Schickwellenreiter-Blog wurden von Jörg Kantel mit TigerJython [hier](http://blog.schockwellenreiter.de/g2022/b202202/202202bild22.html) zufällige Rechtecke gezeichnet.

Ich habe das zum Anlass genommen das Programm in den miniworldmaker zu übersetzen - und so sieht es aus:

![Random rectangles](/images/random_rectangles.png)

Dies ist der Code:

``` python
from miniworldmaker import *
from random import randint

WIDTH = 600
HEIGHT = 400

board = Board(WIDTH, HEIGHT)

board.add_background((235, 215, 182))

for _ in range(200):
    x = randint(15, WIDTH -15)
    y = randint(10, HEIGHT - 15)
    w = randint(10, 50)
    h = randint(10,50)
    
    rect = Rectangle((x, y), w, h)
    
    r = randint(10, 200)
    g = randint(10, 200)
    b = randint(10, 200)
    alpha = 0.7 * 255
    
    rect.color = (r, g, b, alpha)
    
print("I did it, Babe")
board.run()
```