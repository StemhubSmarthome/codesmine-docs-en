# Case 01: Smart Saving light bulb

Level: ![level](images/level1.png)
![auto_fit](images/Case1/intro.png)<P>


## Goal
<HR>
Make a smart light bulb by detecting motion around the environment.<P>

## Background
<HR>
<span id="subtitle">What is a smart light bulb?</span><P>

Smart light bulb is a light bulb that turns on and off automatically depending on the presence of people around the environment. Deploying it in home toilets can help save electricity. When no one is inside the toilet the bulb will automatically turn off.<P>

<span id="subtitle">Smart light bulb operation</span><P>

Motion sensor is used to detect the presence of human activity in the room. If there are people moving in the room, the light bulb will turn on, vice versa.<BR>

## Part List
<HR>

![auto_fit](images/Case1/blank.png)<P>


## Assembly step
<HR>

<span id="subtitle">Step 1</span><BR><P>
Use M4 screw to Install the motion sensor on wall.<BR><P>
![auto_fit](images/Case1/Case1_ass1.png)<P>
<span id="subtitle">Step 2</span><BR><P>
Use M4 screw to install the multi-color LED on wall.<BR><P>
![pic_40](images/Case1/Case1_ass2.png)<P>


## Hardware connect
<HR>

1. Connect the motion sensor to P0<BR>
2. Pull up the switch to avoid interference from buzzer<BR>
3. Connect the Multi-color LED(WS2812) to P1<BR>

<BR>![auto_fit](images/Case1/Case1_hardware.png)
<P>

## Programming (MakeCode)
<HR>

<span id="subtitle">Step 1. Initialize Multi-Color LED</span><BR><P>
* Before using the Multi-Color LED, need to do initialize
* Pull the `set strip to NeoPixel at pin P1 with 1 leds as RGB(GRB format)` to `on start`

![auto_fit](images/Case1/Case1_p1.png)<P>

<span id="subtitle">Step 2. Change the LED Color by motion sensor result</span><BR><P> 
* In `Forever`, add a `if-else` statement
* Set (`Get motion (triggered or not) at Pin P0` = `true`) as condition
* Snap `strip show color white` into the `if` segment
* Snap `pause(ms) 2000` into `if` segment to keep light up for 2 second
* Snap `strip show color black` into the `else` segment
* When the condition is correct, that’s say motion is triggered, someone passes by.<BR>The program will run the `if` segment to turn on the light
* Otherwise, the program will run the `else` segment to turn off the light
![pic_90](images/Case1/Case1_p2.png)<P>

<span id="subtitle">Full Solution<BR><P>
MakeCode: [https://makecode.microbit.org/_hECbKo7rofEM](https://makecode.microbit.org/_hECbKo7rofEM)<BR><P>
You could also download the program from the following website:<BR>
<iframe src="https://makecode.microbit.org/#pub:_hECbKo7rofEM" width="100%" height="500" frameborder="0"></iframe>

<P>

## Result
<HR>

When the people are moving in the room, the motion sensor will trigger and keep the LED turned on. When there is no one moving, the LED will turn off.<BR><P>
![auto_fit](images/Case1/Case1_result.png)<P>

## Think
<HR> 

Q1. Besides implementing the smart light bulb into the toilet, where other places can the light bulb also be implemented? Discuss the place and briefly explain the point on energy reservation.<BR><P>
Q2. Suggest addition of any component that allows the light bulb to be even smarter.
<BR><P>