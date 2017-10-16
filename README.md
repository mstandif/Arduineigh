# Arduineigh
The open pony-themed Arduino clone

The following walk-through is intended for those new to the realm of making your own Arduino-type board. If this isn't your first rodeo, then you can ignore it and go straight to the fun stuff.

## Building Your Arduineigh
#### So you bought the blank board... what now?
Well first of all you need to buy the tools and parts required to get this thing up and running. If you are already an electronics hobbyist or enthusiast, you likely have most of it already. If you're new/new-ish here's what you need.

#### Necessary Tools
1. Soldering Iron
    - I'd recommend getting an iron with proper temperature control such as the Weller WLC100, Hakko FX888, or even some chinese knock-off like the 937D+. If the iron plugs directly into a wall outlet, don't buy it.
2. Solder
    - Lead solder will be easier to use (lower melting temperature, less chance of splatter, better flow), however lead is toxic so lead-free is highly recommended. Also since this is surface mount stuff, thinner diameter solder is better.
    - Pro tip: Pb is the chemical symbol for Lead, Sn is Tin, Ag is Silver, and Cu is Copper. Pay attention to the composition of your solder. Lead solder is usually 60% Sn and 40% Lead, lead-free is normally 99% Sn and the last 1% both Ag and Cu. Solder with high amounts of Ag is Jewelers solder, and solder with high amounts of Cu is welding solder; you do not want these.
3. SMD Tweezers
    - They grab tiny parts, what more could you ask for?
4. Flux "no-clean" Pen
    - Flux helps make the solder flow easily and nicely, soldering a 32-pin IC like the ATMega328 is a living hell without flux. If you do not get "no-clean" flux, you will have to get flux remover or rubbing alcohol to clean off the flux when finished. Flux can otherwise cause corrosion and nasty residues.
5. Solder Wick
    - Wicks away any mistakes you may make. Be sure to not touch the wick itself during use, you will burn yourself.
6. Safety Glasses
    - Solder and flux can sizzle and splatter, it's dangerous, protect your eyes!
7. Multimeter (highly recommended)
    - Great for debugging problems! Personally I use a Fluke meter ($200+) but almost any cheap meter will be sufficient for hobby needs.
    
#### Parts For The Board
See the Arduineigh Bill of Materials file for a list of all components for a fully assembled board. Part numbers for Digi-key are provided, but you can source them from wherever so long as they are the correct part. Some compnents like the LED's, female headers, and power regulators are not truely necessary if you only want the bare minimum. However to have full compatibility with arduino shields, and best user experience, you should purchase all required components.

#### Time To Solder!!!
Don't know how to solder? Never soldered surface mount components? No Problem!
After an exhausting 5 minutes of searching, I have found "the best" video tutorial on soldering passive components and more complex IC's. This teaches the same methods that I use to hand solder these types of things.
[EEVblog #997 - How To Solder Surface Mount Components](https://www.youtube.com/watch?v=hoLf8gvvXXU)

## Programming Your Arduineigh
So you've built the thing, now it's time to make it do the things... 

Oh and don't forget to install the Arduino IDE.

#### Flashing The Arduino Uno Bootloader
The easiest way to do this is to use another arduino board as shown here: [Using an Arduino as an AVR ISP](https://www.arduino.cc/en/Tutorial/ArduinoISP)
You can also use a USBtinyISP or Atmel ICE and just skip straight to the "Burn Bootloader" step.
The Arduino Uno bootloader is probably your best choice (as it takes up the least space), however you can also use the Arduino Duemilanove, Arduino Diecimila, or Arduino Mini bootloaders and it should work just fine.

#### Programming
This board does not include it's own USB to serial converter, so you will need to purchase one of the following add-ons and plug it onto connector P4 before you can program it to do anything.
[Sparkfun BOB-13830](https://www.digikey.com/product-detail/en/sparkfun-electronics/BOB-13830/1568-1504-ND/6674603)
[Sparkfun DEV-09716](https://www.digikey.com/product-detail/en/sparkfun-electronics/DEV-09716/1568-1103-ND/5318745)

To make sure everything is working as intended, you should first upload the Blink sketch. 

Start by going to File > Examples > 1.Basic > Blink, then click the Upload arrow. It should upload succussfully and the second LED on the board should start to flash (if your board was purchased at BronyCon 2017, you do not have this second LED and will have to add a resistor and LED in series from pin 13 to GND).

If the LED is blinking, then congratulations! You have successfully built your very own Arduineigh!

## Everything Is On Fire (Issues and how to fix them)
Shit happens, things break, everything is fine....

#### My power LED (D1) is not turning on
    1. Does the board have power?
        - Check 5V and GND with your multimeter set to DC voltage. If you see no voltage, skip to "Power Is Not Reaching My Board".
    2. Is your LED soldered correctly?
        - Remove power, set your multimeter to diode (looks like this: -|<|- ), and place the black probe to the LED pad closest to R3, and the red probe to GND. If the LED lights dimly, your LED is backwards.
        - Switch your multimeter to resistance (Ω) and measure accross R3. It should be ~330 ohms. If it's 0 ohms, or vastly greater (millions of ohms or more) you have a bad resistor.
    3. Are your solder joints good?
        - If you still havn't identified the problem, try redoing your solder joints, there may be a bad connection.
        
#### My Blink Sketch isn't doing anything
    1. Does the board have power?
        - Check 5V and GND with your multimeter set to DC voltage. If you see no voltage, skip to "Power Is Not Reaching My Board".
    2. Did you flash the Bootloader?
        - You need the bootloader before the board can be used with any sketches. Find out how here: [Using an Arduino as an AVR ISP](https://www.arduino.cc/en/Tutorial/ArduinoISP)
    3. Did you selct the right board/port?
        - For a sketch to upload properly, you need to select the board (should be the one corresponding with the bootloader you selected) and the correct port (normally the highest port number is your USB device).
    4. Did your sketch upload?
        - If you got an error message during upload, google it and look for a solution on the Arduino Forums. 
    5. Is your LED connected correctly?
        - Remove power, set your multimeter to diode (looks like this: -|<|- ), and place the black probe to pad 13, and the red probe to GND. If LED D2 lights dimly, your LED is backwards.
        - Set your multimeter to resistance (Ω) and measure accross R4. It should be ~330 ohms. If it's 0 ohms, or vastly greater (millions of ohms or more) you have a bad resistor.
        - As a final check, set your multimeter back to diode mode, and place the red probe on pin 13, and the black on GND. If the LED lights dimly, then your test LED is correctly connected, and not the issue. 
    6. Is the Atmega doing anything?
        - Apply power to your board, set your multimeter to DC voltage, and place the red probe on pad 13, and the black to GND. You should see the voltage switching between 5V and 0V about once per second. If not, you may have a bad solder joint, or a bad microcontroller.
    7. Is the Atmega soldered properly?
        - Look very closely at the pins on the Atmega328 (a magnifying glass and light source may help with this). If any pins look like they aren't actually soldered down (like the pin is just sitting on top of the pad) try touching it up with the soldering iron again. 
    8. What else can I do?
        - Check that your crystal, C8, and C9 are all soldered properly. 
        - You could try replacing the Atmega and try again.
        - Ask a friend for help.

#### Something is getting warm...
    1. Did you solder correctly?
        - If something is getting warm, it could be a soldering mistake (usually the case for IC's and transistors). Check part orientation, and look for any pins that were accidentally bridged together. Fix anything that looks even remotely suspicious, and hope there wasn't permanent damage.
    2. Did a component Fail?
        - Feel around for which part is warming up (usually it's capacitors that fail) and simply remove it and see if the problem is fixed. For board stability it should be replaced with an equivalent component, but they aren't necessary for troubleshooting.

#### Power Is Not Reaching My Board
    1. Is your power source connected correctly?
        - This board can be powered in two ways. The first is connecting a 5V supply directly to the 5V pin, and the second is connecting a 6V-16V supply to the VIN pin. Note that if 3V is needed, you must either go with using the VIN method, or have a second power supply of 3V connected to the 3V pin. 3V doesn't power anything on the board itself, but may be used by certain Arduino shields.
    2. Is something shorting your power supply?
        - Check if something on the board is warm (or hot) to the touch. If so, go back to "Something is getting warm...".
        - Set your multimeter to Continuity mode. Check between VIN and GND, 5V and GND, and 3V and GND. If any of these three show continuity (most meters will beep) then you have a short between those two point. This could be a solder bridge between two pins, a bad component, or a conductive contaminant somewhere.  
    
#### The magic smoke came out of my board
    1. How do I get the smoke back in?
        - Sorry but you can't. Whether the component was soldered on wrong, was faulty from the start, or you connected something you shouldn't have, that component is gone and ain't coming back. Remove the damaged part from the board and replace it.
        - Important note: If you smoked one component, it's very possible you killed others too. It may be smart to have spares on hand just in case.
    
