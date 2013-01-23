Wideband analog FM receiver
===========================

Build & use
-----------
The only non-standard library you'll need is [FFTW](http://www.fftw.org/). Build with
`make`

To run it:
>Usage: fm_receiver [OPTIONS]
>
>Valid options:

>  -r file         Use recorded data from file instead of an rtl-sdr device

>  -f frequency    Frequency to tune to, in Hz (default: 97.70 MHz)

>  -d device_index Rtl-sdr device index (default: 0)

>  -h              Show help


FM demodulation
---------------

In the context of SDR, analog FM demodulation usually works like this:
* apply a low-pass filter on the baseband signal - wideband FM is around 150 KHz wide
* use a [quadrature phase detector](https://en.wikipedia.org/wiki/Detector_%28radio%29#Quadrature_detector) to demodulate the signal
* apply another low-pass filter to filter out anything above the [15 KHz mono sound](https://en.wikipedia.org/wiki/FM_broadcasting#Other_subcarrier_services)
* downsample to sound card frequency
* apply a [de-emphasis](https://en.wikipedia.org/wiki/FM_broadcasting#Pre-emphasis_and_de-emphasis) filter

Optionally, the signal from 23 to 53 kHz can be mixed with the mono sound to obtain stereo sound. See the [Wikipedia page on FM broadcasting](https://en.wikipedia.org/wiki/FM_broadcasting#Other_subcarrier_services).

[This Linux Journal article](http://www.linuxjournal.com/article/7505?page=0,0) explains everything in a lot more detail.

Limitations
-----------

This software skips the first low-pass filter (for me there's not much noise with a 500 KHz baseband). The audio low pass filter is implemented using FFT rather than the faster, and more common, [FIR filter](https://en.wikipedia.org/wiki/Finite_impulse_response) approach. In addition, there's no [FFT windowing](https://en.wikipedia.org/wiki/Window_function#Spectral_analysis), which adds a bit of noise. Downsampling is down to non-standard 50KHz. The de-emphasis filter is also skipped. It only decodes mono sound.

Even with these limitations, the sound quality is acceptable.

Included data
-------------

The data folder includes short rtl_sdr I/Q capture files of some local radio stations. You can use the '-r' flag to listen to them.
