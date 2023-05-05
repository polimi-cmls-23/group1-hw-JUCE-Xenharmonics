# HW2 - Analysis of a JUCE Plugin - Chow Tape Model
The **JUCE** plugin we've decided to analyze for our report is the [**Chow Tape Model**](https://github.com/jatinchowdhury18/AnalogTapeModel) plugin by **Jatin Chowdhury** (*chowdsp*).

It's an effect plugin which simulates the qualities and imperfections of analog audio tape.

# About
**Chow Tape Model** is an analog tape machine emulation plugin that was initially based on the **Sony TC-260**. This latest version uses physics-based emulation methods to imitate a wide range of reel-to-reel tape devices.

The user is able to customize the physical properties of the tape machine and magnetic tape being simulated using a variety of parameters. Even more damaging and extreme effects than would be actually possible with a real tape machine can be added to the input signal.

This is the **GUI** of the plugin we've analyzed:

![screenshot of the plugin](CTM%20screenshot.png)

From the graphical interface we can see these parameters that the instrument provides, these are used by multiple effects that are implemented in order to create a more detailed and realistic emulation of analog tape.</br></br>

The main parts the plugin is divided into are:

+ **Main Controls**:
  - *Gain*: allows the user to control in/out gain and the dry/wet ratio
  - *Filters*: paramters for the low-cut and high-cut filters applied to the input signal, before the actual processing is performed on the audio data
  - *Stereo*: panning controls and left/right-mid/side stereo processing choice
  
+ **Physical tape parameters**:
  - *Tape*: implements the nonlinear hysteresis process (the one used in this case is the Jiles-Atherton model of magnetic hysteresis)
  - *Compression*: reduces the dynamic range of the signal before the hysteresis process
  - *Tone*: applies pre/post-emphasis filters before and after the hysteresis process
  
+ **Tape wear**:
  - *Loss*: simulates the tape's frequency response that is dependent on the amount of space between the playhead and the tape, the width of the playhead gap and the thickness of the actual tape
  - *Degrade*: simulates the aging process of the tape and the related loss in audio quality
  - *Chew*: applies qualities and imperfections analogous to physical damage inflicted on the tape by a malfunctioning tape machine
  
+ **Wow/Flutter**: applies timing irregularities due to possible small imperfections in the mechanics of the tape machine (causing the tape to subtly speed up and slow down) 
