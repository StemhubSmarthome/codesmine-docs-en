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

<span id="subtitle">Step 4. Read and show the data</span><BR><P>
* In `Forever`, put `set humd to DHT11 Read humidity at pin P2` to read humidity
* Put `set temp to DHT11 Read temperature at pin P2` to read temperature
* add up the counter by `change counter by 1`
* Clear the display before each update by `clear OLED display`
* Show the temperature with formatted text by `show string join Temperature: temp C`
* Show the humidity with formatted text by `show string join humidity: humd %`
* ![auto_fit](images/Case10/Case10_p8.png)<P>

<span id="subtitle">Step 5. Examine and send the data</span><BR><P>
* Add a `if` statement with condition `counter >= 15`
* Put `call send to Thingspeak` function to start the upload process
* Add a `if` statement with condition `temp > 28`
* Put `call warning_hot` function to play the alert sound
* Add a `if statement` with condition `humd <= 50`
* Put `call warning_dry` function to play the alert sound
* Add `pause(ms) 1000` to read and check data for each second

![auto_fit](images/Case10/Case10_p9.png)<P>


<span id="subtitle">Full Solution<BR><P>

MakeCode: [https://makecode.microbit.org/_01h9FpcbVicW](https://makecode.microbit.org/_01h9FpcbVicW)<BR><P>
You could also download the program from the following website:<BR>
<iframe src="https://makecode.microbit.org/#pub:_01h9FpcbVicW" width="100%" height="500" frameborder="0"></iframe>





## Result
<HR>

After turn on, sensors will start collecting temperature and humidity data for each second. <BR>For every 15 times data collection, it will upload to Thingspeak.<BR>
When the temperature or humidity value is over the range, it will trigger the warning alert.
<P>

![auto_fit](images/Case10/Case10_result.png)<P>


## Think
<HR>

Q1. How to make use of the data to analyst the home environment? (for example, checking the time period that mostly trigger alert?)
