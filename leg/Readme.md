
First note how the PC works in the two modes: "ARM" and "Thumb" mode
https://stackoverflow.com/questions/24091566

Examine the leg.asm file.

Note that key1 is in "ARM" mode, and the 'bx' instruction in key2 switches to "Thumb" mode

Here's the calculations:

Python 3.7.5 (default, Apr 19 2020, 20:18:17) 
[GCC 9.2.1 20191008] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> key1 = 0x00008ce4
>>> key2 = 0x00008d08
>>> key2 += 4
>>> key3 = 0x00008d80 
>>> key1 + key2 + key3
108400

