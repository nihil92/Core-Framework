This documentation is valid for version 0.23.02.

# Core Framework 

# INTRODUCTION

For get started, we assume that you have some prior knowledge related about Clickteam Fusion to use this framework. Otherwise, you might have trouble understanding how we made some stuff. For this reason, we recommend that you learn the following topics so that you don't have any problems developing on Core:

- Clickteam Fusion features and synthax;
- Alterable Values, Alterable Strings and Flags (Booleans);
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

# FUNCTIONS

``function_RandomPool``: Returns a random number from a defined list.
1. Set "PoolList" to the list of numbers you want to pick up. If you want to take a number bettween 1, 3 and 5, do it: "135".
2. Set "PoolDigits" to the number of digits your number have. If your numbers are ``1, 3, 5`` make it 1, if your numbers are ``08, 16, 32`` it is 2.
3. Run "function_RandomPool" 1 time.
4. Set your variable to the "PoolResult".

# SHADERS

Shaders are very useful tools for manipulating images. Using a shader lets you take advantage of the processing power of the GPU instead of the system CPU. As the shaders run on the graphics card itself, this means they are extremely fast to process, freeing up valuable CPU cycles for running the game. For example, in the past, we used the built-in Replace Color tool. But this was such a bad tool in terms of performance, that the screen would freeze for a few seconds before the level started to swap the colors. As we don't use this technique anymore, the game changes colors instantly. In Clickteam Fusion, shaders are called **"effects"**.


## How to select a effect

Just go to the object's properties and select the effect you like. Clickteam Fusion has some standard effects like monochrome, add, subtract, etc. but it is also possible to use custom effects.

## How to install a custom effect

Just extract the contents of the desired shader to the "Effects" folder contained in the main Clickteam Fusion directory. It is recommended that you install the effect before opening Clickteam Fusion. This will prevent some error messages in the location of the effect. But you can always "ignore" the warning message and remove the effect if you don't have the required effect.

## Included Effects

- Pixel Palette with lerp (DX9 and DX11)
- Studiopolis Glass (DX9 and DX11)

### Pixel Palette with lerp

This effect is used to switch from an **"original palette"** to a **"target palette"**. This can be done by defining the effect texture for a image with the desired palettes and editing the ``"lerpVal"`` parameter. Values closer to 0.0 will make the palette be more closer to the **original**, while values closer to 1.0 will make the palette be more closer to the **target** one. You can alternate two palettes smoothly, just setting the EffectParam ``"lerpVal"`` to ``Sin(GlobalTimer( "MasterLevel" ) * <desired value>)``. Furthermore, you can use something like ``Max(EffectParam( "Your Object", "lerpVal" ) + <desired value>, 1.0)`` to make a smooth transition between the **original palette** and the **target palette** (e.g. transition to sunset palette).

There are, however, some shader limitations depending on which DX version you use. The image must necessarily be 2x256, even though it doesn't fill all the space (you can leave a transparent space in this case). DX9 is limited to 32 colors per object, while DX11 is limited to 256. Also, this shader applied directly to the object can cause the Frame Editor to slow down on some computers. You can avoid this problem by hiding the layer the object in question is on. By the way, I recommend that you use the folders in the left corner instead of messing with objects outside the frame.

A variation of this shader can be used for the underwater palette. The problem is that the shader for water has a limitation and will not paint transparent objects. This doesn't look like a fault of Fusion, but of the way shaders work in DirectX11. Even in Orbinaut Framework, there is this limitation. We've tried to do everything we can to make it work, but that doesn't seem possible at the moment. Since the underwater palette effect don't reached good results for objects with transparency we decided to make it optional in the demo. If you want to use it, simply remove the "Set effect to subtract" line on the "Water (Pre)" group. Well, as long the shader works perfectly for a Genesis kind of game, as Sonic 2 TQ demonstrated well:

![image](https://user-images.githubusercontent.com/66818008/150613069-fda813e8-c460-4a17-bd83-4d4b189adcb3.png)


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

First, keep in mind that you can use whatever size you like, as long as all the pieces are at least the size of the window. If your game uses 320×224, all pieces must be **at least** this size. Otherwise, gaps between the parallax pieces can become visible. Furthermore, it is important that you keep all the pieces to the top left hotspot (0,0) and make sure all of the pieces have the same size (e.g. if you have a piece with 640x480 of size, make all the others have the same size). 

To generate a new parallax piece, simply clone a parallax piece by right-clicking on a parallax piece and accessing the "clone" option. This ensures that all parts maintain their properties correctly.

The system is fully automated, so you don't need to mess around with math for each piece to move. All you need to do is edit the Offset or Scroll values to the desired values. Recently, a system to facilitate the ordering of parallaxes was implemented. All you need to do is edit the "SubLayer" value to the desired value, considering that the higher the number, the further forward it will be.

Parallax has support for act transition, but this can be complex for beginners. The fact is that when the transition is activated, the framework automatically loads the positions that each piece of parallax had in the previous level room. Note that in ACT 1 the parallax IDs range from 1 to 4, but in ACT 2 they range from -1 to 4. This is because ACT 2 also uses the parallaxes from ACT 1. So to prevent them from appearing incorrectly in the transition, the IDs of each parallax piece need to match what they were in the previous level.

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
Group.2 - Cancel Slope Checking
Group.3 - Layer 0
Group.4 - Layer 1
Group.5 - Force Slope Checking
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
Group.Ball - Bumpers
Group.Invisible - Breaking Platforms
Group.Powerup - Monitors

Group.Drawning Tools - Bridges
Group.Neutral - Swing (Spawner)
Group.Good - Swing (Main Object)
Group.Engine - Remove objects outside the frame
Group.Reference Points - Invincible Stars

Group.Movable - Conveyor Belts
Group.Value Holder - Corkscrews
Group.Dissolving - Falling Platforms
Group.Waveform - Fans

Group.Bosses - ...Bosses
Group.Arrows - Hanging Bars
Group.Explosions - Explosions
Group.Keys - Switches
Group.Doors - Doors
Group.Obstacles - Solid 
(for when you want a Group.0 object to collide with another solid surface).
Group.Target - Portals

Group.Generic 1 - Platform
Group.Generic 2 - Spike Balls (Mighty)
```

## Limitations

- The underwater palette shader is not compatible with alpha blend (transparency).

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

### Convert "GameTimer"
```1000 * <Seconds>```

# OBJECTS USAGE

## Pushables

This block is one object labeled with the 'qualifier/group' ``Group.7`` which is associated to pushable objects behavior. If you want different behaviors, you can clone this block and edit the startup values.

Here is a explanation of the variables that you can edit.

- ``Weight`` As the name says, it defines the weight of the block. The lower the value used, the lighter the block will be. I recommend using the number 3 as default.
- ``LeftLimit`` Set the limit (in pixels) that the block can move to the left.
- ``RightLimit`` Set the limit (in pixels) that the block can move to the right.
- ``Direction`` Set the directions the block can move (0 for both, 1 for left and -1 for right).
- ``Repositionable`` Set whether the block can be repositioned to their original position after a certain distance.

This block is one object labeled with the 'qualifier/group' ``Group.7`` which is associated to pushable objects behavior. If you want different behaviors, you can clone this block and edit the startup values.
