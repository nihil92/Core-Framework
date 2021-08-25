# General Tips #

- To close all the codes group, go to "Events" > "Close all groups".

- To increase the free space outside the frame, simply access "Tools" > "Proprieties" > "Frame Editor" and edit the "Margins" as you like.

- If you want to see a object in event editor by icon, name or both, simply go to "Tools" > "Proprieties" > "Event List Editor" and check the flags as you like.

- To make a backdrop solid, just check the object proprieties and set the Obstacle Type as "Obstacle".

# Used Groups #

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

# Math

You need to compare two general values to use these formulas. 
To get "compare two general values" condition, just click on gear icon and select the option there.

## Getting the distance between 2 points
```Abs(x1 - x2) pow 2 + abs(y1 - y2) pow 2```

## Getting the distance between 2 points (Euclidean)
```Sqr(((x1 - x2) + pow2) + ((y1 - y2) pow 2))```

## Getting the distance between 2 points (Manhathan)
```Abs(x1 - x2) + abs(y1 - y2)```

## Getting the angle between 2 points
```Atan2(y2 - y1, x2 - x1)```

## Getting the difference between two angles
### If "Abs" is omitted the sign indicates the direction (clockwise or anti-clockwise)
```Abs((((a - b + 540) mod 360) - 180)```

## Generate random numbers
```RRandom(a, b)```

## Generate random numbers in the range A-B
```Random(b - a) + a```

## Check if a number is even
```I<Insert Number> mod 2 = 0```

## Check if a number is odd
```<Insert Number> mod 2 = 1```

## Return the sign of a number
```<Insert Number> / Abs(<Insert Number>)```

## Convert a Hex Angle
```(256 - <Hex Angle>) * 1.40625```

## Flashing (Nihil's)
Set alpha-blending coefficient to ```((GlobalTimer("MasterLevel") / <flash cycle duration> ) mod 2) * 255```

## Flashing (YohananDiamond's)
```Floor(( GlobalTimer("MasterLevel")  mod <flash cycle duration> * 2) / <flash cycle duration>) * 255```
