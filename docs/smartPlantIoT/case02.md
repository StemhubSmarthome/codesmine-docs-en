# Case 02: Environment Monitoring Display


Level: ![level](images/level1.png)
![auto_fit](images/Case2/blank.png)<P>

## Goal
<HR>

Mount and LCD display that will show the real time plant data such as the environment temperature, humidity and the soil moisture. <BR><P>

## Background
<HR>

<span id="subtitle">What is an Environment Monitoring Display?</span><P>
In the days of old determining the environmental factors for suitable plant growth was either extremely difficult, or extremely expensive. The analogue methods might have worked for meatsureing temperature, but determining air humidity and soil moisture accurately was possible after the advent of electronics.<P>Nowadays we can accurately measure the environmental factors for optimal plant growth. And of course combining all of the relevant data and showing it in one central screen is the next logical step in making the process more convenient. <BR><P>

<span id="subtitle">Environment monitoring display operation</span><P>
The plant pot is mounted with two modules, temperature and humidity sensors as well as soil moisture sensor. Additionally we mount the LCD display which will show the real time temperature, humidity and soil moisture. <BR><P>

When there are no vacancies (detected by light sensor), then the gate will keep closed.<BR><P>
![pic_70](images/Case2/blank.png)<P>


## Part List
<HR>

![auto_fit](images/Case2/Case2_parts.png)<P>

## Assembly step
<HR>

Wait for asm
![pic_60](images/Case2/blank.png)<P>


## Hardware connect
<HR>

1. Connect the LCD1602 module to I2C socket.
2. Connect the Temperature and Humidity sensor(DHT11) to P1.
3. Connect the soil moisture sensor to P2.

![auto_fit](images/Case2/Case2_hardware.png)<P>

## Programming (MakeCode)
<HR>

<span id="subtitle">Step 1. Initialize the LCD1602</span><BR><P>
* Put `connect LCD at I2C address 39` into `on start`
![pic_50](images/Case2/Case2_p1.png)<P>

<span id="subtitle">Step 2. Show the result of temperature and humidity</span><BR><P>
* Put `LCD1602 show MakerBit at position 1 with length 16`inside `Forever`
* Replace the `MakerBit` with a formatted text and reading result, also adjust the start position and the length, such as `LCD1602 show join Temp: DHT Read temperature at pin P1 at position 1 with length 8`
* Repeat it again with little adjustment for humidity
![auto_fit](images/Case2/Case2_p2.png)<P>

<span id="subtitle">Step 3. Show the result of soil moisture</span><BR><P>
* Put `LCD1602 show join Soil: value of soil moisture(0~100) at pin P2 at position 17 with length 16`
* Pause for 1000ms to read the sensor each second
![auto_fit](images/Case2/Case2_p3.png)<P>


<span id="subtitle">Full Solution<BR><P>
MakeCode: [https://makecode.microbit.org/_gc66LtY7pRMd](https://makecode.microbit.org/_gc66LtY7pRMd)<BR><P>
You could also download the program from the following website:<BR>
<iframe src="https://makecode.microbit.org/#pub:_gc66LtY7pRMd" width="100%" height="500" frameborder="0"></iframe>

## Result
<HR>

From turn on, micro:bit will collect the information from different sensors. After that, the information will show on the LCD display<BR><P>
![auto_fit](images/Case2/Case2_result.png)<P>

## Think
<HR>

1. Can you make the display format become more readable?
2. Try to turn off the backlight to save energy?
