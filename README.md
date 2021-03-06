Patch Editor/Librarian the XVA1 FPGA synth

Alpha 2_R2 release March 10 2021 - mostly there but does not support some of the latest XVA1 features.


This is an editor/librarian for the XVA1 FPGA synthesizer designed by Rene Ceballos. Details of the 
design and instructions for building the XFM2 are at Rene's website: https://www.futur3soundz.com/

Video demonstration of the XFM2 patch editor which is very similar: https://www.youtube.com/watch?v=Ny7eByV2aGQ

The XVA1 editor was created using CTRLR https://ctrlr.org/

Many thanks to the authors of the DX7 and TG33 CTRLR panels - I learned a lot from their work and used quite a bit of their graphics and code. 
I could not have achieved this without their efforts to guide me. I was still a helluva lot of work!

You will need to install CTRLR to use this editor a.k.a. a CTRLR panel. I recommend version
5.3.201 which is the current stable release. I had lots of issues with later releases of CTRLR.

The editor uses MIDI sysex messages only and does not use the XFM2 USB connection - but you will still need USB to power the XFM2.
You will need a MIDI adapter for your computer and you will have to build the XFM2 with MIDI in and MIDI out connectors.

** I recommend you wire the MIDI out ground to actual ground, not pin 28 as shown on Rene's web site. A couple of users have had problems because of that. 

The panel should be self explanatory if you have read Rene's documentation but managing patches 
deserves some explanation. The "Patch" subpanel on the global controls tab is where you load and save patches. 
There are four memories we have to manage:


Working (RAM) memory on the XFM2

Patch storage memory on the XFM2

Editor memory (state of the UI controls)

Disk storage


The "PGM Select" button sends MIDI program change messages to the XFM2 - this causes the XFM2 to load that program from patch storage to working memory.

To sync the editor UI to the XVA1 use "load"/"program from XFM2". After this is done any changes to the UI controls will be sent to the XVA1 and they should both stay in sync.

To save the current state of the XFM2 RAM to patch storage memory, first set the write slot (patch number) you want to use and "save"/"program to XVA1".

To save the current state of the editor to disk use "save"/"program to file"

To load a patch from disk use "load"/"program from file". This will load the editor AND the XFM2 RAM with the patch.


Format of the .syx files:

5 byte header 0xf0 0x43 0x00 0x00 0x00   - 3rd byte is XFM2 unit number, always 0 in .syx files

512 parameters stored in MSB LSB midi format. range of most XFM2 parameters is 0-255

1 byte trailer 0xf7




Rich Heslip rheslip@hotmail.com

