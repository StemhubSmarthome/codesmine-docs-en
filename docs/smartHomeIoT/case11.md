# IoT Case 11: Kitchen Safety Flame Monitoring Alert

Level: ![level](images/level4.png)
![auto_fit](images/Case11/intro.png)<P>

## Goal
<HR>

Make a flame monitoring alert system by detecting the existence of strong fire nearby.

## Background
<HR>

Nowadays, fire accidents always happen when the homeowner is sleeping or outside the home. It is good to install an IOT system in the kitchen or living room to alert the user on his/her phone when he/she is sleeping or in the office so that he/she will wake up and rush out of the home to prevent a terrible accident from happening. 

<BR><P>
<span id="subtitle">Kitchen Safety Flame Monitoring Alert principle</span><BR><P>
By installing a fire sensor in the area, the system will trigger an alarm and send a IFTTT notification to the house owner when there is fire detected in the sensor’s sight.
<BR><P>


## Part List
<HR>

![pic_90](images/Case11/Case11_parts.png)<P>
 
## Assembly step
<HR>

<span id="subtitle">Step 1</span><BR><P>
Insert the two L2 cardboard to L1 cardboard, then fold the L1 cardboard into box shape, aligned with the holes. <BR><P>
![pic_80](images/Case11/Case11_ass1.png)<P>
<span id="subtitle">Step 2</span><BR><P>
Stick the paper that drawing your favorite cooking stove look<BR><P>
![pic_80](images/Case11/Case11_ass2.png)<P>

<span id="subtitle">Step 3</span><BR><P>
Use M4 screws and nuts to install the flame sensor to B3 cardboard<BR><P>

![pic_80](images/Case11/case11_ass3.png)<P>

<span id="subtitle">Step 4</span><BR><P>
Use M4 screws and nuts to install the multi-color LED to B3 cardboard<BR><P>

![pic_80](images/Case11/case11_ass4.png)<P>

<span id="subtitle">Step 5</span><BR><P>
Insert the E3 cardboard on A cardboard, align with holes at A and B2 cardboard<BR><P>

![pic_80](images/Case11/case11_ass5.png)<P>

<span id="subtitle">Step 6</span><BR><P>
Insert the E2 cardboard on A cardboard, align with holes at A and B2 cardboard<BR><P>

![pic_80](images/Case11/case11_ass6.png)<P>

<span id="subtitle">Step 7</span><BR><P>
Place the cooking stove model to correct place<BR><P>

![pic_80](images/Case11/case11_ass7.png)<P>

<span id="subtitle">Step 8 (Optional, assembly step reference to case 5)</span><BR><P>
Place the fridge model to suitable place  <BR><P>

![pic_80](images/Case11/case11_ass8.png)<P>



## Hardware connect
<HR>

1. Connect the flame sensor to P2
2. Connect the Multi-Color LED to P1
3. Pull down the buzzer switch to connect buzzer

![pic_80](images/Case11/Case11_hardware.png)<P>


## IoT (IFTTT)
<HR>

### Part 1: Setup IFTTT
1. Create a IFTTT account and login
2. Create a new Applet
3. In the IF, search "Webhooks" and click the Webhooks application<BR>
![pic_80](images/Case11/Case11_iot1.png)<P>
4. Choose the "Received a web request" and enter the event name "fire"<BR>
![pic_80](images/Case11/Case11_iot2.png)<P>
![pic_80](images/Case11/Case11_iot3.png)<P>
5. In the THEN, search "Notifications" and click the notifications application
6. Choose the "Send a notification from the IFTTT App"<BR>
![pic_80](images/Case11/Case11_iot4.png)<P>
7. After the applet is finish setup, click the Webhooks icon -> documentation<BR>
![pic_80](images/Case11/Case11_iot5.png)<P><BR>
![pic_80](images/Case11/Case11_iot6.png)<P>
8. Copy the Key<BR>
![pic_80](images/Case11/Case11_iot7.png)<P>
<HR>
<H4>Optional: Use email as notification method</H4>

In the THEN field, search for the “email” and use it to replace the “notifications” in previous step
![pic_70](images/Case11/Case11_iot8.png)<P>
![pic_70](images/Case11/Case11_iot9.png)<P>
![pic_70](images/Case11/Case11_iot10.png)<P>

### Part 2: Install the IFTTT App on smartphone
1. Go to <U>play store</U> or <U>app store</U> to search and download the IFTTT App
![auto_fit](images/Case11/Case11_iot11.png)<P>
2. Login to your IFTTT account
![auto_fit](images/Case11/Case11_iot12.png)<P>

## Programming (MakeCode)
<HR>

<span id="subtitle">Step 1. Initialize OLED, IoT:bit and connect to WiFi, create variable</span><BR><P>
* Snap `Initialize OLED with width:128, height: 64` to `on start`
* Snap `Initialize IoT:bit TX P16 RX P8` from `IoT:bit` to `on start`
* Snap `Set Wi-Fi to ssid pwd` from `IoT:bit`
* Enter your Wi-Fi name and password. Here we set `smarthon` as `SSID` and `12345678` as `password`
* Snap `Set strip to NeoPixel at pin P1 with 1 leds as RGB(GRB format)`
![pic_60](images/Case11/Case11_p1.png)<P>

<span id="subtitle">Step 2. Show icon “tick” after WiFi connection</span><BR><P>
* Snap `show icon` from `basic` to `On WiFi connected` and select icon `tick`
![pic_50](images/Case11/Case11_p2.png)<P>

<span id="subtitle">Step 3. Check the internet connection status</span><BR><P>
* In the `Forever`, put a `if` statement with condition `WiFi connected?` to check the connection status
![pic_50](images/Case11/Case11_p3.png)<P>

<span id="subtitle">Step 4. Check the flame sensor result and action on OLED display</span><BR><P>
* Put another `if` statement with condition `Get flame detection at Pin P2 = true` to recognize the flame 
* Play a warning sound when the flame was detected 
![pic_70](images/Case11/Case11_p4.png)<P>

<span id="subtitle">Step 5. Action on Warning LED</span><BR><P>
* The LED should be blinking to telling dangerous 
* Put `strip show color red` to turn on the LED in red color
* Add a `pause (ms) 100` to wait for 0.1 second
* Put `strip show color black` to turn off the LED
* Pause for 0.1 second again
![auto_fit](images/Case11/Case11_p5.png)<P>

<span id="subtitle">Step 6. Action on IFTTT</span><BR><P>
* Put a `Send IFTTT key* XXXXXXXXX event_name* XXXXX ....` to send the event to IFTTT
* Fill in the `IFTTT key` from your Webhooks and the Applet's `event_name`
![pic_50](images/Case11/Case11_p6.png)<P>

<span id="subtitle">Step 7. Know the Upload result</span><BR><P>
* To check the upload state, use the `On IFTTT Uploaded` to get the sending result
* Inside the `On IFTTT Uploaded`, use OLED display to show the information
* Clear the OLED display before each update by `clear OLED display`
* Show upload state by `show string join IFTTT: Status`, the `Status` value is from the function's placeholder
* Show error_code by `show string join Error: Error_code`, the `Error_code` value is from the function's placeholder
![pic_50](images/Case11/Case11_p7.png)<P>


<span id="subtitle">Full Solution<BR><P>
MakeCode: [https://makecode.microbit.org/_PaX5qwPeRa0e](https://makecode.microbit.org/_PaX5qwPeRa0e)<BR><P>
You could also download the program from the following website:<BR>
<iframe src="https://makecode.microbit.org/#pub:_PaX5qwPeRa0e" width="100%" height="500" frameborder="0"></iframe>




## Result
<HR>

When the flame source is detected by the flame sensor, it will trigger to blink the LED, making alert sound, and send the warning notification to IFTTT
<BR><P>
![auto_fit](images/Case11/Case11_result.gif)<P>
![auto_fit](images/Case11/Case11_result2.png)<P>

## Think
<HR>

1. Other than warning, any task we can do when we detect the flame? (e.g add a fan or sprinkler to extinguish the fire, call the police?)
<BR><P>
