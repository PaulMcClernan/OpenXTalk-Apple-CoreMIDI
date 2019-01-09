# lcbCoreMIDI

IT'S ALIVE!!!

WHAT IS IT?:

  This is a LiveCode Builder Library for macOS (possibly iOS too) that builds as a binary module that, when the module is loaded in the LiveCode Engine, adds handlers and utility functions for use in LiveCode Script for interacting with Apple's MIDI/Music Services.
  It allows your LiveCode scripts to do things like register as a MIDI Client, register as a virtual MIDI Source, send arbitrary bytes as MIDI Data though that LC Virtual Source, Retreive info from macOS various infos about the current state of the MIDI setup on the current system. This repo also includes a few demo LiveCode stacks that can be used in conjunction with GarageBand or other external MIDI app to see how it works.

So far this library consists of:

- LiveCode Builder (LCB) Bindings to create a MIDI Client and register as a Virtual MIDI Source from LiveCode Script.
- Handlers which creates a byte buffer that enables sending binary MIDI data out from LiveCode Script (LCS)
- TimeStamping, it has a seperate 'Send' handler that allows for sending MIDI messages with millisecond offsets from 0 (from when the bytes were passed to it) from LiveCode Script (LCS), obsuring away the conversion to nanosecond time stampings, and retreival (mach_kernel time, used by MIDI Services is a struct that includes division values to use to get most accurate timing on different clock speed processors) from the LCS.
- LiveCode Builder (LCB) Bindings to retreive various infos about the present state of the MIDI Setup on the system, mostly Plist XML right now (WIP).


To Do:
- Some Error Checking and Reporting in the LCB end to return descriptive information about any errors that may occur.
- Create the in-line Documentation markup describing the handlers of the library module for LiveCode's Dictionary.
- MIDI In with callbacks to tell new incoming MIDI Data is available for passing to the LiveCode engine and any processing any related TimeStamp info for received MIDI events (Core MIDI nanoseconds to milliseconds for LC)
- MIDI Setup changed notifications to alert LiveCode of changes to the current setup (a MIDI Instrument gets turned off for example)
- Add AudioToolbox / AUAudioUnit / Core Audio Kit bindings to create an AUGraph and load Apple's DLS Synth virtual instrument, this will give LiveCode Script new handlers to load SoundFont SF2 files or Downloadable DLS files into it for uses in direct playback of MIDI from LiveCode (no GarageBand or other MIDI apps needed).
- Add handlers & functions for connecting to/from other Sources, Destinations, Ports, Entities and Endpoints that are available on the current system, and for determining whether an Device / object is offline or not.
- Also need to add functions to read SoundBank info from the SoundFont SF2 or DLS files, for use with selecting sounds from the file and in sending Bank Change/Patch Change MIDI Messages to select them in your MIDI streams or file. I already created a few LC Scripts that parse both SF2 and DLS (they are both RIFF Container formats) for bank/patch names info, see the demo stacks in my other project LiveCode AVMIDIPLayer (that can already load SF2 or DLS but can only playback Standard MIDI Files, not for live performance/instantaneous play)
- Add handlers & functions for using Apple's Music Player Sequencing Services to create and record tracks in multi-track sequences, associate endpoints with tracks, right data out to Standard Files, etc.
- Add transport function MIDI Messages Stop, Start, Pause, Play, Record (See demo stack for transport control of GarageBand via AppleSCript.)
- Add bindings for MIDI Thru Connection, a part of Core MIDI that facilitates realtime manipulation of MIDI Data as it passes though the MIDI Setup.

To Do, Maybe:

- maybe merge in my GM MIDI Utils Project (for GM/GS standard Names, Numbers, Controller Names, etc.)
- maybe Port to LCB, or replace with LCB, UDI's Hypercard style 'ABC' Notation compatible opensource LCS Lib called makeSMF. This library was very well written all the way back in the early 2000s (late 1990s?). I've already updated it slightly, mostly to use 'bytes' instead of 'char' keyword (since it was written LiveCode has become fully Unicode ready, so a 'char' could be multi-byte unicode).
- maybe port to LCB, or replace with LCB, my LCS scripts for dealing with MIDI's variable length quantities (VLQ), converting back and forth from 7-bits-per-byte (VLQ) to and from standard 8 bit bytes, hex, or decimal numbers. Useful for encoding and decoding TimeStamp numbers in the Standard MIDI file specification.
