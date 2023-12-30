# Max/MSP Abstraction:   
## br.stutter.c.1.0



By Brian Riordan  
[guaguanco127@gmail.com](mailto:guaguanco127@gmail.com)  
[brianriordanmusic@gmail.com](mailto:brianriordanmusic@gmail.com)  
[https://www.brianriordanmusic.com/](https://www.brianriordanmusic.com/) 
  
Repository for br.stutter.c.1.0, with all related files, can be found here: [https://github.com/guaguanco127/br.stutter.c.1.0](https://github.com/guaguanco127/br.stutter.c.1.0)  
Additional programs can be found here: [https://github.com/guaguanco127/plugins](https://github.com/guaguanco127/plugins)

These files were created with Max/MSP version 8.5.6. 

## Table of Contents 

[About](#About)   
[What is an abstraction?](#Abstraction)  
[How To Install](#Install)  
[How To Use](#Use) 
 
 

## <a name="About"></a>About

This is an abstraction for Max/MSP that is built around the Max/MSP stutter~ object. This contains all features as the br.stutter.b.1.0 but with extras. This effect includes an auto re-triggering feature, auto-detection, adjustment of the phase (starting position) of the grains, and a refresher that restarts the grain when it reaches a certain position within the phase.

For simpler version of this effect, try [br.stutter.a.1.0](https://github.com/guaguanco127/br.stutter.a.1.0) or [br.stutter.b.1.0](https://github.com/guaguanco127/br.stutter.b.1.0)
  
**On/Off:** When Stutter is turned on, the signal is interrupted and a history of the signal is repeated based on the grain size. 

**Button:** While the stutter is on, pressing the button acts like a re-trigger, capturing another grain of the live signal that was fed into the stutter at the time, regardless of what the stutter was just playing. There is no feedback option. 

**Speed:** The playback speed of the grains. 1.0 is the default and is normal speed. Negative speeds play the grains backwards. The range is a float from -32.0 and 32.0. 

**Latent Mode:** When "Latent" is on, the stutter waits to record the next grain of sound before switching to the next stutter sound. The latency is equal to the next grain size. This is a valuable feature because it captures what comes next, as opposed to what already has come and gone. Turning the latent mode off captures the previous grain size prior to pressing the re-trigger button. The default is on. 

**Mix Mode:** There are two mix modes, "Gate" and "Insert" with "Gate being the default. "Gate" allows the dry unaffected signal to pass through while the stutter effect is turned off. The dry signal then mutes once the stuter is turnes on. This feature is best in an effects chain. The "Insert" mode does not allow any dry signal to pass through while the stutter effect is turned off. Instead, you only hear the grains play once the effect is turned on. This feature is useful for auxilliary effect return tracks. 

**Auto Mode:** When turned on, it automatically starts to randomly re-trigger the effect. "Auto 1" is compared with "Auto 2" and a random size is chosen between these two parameters. The range is between 100 ms and 2000 ms.

**Auto 1:** The first potential auto mode timings. "Auto 1" is compared with "Auto 2" and a random size is chosen between these two parameters. The range is between 100 ms and 2000 ms. The default is set to 100 ms. 

**Auto 2:** The second potential auto mode timings. "Auto 1" is compared with "Auto 2" and a random size is chosen between these two parameters. The range is between 100 ms and 2000 ms. The default is set to 1000 ms. 

**Transient Detect:** When both "Stutter" and "Detect" are on, the effect and re-trigger will occur automatically based on the transient detection sensitivity settings. Detections cannot occur faster than 100 ms.   

**Sensativity:** When both "Stutter" and "Detect" are on, this will determine how sensitive the transient detection is. Between 0. and 1., 0. is the lowest sensitivity, while 1. is the most sensitive. 0.5 is the default

**Refresh Button:** Press this button and the stutter grain will restart from the beginning. 

**Refresh Mode:** Potential modes for automatically restarting the grain from the beginning. When "Off" is selected the "Refresh Phase" is reset to 1.0. When "Cascara" is selected, each grain will either play its full duration, or half of its duration. When "Prog" is selected, each grain will either play its full duration, or 66% of its duration. When "Random" is selected, each grain will refresh at a random point in  its duration. All settings except for "Off" reset the "Refresh Phase" to 0.0. 

**Refresh Phase:** While the "Refresh Mode" is turned off, adjusting the "Refresh Phase" adjusts the phase, or the starting position) of each grain.  

**Size:** The size, in milliseconds, of the current grain that is playing. "Size 1" is compared with "Size 2" and a random size is chosen between these two parameters. The range is between 5 ms and 1000 ms. This is only a meter that tells you its size, you cannot adjust it. 

**Size 1:** The first potential size timings. "Size 1" is compared with "Size 2" and a random size is chosen between these two parameters. The range is between 5 ms and 1000 ms. The default is set to 5 ms.

**Size 2:** The second potential size timings. "Size 1" is compared with "Size 2" and a random size is chosen between these two parameters. The range is between 5 ms and 1000 ms. The default is set to 1000 ms.

**Filter Type:** Defines how the grains will be filtered based on the "Filter Shape." "Off" is the default, and the two different filter types are "Lowpass" and "Bandpass" 

**Filter Shape:** The shape of the filter envelope for the duration of each grain. "Sine" is a basic sine ton going up then down. "Up" is a upward phasing sawtooth wave. "Tri" is a triange shape that is the opposite direction of the sine tone. "Down" is the opposite of the "Up" as it is a downward phasing sawtoth wave. "Square" alternates between "Freq 1" and "Freq 2" without phasing in between. "Rand Step" randomly selects a different filter frequency and "Rand Ramp" randomly envelopes to the next filter frequency. The range of the filter is between "Freq 1" and "Freq 2" 

**Freq 1:** The first of the two frequency ranges that dictate the range of the filter shape envelope. Can be set above or below "Freq 2" 

**Freq 2:** The second of the two frequency ranges that dictate the range of the filter shape envelope. Can be set above or below "Freq 1" 

**Ressonance:** The ressonance of the filter. 0. is the default, and the range is between 0.0 and 0.85

**Amp Mode:** Defines how amplitude envelopes will be applied to each grain. Sine moves up then down, up moves from silence up to full amplitude for the duration of the grain, tri moves down then up, down starts at full amplitude then down to silence, rand step is a random amplitude for the duration of each grain, and rand ramp is an envelope that ramps up and down randomly across the duration of the grain.

**Amp Width:** The width, or the duty cycle, of the phase of the amplitude envelope. 

**Pan Mode:** Defines how the grains will be panned in the stereo field. The different modes are sine tone, right (each grain moves from left to right), triangle, left (each grain moves from right to left), alt (each grain alternates between hard left then right), rand step (each grain starts from a random position) rand ramp (each grain pans in a random direction for its duration before moving differently each time), and rand start (each re-trigger plays from a different random panning position. 

**Spread:** The "width" of the stereo spread of the grains. The default is 100.


## <a name="Install"></a>How To Install 

1. Make sure you have Max/MSP 8 installed in your computer. And, make sure you are using a Max patch that is inside of a folder.  

2. Copy and paste br.stutter.c.abs.1.0.maxpat inside of the same folder as the Max patch you are using.    

3. In the Max patch you are using, create an object called br.stutter.c.abs.1.0 

4. Alternatively, you could also create this inside of a bpatcher object and use all of the preset UI objects featured inside the abstraction. To do this, create a bpatcher object. Then, go inside of its inspector, select "choose" next to "Patcher File" and select the br.munge.abs.1.0.maxpat located within the same folder as your project. 

## <a name="Use"></a>How To Use

Read the "Above" section and inspect each inlet of the abstraction. 



 





