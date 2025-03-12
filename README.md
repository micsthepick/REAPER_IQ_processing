# REAPER_IQ_processing
Processing of IQ data from a Software Defined Radio

## Prerequisites
* REAPER (or a JSFX host)
* an IQ recording or a setup that allows live IQ analysis: example GNURadio Companion app included!
  - n.b. In order to listen to the output audio I ran reaper in WaveOut Mode at 384KHz and installed the optional ReaRoute ASIO driver and enabled that in the HiFi Cable, another way might be to use two audio cables both at 384KHz and ASIO4all, and finally to listen to the output cable, alternatively in macosx I've found that creating an aggregate device with blackhole (brew install blackhole-2ch or brew install blackhole-16ch) and the external speakers works quite well.
* CookDSP Library (may be found at https://github.com/belangeo/cookdsp)

## The scripts so far:

### Stereo_FM.jsfx
a stereo WBFM decoder written in JSFX.
So far it decodes FM signals found in the centre of the IQ, so make sure to tune the SDR exactly or preprocess the IQ samples to re-centre on the FM signal.
It low-passes the IQ to isolate the FM signal, isolates the 19KHz pilot with a complex valued Band-Pass, then locks a PLL to the tone, and demodulates the side channel with a sin(2*PLL_phase) wave, and demodulates the mid channel with a low pass. All this is done in realtime!
