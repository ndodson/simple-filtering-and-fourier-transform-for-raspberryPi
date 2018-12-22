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


![alt-text-1](sin.png "title-1") ![alt-text-2](frequency.png "title-2")


Next, we will add noise to our wave. We will do this by adding the following lines to the above code.

``` python
sine_noise = [np.sin(2 * np.pi * noisy_freq * x1/  sampling_rate) for x1 in range(num_samples)]
combined_signal = sine_wave + sine_noise
```
If we plot the data thus far, this is what we wil have.

![alt-text-1](Figure_1.png "title-1")


