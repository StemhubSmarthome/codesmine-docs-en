# IoT Case 13: Alexa Voice Control Fan

Level: ![level](images/level5.png)
![auto_fit](images/Case13/blank.png)<P>

## Goal
<HR>

Make a remotely controlled by using Amazon Alexa service.


## Background
<HR>

<span id="subtitle">What is Alexa voice control fan?</span><BR><P>
Alexa voice control fan is a fan that is connected to internet and can be woken up by voice command.<BR><P>

<span id="subtitle">Alexa voice control fan principle
</span><BR><P>
By using Smarthon IoT:bit extension on IFTTT platform, commands can be pre-set such that when a specific phrase is said to Alexa it will send the commands automatically through the internet to the fan and trigger on or off actions.<BR><P>


## Part List
<HR>

![auto_fit](images/Case13/Case13_parts.png)<P>
 
## Assembly step
<HR>

<span id="subtitle">Step 1</span><BR><P>
Use M4 screw and nuts to install the Multi-color LED to B4 cardboard<BR><P>
![auto_fit](images/Case13/blank.png)<P>




## Hardware connect
<HR>

1. Connect the motor module to P1
![auto_fit](images/Case13/Case13_hardware.png)<P>

## Programming (MakeCode)
<HR>

<span id="subtitle">Step 1. Initialize OLED, IoT:bit and connect to WiFi</span><BR><P>
* Snap `Initialize OLED with width:128, height: 64` to `on start`
* Snap `Initialize IoT:bit TX P16 RX P8` from `IoT:bit` to `on start`
* Snap `Set Wi-Fi to ssid pwd` from `IoT:bit`
* Enter your Wi-Fi name and password. Here we set `smarthon` as `SSID` and `12345678` as `password`
![pic_60](images/Case13/Case13_p1.png)<P>

<span id="subtitle">Step 2. Show icon “tick” and Device ID after WiFi connection</span><BR><P>
* Snap `show icon` from `basic` to `On WiFi connected` and select icon `tick`
* Draw the `Device ID` variable from `On WiFi connected` to the `show string` block placeholder
![pic_50](images/Case13/Case13_p2.png)<P>

<span id="subtitle">Step 3. Receive Command</span><BR><P>
* Inside the `On WiFi Received`, show the command on OLED display
* Clear the display before each update by `Clear OLED display`
* Show the `WAN_Command` with text explanation by `show string join Command: WAN_Command`
![pic_50](images/Case13/Case13_p3.png)<P>

<span id="subtitle">Step 4. Action with command</span><BR><P>
* put a nested `if-else` statement with different conditions
* Set the first condition as `WAN_Command = turn_off_fan`
* In the `if` segment, turn off the fan by `set Motor fan with speed 0 at P1`
* In the second `if` condition, use `WAN_Command = turn_on_fan`
* In the second `if` segment, turn on the fan by `set Motor fan with speed 1023 at P1`

![auto_fit](images/Case13/Case13_p4.png)<P>

<span id="subtitle">Full Solution<BR><P>
MakeCode: [https://makecode.microbit.org/_eW2fDXbpAFU3](https://makecode.microbit.org/_eW2fDXbpAFU3)<BR><P>
You could also download the program from the following website:<BR>
<iframe src="https://makecode.microbit.org/#pub:_eW2fDXbpAFU3" width="100%" height="500" frameborder="0"></iframe>


## IoT (Alexa, Cloud Control, IFTTT)
<HR>

<span id="subtitle">Step 1. Create Amazon Account (if not have amazon account)<BR><P>
* Go to [Amazon](https://www.amazon.com) and create a new account
* If you have exist amazon account, skip this step

![pic_70](images/Case13/Case13_iot1.png)<P>

<span id="subtitle">Step 2. Get the Amazon alexa apps<BR><P>

* Depend on your mobile device, you may get the Amazon Alexa Apps from different places:<BR>
1. Android:[google play store](https://play.google.com/store/apps/details?id=com.amazon.dee.app&hl=zh_HK&gl=US)
2. IOS: [App store](https://apps.apple.com/us/app/amazon-alexa/id944011620)

* Download and install it
* Follow the App instruction to setup your Alexa device and connect to your amazon account

![pic_80](images/Case13/Case13_iot2.png)<P>

<span id="subtitle">Step 3. Setup IFTTT Alexa<BR><P>

* In the IFTTT application explore page, choose Amazon Alexa in the if segment
* 
![pic_70](images/Case13/Case13_iot3.png)<P>

* Click the `Connect` button, then login into the amazon that connected to Alexa

![auto_fit](images/Case13/Case13_iot4.png)<P>

<span id="subtitle">Step 4. Setup IFTTT Applet<BR><P>

* Create a new applet, at the `IF` segment,search and choose `Amazon Alexa`
* In `Amazon Alexa` , choose `Say a specific phrase` to custom the speech command
![pic_80](images/Case13/Case13_iot5.png)<P>

* Input the word of speech as `command`
* Press `Create trigger`
![pic_80](images/Case13/Case13_iot6.png)<P>

* At the create applet's `THEN` segment, search and choose `Smarthon IoT (micro:bit)`
![pic_80](images/Case13/Case13_iot7.png)<P>

* In `Smarthon IoT (micro:bit)`, choose `Control Command` to send specific command to IoT:bit
![pic_70](images/Case13/Case13_iot8.png)<P>

* Input the `Device ID` for your IoT:Bit, and the `Command` need to send to IoT:bit
![pic_90](images/Case13/Case13_iot9.png)<P>

* Finish the setup of applet
![pic_80](images/Case13/Case13_iot10.png)<P>


## Result
<HR>
When say “Alexa trigger turn on the fan”, the fan will be turn on<BR><P>

![auto_fit](images/Case13/Case13_result1.png)<P>
When say “ Alexa trigger turn off the fan”, the fan will be turn off
<BR><P>
![pic_90](images/Case13/Case13_result2.png)<P>


## Think
<HR>

1. Apart from "Say a specific phrase” Alexa IFTTT trigger, any other Alexa trigger can use in case? <BR>
