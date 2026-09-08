# SimpleSNESSoundEngine
Simple SNES Sound Engine for the SPC700 processor of the Super Nintendo Entertainment System

The Simple SNES Sound Engine is written in SPC700 assembly in accordance with [the SPCASM compiler](https://codeberg.org/filmroellchen/spcasm). It's aim is to provide a basic sound engine interface for those who wish to have granular control over their own SNES sound driver. 

The SPCASM compiler's version of [SPC700 assembly is well documented](https://spcasm.filmroellchen.eu/doc/), and those who wish to make custom changes to the sound engine would best be familiar with the instruction set. 
The SPCASM compiler is available as a [web app](https://spcasm.filmroellchen.eu/index.html), but for the purposes of this project the compiled program is used to compile the sound engine locally. 

## Compiling
The local SPCASM compiler is used to compile the sound driver program.
```
spcasm -f plain soundengine-spc700.s soundEngine-SPC700.BIN
```
The resulting soundEngine-SPC700.BIN file can be included in the SNES game ROM and then transferred to the APU. 

**Note that this binary file represents the whole memory space from 0x000 to 0xFFFF. If you wish to retain the 0x200 byte startup program to transfer data, then the first 0x200 bytes of the file must be skipped in the transfer to the APU!**

## Future Work
Currently the sound engine code is a snap shot of the sound engine as is present in the SNES game [〇 Star](https://inkbox-software.itch.io/zerostar). Future changes will come to a more generic version of the sound driver later including:

+ Only one song being allowed in memory at any time
+ Commands to prepare for data transfer for replacing the current song
+ Commands to pause and resume a song

These features will be rolling out within a few months
