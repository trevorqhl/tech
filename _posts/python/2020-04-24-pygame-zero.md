---
layout: post
title:  "How to use Pygame Zero" 
date:   2020-04-24 22:30:52 -0400
img: python.png
categories: Python
tags: Pygame
---

![Linux]({{site.baseurl}}/images/pgzero.svg)

Pygame is a cross-platform set of Python modules designed for writing video games. It includes computer graphics and sound libraries designed to be used with the Python programming language.

[Pygame Zero][Pygame Zero] is a beginner friendly wrapper around the powerful [Pygame][Pygame] library for writing video games using Python. 


### Install Pygame Zero in Centos
{% highlight ruby %}
# It will install dependencies including pygame
pip3 install pgzero
{% endhighlight %}

### My first game created by Pygame Zero
{% highlight ruby %}
#!/usr/bin/python3

import pgzrun
from random import randint
import time
import math

def draw():
    screen.fill("blue")
    hedgehog.draw()
    coin.draw()
    screen.draw.text("score: "+ str(score),(10,10))
    screen.draw.text("time: "+ str(total_time),(WIDTH - 100,10))

    if game_over:
        screen.fill("red")
        screen.draw.text("Game Over", (90, 170),fontsize = 60)
        screen.draw.text("score: "+ str(score),topleft = (10,10),fontsize = 60)
        reset.draw()
        sounds.lol.stop()

def place_coin():
    coin.x = randint(20, WIDTH - 20)
    coin.y = randint(20, HEIGHT - 20)

def time_up():
    global game_over
    game_over = True

def update():
    global score
    global start_time
    global current_time
    global total_time
    current_time = time.time()
    total_time = math.floor(current_time - start_time)

    if (keyboard.a or keyboard.left) and hedgehog.x > 0.0:
        hedgehog.x -=5
    elif (keyboard.d or keyboard.right) and hedgehog.x < WIDTH:
        hedgehog.x +=5
    elif (keyboard.w or keyboard.up) and hedgehog.y > 45.0:
        hedgehog.y -=5
    elif (keyboard.s or keyboard.down) and hedgehog.y < HEIGHT:
        hedgehog.y +=5

    coin_collected = hedgehog.colliderect(coin)
    if coin_collected:
       score += 1
       place_coin()


def on_mouse_down(pos):
    global score
    global game_over
    score = 0
    game_over = False
    if reset.collidepoint(pos):
        print("good hit")
        start_game()

def start_game():
    global score
    global start_time
    global current_time
    global total_time

    start_time = time.time()
    current_time = time.time()
    total_time = math.floor(current_time - start_time)
    score = 0

    clock.schedule(time_up, 15.0)
    place_coin()
    sounds.lol.play()

WIDTH = 400
HEIGHT = 400
score = 0
game_over = False
start_time = 0
current_time = 0
total_time = 0

hedgehog = Actor("hedgehog")
hedgehog.pos = 100,100 
coin = Actor("coin")
coin.pos =  200,200
reset = Actor("reset")
reset.pos = 200,300
start_game()
pgzrun.go()

{% endhighlight %}

[Pygame]: https://www.pygame.org
[Pygame Zero]: https://pygame-zero.readthedocs.io/en/stable/
