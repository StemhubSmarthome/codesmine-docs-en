# Case 08: Automatic Sunlight Detecting Curtain
Level: ![level](images/level3.png)

![auto_fit](images/Case8/intro.png)<P>

## Goal
<HR>

Make a smart curtain know how to operate automatically by detecting the sunlight around the house.<BR><P>

## Background
<HR>

<span id="subtitle">What is Automatic Sunlight Detecting Curtain </span><P>
Automatic Sunlight Detecting Curtain is a curtain that scrolls up or down automatically according to the detection of sunlight.<BR><P>

<span id="subtitle">Automatic Sunlight Detecting Curtain principle</span><P>
The light sensor is implemented outside of the house. When it returns light it indicates that there is sunlight that can reach the house. The curtain in this case should scroll down for cutting heat energy transferring into the house, to reduce power waste of air conditioner.
<BR><P>

## Key knowledge
In programming part, there is a "flag" concept to be used in this case. It can check whether the curtain is pulled down or not and prevent from keeping pull down the curtain.


## Part List
<HR>

![auto_fit](images/Case8/Case8_parts.png)<P>

 
## Assembly step
<HR>
<span id="subtitle">Step 1</span><P>
Cut the Curtain paper to 8cm*8cm<BR><P>

![auto_fit](images/Case8/Case8_ass1.png)<P>

<span id="subtitle">Step 2</span><P>
Stick the paper to the rod, stick some weight at the bottom, install the rod into servo and  <BR><P>

![auto_fit](images/Case8/Case8_ass2.png)<P>

<span id="subtitle">Step 3</span><P>
Use M2 screw to install the servo to the placeholder and check the place of curtain<BR><P>

![auto_fit](images/Case8/Case8_ass3.png)<P>

<span id="subtitle">Step 4</span><P>
Install the light sensor on the C1 cardboard<BR><P>

![auto_fit](images/Case8/Case8_ass4.png)<P>


## Hardware connect
<HR>

1. Connect the light sensor to P0
2. Connect the 360 degree servo to P2
3. Pull up the buzzer switch to disconnect the buzzer
![auto_fit](images/Case8/Case8_hardware.png)<P>

## Programming (MakeCode)
<HR>

<span id="subtitle">Step 1. Initialize OLED and create the variable</span><P>
* On start, initialize the OLED display by `initialize OLED with width 128 height 64` 
* Create the `curtainOn` variable and set it to `false`

![auto_fit](images/Case8/Case8_p1.png)<P>

<span id="subtitle">Step 2. Create curtain control function "openCurtain"</span><P>
* Create function `openCurtain` 
* Inside the function, control the speed and direction of the 360 degree servo at connected pins, such as `Turn 360 Servo with clockwise direction speed level 3 at P2`
* Add pause to wait it rotate for few second (depend on your model setup)
* Stop the 360 servo with same method, such as `Turn 360 Servo with clockwise direction speed level 0 at P2`
* set the `curtainOn` variable to `true`

![auto_fit](images/Case8/Case8_p2.png)<P>

<span id="subtitle">Step 3. Create curtain control function "closeCurtain"</span><P>
* Create function `closeCurtain` 
* Inside the function, following the previous function, but in reversed direction and state
* control the speed and direction of the 360 degree servo at connected pins, such as `Turn 360 Servo with anti-clockwise direction speed level 3 at P2`
* Add pause to wait it rotate for few second (depend on your model setup)
* Stop the 360 servo with same method, such as `Turn 360 Servo with anti-clockwise direction speed level 0 at P2`
* set the `curtainOn` variable to `false`
![auto_fit](images/Case8/Case8_p3.png)<P>

<span id="subtitle">Step 4. Get the light intensity value</span><P>
* In `Forever`, reading the value by `set light to Get light value (percentage) at Pin P0`
* Clear the OLED display before each update by `clear OLED display`
* Show the number of value on display by `show number light`

![auto_fit](images/Case8/Case8_p4.png)<P>

<span id="subtitle">Step 5. Examine the light intensity value and reaction</span><P>

* Snap a nested `if statement` to `Forever`
* Set `light2 >= 30 ` and `curtainOn =  true` as first condition
* In the `if` segment, that's means the sunlight is strong, need to close the curtain, `call closeCurtain`
* In the second condition, use `light2 < 30` and `curtainOn = false` 
* In the second `if` segment, that's means the sunlight is weak, need to open the curtain, `call openCurtain`

![auto_fit](images/Case8/Case8_p5.png)<P>

<span id="subtitle">Full Solution<BR><P>
MakeCode: [https://makecode.microbit.org/_Kwc4M2EhWW8P](https://makecode.microbit.org/_Kwc4M2EhWW8P)<BR><P>
You could also download the program from the following website:<BR>
<iframe src="https://makecode.microbit.org/#pub:_Kwc4M2EhWW8P" width="100%" height="500" frameborder="0"></iframe>


## Result
<HR>

When the light sensor detects the light value outside the house is strong, the servo will rotate to scroll down the curtain. When the light is not strong, the servo will rotate in anti direction to scroll up the curtain

![auto_fit](images/Case8/Case8_result.gif)<P>

## Think
<HR>

Q1. Apart from the sunlight value, any other condition can be used to determine the curtain state? <BR><P>
