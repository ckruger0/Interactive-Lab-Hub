# IDD-Fa18-Lab1: Blink!

**A lab report by Chris Kruger**

## Part A. Set Up a Breadboard

<img src="https://i.imgur.com/RUfRL8b.jpg">

## Part B. Manually Blink a LED

**a. What color stripes are on a 100 Ohm resistor?**<BR>
A 100 Ohm resistor has brown (band + multiplier), black (band), and yellow (tolerance) stripes.<BR>
The 220 Ohm resistor supplied for this lab has red, black, and red stripes.
 
**b. What do you have to do to light your LED?**<BR>
Have to hold down the switch to turn the LED on. 

## Part C. Blink a LED using Arduino

### 1. Blink the on-board LED

**a. What line(s) of code do you need to change to make the LED blink (like, at all)?**<BR>
The "digitalWrite()" function is used to change the voltage level of the LED, setting it to "HIGH" turns it on. As supplied though, nothing needs be changed in the sample "Blink" code.

**b. What line(s) of code do you need to change to change the rate of blinking?**<BR>
A combination of "digitalWrite()" and "delay()" are used to control the rate of blinking. First, setting digitalWrite() to "LOW" turned the LED off, and delay() can be populated with time in ms to control how long the LED is in the digitalWrite() state for. Finally you can use digitalWrite() to set it back to HIGH to get the LED back on.

**c. What circuit element would you want to add to protect the board and external LED?**<BR>
You need to add a resistor to protect the LED and board.
 
**d. At what delay can you no longer *perceive* the LED blinking? How can you prove to yourself that it is, in fact, still blinking?**<BR>
I was able to perceive the LED blinking all the way down to a 2ms delay, inclusive. Once it got to 1ms it appeared solid. It would probably be possible to determine that it's still blinking by using a slow motion camera, or just having faith in the same line of that can properly execute a blink at 2ms can also do it at 1ms. 
 
**e. Modify the code to make your LED blink your way. Save your new blink code to your lab 1 repository, with a link on the README.md.**


### 2. Blink your LED

**Make a video of your LED blinking, and add it to your lab submission.**<BR>

<a href="https://youtu.be/Qhy_E0TosvQ">https://youtu.be/Qhy_E0TosvQ</a>


## Part D. Manually fade an LED

**a. Are you able to get the LED to glow the whole turning range of the potentiometer? Why or why not?**<BR>


## Part E. Fade an LED using Arduino

**a. What do you have to modify to make the code control the circuit you've built on your breadboard?**<BR>
It seems like the most common thing I've had to change in the examples to control the circuit is the **pinMode()** function. For the fade example however, my LED was already connected to pin 9 so I didn't have to change anything there. 

**b. What is analogWrite()? How is that different than digitalWrite()?**<BR>
 analogWrite() writes an oscillating value to a pin between 0 and 255 to vary the brightness of an LED. This is different than the "all or nothing" approach seen in digitalWrite() where it's more of a binary "HIGH" for full brightness or "LOW" for no brightness. <a href="https://www.arduino.cc/reference/en/language/functions/analog-io/analogwrite/">src</a>


## Part F. FRANKENLIGHT!!!

### 1. Take apart your electronic device, and draw a schematic of what is inside. 

**a. Is there computation in your device? Where is it? What do you think is happening inside the "computer?"**<BR>
There is likely computation on the device that converts manual inputs into vectors for the computer to read. I think that there is likely an X-Y coordinate system that is constantly feeding from the optical sensor to the attached computer.

**b. Are there sensors on your device? How do they work? How is the sensed information conveyed to other portions of the device?**<BR>
Yes. Most evident are the 2 push button sensors (SW1 SW2) and the optical sensor used to track mouse movement. The push buttons are straightforward in that they have plastic switches than can be depressed. The optical sensor I imagine uses an XY coordinate system.<BR><BR>
The interesting sensor to me appeared in how the scroll wheel functionality works. It appears there is a small optical sensor of some kind on either side of the rubber wheel, and it calculates scrolling by counting what appears to be a slotted interior on the wheel. 

**c. How is the device powered? Is there any transformation or regulation of the power? How is that done? What voltages are used throughout the system?**<BR>
The device is typically powered with a single AA battery. 

**d. Is information stored in your device? Where? How?**<BR>
It does not appear as though information is stored onboard the wireless mouse. 
 
### 2. Using your schematic, figure out where a good point would be to hijack your device and implant an LED.

My original plan was to have the wireless mouse be 100% under its own power supplied from the AA battery, however despite all my arrangements it did not seem to work. I ended up attaching the 5V and ground wires from my microcontroller to complete the powered circuit.<BR><BR> 
 
As an initial gut check I simply fitted an LED to the positive and negative terminals originally provisioned for the battery, and the LED lit as expected. See below:

<img src="https://i.imgur.com/7f7QmTX.jpg">

### 3. Build your light!

I then looked deeper into the schematic of the wireless mouse and realized there was an opportunity to attach the LED to the exposed wire originally used to connect the optical LED used to track movement. A video of it in action can be seen below (apologies in advance for the crime of vertical video):

<a href="https://youtu.be/KjgJuvxJ9EA">https://youtu.be/KjgJuvxJ9EA</a>

One interesting thing that I noticed was that when I tested the LED directly on the wires originally used for the battery, it generated a continuous, solid light. However when the LED was joined to the exposed wire for the optical motion sensor it flickered at regular intervals. I double checked to make sure it wasn't just making contact in a haphazard way and it appears there is some purpose behind this flickering. 
