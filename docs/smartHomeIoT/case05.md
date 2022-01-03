# Case 05: Smart Fridge Alert

Level: ![level](images/level3.png)
![auto_fit](images/Case5/intro.png)<P>

## Goal
<HR>

Create a fridge that can detect the door state, when the door was not in close state for a long time, warning the user.
<BR><P>

## Background
<HR>

<span id="subtitle">What is Smart Fridge Alert?</span><P>
Smart Fridge is a Fridge that has an extra sensor to help it determine the door close state, when the user forgets to close the door, it will warn the user to close it to reduce waste of energy and prevent food poisoning.<BR><P>

<span id="subtitle">Smart Fridge Alert Principle</span><P>
When the door is closed, the inside of the fridge should be dark.<BR>When the door is opened, the room light will go into the fridge.<BR>So a light sensor can easily detect the door state, then take the following action. <BR><P>

## Part List
<HR>

![auto_fit](images/Case5/blank.png)<P>

## Assembly step
<HR>

<span id="subtitle">Step 1</span><P>
Use M4 screws and nuts to install the light sensor on the fridge door.
<BR><P>
![auto_fit](images/Case5/Case5_ass1.png)<P>

## Hardware connect
<HR>

1. Connect the Light sensor to Pin P1
2. Pull down the Buzzer switch to connect buzzer

![auto_fit](images/Case5/Case5_hardware.png)<P>

## Programming (MakeCode)
<HR>

<span id="subtitle">Step 1. Initialize counter variable</span><P>
* On start, create a “counter” variable and set to 0

![auto_fit](images/Case5/Case5_p1.png)<P>
![auto_fit](images/Case5/Case5_p2.png)<P>

<span id="subtitle">Step 2. Examine the light intensity</span><P>
* In `Forever`, put a `if-else` statement
* Use `Get light value (percentage) at Pin P1 > 30` as condition
![auto_fit](images/Case5/Case5_p3.png)<P>

<span id="subtitle">Step 3. Warning counter</span><P>
* In the `if` segment, that's means the light intensity is strong, the door was opened
* Add the counter with 1 by `change counter by 1` to sum up the time of door opened
* Put the second `if` statement with `counter >= 60` condition to examine when should issue warning sound
* In the sencond `if` segment, put `start melody jump down repeating once` to issue the warning sound
* Back to the first `if-else` level, in the `else` segment, that's means light intensity is weak, door was closed, so reset the counter to 0 by `set counter to 0`
* Put a `pause (ms) 1000` to check the door each second
![auto_fit](images/Case5/Case5_p4.png)<P>


<span id="subtitle">Full Solution<BR><P>
MakeCode: [https://makecode.microbit.org/_YUbMtDiJJhWg](https://makecode.microbit.org/_YUbMtDiJJhWg)<BR><P>
You could also download the program from the following website:<BR>
<iframe src="https://makecode.microbit.org/#pub:_YUbMtDiJJhWg" width="100%" height="500" frameborder="0"></iframe>


## Results
<HR>
When the door is opened for more than 1 minute, the buzzer will play some sound to warn the user.
<BR><P>

![auto_fit](images/Case5/Case5_result.png)<P>

## Think
<HR>

1. Apart from making the sound from the buzzer, another method to warn the user?
2. Can you make use of the fridge, to make a smart box to alert users?


