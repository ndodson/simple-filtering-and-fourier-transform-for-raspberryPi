# simple-filtering-and-fourier-transform-for-raspberryPi


First, we will generate a .wav file representing a 1000 Hz sine wave. Here is the code to do so.

```python
import numpy as np
import wave
import struct
import matplotlib.pyplot as plt

frequency = 1000
num_samples = 48000
noisy_freq = 50
sampling_rate = 48000.0
amplitude = 16000
file = "test.wav"
sine_wave = [np.sin(2 * np.pi * frequency * x1 / sampling_rate) for x1 in range(num_samples)]
```



Analyzing the clean wave, this is what we will have



<p align="center">
  <img width="460" height="300" src="https://github.com/ndodson/simple-filtering-and-fourier-transform-for-raspberryPi/blob/master/frequency.png">
</p>

<p align="center">
  <img width="600" height="300" src="https://github.com/ndodson/simple-filtering-and-fourier-transform-for-raspberryPi/blob/master/sin.png">
</p>


Next, we will add noise to our wave. We will do this by adding the followin lines to the above code.

``` python
sine_noise = [np.sin(2 * np.pi * noisy_freq * x1/  sampling_rate) for x1 in range(num_samples)]
combined_signal = sine_wave + sine_noise
```
