*Full manuals are available for download from* https://www.caen.it/ :

*-- DT5742 User Manual*

*-- 742 Quick Start Guide*

*-- WaveDump User Manual*

*-- WaveDump QuickStart Guide*

# How to install Wavedump on Windows 10

**Step 1.** Digitizer driver

Download from caen.it

Turn on the digitizer and plug the USB cable into the desktop

If Windows doesn’t find the drivers, follow manual steps from 742 Quick Start manual

**Step 2.** Wavedump

Download from caen.it

Give administrator rights to the C:\ProgramFiles\CAEN\Digitizers\WaveDump directory

Issues can arise with Windows antiviruses, they can be fixed by adding C:\ProgramFiles\CAEN to exceptions


# How to make an Acquisition with Fast Trigger TRn

**Step 1.** Input signal

Negative pulse from pulse generator with ∼1 V amplitude, width ∼200 ns, and 200 Hz split into CH0 and TR0.

**Step 2.** Wavedump configuration files in \WaveDump\bin

Do NOT touch WaveDumpConfig.txt ever.

In WaveDumpConfig_X742.txt, edit:

      PULSE POLARITY          NEGATIVE 
      [0]
      DCOFFSET                -12
      #GRPCHDCOFFSET          3,0,0,0,0,0,0,0
      [TR0]
      DCOFFSET                32768
      TRIGGERTHRESHOLD        23574
 
 In case the signal is split into CH0 and TR0, use settings "Negative signal on TRn: V =0 ÷ -400 mV" from the manual table:
 
      Signal on TRn                             DC OFFSET     TRIGGER THRESHOLD
      NIM signal                                32768         20934
      Negative signal: V = 0 ÷ -400 mV          32768         23574
      Negative signal: V = 0 ÷ -200 mV          32768         24894
      Positive signal: V = 0 ÷ ≥2 V             43008         26214
      Positive signal: V = 0 ÷ 2 V              37287         26214
 
 
 # How to make an Acquisition with Self-Trigger

**Step 1.** Input signal

Negative pulse from pulse generator with ∼1 V amplitude, width ∼200 ns, and 200 kHz into CH0

**Step 2.** Wavedump configuration files in \WaveDump\bin

Do NOT touch WaveDumpConfig.txt ever.

In WaveDumpConfig_X742.txt, edit:

      #WRITE_REGISTER        8000 2000 2000
      WRITE_REGISTER         1080 9C4 FFFF
      WRITE_REGISTER         10A8 1 F
      DRS4_FREQUENCY         2

 # Using Wavedump

**Running/stopping acquisition**  Press “s”.

**Display traces**  Press “P”.

**Disable the display of a particular trace**  Press the number of the channel, e.g.  “1”. TR0 is channel 8.

**Change scale of display**  Press “a”.

**Write data**  Press “C”.

 
 
