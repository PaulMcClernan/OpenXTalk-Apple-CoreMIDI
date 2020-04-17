# LiveCode Builder CoreMIDI Library

## WHAT IT IS:

  This is a LiveCode Builder Library for macOS (possibly iOS too) that builds as a binary module that, when the module is loaded in the LiveCode Engine, adds handlers and utility functions for use in LiveCode Script for interacting with Apple's MIDI/Music Services.
  It allows your LiveCode scripts to do things like register as a MIDI Client, register as a virtual MIDI Source, send arbitrary bytes as MIDI Data though that LC Virtual Source, and Retreive various infos about the current state of the MIDI setup from the OS. This repo also includes a few demo LiveCode stacks that can be used in conjunction with GarageBand or other external MIDI app to see how it works.

A short video demonstration (early version) is veiwable here:
https://www.youtube.com/watch?v=ruauWh3INfw

Another more recent demo:
https://www.youtube.com/watch?v=s_knX8mJg1c

### So far this library consists of:

- LiveCode Builder (LCB) Bindings to create a MIDI Client and register as a Virtual MIDI Source from LiveCode Script.
- Handlers which creates a byte buffer that enables sending binary MIDI data out from LiveCode Script (LCS)
- TimeStamping, it has a seperate 'Send' handler that allows for sending MIDI messages with millisecond offsets from 0 (from when the bytes were passed to it) from LiveCode Script (LCS), obsuring away the conversion to nanosecond time stampings, and retreival (mach_kernel time, used by MIDI Services is a struct that includes division values to use to get most accurate timing on different clock speed processors) from the LCS.
- In-line Documentation markup describing the handlers of the library module for LiveCode's Dictionary.
- LiveCode Builder (LCB) Bindings to retreive various infos about the present state of the MIDI Setup on the system, mostly Plist XML right now (WIP).
- Utility handlers for generating common MIDI messages (no converting to bytes needed) such as Note On/Off, Pitchbend, Controllers, etc.
- Some more Error Checking and Reporting in the LCB end to return descriptive information about any errors that may occur.
- MIDI Setup changed notifications to alert LiveCode of changes to the current setup (a MIDI Instrument gets turned off for example)

### To Do:

- MIDI In with callbacks to tell LiveCode engine that new incoming MIDI Data is available for receiving and processing any related TimeStamp info for received MIDI events (Core MIDI nanoseconds to milliseconds for LC)

- Add handlers & functions for connecting to/from Destinations, Ports, Entities and Endpoints that are available on the current system, and for determining whether an Device / object is offline or not.

- Add handlers & functions for using Apple's Music Player Sequencing Services to create and record tracks in multi-track sequences, associate endpoints with tracks, right data out to Standard Files, etc.

- Add transport function (AppleEvent) Messages for Stop, Start, Pause, Play, Record (See demo stack for transport control of GarageBand via AppleSCript).

- Add bindings for MIDI Thru Connection, a part of Core MIDI that facilitates realtime manipulation of MIDI Data as it passes though the MIDI Setup.

### To Do...(Maybe):

- maybe merge in my GM MIDI Utils Project (for GM/GS standard Names, Numbers, Controller Names, etc.)

- maybe Port to LCB, or replace with LCB, UDI's Hypercard style 'ABC' Notation compatible opensource LCS Lib called makeSMF. This library was very well written all the way back in the early 2000s (late 1990s?). I've already updated it slightly, mostly to use 'bytes' instead of 'char' keyword (since it was written LiveCode has become fully Unicode ready, so a 'char' could be multi-byte unicode).

- maybe port to LCB, or replace with LCB, my LCS scripts for dealing with MIDI's variable length quantities (VLQ), converting back and forth from 7-bits-per-byte (VLQ) to and from standard 8 bit bytes, hex, or decimal numbers. Useful for encoding and decoding TimeStamp numbers in the Standard MIDI file specification.
