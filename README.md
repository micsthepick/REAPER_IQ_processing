# REAPER_IQ_processing
Processing of IQ data from a Software Defined Radio

## Prerequisites
REAPER (or a JSFX host)
an IQ recording or a setup that allows live IQ analysis: example GNURadio Companion app included!

## The scripts so far:

### Stereo_FM.jsfx
a stereo WBFM decoder written in JSFX.
So far it decodes FM signals found in the centre of the IQ, so make sure to tune the SDR exactly or preprocess the IQ samples to re-centre on the FM signal.
It low-passes the IQ to isolate the FM signal, isolates the 19KHz pilot with a complex valued Band-Pass, then locks a PLL to the tone, and demodulates the side channel with a sin(2*PLL_phase) wave, and demodulates the mid channel with a low pass. All this is done in realtime!
