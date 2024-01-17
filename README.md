# Piezo Lick Detector

An amplifier for detecting rodent licks using piezo-based sensor systems

## General Use

Each board has three channels that can receive separate input from three different piezo sensors. Each channel has independently controllable gain and dual outputs: raw analog voltage and 5V TTL.

### Piezo Concerns

- We use 12mm piezo disks that are extremely common and cheap. 

- "Positive" input on the amp is considered the crystal side of the piezo (the white center of the disk/strip) and "negative" the surrounding copper. If you wire it backwards, you will still get a signal (piezo output is AC), but it may not be the side of the signal you want. The amp cuts anything below zero as it enters the circuit, so depending on the orientation of the piezo in the sensor, or with respect to the animal, the "positive" voltage swing may be bigger, or smaller than the "negative" swing when the animal licks. Best practice is just to test output response once the system is in place and wire it the way you get the biggest signal.

- If you're solding the wires to the piezo yourself, take care not to overheat the piezo. Even if it doesn't visibly delaminate the piezo, you could do enough unseen damage to end up with a poor sensor. If you're not confident in your soldering skills, piezos are available pre-wired.

- This is a voltage-mode piezo amp. The length of the wire between the piezo and the amp should be kept to a minimum, else the capacitance of the cable will start to interfere with the sensor.

### Gain

The gain of the amplifier is adjusted using the round trimmer marked "Gain" for the appropriate channel. This trimmer is multi-turn to add some precision to the adjustments, however it has no stops to indicate the start, or end of the range. On first use, it's a good idea to simply turn it counter-clockwise several (~10) full turns to be sure you're at the bottom and then slowly work your way up until you reach the desired signal.  

Choosing the correct gain can be tricky with piezo-based systems and the quality of the detection you get will depend on the type of piezo/lick-spout you deploy, the placement of your sensor with respect to the animal and how well the sensor is physically isolated from other sources of shock/vibration. This is not trivial and takes some practice to get your setup and positioning perfect. 

### Threshold

The 5V TTL output is based on thresholding the raw voltage signal. That threshold is controlled using the square single-turn trimmer labeled "Threshold" for the appropriate channel. The available threshold does not cover the entire 0-5V range of the device. By default, it covers 2.5V-3.75V. This range was found (for our purposes) to encompass the best gain settings for noise when the setup is well optimized. You can, of course alter the range by changing the values of R2, R9 and R10 (as an example for channel 1) if you find it doesn't suit your use-case, but the default is a good starting point. You could also just bring the raw signal in through a DAQ and threshold in software if that suits your setup design.

## Building

This project came before I started converting all my projects to through-hole, so most of the parts are surface-mount. It's not too bad and If you practice a bit with a rework station you can get through it. If you have access to a surface-mount oven it's easy. Otherwise, there are many services that will populate the board with the parts for you. 

I may eventually get around to updating this to through-hole construction, but you can also just build it on a breadboard, or an Adafruit perma-proto board by following the schematic, without the custom PCB. This is probably the easiest way to get up and running for the least money and all of the parts I've used have through-hole equivalents.