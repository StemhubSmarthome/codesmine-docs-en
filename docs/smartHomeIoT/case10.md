# IoT Case 10: Home Health Data Monitoring

Level: ![level](images/level4.png)
![auto_fit](images/Case10/blank.png)<P>

## Goal
<HR>

Make a home health data monitoring system by collecting data from the sensors inside the house.<BR><P>

## Background
<HR>

<span id="subtitle">What is home health data monitoring system?</span><BR><P>
Health monitoring is the concept of tracking the conditions of different parameters inside the user’s house. From the simplest temperature and humidity data to more advanced detection of CO2, town gas etc, having such system can help make alert for prevention of accident, like town gas leakage or short of oxygen inside the house.<BR><P>

<span id="subtitle">Home health monitoring system operation</span><BR><P>
In this scenario, integrated temperature and humidity sensor DTH11 is used. It can track and send back the data collected to the main control board for further analysis, constant display and cloud server storage. If the conditions breach certain limits, warnings will be made, else the system will keep silent.<BR><P>
![auto_fit](images/Case10/blank.png)<P>

## Part List
<HR>

![auto_fit](images/Case10/blank.png)<P>

## Assembly step
<HR>

<span id="subtitle">Step 1</span><BR><P>
* Use M4 screws to install the DHT11 temperature and humidity sensor to C4 cardboard
* Use M2 screws to install the OLED display to C4 cardboard
![auto_fit](images/Case10/blank.png)<P>

<span id="subtitle">Step 2</span><BR><P>
Insert the C4 cardboard on A cardboard, align with holes at A and B2<BR><P>
![pic_40](images/Case10/blank.png)<P>


## Hardware connect
<HR>

1. Connect the temperature and humidity sensor DHT11 to P2
2. Pull down the buzzer switch to connect the buzzer
3. Connect the OLED display to IoT:bit I2C port with extend cable

![auto_fit](images/Case10/Case10_hardware.png)<P>

## IoT (Thingspeak)
<HR>

<span id="subtitle">Step 1. Create Thingspeak channel</span><BR><P>
* Go the https://thingspeak.com/ create an account and create a channel
![auto_fit](images/Case10/Case10_p1.png)<P>

<span id="subtitle">Step 2. Get channel API</span><BR><P>
* After created a new channel, get the write in API
![auto_fit](images/Case10/Case10_p2.png)<P>


## Programming (MakeCode)
<HR>

<span id="subtitle">Step 1. Initialize OLED, IoT:bit and connect to WiFi, create and initialize variable</span><BR><P>
* Create variable `counter`
![auto_fit](images/Case10/Case10_p3.png)<P>

* Snap `Initialize OLED with width:128, height: 64` to `on start`
* Snap `Initialize IoT:bit TX P16 RX P8` from `IoT:bit` to `on start`
* Snap `Set WiFi to ssid smarthon_ss8 pwd Qw64811051` to `on start`
* Initialize the variable `counter` to 0
![auto_fit](images/Case10/Case10_p4.png)<P>

<span id="subtitle">Step 2. Show icon “tick” after WiFi connection</span><BR><P>
* In `On WiFi connected`, put a `show icon tick` get notice after WiFi is connected.
![pic_60](images/Case10/Case10_p5.png)<P>

<span id="subtitle">Step 3. Sending data to Thingspeak</span><BR><P>
* Create a new function `send to Thingspeak`
* Put a `if` statement inside
* In the condition, use `WiFI connect?` to make sure the internet was connected
* Sending data to thingspeak by using `Send Thingspeak key* XXXXX field1 value xxx field2 xxx ....`, fill in the write API of your channel and the value that want to upload
* reset the `counter` variable to `0`
![pic_80](images/Case10/Case10_p6.png)<P>

<span id="subtitle">Step 4. Create two warning function</span><BR><P>
* Create a function called `warning_dry`
* Show string `Humidity is too low!` 
* play the warning sound by `play melody xxx at tempo 500 bpm`
* Create another function called `warning_hot`
* Repeat again the steps.

![auto_fit](images/Case10/Case10_p7.png)<P>

<span id="subtitle">Step 4. Create two warning function</span><BR><P>
* Create a function called `warning_dry`
* Show string `Humidity is too low!` 
* play the warning sound by `play melody xxx at tempo 500 bpm`
* Create another function called `warning_hot`
* Repeat again the steps.

![auto_fit](images/Case10/Case10_p7.png)<P>



<span id="subtitle">Full Solution<BR><P>
<<<<<<< HEAD
MakeCode: [https://makecode.microbit.org/_6DuRvwD5PYpU](https://makecode.microbit.org/_6DuRvwD5PYpU)<BR><P>
You could also download the program from the following website:<BR>
<iframe src="https://makecode.microbit.org/#pub:_6DuRvwD5PYpU" width="100%" height="500" frameborder="0"></iframe>
=======
MakeCode: [https://makecode.microbit.org/_2cRf6LWq69AL](https://makecode.microbit.org/_2cRf6LWq69AL)<BR><P>
You could also download the program from the following website:<BR>
<iframe src="https://makecode.microbit.org/#pub:_2cRf6LWq69AL" width="100%" height="500" frameborder="0"></iframe>
>>>>>>> f16ca1229b020beb4e91d7e16791193a6cb0c679




## Result
<HR>

The micro:bit is controlled by IFTTT (trigger by date&time). The LED light will be turned on at 6pm and turned off at 6am every day.<BR><P>
![auto_fit](images/Case10/blank.png)<P>


## Think
<HR>

Q1. How to turn on the light automatically if the today’s weather is cloudy reported by IFTTT.
