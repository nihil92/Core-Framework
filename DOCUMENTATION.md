This documentation is valid for version 0.23.02.

# General Tips

- To close all the codes group, go to _Events > Close all groups_.

- To increase the free space outside the frame, simply access _Tools > Proprieties > Frame Editor_ and edit the "Margins" as you like.

- If you want to see a object in event editor by icon, name or both, simply go to _Tools > Proprieties > Event List Editor_ and check the flags as you like.

- To make a backdrop solid, just check the object proprieties and set the Obstacle Type as "Obstacle".

- If the names in global events "disappear" go to _Application Proprieties > Events_ and change the base frame.

- You can use search tool pressing CTRL+SHIFT+F.

# Core Framework

## Customization options by level 

We can set different options for each level. Whether there will have water or not, the type of goal or whether the level in question is an act 1 or 2, etc. To make it easier, we've created a group located at _Frame Editor > Level Unique > Custom Level_. Just edit the options you want.

## Audio System

### Music Loop

To use the loop system, simply set the values of LoopEnd and LoopStart to the correct number values for the loop point. 

The loop points are measured exactly like normal music. But it can be confusing without the colons. so 123000 would be 1:23 exactly.

## Parallax System

#### INTRODUCTION

As a alternative for the parallax system from Sonic Worlds, we decided to work on a completely new system, built from the ground up. In addition to allowing easily animated parallaxes, it offers an better performance than using Background System Box, built-in layers system or through the Layer Object extension. However, it can be tricky to use without understanding how this system works first.

#### BASIC USAGE

First, keep in mind that you can use whatever size you like, as long as all the pieces are at least the size of the window. If your game uses 320×224, all pieces must be at least this size. This is necessary, as gaps between one part and another can become visible if they are smaller than the size of the window. Furthermore, it is important that you keep all the pieces to the top left hotspot (0,0) and make sure all of the pieces have the same size (e.g. if you have a piece with 640x480 of size, make all the others have the same size). To generate a new parallax piece, simply clone a parallax piece by right-clicking on a parallax piece and accessing the "clone" option. This ensures that all parts maintain their properties correctly.

The system is fully automated, so you don't need to mess around with math for each piece to move. All you need to do is edit the Offset or Scroll values to the desired values. Recently, a system to facilitate the ordering of parallaxes was implemented. All you need to do is edit the "SubLayer" value to the desired value, considering that the higher the number, the further forward it will be.

## Layer Switching

To prevent the player to gets stuck in loopings, please keep all the objects related to layer switching with the option "Inactive if too far from window" _DISABLED_. If you ever need the posibility of creating more complex level layouts, like S3 Angel Island Loop closer to the tree, or Sandopolis loop gimmick. With this you can get a start up in it. Layer 2 makes all layers deactivate, so you need to add an extra collision system that only checks for it. Layer 3 makes all layers activate, this can by tide to a gimmick of sort, like the already mention Sandopolis Act 2 Gimmick.

## Adding a new character

Duplicate a character, edit the CharacterID value and edit entire Player Animation section. Other than this, will require _specific_ actions coding. 

## Adding bridges

Duplicate a bridge spawner, edit the object width to a number multiples of 16 and the bridge will spawn the corresponding to (Width / 16).

## Helper Objects

### No Land Object
>If the sensors collides with this region, the angle detecting will be locked. This is useful for stairs using too short tiles, like 16x16 or sloped ledges.

### Crush Object
>It's self-explanatory, but that's okay. If the wall, ground or ceil sensors collide with this region, the player will be crushed.

### Stop Object
>Used to stop or revert direction for almost everything in the framework, like enemies and gimmicks. It's very useful as we don't need to create a sensor for each object.

### Angle Breakers
>Used to replicate that ramp launchers (that ones after the S-tunnels on Green Hill Zone)

## Used Groups (Qualifiers)

```
Group.0 - Solid // Flag 0 on = NON SOLID / Flag 0 off = SOLID
Group.1 - Platform
Group.2 - No Slope Checking
Group.3 - Layer 0
Group.4 - Layer 1
Group.5 - Special Slopes (for when it have issue to check angle)
Group.6 - Moving Platform
Group.7 - Pushable
Group.8 - Crushable
Group.9 - Attach Objects

Group.Data - Pausable (to stop the animations during the pause).
Group.Player - Skins
Group.Friends - Sensors
Group.Enemy - Badniks
Group.Arm - Hurtable Object
Group.Bullet - Bullet
Group.Shield - Global Stop
Group.Ball - Bumpers
Group.Invisible - Breaking Platforms
Group.Powerup - Monitors

Group.Drawning Tools - Bridges
Group.Neutral - Swing (Spawner)
Group.Good - Swing (Main Object)
Group.Engine - Remove objects outside the frame
Group.Flowers - Swing Ropes
Group.Reference Points - Invincible Stars

Group.Movable - Conveyor Belts
Group.Value Holder - Corkscrews
Group.Dissolving - Falling Platforms
Group.Waveform - Fans
Group.Particles - Bubbles
Group.Bosses - ...Bosses
Group.Arrows - Hanging Bars
Group.Clothes - Capsule
Group.Explosions - Explosions
Group.Keys - Switches
Group.Doors - Doors
Group.Obstacles= Solid 
(for when you want a Group.0 object to collide with another solid surface).
Group.Target - Portals

Group.Generic 1 - Platform
Group.Generic 2 - Spike Balls (Mighty)
```

## Math

You need to compare two general values to use these formulas. 
To get "compare two general values" condition, just click on gear icon and select the option there.

### Getting the distance between 2 points
```Abs(x1 - x2) pow 2 + abs(y1 - y2) pow 2```

### Getting the distance between 2 points (Euclidean)
```Sqr(((x1 - x2) + pow2) + ((y1 - y2) pow 2))```

### Getting the distance between 2 points (Manhathan)
```Abs(x1 - x2) + abs(y1 - y2)```

### Getting the angle between 2 points
```Atan2(y2 - y1, x2 - x1)```

### Getting the difference between two angles
##### If "Abs" is omitted the sign indicates the direction (clockwise or anti-clockwise)

```Abs((((a - b + 540) mod 360) - 180)```

### Generate random numbers
```RRandom(a, b)```

### Generate random numbers in the range A-B
```Random(b - a) + a```

### Check if a number is even
```<Insert Number> mod 2 = 0```

### Check if a number is odd
```<Insert Number> mod 2 = 1```

### Return the sign of a number
```<Insert Number> / Abs(<Insert Number>)```

### Convert a Hex Angle
```(256 - <Hex Angle>) * 1.40625```

### Flashing (Nihil's)
```Set alpha-blending coefficient to ((GlobalTimer("MasterLevel") / <flash cycle duration> ) mod 2) * 255```

### Flashing (YohananDiamond's)
```Set alpha-blending coefficient to Floor(( GlobalTimer("MasterLevel")  mod <flash cycle duration> * 2) / <flash cycle duration>) * 255```

### Lerp
```<x>*(1-<a>) + <y> * <a>```
