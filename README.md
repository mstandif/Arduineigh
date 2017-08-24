# Arduineigh
The open pony-themed Arduino clone

The following walk-through is intended for those new to the realm of making your own Arduino-type board. If this isn't your first rodeo, then you can ignore it and go straight to the fun stuff.

## Building Your Arduineigh
#### So you bought the blank board... what now?
Well first of all you need to buy the tools and parts required to get this thing up and running. If you are already an electronics hobbyist or enthusiast, you likely have most of it already. If you're new/new-ish here's what you need.

#### Necessary Tools
1. Soldering Iron
    -I'd recommend getting an iron with proper temperature control such as the Weller WLC100, Hakko FX888, or even some chinese knock-off like the 937D+. If the iron plugs directly into a wall outlet, don't buy it.
2. Solder
    -Lead solder will be easier to use (lower melting temperature, less chance of splatter, better flow), however lead is toxic so lead-free is highly recommended. Also since this is surface mount stuff, thinner diameter solder is better.
    -Pro tip: Pb is the chemical symbol for Lead, Sn is Tin, Ag is Silver, and Cu is Copper. Pay attention to the composition of you solder. Lead solder is usually 60% Sn and 40% Lead, lead-free is normally 99% Sn and the last 1% both Ag and Cu. Solder with high amounts of Ag is Jewelers solder, and solder with high amounts of Cu is welding solder; you do not want these.
3. SMD Tweezers
    -They grab tiny parts, what more could you ask for?
4. Flux "no-clean" Pen
    -Flux helps make the solder flow easily and nicely, soldering a 32-pin IC like the ATMega328 is a living hell without flux. If you do not get "no-clean" flux, you will have to get flux remover or rubbing alcohol to clean off the flux when finished. Flux can otherwise cause corrosion and nasty residues.
5. Safety Glasses
    -Solder and flux can sizzle and splatter, it's dangerous, protect your eyes!

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

## Everything Is On Fire
Shit happens, things break, everything is fine....

#### Potential Issues
Nothing here yet...
