This documentation is valid for version 0.23.02.

# Core Framework 

# INTRODUCTION

For get started, we assume that you have some prior knowledge related about Clickteam Fusion to use this framework. Otherwise, you might have trouble understanding how we made some stuff. For this reason, we recommend that you learn the following topics so that you don't have any problems developing on Core:

- Clickteam Fusion features and synthax;
- Alterable Values, Alterable Strings and Flags;
- Arrays;
- Layer Object;
- Shaders Basics;
- Fast loops and for each loops;
- Groups/Qualifiers;
- Object Scoping;
- Expressions;

## General Tips

- To close all the codes group, go to _Events > Close all groups_.

- To increase the free space outside the frame, simply access _Tools > Proprieties > Frame Editor_ and edit the "Margins" as you like.

- If you want to see a object in event editor by icon, name or both, simply go to _Tools > Proprieties > Event List Editor_ and check the flags as you like.

- To make a backdrop solid, just check the object proprieties and set the Obstacle Type as "Obstacle".

- If the names in global events "disappear" go to _Application Proprieties > Events_ and change the base frame.

- You can use search tool pressing CTRL+SHIFT+F.


# SHADERS

Shaders are very useful tools for manipulating images. Using a shader lets you take advantage of the processing power of the GPU instead of the system CPU. As the shaders run on the graphics card itself, this means they are extremely fast to process, freeing up valuable CPU cycles for running the game. For example, in the past, we used the built-in Replace Color tool. But this was such a bad tool in terms of performance, that the screen would freeze for a few seconds before the level started to swap the colors. As we don't use this technique anymore, the game changes colors instantly. In Clickteam Fusion, shaders are called **"effects"**.


## How to select a effect

Just go to the object's properties and select the effect you like. Clickteam Fusion has some standard effects like monochrome, add, subtract, etc. but it is also possible to use custom effects.

## How to install a custom effect

Just extract the contents of the desired shader to the "Effects" folder contained in the main Clickteam Fusion directory. It is recommended that you install the effect before opening Clickteam Fusion. This will prevent some error messages in the location of the effect. But you can always "ignore" the warning message and remove the effect if you don't have the required effect.

## Included Effects

- Replace Color Smoothly (DX9 and DX11)
- Dynamic Color Replacer (DX9 and DX11)
- Studiopolis Glass (DX9 and DX11)

### Replace Color Smoothly

This shader was ordered from a Clickteam staff member so that we have an optimized option to have the glow effect on superforms and afterimages. This effect is used to switch from an **"original palette"** to a **"target palette"**. This can be done by defining textures for images with the desired palettes and editing the ``"lerpVal"`` parameter. Values closer to 0.0 will make the palette be the **original**, while values closer to 1.0 will make the palette be the **target** one. You can alternate two palettes smoothly, just setting the EffectParam ``"lerpVal"`` to ``Sin(GlobalTimer( "MasterLevel" ) * <desired value>)``. Furthermore, you can use something like ``Max(EffectParam( "Your Object", "lerpVal" ) + <desired value>, 1.0)`` to make a smooth transition between the **original palette** and the **target palette** (e.g. transition to sunset palette). 

There are, however, some shader limitations depending on which DirectX you use. DX9 is limited to 32 colors and works with alpha blend and semi-transparency, while DX11 is limited to 256 and does not work alpha blend and semi-transparency. For that, it was necessary to include an ``alpha`` parameter. If your application runs in DX11, use the parameter instead of blend coefficient **in the object that used the effect**. You can still use alpha/blend coef and semi-transparency in your application, as long as the object that uses the shader uses the parameter.

# CUSTOMIZATION OPTIONS PER LEVEL

We can set different options for each level. Whether there will have water or not, the type of goal or whether the level in question is an act 1 or 2, etc. To make it easier, we've created a group located at _Frame Editor > Level Unique > Custom Level_. Just edit the options you want.

# AUDIO SYSTEM

## Music Loop

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
