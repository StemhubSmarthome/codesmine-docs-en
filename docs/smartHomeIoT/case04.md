# Case 04: Toilet Water Leakage Detection System

Level: ![level](images/level2.png)
![auto_fit](images/Case4/intro.png)<P>

## Goal
<HR>

Make a toilet water leakage detection system by checking the conductivity of device connected.<BR><P>

## Background
<HR>

<span id="subtitle">What is a toilet water leakage detection system?</span><P>
Toilet water leakage detection system is a system that can trigger alert upon unwanted water leakage situations.<BR><P>

<span id="subtitle">What is an Electrical circuit?</span><P>
Electrical Circuit is one of basic concepts in electronic engineering, when something can let electric current pass through, it builds up a circuit.<P>
Generally, a circuit will have two states, if the circuit is complete, able to let the current pass, it is called closed circuit. If the circuit has a breakpoint, and cannot let the current pass, it becomes an open circuit.<P>
However, how to let the current pass through? It is related to the material of the circuit. In daily life, metal usually has a high conductivity, so it can be used to build the circuit. In addition, some ionic material such as tap water also takes the same property, able to become a conductor to build a circuit. But air has very bad conductivity, so it is hard to let current pass through.<BR><P>


![pic_80](images/Case4/Case4_bg1.png)


<span id="subtitle">Toilet water leakage detection system principle</span><P>

The system will consist of two crocodile clips each with one side connected to the board, one installed to the place of detection, with two clips physically disconnected. Air is an excellent insulator, so the circuit will become open circuit.  When water is leaked around that area, the water will replace the air between two clips, thus becoming a closed circuit, electricity will flow between the Board's detection Pin and ground Pin. It will trigger the detection to make the water leakage be detected and the system will send an alert.<BR><P>

![pic_90](images/Case4/Case4_bg2.png)


<span id="subtitle">What is “Pin is Pressed”?</span><P>
"Pin is Pressed” means the Pin connected to the ground, it will get the analog reading “0” and return “True". When it is not connected to ground, the reading will be not “0” and return “False”.<BR>
Apply to this example case:<P>

![pic_90](images/Case4/Case4_bg3.png)


## Part List
<HR>

![auto_fit](images/Case4/Case4_parts.png)<P>

## Assembly step
<HR>

<span id="subtitle">Step 1</span><P>
Now, we will build a toilet room. Insert E2 cardboard on A cardboard, align with holes at A, B2<BR><P>

![pic_80](images/Case4/Case4_ass1.png)<P>
<span id="subtitle">Step 2</span><P>
Insert E1 cardboard on A cardboard, align with holes at A,B3<BR><P>

![pic_80](images/Case4/Case4_ass2.png)<P>

<span id="subtitle">Step 3</span><P>
* Find a plastic water bottle and cut it to become a water tank<P>
* Place the water tank in the toilet<P>

Place two clips to position that want to detect water flowing
<BR><P>

![pic_80](images/Case4/Case4_ass3.png)<P>


## Hardware connect
<HR>

1. Connect the two crocodile clip cables to P1 and GND
2. Pull down the buzzer switch to connect the buzzer


![pic](images/Case4/Case4_hardware.png)<P>

## Programming (MakeCode)
<HR>

<span id="subtitle">Step 1</span><P>
<span id="subtitle">Step 1. Check the Pin state</span>
* In `Forever`, put a `if` statement
* Put `pin P1 is pressed = true` as condition
![pic_90](images/Case4/Case4_p1.png)<P>

<span id="subtitle">Step 2. Alert warning</span><P>
* If in `if` segment, that's means the water was connected two clips
* Use `play tone High A for 2 beat` to play warning sound
![pic_90](images/Case4/Case4_p2.png)<P>


<span id="subtitle">Full Solution<BR><P>
MakeCode: [https://makecode.microbit.org/_bPw0ViLrR6Jm](https://makecode.microbit.org/_bPw0ViLrR6Jm)<BR><P>
You could also download the program from the following website:<BR>
<iframe src="https://makecode.microbit.org/#pub:_bPw0ViLrR6Jm" width="100%" height="500" frameborder="0"></iframe>


## Results
<HR>

When the water level rises to the crocodile clip’s position, the warning sound is triggered to warn the user.<BR><P>
![pic](images/Case4/Case4_result.gif)<P>

## Think
<HR>

Q1. Apart from the warning by buzzer, any other method can be used to notify the house owner? i.e. showing red LED<BR><P>

