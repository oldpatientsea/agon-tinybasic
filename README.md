# agon-tinybasic
Port of Tom Pittman's Tiny Basic to the Agon Light. See http://www.ittybittycomputers.com/IttyBitty/TinyBasic/index.htm

To compile, open the tinybasic.zdsproj with Zilog's Developer Studio II. This is Windows software (which works on Wine) and free as in beer, not free as in speech. Tested with ZDS II 5.3.5 on Debian 11 Bullseye using the version of Wine in the official stable repository (wine-5.0.3 (Debian 5.0.3-3)).

ZDS II outputs a .hex file which you can convert to a .bin for example by running -

```
objcopy -I ihex tinybasic.hex -O binary tinybasic.bin 
```

```objcopy``` is part of binutils.

The bin file can then be copied to the microSD card and run on the Agon Light.

It should be fairly easy to get this to compile using SDCC but I haven't tried it yet.

## What Is It?

Defining Tiny BASIC for the Homebrew Computer Club, Pittman wrote, "Tiny BASIC is a proper subset of Dartmouth BASIC, consisting of the following statement types only: LET, PRINT, INPUT, IF, GOTO, GOSUB, RETURN, END, CLEAR, LIST, RUN. Arithmetic is in 16-bit integers only with the operators + - * / and nested parentheses. There are only the 26 single letter variable names A, B, ...Z, and no functions. There are no strings or arrays... Tiny BASIC specifies line numbers less than 256."

Note, this version of Tiny BASIC is written in C not assembly and is an order of magnitude larger as a result. Tom Pittman's BASIC is implemented in a virtual machine which is in turn interpreted. This is true to the spirit of the [original design](http://www.ittybittycomputers.com/IttyBitty/TinyBasic/DDJ1/Design.html).  

There's copy of the relevant sections of the Dr Dobb's articles describing both the original Tiny BASIC and the C version in the thirdpartydocs folder, along with a copy of Tom Pittman's original c source.

## How to Run Tiny BASIC

```
load tinybasic.bin
run
```

or to load a BASIC listing from a txt file, eg Euphoria.txt from the examples directory:

```
load tinybasic.bin
run . Euphoria.txt
```
The ```.``` informs MOS to use the default value there (&40000) which is the start of the area of the memory map reserved for the user programs.

## How to Quit Tiny BASIC

The StopIt function has not been implemented yet so for now you need to reset the Agon Light to quit.

## Licence

Tiny Basic Intermediate Language Interpreter C version (c) Tom Pittman -- 2004 July 19 

Licence: 
"My TinyBasic is free to use. If you want to conform to the letter of the law, 
you can attach to any copies this notice: 'TinyBasic interpreter Copyright 1976 Itty 
Bitty Computers, used by permission.'" 
http://www.ittybittycomputers.com/IttyBitty/TinyBasic/ 

Combined with the Agon template by Jeroen Venema 
https://github.com/envenomator/Agon.
Licence: GNU General Public License v3.0

Minor changes to make it to run on Agon Light by Tim Delmare 2023
https://github.com/oldpatientsea/agon-tinybasic
Licence: GNU General Public License v3.0

