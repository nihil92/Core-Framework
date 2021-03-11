![cats](https://user-images.githubusercontent.com/66818008/110716817-a7a4f900-81e6-11eb-9fdf-2d727352bcb1.png)

# Core Engine

This is a open-source Sonic engine for _Clickteam Fusion 2.5+_ created by Nihil in association with Tyson Tay, Lighto, Ainand, YohananDiamond, Chopp, Yonatankr, Dark, Joshyflip, Carlos Ushiromiya, Dolphman, Yolkin, Troopsushi, Angeloz, Jeloboi and Nuclear. The engine was built from the Sonic Worlds base (created by Damizean), but it's entire core has been radically modified to offer infinitely greater precision, making Core a unique, cohesive and solid experience.

# Features

The base 360 Platform Movement and physics is already finished. The codes were built to be more economical, saving performance and making it easier for users to understand. An extensive internal documentation was been written, including used groups and math formulas.

Talking about the base, we keep some things from the original base, such as some parts of the movement routine and the actions system using group activation/deactivation, but everything with some rewritting and/or improvements (e.g. the actions which were all rewritten, keeping only the way they are activated and deactivated).

Other important parts like rings, camera, sensors, physics, collision, landing and angle detection, have been completely different. It has support for SDL Joystick, volume control, display options, save system, smooth rotation and classic rotation. It also contains alot of gimmicks, items and features to you build your fangame with the most higher standards.

We've added a gumball machine bonus stage and a unfinished Blue Spheres example created by Yonatankr. Some things that naturally worked great were ported from Sonic Worlds Delta, like the parallax system, tunnels, screw, corkscrew and breakable floor in with slight adaptations, but everything else was rewritten by us..

# Important

Make sure to install the most recent version of [**SDL**](https://github.com/SortaCore/SDLJoystick/releases) to make this works.

# Disclaimer
This is a non-profit project made for learning purposes. We do not intend to infringe any copyright. Do whatever you want with this engine, as long as you give credit to everyone involved in this project and that you do not sell Sonic games made with this engine under any circumstances.

# Documentation

Used groups:

0: Solid (Flag 0 on = NON SOLID / Flag 0 off = SOLID)
1: Platform (in case of you want to use a platform backdrop, put this one AND Generic 1)
2: No Slope Checking
3: Layer 0
4: Layer 1
5: Platform Sink
6: Moving Platform
7: Pushable
8: Crushable
9: Attach Objects

Data: Pausable (to stop the animations during the pause).
Player: Skins
Friends: Sensors
Enemy: Badniks
Arm: Hurtable Object
Bullet: Bullet
Shield: Stop
Ball: Bumpers
Invisible: Breaking Platforms
Powerup: Monitors

Drawning: Bridges
Neutral: Swing (Spawner)
Good: Swing (Main Object)
Engine: Remove objects outside the frame
Flowes: Vines (Swing Rope)
Reference Points: Invincible Stars

Movable: Conveyor Belts
Value Holder: Corkscrews
Dissolving: Falling Platforms
Water: Water Pools
Waveform: Fans
Particles: Bubbles
Bosses: ...Bosses
Arrows: Hanging Bars
Clothes: Capsule
Explosions: ...Explosions
Keys: Switches
Doors: Doors
Obstacles: Solid (to work with another solid).
Target: Portals.

Generic 1: Platform
Generic 2: Spike Balls (for Mighty)
