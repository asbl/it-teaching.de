---
title: "Vectors and Arrays"
date: "2022-03-06"
published: true
type: post
author: asbl
image: /images/gradient.png
categories:
  - Informatik
  - miniworldmaker
tags:
  - miniworldmaker
  - python
  - Informatik
---

Ich habe es erneut getan.

Nachdem ich [zuletzt](https://it-teaching.de/2022-03-01-random-rectangles/) bereits schonmal ein Skript aus dem Schockwellenreiter-Blog hier kopiert habe, habe ich mir ein weiteres Skript vorgenommen. (An dieser Stelle ein kleines Dankeschön :-) - Sein Blog ist für mich eine Quelle der Inspiration )

Diesesmal ging es um Vektoren - Etwas was ich schon länger in den miniworldmaker einbauen wollte. Die Original TigerPython-Version findet sich [hier](http://blog.schockwellenreiter.de/g2022/b202203/202203bild02.html)

Zunächstmal: So sieht das Skript im miniworldmaker aus:

``` python
from miniworldmaker import *

board = Board()
player = Circle((200,200), 20)

flee = Circle((100,100),20)
flee.color = (0,255,0)
chaser = Circle((300,300),20)
chaser.color = (255,0,0)
chaser_speed = 1.1
flee_speed = 1.1

@player.register
def act(self):
    player.position = board.get_mouse_position()

@chaser.register
def act(self):
    v1 = Vector.from_tokens(player, chaser)
    v2 = - v1.normalize().multiply(chaser_speed)
    chaser.move_vector(v2)

@flee.register
def act(self):
    v1 = Vector.from_tokens(player, flee)
    if  v1.length() < 100:
        v1 = Vector.from_tokens(player, flee)
        v2 = v1.normalize().multiply(flee_speed)
        flee.move_vector(v2)
        
board.run()
```

 <video controls loop>
  <source src="/videos/chaser.webm" type="video/webm">
  <source src="/videos/chaser.mp4" type="video/webm">
  Your browser does not support the video tag.
</video>

Damit das ganze funktioniert, habe ich zum miniworldmaker eine grundlegende Vektorklasse geschrieben, die [hier](https://miniworldmaker.de/api/vector.html) dokumentiert ist.

Um das ganze zu testen, habe ich noch etwas mehr programmiert, u.a. Beispiele von processing.org kopiert und dann einen kleinen Rennspiel-Prototyp geschrieben - 
Kein vollständiges Spiel, aber eine Idee auf der man aufbauen könnte:

 <video controls loop>
  <source src="/videos/racing.webm" type="video/webm">
  <source src="/videos/racing.mp4" type="video/webm">
  Your browser does not support the video tag.
</video>

Der Code zu diesem Programm sieht so aus:

``` python
from miniworldmaker import *

board = Board()

player = Rectangle((200,350),20, 40)
player.acceleration = 0
player.velocity = 1
player.limit = 5
player.vector = Vector(1,0)
obstacles = []
obstacles.append(Rectangle.from_center((200,200),200,200))
obstacles.append(Rectangle((180,300),20,100))
goal = Rectangle((160,300),20,100)
goal.color = (0,255,0)

@player.register
def act(self):
    self.direction = self.vector
    self.vector.limit(5)
    self.move_vector(self.vector)

@player.register
def on_key_pressed_a(self):
    self.vector.rotate(-5)

@player.register
def on_key_pressed_d(self):
    self.vector.rotate(5)

@player.register
def on_key_pressed_w(self):
    self.speed += 0.01
    self.vector.multiply(self.speed)

@player.register
def on_key_pressed_s(self):
    self.speed -= 0.01
    self.vector.multiply(self.speed)
    
@player.register
def on_sensing_token(self, other):
    if other in obstacles:
        Text((50,50), "Kaboom!")
        self.board.stop()
    if other == goal:
        Text((50,50), f"Success! Time: {self.board.frame}")
        self.board.stop()
        
@player.register
def on_sensing_not_on_board(self):
    Text((50,50), "Kaboom!")
    self.board.stop()
    
board.run()
```

Zuletzt habe ich gefallen daran gefunden, Processing-Funktionen irgendwie zu "klauen" und habe mich an die Voraussetzung gewagt, mit der auch Bildbearbeitung möglich ist. 

So sieht das erste Ergebnis aus, welches einen grauen Hintergrund in einen bunten Gradient umwandelt:

``` python
from miniworldmaker import *

board = Board()
background = board.background
arr = background.to_array()
for i in range(len(arr)):
    for j in range(len(arr[0])):
        arr[i][j][0] = ((i +1 ) /board.width) * 255
        arr[i][j][1] = ((j +1 ) /board.width) * 255
print(arr)
background.from_array(arr)
board.run()
```

![Gradient](images/gradient.png)

Das nächste Ziel ist es nun diese Funktionalitäten in die miniworldmaker-Tutorials einzubauen.