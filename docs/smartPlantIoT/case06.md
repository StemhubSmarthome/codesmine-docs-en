# IoT Case 06: Plant health data monitoring

Level: ![level](images/level4.png)
![auto_fit](images/Case6/blank.png)<P>

## Goal
<HR>

Create a plant health monitoring system that will track the environment's humidity, temperature, light intensity and the plant’s soil moisture. The data is then sent and stored in thingspeak where it can be remotely monitored and analyzed over long periods of time. <BR><P>

## Background
<HR>

<span id="subtitle">What is plant health data monitoring?</span><BR><P>
Monitoring plant data is immensely important. However, if you will only monitor the immediate data you risk not seeing the bigger picture. <BR>If you have the habit of measuring and recording plant data over long periods of time it can show you patterns that you could have easily missed. Maybe there is a consistent overtime degradation of the plant health that is not noticable in day-to-day life. Or there is a sudden growth spurt and you want to study what caused it. Moreover, if you implement a system that will categorize and sort the data automatically into easy to analyze graphs, it can greatly increase your efficiency as a botanist as well as save you enormous amounts of time. 
 <BR><P>

<span id="subtitle">Plant health data monitoring operation</span><BR><P>
The pot is mounted with three module temperature and humidity sensor, soil moisture sensor, light intensity sensor. The board attempts to connect to the internet, and if it is connected successfully the sensor readings are sent to thingspeak. Afterwards there is a 15 second break. After the break, the cycle repeats. <BR><P>
![auto-fit](images/Case6/blank.png)<P>

## Part List
<HR>

![auto_fit](images/Case6/Case6_parts.png)<P>

## Assembly step
<HR>
wait for asm

![pic_60](images/Case6/blank.png)<P>

## Hardware connect
<HR>

1. Connect Temperature and humidity sensor to P1
2. Connect Soil moisture sensor to P2
3. Connect BH1750 Light sensor to I2C

![auto_fit](images/Case6/Case6_hardware.png)<P>


## IoT (ThingSpeak)
<HR>

<span id="subtitle"> Step 1. Login and create channel</span><BR><P>
* Go to [https://thingspeak.com](https://thingspeak.com/), Choose Channels -> My Channels -> New Channel<BR><P>
* Input Channel name, Field1, Field2, Field3 and Field4 name, then click “Save Channel”
![auto_fit](images/Case6/Case6_p1.png)<P>

<span id="subtitle"> Step 2. Get the API key</span><BR><P>
* Select your channel > “API Keys” ，copy the API key
![auto_fit](images/Case6/Case6_p2.png)<P>


## Programming (MakeCode)
<HR>

<span id="subtitle">Step 1. Create variables, initialize OLED, IoT:bit and connect to WiFi</span><BR><P>
* Snap `Initialize OLED with width:128, height: 64` to `on start`
* Snap `Initialize IoT:bit TX P16 RX P8` from `IoT:bit` to `on start`
* Snap `Set Wi-Fi to ssid pwd` to `on start` and fill in the SSID and password
![auto_fit](images/Case6/Case6_p3.png)<P>
* Set variable `temp`, `humd`, `soil` and `light`
![auto_fit](images/Case6/Case6_p4.png)<P>

<span id="subtitle">Step 2. Show icon "tick" after WiFi connection</span><BR><P>
* Snap `show icon` from `basic` to `On WiFi connected` and select icon `tick`
![auto_fit](images/Case6/Case6_p5.png)<P>

<span id="subtitle">Step 3. Get temperature, humidity, soil moisture and light values</span><BR><P>
* In `Forever`, put a `if` statement, use `WiFi connected?` as condition
* In the `if` segment, start to read data
* Use `set temp to DHT11 Read temperature at pin P1` read temperature
* Use `set humd to DHT11 Read humidity at pin P1` read humidity
* Use `set soil to value of soil moisture(0~100) at pin P2` to read soil moisture
* Use `set light to value of light intensity(Lx) from BH1750` to read light intensity

![auto_fit](images/Case6/Case6_p6.png)<P>

<span id="subtitle">Step 4. Upload data to thingspeak</span><BR><P>
* Put `Send Thingspeak key* XXXXXXX field1 xxxx .....` in the `if` segement
* In the `Send Thingspeak key....` block, fill in the required infromation, such as API key, field1,2,3,4 value
* Add `pause(ms) 15000` to wait 15 second between each uploading
![auto_fit](images/Case6/Case6_p7.png)<P>


<span id="subtitle">Step 5. Show ThingSpeak upload status</span><BR><P>
* Put `On Thingspeak Uploaded` to editor
* Clear the display before each update
* Show the upload status and error_code by `show string Status` and `show string Error_code`
![auto_fit](images/Case6/Case6_p8.png)<P>



<span id="subtitle">Full Solution<BR><P>
MakeCode: [https://makecode.microbit.org/_4pmd65cHVDTo](https://makecode.microbit.org/_4pmd65cHVDTo)<BR><P>
You could also download the program from the following website:<BR>
<iframe src="https://makecode.microbit.org/#pub:_4pmd65cHVDTo" width="100%" height="500" frameborder="0"></iframe>


## Result
<HR>
When the IoT:bit was connected to WiFi, the tick will be show.<BR>
Then collect data from each sensor, and upload to thingspeak through Internet.<BR>The upload will be every 15 second because the free account of thingspeak limited the frequency.

![auto_fit](images/Case6/Case6_result1.png)<P>

After uploaded, the data will be shown in the chart on the website.

![auto_fit](images/Case6/Case6_result2.png)<P>

## Think
<HR>

1. How do you use the data after you collected? (hints: analyst the time period? Relationship between temperature, humidity and soil moisture?)