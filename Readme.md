#Little Wire - v1.2

![little wire](lw.jpg)

1\.  [Short Story](#shortstory)  
2\.  [Features](#features)  
2.1\.  [Experimental Features](#experimentalfeatures)  
3\.  [Software Support](#softwaresupport)  
3.1\.  [Ruby library: _littlewire.rb_](#rubylibrary:_littlewire.rb_)  
4\.  [Firmware Upgrade / Installation](#firmwareupgrade/installation)  
4.1\.  [If you have a bare Attiny85 chip:](#ifyouhaveabareattiny85chip:)  
4.2\.  [If your Attiny85 has _micronucleus_ bootloader installed:](#ifyourattiny85has_micronucleus_bootloaderinstalled:)  
4.3\.  [If your Attiny85 has _fast tiny & mega UART_ bootloader installed:](#ifyourattiny85has_fasttiny&megauart_bootloaderinstalled:)  
4.4\.  [If you bought your _Little Wire_ from Seeedstudio:](#ifyouboughtyour_littlewire_fromseeedstudio:)  
5\.  [Where are the pre-compiled binaries, drivers and archives?](#wherearethepre-compiledbinariesdriversandarchives?)  
6\.  [Pin Mapping](#pinmapping)  
7\.  [Reference projects](#referenceprojects)  
8\.  [Contact](#contact)  
9\.  [Please note:](#pleasenote:)  

<a name="shortstory"></a>

##1\. Short Story

When i saw simpleavr's [implementation](http://www.simpleavr.com/avr/vusbtiny+) of usbtiny on attiny45 , i thought it would be cool if i make a kit version of this with a minimal form factor. Then i designed a PCB and sent for first prototype. Later on i thought, if i want to sell this, it would be much cooler ,and more suitable with "[Open Source Hardware](http://www.oshwa.org/definition/)" concept, if i bring this project one step ahead. So i tried to fit anything extra to the device and this project came out.

I collaborated with the [Seeedstudio](www.seeedstudio.com) and they produced an initial batch for me and _Little Wire_ kits went [online](http://www.seeedstudio.com/depot/little-wire-p-1212.html) in June 2012. After that batch finished in April 2013, _notice the time difference_, I decided not to continue producing them through contract manifacturing. Currently, you can't buy readymade _Little Wire_ kits but since this is an OSHW project, you are free and welcomed to produce your own version.

<a name="features"></a>

##2\. Features

- _usbtinyisp_ compatable AVR programmer.
- 4 channel GPIO.
- ADC with 10 bit resolution.
- 2 parallel hardware PWM outputs.
- SPI interface.
- I2C interface.
- 1-Wire interface
- WS2812 RGB LED interface.
- Multiple device support.
   
<a name="experimentalfeatures"></a>

###2.1\. Experimental Features
- 3 parallel software PWM outputs.
- [Printf style debugging over AVR-ISP pins!](http://blog.kehribar.me/?p=36)
- [Pic24f programmer with limited device support.](http://blog.kehribar.me/?p=171)
- USB to UART converter, by loading another firmware _([CDC-232](http://www.recursion.jp/avrcdc/cdc-232.html) port)_ Maximum advised baud rate is 4800 bps.

**Note:** This tool has to take instructions at run-time over USB. It can't work in a computerless environment.

<a name="softwaresupport"></a>

##3\. Software Support

When i first released _Little Wire_ , it had native C,C++,C# and Processing support through custom libraries written by me. Later, maintaining multiple software libraries became a very demanding task. Therefore I dropped support for C++,C# and Processing libraries with the v1.2 release of _Little Wire_. If you still use your v1.0 / v1.1 firmware you can look at the archive releases to get support for those languages. **Beware**, software libraries are **not** backward/forward compatible and I definitely advice you to get the latest v1.2 firmware onto your device.

Doxygen documentation for the current _C library_ can be found here: <http://littlewire.cc/documentation/>

For further support, please take a look at _examples_ folder. If you want to contribute an example you can make a pull request so that I can add it to the main repo, or if you find a bug in one of the examples please open an issue ticket.

<a name="rubylibrary:_littlewire.rb_"></a>

###3.1\. Ruby library: _littlewire.rb_

Even though this is not an official and complete library for the _Little Wire_, it is well developed and worth mentioning. This library is maintained by [@Bluebie](http://twitter.com/bluebie) and covers _most_ of the _Little Wire_ features. If you are interested in controlling your _Little Wire_ device from Ruby, it would be worth looking. You can find the details about this library here: <https://github.com/Bluebie/littlewire.rb>

<a name="firmwareupgrade/installation"></a>

##4\. Firmware Upgrade / Installation

<a name="ifyouhaveabareattiny85chip:"></a>

###4.1\. If you have a bare Attiny85 chip:

- First, you should upload the _micronucleus_ bootloader software to your chip and you should set the fuses properly. Following is an example 

		avrdude -c usbtiny -p t85 -U flash:w:micronucleus-1.02.hex -U lfuse:w:0xe1:m -U hfuse:w:0x5d:m -U efuse:w:0xfe:m

- After you upload the bootloader to your chip, you can follow the steps below. 

<a name="ifyourattiny85has_micronucleus_bootloaderinstalled:"></a>

###4.2\. If your Attiny85 has _micronucleus_ bootloader installed:

- You can upload the desired firmware via the micronucleus commandline application.

		micronucleus littlewire_v12.hex
		
- You can find the micronucleus commandline application from here: <https://github.com/Bluebie/micronucleus-t85>

<a name="ifyourattiny85has_fasttiny&megauart_bootloaderinstalled:"></a>

###4.3\. If your Attiny85 has _fast tiny & mega UART_ bootloader installed:

- You can upload the latest firmware via onboard bootloader, but I don't recommend this.
- You can use a HVSP programmer like STK500, AVR Dragon or a high voltage fuse resetter device like "HV Rescue Shield" or "HSVP Fuse Resetter" to reset your device completely. After you disable the RSTDISBL fuse, you can follow the _"If you have a bare Attiny85 chip"_ steps.
- You can buy an empty Attiny85 chip and start from the begining.

<a name="ifyouboughtyour_littlewire_fromseeedstudio:"></a>

###4.4\. If you bought your _Little Wire_ from Seeedstudio:
- Unfortunately, micronucleus bootloader wasn't a _thing_ when I was designing the v1.0 release of the _Little Wire_. Therefore your device has the _fast tiny & mega UART_ bootloader. You can follow the steps above.

<a name="wherearethepre-compiledbinariesdriversandarchives?"></a>

##5\. Where are the pre-compiled binaries, drivers and archives?

You can find them from the _Little Wire_ web page: <http://littlewire.cc/downloads.html>

<a name="pinmapping"></a>

##6\. Pin Mapping
	
|Silkscreen|usbtinyisp|Hard PWM|Soft PWM|ADC |I2C|SPI|Onewire|WS2812|CDC-232|
|----------|----------|--------|--------|----|---|---|-------|------|-------|
|pin1      |MISO      |CH_B    |CH_2    |-   |-  |DO |-      |DATA  |TX     |
|pin2      |SCK       |-       |CH_3    |CH_1|SCL|SCK|DATA   |DATA  |-      |
|pin3      |RESET     |-       |-       |CH_0|-  |CS |-      |DATA  |-      |
|pin4      |MOSI      |CH_A    |CH_1    |-   |SDA|DI |-      |DATA  |RX     |

<a name="referenceprojects"></a>

##7\. Reference projects

- This project is proudly and heavily based on: 
    - Original usbtiny project: <http://www.xs4all.nl/~dicks/avr/usbtiny/>
    - Ladyada version of usbtiny: <http://www.ladyada.net/make/usbtinyisp>/
    - simpleavr's implementation of usbtiny on Attiny45: <http://www.simpleavr.com/avr/vusbtiny>
    - "fast tiny & mega UART bootloader" project from AVR freaks: <http://tinyurl.com/fastTinyAndMega-UARTbootloader>
    - Micronucleus bootloader: <https://github.com/Bluebie/micronucleus-t85>

<a name="contact"></a>

##8\. Contact

For any reason, you can contact me through: _ihsan{at}kehribar{dot}me_

<a name="pleasenote:"></a>

##9\. Please note: 

	Do not use the Adafruit USB VID/PID without written permission from Adafruit Industries, LLC and 
	Limor "Ladyada" Fried (support@adafruit.com). Permission is granted for littlewire, Ihsan Kehribar
	and Seeed Studio by Adafruit Industries, LLC to use the Adafruit USB VID/PID for littlewire 
	(SKU:AVR06071P)		
