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

Lets take fourier transform to take a look at the frequency domain of our noisy wave.

![alt-text-1](Figure_2.png "title-1")

Next, we will apply our filter to the wave to try to clean it. We will do this with the follwing logic and plot the results.

```python
filtered_freq = [f if (950 < index < 1050 and f > 1) else 0 for index, f in enumerate(freq)]
```
![alt-text-1](Figure_3.png "title-1")

Finally, we will use the inverse fourier transform formula to revert our wave back to the time domain, and plot the results.

![alt-text-1](Figure_4.png "title-1")


The entire code will be as follows

```python
