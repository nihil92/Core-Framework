This changelog is all after Core Framework Plus release.

**0.22.11**

- Improved parallax system and added alot of significant documentation about it.
- To avoid confusion, we moved parallax and bubble numbers code groups into Frame Editor code, instead of Global.
- An better system for ring panning were implemented.
- **Control** and **Movement** code groups were optimised.
- Removed unecessary stuff on **Sensors** code group.
- Moved Angle Breakers into **Tools** code group.
- Thinking about beginners, we added an brand active to control the boss' camera. I know it sucked to remove, but now we have a much better system that only uses one active.
- Fixed top collision.
- Added Water Mark. So now you can set the water level again using a active.
- Updated Fling Ramps (graphics by joshyflip).
- Updated Bonus Stage frame.
- Fixed underwater bug.

**0.22.10**

- Fixed pitch audio.
- Fixed issues bettween test level and bonus stage.
- Fixed general issues with audio system.
- Added an event to reset values like invincibility, powershoes, trail, etc.
- Fixed bug with saving.

**0.22.09**

- Some glitches related all the characters appearing at the same time on bonus stage was been fixed.
- Fixed issue on level starting: It was starting on Bonus Stage before.
- The devkit now contains only SDL, Studiopolis Shader and the Dark Theme made by myself.

**0.22.08**

- The physics code has been completely overhauled and is now accurate to Genesis. Slope acceleration during landing were redone, air drag, movement and friction too.
- The code was entirely redone. Now all player-related variables boxes have been unified into a single object.
- Complete revision on camera code, featuring SCD's extended camera.
- The ring bounce code has been redone from scratch using a collision mask trick.
- The player's collisions have been improved to prevent the player from entering walls at high speeds.
- A whole new rotation method (much smoother than the previous one) has been implemented. We no longer depends of that Sonic Worlds' super complicated old system!
- Now the checkpoint saves which ones were activated when the frame restarts.
- Text Blitter for titlecards were redone.
- The water polls were removed.
- Fixed sensors shaking issue by removing transparent voids from sensors.
- The hanging action bugs were fixed.
- Improved hang lift code.
- Removed camera limiters for bosses.
- Revision on afterimage's code.
- The ground sensor collision were removed, now it is only used to landing and interaction with objects.
- The sparks from Thunder Shield no longer uses bounce ball.
- The ramps from Angel Island Zone were remade.
- Fixed bug where looping layer stays solid at high speeds when camera moves away from player. Set the "destroy object if too far from window" option to "NO" on layer objects.
- The monitors were completely revised.
- Audio System redone! Now 1-UP, volume, fade and frequency up/down work as intended.
- A ton of minor bugs were fixed. There are so many that it would not be worth listing them all here.
- Implemented a system to force landing on slopes that have angle detection problems. Use a slope as active with "Group.5".
- Implemented a new parallax system with actives instead of BSB.
- The events that load the lives you had were improved.
- The flashing glitch during window resizing Glitch is now fixed. Each time the screen size changes, you need to run the Screen loop 4 times.
- The blue spheres special stage was removed because it was unfinished.
- Titlecard was been improved.

**Notes**

- According to Clickteam staff, there are compatibility issues using "Identical" mode for global objects. Please use ONLY "Same Name and Type" if you want your objects to be global.
- Using "Wrap Horizontally" or "Wrap Vertically" in layer 1 can damage motobugs (it's fucking insane, but it happens).
- Do not use "machine independent-speed". It have some optimization issues, that can make some loops sudden stop do work correctly.

**0.13.2**

- Fixed bugs on data menu, angle flip and static motobug.
- Fixed black fade on Test Stage.
- Implemented Studiopolis shader.
- Improved Main Menu.
- Edited Level Layout.

**0.13.0**

- Looking up and crouch down camera bug was been fixed.
- Added "AllowLand = 1" as a "LAND" condition. Without fix fix, Sky Sanctuary Orb and other gimmicks can work as it was intended.
- Fixed Spindash Dust.
- Fixed drowning BGM.
- Fixed afterimage!
- Optimized Springs.
- Alot of common gimmicks were redone with substantial improvement, such like moving spikes, swing platforms, moving platforms, pushables, monitors (including the ones for signpost!!!), breakable blocks.
- Due to the change on pushables, StopPushables don't exist anymore.
- Now it's possible to attach objects to moving platforms (group.6). To use it, just place an object with (group.9) within a custom radius to the platform. Be careful, there are exceptional conditions for rings and monitors.
- Portal was redone, now it uses the qualifier TARGET.
- Implemented a main menu.
- Removed titlescreen.
- Named FLAGS.
	

**0.11.6**

- Edited Big Rings effect to a more stylish one (take a look in the loop I included in TAKING DAMAGE and the edit I made on the sprite and the effect events itself).
- Fixed a bug with movable spike.
- Fixed X Control (finally looks accurate).
- Fixed Life's monitor icon for Amy Rose.


**0.11.5**

- When the player went into debug mode inside the tunnel and then left, the player was no longer able to fall. This has been fixed.
- Fixed jump trough and falling platforms. Now it use also flag 2.
- Fixed falling platforms.
- Created rotation platforms from Scrap Brain Zone (from scratch).
- Palettes fixed.
- Fixed camera.
- Restored Mania's jogging animation.
- The deceleration quirk described in Sonic Physics Guide was wrong, so I improved the code. You can check it, taking a look over X Control code.
- Now music runs externally.
- 1 Up music is now more simple.
- Fixed Pellout odd glitch.
- The breakable walls had issues. I fixed this by setting speed Y to 0 at the time of the ground (I've cut from Y control and paste inside landing group).
- Fixed ring spawning.
- Fixed Ring Collision with solid objects.
- Fixed interaction of Mighty with spikes.
- Fixed capsule collision.
- Debug was disabled by default.
- Due to a request, I tried to port Core framework into non-DLC Fusion, but it's not possible anymore. Only if we sacrifice global events, so copy and paste all the code into frame editor and here we go.

**0.11.0**

- Revised Sensors, Movement Routines and Physics (X Control and Y Control). This fixes that damn bug in which Sonic detected angle on the corners of straight platforms/backdrops and that bug what makes Sonic stops in a 60/300º slope. The max land angle what the framework can reach is 78/282º (the original one reaches to ~80/280º -- Approximate value). It also fixes a weird bug collision on Swing Platforms.
- Fixed bugs in Mighty's Hammer Drop and Ray's Glide.
- Fixed Knuckles gliding and revised fall/land. Now Knuckles can do spindash after the fall/land after glide, as it was intended to do.
- Fixed lives issue. Now it load the lives you was before, instead of erase everything and put 3.
- Fixed Swing Platforms collision in swing platform group. Yeah, it's appart the revision over sensors, movement routines and physics. Both needs to still on the code to make everything works. 
- Fixed save slots.
- Limited save slots to 10 instead of 100. To change this, simply change the X Dimension of the array responsible to save the progress.
- Increased input support, adding options for PS4 and Xbox One controller -- was added by Ainand. 

**0.9.5**

- Fixed landing bug.
- Fixed stuck in the slope bug -- Thanks for Israel!


**0.9.4**

- All the shaders was been removed.
- Added fireball thrower gimmick.
- X axis control was been redone.
- All the characters animations was been redone.
- Added Camera Lag to Fire Shield.
- Replaced ini by array.
- Redone loading screen from scratch.
- Improved the entire water code.
- Physics now use accurate values.
- Gumball Machine bonus was been implemented.
- A brand new transition between acts system was been included.
- Renamed Alterable Values ​​to facilitate the understanding of the average user.
- Unified looking up, crouch down and skidding animations for the same ID (e.g. looking up and looking up reverse now use the same ID).
- Angle Calculator was been removed. Now the angle changes directly in the events responsible for angle detection.
- Added 2 new camera modes: 3 (Death) and 4 (Act 2 transition).
- Fixed Control Lock
- Skidding, Ray's glide and Tails flying was been improved.
- Fixed balancing animations.
- Breakable Walls now seems accurate.
- Now animation and player angle will always be "0" when on the air like it was supposed to be. This fix weird bugs, like, if you suffered damage while walking in a slope, the knockout or death animation showed the angle changing for a few seconds. And when you were thrown down the ramps or diagonal springs in a slope, the same thing happened. All of this has been fixed.
- Fixed ceiling land bug.
- Added GHZ collapsing floor created by Dark.
- Implemented a all new Genesis fade.
- Now the breakable blocks can be destroyed from below during springs action (like Mania).
- Fixed a bug on top collision.
- Implemented a new variable on PlayerMovementValues2 called StoreXSpeed, like the name suggests it only store the current XSpeed of the character when on the ground. This is used to make Chopp's animation works correctly. I mean, according with SPG animation speed should be the same in case of the player is rolling and swap to air state.
- Removed alot of UNUSED values.
- Now Mighty can deflect bullets from the enemies during spindash action.
- LifeGain was moved to a global value. We have now a life gain value for lives obtained by collecting rings and another one for lives obtained by reaching 50,00 points like Genesis games.
- Now the player can receive 1 extra life if it reaches 50,000 points (I've used Chopps system as a base to do this one).
- Now the user can set the number of rings to receive a extra life. The same for score.
- Insta-Shield from Sonic 3 is back and now it deflect bullets too!
- Fixed a small issue on Combine Rings collision.
- Fixed lava gimmick.
- Redone Debug Mode.
- Redone Air Roll.
- Redone Top Collision.
- Fixed shield trigger for gimmicks (flippers, bounce floor, oil pools, oil falls and bumpers).
- Fixed Tail's animations.
- Removed the functions of JumpVariable related to shields. Now it is used ONLY to stop jump in the air. If you want to cancel the stop jump in the air simply set the JumpVariable to -1.
- Implemented a all new code for Shields. Now we use a value called ShieldLimit to perform the special skills.
- Redone X/Y Movement.
- Added vertical tunnels.
- Improved Game Over/Time Over.
- Removed Death Layer object. It was replaced by a variable instead.
- Improved landing and fixed Hammer Drop landing.
- Fling Ramps, Moving Spikes and Vaporwave Mode was been redone.
- Fang/Nack easter egg was been added.
- Implemented a new animation system for goal sign.
- The waterfall sound effect have a more smooth sound effect that obey the volume options and the music loop.
- Now skidding use the same physics of X Control group and the original skidding code was been redone.
- Added our own SDL input code made from scratch.
- Fixed boss bugs related to pause.
- Now pause is significantly faster.
- Spining speed is now based of the physic guide animation system (or HedgeSpin)
- Edits to badniks (Newtron and Buzzbomber) and HPZ/SSZ teleporter.
- Fixed drowning for what seems like the 10th time, redone bubble numbers.
- Fade has been fixed, fade in happens after a 1up only now.
- Now the code was ported to global events. Due to this change, this version are not recommended for non-Plus Fusion users or low-end PC users.
- Redone entire sensors code, making this version uncompatible with any previous version.
- The titlecard code was improved by Dark with some adjustments of YohananDiamond.
- Updated the collision method of the combine rings.
- Redone Warp Ring.
- Sky Sactuary Teleporter and Hang Lift was been added. We don't use exactly the same method as Worlds, so it's a redone from scratch.
- Amy Rose was been added.
- Added a brand new scale effect and optimizations for P3D spike ball.


