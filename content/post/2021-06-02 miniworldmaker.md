---
title: "Miniworldmaker"
date: "2021-06-02"

type: post
author: asbl
categories:
  - Informatik
  - Miniworldmaker

tags: 
  - Informatik
  - Miniworldmaker
  - Python
---
Ich habe in den letzten Tagen den [miniworldmaker](miniworldmaker.de) wieder ausgegraben und aktualisiert. Die meisten Dinge funktionieren jetzt auch mit pygame 2. Musik macht noch Probleme. Ich versuche die Struktur etwas zu ändern, um möglichst einen wirklichen "Objects first"-Ansatz umzusetzen. Daher werde ich Dokumentation und Beispiele in den nächsten Wochen nochmal überarbeiten und möglicherweise auch das ein- oder andere Feature hinzufügen. 

Der miniworldmaker wird von mir immer im Rythmus von einem halben Jahr weiterentwickelt. Er ruht, wenn ich gerade keine Kurse habe die damit arbeiten und wird dann wieder aktiv weiterentwickelt, wenn Kurse damit arbeiten und/oder eine Projektwoche ansteht.

Hier ein Beispielprogramm:

![Miniworldmaker - Example](/images/mwm_2021.png)

```python
import miniworldmaker
import random

board = miniworldmaker.TiledBoard()
board.add_background("images/space.jpeg")
board.columns = 10
board.rows = 10
board.tile_size = 40
board.speed = 40
player = miniworldmaker.Token()
player.position = (5,5)
player.add_costume("images/ship.png")
player.costume.is_rotatable = False


@player.register
def act(self):
    # self.move()
    pass

@player.register
def on_key_down_w(self):
    self.point_in_direction(0)
    self.move()

@player.register
def on_key_down_s(self):
    self.point_in_direction(-180)
    self.move()
    
@player.register
def on_key_down_space(self):
    laser = miniworldmaker.Token()
    laser.position = (self.x + 1,self.y)
    laser.add_costume("images/laser.png")
    @laser.register
    def act(self):
        self.point_in_direction(90)
        self.move()
    @laser.register
    def on_sensing_token(self, token):
        token.remove()
        explosion = miniworldmaker.Token()
        explosion.position = (self.x, self.y)
        self.remove()
        print("explosion")
        explosion.position = (self.x, self.y)
        explosion.add_costume()
        explosion.costume.add_images(["images/explosion01.png",
                                "images/explosion02.png",
                                "images/explosion03.png",
                                "images/explosion04.png",
                                "images/explosion05.png",
                                "images/explosion06.png",
                                "images/explosion07.png",
                                "images/explosion08.png"])
        explosion.costume.animation_speed = 50
        explosion.costume.is_animated = True
        # miniworldmaker.ActionTimer(24, explosion.remove, None)

@player.register
def on_sensing_token(self, token):
    print("Damage!!!!!")
    self.remove()
    

asteroid = miniworldmaker.Token()
asteroid.add_costume("images/asteroid.png")
asteroid.position = (9,1)

@asteroid.register
def act(self):
    self.point_in_direction(-90)
    self.move()
    if self.x < 1:
        self.x = 9
        self.y = random.randint(1,9)
        
asteroid2 = miniworldmaker.Token()
asteroid2.add_costume("images/asteroid.png")
asteroid2.position = (8,4)

@asteroid2.register
def act(self):
    self.point_in_direction(-90)
    self.move()
    if self.x < 1:
        self.x = 9
        self.y = random.randint(1,9)

board.run()
```