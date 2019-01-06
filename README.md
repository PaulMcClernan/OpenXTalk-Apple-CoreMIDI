# lcbCoreMIDI

IT'S ALIVE!!!

WHAT IS IT?:
This is a LiveCode Builder Library that builds a module that, when the module is loaded in the LiveCode Engine, adds handlers and utility functions for use in LiveCode Script that register LiveCode as a MIDI Client, register LiveCode as a virtual MIDI Source.

So far this library consists of:
- LiveCode Builder (LCB) Bindings to create a MIDI Client and register as a Virtual MIDI Source from LiveCode Script.
- Handlers which creates a byte buffer that enables sending binary MIDI data out from LiveCode Script (LCS)
- TimeStamping, it has a seperate Send handler that allows for sending MIDI messages with millisecond offsets from 0 (or now) from LiveCode Script (LCS), obsuring away the nanosecond time stampings retreival (mach_kernel time, a struct that includes division values to use to get most accurate timing on different clock speed processors) and subsequent math from the LCS. 
- LiveCode Builder (LCB) Bindings to retreive various infos about the present state of the MIDI Setup on the system. (WIP)
