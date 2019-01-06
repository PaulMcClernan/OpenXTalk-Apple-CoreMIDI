# lcbCoreMIDI

IT'S ALIVE!!!

WHAT IS IT?:
  This is a LiveCode Builder Library, it builds a binary module that, when the module is loaded in the LiveCode Engine, adds handlers and utility functions for use in LiveCode Script for interacting with Apple's MIDI/Music Services.
  It allows your LiveCode scripts to do things like register as a MIDI Client, register as a virtual MIDI Source, send arbitrary bytes as MIDI Data though that LC Virtual Source, Retreive info from macOS various infos about the current state of the MIDI setup on the current system

So far this library consists of:
- LiveCode Builder (LCB) Bindings to create a MIDI Client and register as a Virtual MIDI Source from LiveCode Script.
- Handlers which creates a byte buffer that enables sending binary MIDI data out from LiveCode Script (LCS)
- TimeStamping, it has a seperate 'Send' handler that allows for sending MIDI messages with millisecond offsets from 0 (from when the bytes were passed to it) from LiveCode Script (LCS), obsuring away the conversion to nanosecond time stampings, and retreival (mach_kernel time, used by MIDI Services is a struct that includes division values to use to get most accurate timing on different clock speed processors) from the LCS.
- LiveCode Builder (LCB) Bindings to retreive various infos about the present state of the MIDI Setup on the system. (WIP)
