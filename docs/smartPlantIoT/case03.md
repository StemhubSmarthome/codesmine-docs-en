# Case 03: Smart LED Grow light

Level: ![level](images/level2.png)
![auto_fit](images/Case3/blank.png)<P>


## Goal
<HR>

Create an automatic grow light that will turn on when the light sensor detects the lack of appropriate amount of light.<BR><P>

## Background
<HR>

<span id="subtitle">What is Smart LED grow light?</span><P>
Whenever we grow a plant, we replicate the conditions encountered in nature, with a certain amount of light present during the day. However, when we are indoors, it is hard to replicate those conditions. Under poor lighting, a plant might survive, but it will not thrive. Our smart LED grow light will help the plant as it will track the lighting conditions and turn on whenever the plant needs more light. This type of system is incredibly useful in growing a plant in indoor conditions. <BR><P>

<span id="subtitle">Smart LED grow light operation</span><P>
We will use a light sensor to track the light intensity near the plant. Whenever the light intensity falls under a specific number, the board enables the LED to grow light that will shine on the plant. When we have enough light in the system, the LED will turn off. <BR><P>
![pic_70](images/Case3/blank.png)<P>

## Part List
<HR>

![pic](images/Case3/Case3_parts.png)<P>

## Assembly step
<HR>
Wait for asm

![pic_60](images/Case3/blank.png)<P>

## Hardware connect
<HR>

1. Connect the LCD1602 Display to I2C port
2. Connect the digital light sensor to I2C ports.
3. Connect the LED Grow Light to P2

![pic](images/Case3/Case3_hardware.png)<P>

## Programming (MakeCode)
<HR>

<span id="subtitle">Step 1. Initialize Grow LED light and LCD1602 display</span><P>
* Put `connect LCD at I2C address 39` in `on start`
* Put `set strip to NeoPixel at pin P2 with 10 leds as RGB(GRB format)`
![auto_fit](images/Case3/Case3_p1.png)<P>

<span id="subtitle">Step 2. create the light variable</span><P>
* Create a new variable `light`
![pic_90](images/Case3/Case3_p2.png)<P>

<span id="subtitle">Step 3. Read the light value and show on display</span><P>
* In `Forever`, put `set light to value of light intensity(Lx) from BH1750` to read the value
* Show the value with formatted text on display by `LCD1602 show join Light: light at position 1 with length 16`

![pic_90](images/Case3/Case3_p3.png)<P>

<span id="subtitle">Step 4. Examine the light value to turn on/off the light</span><P>
* Put a `if-else` statement with condition `light < 50`
* In `if` segment, put `strip show color purple`
* In `else` segment, put `strip show color black`

![pic_90](images/Case3/Case3_p4.png)<P>



<span id="subtitle">Full Solution<BR><P>
MakeCode: [https://makecode.microbit.org/_hFtg3YH9mW16](https://makecode.microbit.org/_hFtg3YH9mW16)<BR><P>
You could also download the program from the following website:<BR>
<iframe src="https://makecode.microbit.org/#pub:_hFtg3YH9mW16" width="100%" height="500" frameborder="0"></iframe>


## Result
<HR>

When the environment is blight, the Grow LED Light will not turn on.<BR><P>
When the environment is dark, the reading of light intensity will lower than threshold, then turn on the Grow LED Light.<BR><P>

![auto_fit](images/Case3/Case3_result.png)<P>

## Think
<HR>

1. Try to adjust the threshold of light intensity to get better performance on turn on/off the Light. <BR><P>
