# Unreal Engine Tickrate Limiter
## The Issue
Unreal Engine 1 & 2 games often have glitches related to high framerate. This can be solved for games that use DirectX 7 by simply enabling vsync with your monitor refresh rate set to a reasonable value, but what if you're not playing in fullscreen? And what about games that use DirectX 8, for which vsync currently doesn't work?
## The Solution
The Unreal Engine has a built-in framerate cap, but it's usually disabled. Via this simple patch, you can re-enable it. These patches specifically set it to 60, but you could in theory set it to any number.
## How Does It Work?
The engine limits the framerate by calling a function called `GetMaxTickRate`, implemented by the `UGameEngine` class. This function simply returns a floating point number representing the maximum number of ticks per second, and the game engine paces itself to match this number. This function is set to always return 0 in all the games that I've tested, but the patch makes it always return 60.
## How do I install it?
Grab the .ips file for your game, download [Lunar IPS](https://fusoya.eludevisibility.org/lips/), and apply the patch to your selected game's `Engine.dll` file, which can be found inside the `system` folder. You can verify that it's working by using the `stat fps` command to display the framerate (or the frametime, depending on the game).
