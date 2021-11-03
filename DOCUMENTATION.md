# General Tips

- To close all the codes group, go to "Events" > "Close all groups".

- To increase the free space outside the frame, simply access "Tools" > "Proprieties" > "Frame Editor" and edit the "Margins" as you like.

- If you want to see a object in event editor by icon, name or both, simply go to "Tools" > "Proprieties" > "Event List Editor" and check the flags as you like.

- To make a backdrop solid, just check the object proprieties and set the Obstacle Type as "Obstacle".

- If the names in global events "disappear" go to "Application Proprieties" > "Events" and change the base frame.

- You can use search tool pressing CTRL+SHIFT+F.

# Core Framework

## Audio System

### Music Loop

To use the loop system, simply set the values of LoopEnd and LoopStart to the correct number values for the loop point. 

The loop points are measured exactly like normal music. But it can be confusing without the colons. so 123000 would be 1:23 exactly.

## Parallax System

In order to remove Sonic Worlds' limited parallax system, Lighto and me decided to work on a completely new system. In addition to allowing animations without the need for a workaround, it offers a better performance than using the Background System Box, built-in layers system or extensions. However, it can be tricky to use without understanding how the new system works first. Since this is a new system with different math, you cannot use the same values that you used in Worlds parallaxes. So you need to set different values.

It is important that you keep all the pieces in the top-left hotspot (0,0) and make sure all of them have the same height (e.g if you have a piece with 840 of height, make all the others have the same size). Then, we run one for each loops in order to create copies of the parallax actives that are already in the frame. Then, we give each object it's respective ID later. All you need to do is edit the offset or velocity variables according to your choice (check frame editor). Everything bellow is automatically calculated and should be kept in global events. When you need to customize something, go to frame editor and check there!

You need to make sure the starting image of each piece is the size you want. If the INITIAL image size is different from the CURRENT image size, the part will be calculated as if it had the INITIAL size! So if your image is 500x500 at the start and then change to 424x240 the calculation will be done based on the size of 500x500. The same can be said for images with different sizes between the appearing and stopped animations. Therefore, the system will ALWAYS detect the size that is appearing.


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
