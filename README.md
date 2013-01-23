sdr-examples
============

Examples of software defined radio code. Stuff I write while I mess around with [rtl-sdr](http://sdr.osmocom.org/trac/wiki/rtl-sdr).

I have some limited experience with audio-range DSP, but this is pretty much a new area for me. I've had trouble finding examples of SDR code that is accessible to someone who's just starting to understand the relevant theory. In fact, finding which theoretical concepts I should read about has been more difficult than it should be. This is my attempt at improving things. The software is intended to be as simple as possible, which probably means its performance will be lacking. The [80-20 rule](https://en.wikipedia.org/wiki/Pareto_principle#In_software) applies.

A note on [GNU Radio](http://gnuradio.org/)
-------------------------------------------

I've found GNU Radio (with [GR Companion](http://gnuradio.org/redmine/projects/gnuradio/wiki/GNURadioCompanion)) most helpful to understand high level theory (eg. how do I receive analog FM?). However, just linking ready-made blocks doesn't really allow you to understand how DSP *actually* works. As such, software in this repository doesn't use GNU Radio.

Repository structure
--------------------

The top level directory contains a library providing common DSP functionality (eg. filters). This document contains some pointers to theory relevant for SDR development. Specific example applications reside in subdirectories. Each example comes with some data dumps that can be used instead of rtl-sdr hardware.

Relevant theory
---------------

* [DSP page on Wikipedia](https://en.wikipedia.org/wiki/Digital_signal_processing) - read up on sampling, time and frequency domains
* [Some stuff on Fourier analysis](http://www.cs.man.ac.uk/~barry/mydocs/MyCOMP28512/Last%20year/MS11-3-Barry2.pdf)(PDF) - focused on audio applications, but I've found it more accessible than [the stuff on Wikipedia](https://en.wikipedia.org/wiki/Discrete_Fourier_transform).
* [Quadrature signals](http://www.dspguru.com/sites/dspguru/files/QuadSignals.pdf)(PDF) - thorough explanation of quadrature signals
* [NI page on I/Q data](http://www.ni.com/white-paper/4805/en) - the data we get from SDRs is in the form of I/Q samples
* [Wikipedia page on digital filters](https://en.wikipedia.org/wiki/Digital_filter)

You don't need to remember everything, but at the very least you should have some idea about this stuff before you try to understand the software.
