## Parallax System

In order to remove Sonic Worlds' limited parallax system, me, Lighto and Y.D decided to work on a completely new system. In addition to allowing animated parallaxes without the need for a workaround, it offers a better performance than using the Background System Box, built-in layers system or extensions. However, it can be tricky to use without understanding how the new system works first. Since this is a new system with different math, you cannot use the same values that you used in Worlds parallaxes. So you need to set different values.

### Basic usage

First of all, keep in mind that all the pieces should have **at least** 424x240 of size. Then, it is important that you keep all the pieces in the top-left hotspot (0,0) and make sure all of the pieces have the same size (e.g if you have a piece with 640x480 of size, make all the others have the same size). To generate another parallax, simply copy a parallax piece using right click, so that the generated active keeps the variable names and their group. 

Furthermore, you need to make sure the starting image of each piece is the size you want. If the INITIAL image size is different from the CURRENT image size, the part will be calculated as if it had the INITIAL size! So if your image is 500x500 at the start and then change to 424x240 the calculation will be done based on the size of 500x500. The same can be said for images with different sizes between the appearing and stopped animations. Therefore, the system will ALWAYS detect the size that is appearing.
