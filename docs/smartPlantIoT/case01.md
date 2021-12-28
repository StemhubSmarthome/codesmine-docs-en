# Case 01: Grow LED Light Color Control

Level: ![level](images/level1.png)
![auto_fit](images/Case1/blank.png)<P>


## Goal
<HR>
Create a grow light that can be turned to different colors using the buttons on micro:bit board.<P>

## Background
<HR>
<span id="subtitle">What is a Grow LED Light Color Control?</span><P>

Light is one of the most important aspects of plant growth. The use of supplemental grow lights is essential when you are considering cultivating plants at home. However, what many do not realise is that different colors of light have different effects on the growth of the plant.<P>Using this setup you can experiment and observe the effects of different colors of light on plant growth. Thanks to our multicolor LED you can choose out of many different colors. But by way of experimentation, you can determine a combination of blue and red lights which make purple, is the most efficient light for the plant. 
<P>

<span id="subtitle">Grow LED light control operation</span><P>

The light can assume one of three colors, blue, red or purple. By pressing button “A” the color will turn red.<BR>By pressing button “B”, the color will turn blue. <BR>By pressing both of the buttons the color will turn purple due to the combination of blue and red. <BR>


![pic_60](images/Case1/blank.png)<P>

## Part List
<HR>

![auto_fit](images/Case1/Case1_parts.png)<P>


## Assembly step
<HR>

<span id="subtitle">Step 1</span><BR><P>
Wait for later 
![pic_40](images/Case1/blank.png)<P>


## Hardware connect
<HR>

1. Connect Grow Light to P1
![auto_fit](images/Case1/Case1_hardware.png)
<P>

## Programming (MakeCode)
<HR>

<span id="subtitle">Step 1. Initial the Multi-Color LED</span><BR><P>
* Snap `set strip to NeoPixel at pin P1 with 10 leds as RGB(GRB format)` to `on start` 
![auto_fit](images/Case1/Case1_p1.png)<P>

<span id="subtitle">Step 2. Change all LEDs in red color</span><BR><P> 
* Drag `on button A pressed` to editor
* Use `strip show color red` to change all LEDs to red
![pic_90](images/Case1/Case1_p2.png)<P>


<span id="subtitle">Step 3. Change all LEDs in purple color</span><BR><P> 
* Drag `on button B pressed` to editor
* Use `strip show color purple` to change all LEDs to purple
![pic_90](images/Case1/Case1_p3.png)<P>

<span id="subtitle">Step 4. Change LEDs in mixed color</span><BR><P> 
* Drag `on button A+B pressed` to editor
* Use `strip set pixel color at X to XXX` and `strip show` to build the combination of mixed color
* Each `strip set pixel at X to XXX` need to fill in the number order and color respectively
* After set the pixel, must need to use `strip show` to make it change color
![pic_90](images/Case1/Case1_p4.png)<P>

<span id="subtitle">Full Solution<BR><P>
MakeCode: [https://makecode.microbit.org/_UpXT4vL6qHrh](https://makecode.microbit.org/_UpXT4vL6qHrh)<BR><P>
You could also download the program from the following website:<BR>
<iframe src="https://makecode.microbit.org/#pub:_UpXT4vL6qHrh" width="100%" height="500" frameborder="0"></iframe>

<P>

## Result
<HR>

When pressed the A button, the Grow light change to Red<BR>
When pressed the B button, the Grow light change to Purple<BR>
When pressed the A+B buttons, the Grow light change to a mix of red and blue color<P>
![auto_fit](images/Case1/Case1_result.png)<P>

## Think
<HR> 

Q1. How do you mix the color to get the best effect for plant growth?<BR><P>

