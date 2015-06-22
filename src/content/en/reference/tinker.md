---
word: Tinker
title: The TInker API
order: 13
shared: true
---

#The Tinker API

When the Tinker firmware is installed on your Particle device, it will respond to certain API requests from your mobile app, which mirror the four basic GPIO functions (digitalWrite, analogWrite, digitalRead, analogRead). These API requests can also be made from another application or from the command line, so you can build your own web or mobile app around the Tinker firmware.

## digitalWrite

Sets the pin to HIGH or LOW, which either connects it to 3.3V (the maximum voltage of the system) or to GND (ground). Pin D7 is connected to an on-board LED; if you set pin D7 to HIGH, the LED will turn on, and if you set it to LOW, it will turn off.

    POST /v1/devices/{DEVICE_ID}/digitalwrite

    # EXAMPLE REQUEST IN TERMINAL
    # Device ID is 0123456789abcdef
    # Your access token is 123412341234
    curl https://api.particle.io/v1/devices/0123456789abcdef/digitalwrite \
      -d access_token=123412341234 -d params=D0,HIGH

The parameters must be the pin (A0 to A7, D0 to D7), followed by either HIGH or LOW, separated by a comma. The return value will be 1 if the write succeeds, and -1 if it fails.



## analogWrite

Sets the pin to a value between 0 and 255, where 0 is the same as LOW and 255 is the same as HIGH. This is sort of like sending a voltage between 0 and 3.3V, but since this is a digital system, it uses a mechanism called Pulse Width Modulation, or PWM. You could use *analogWrite* to dim an LED, as an example.

    POST /v1/devices/{DEVICE_ID}/analogwrite

    # EXAMPLE REQUEST IN TERMINAL
    # Device ID is 0123456789abcdef
    # Your access token is 123412341234
    curl https://api.particle.io/v1/devices/0123456789abcdef/analogwrite \
      -d access_token=123412341234 -d params=A0,215

The parameters must be the pin (A0 to A7, D0 to D7), followed by an integer value from 0 to 255, separated by a comma. The return value will be 1 if the write succeeds, and -1 if it fails.




## digitalRead

This will read the digital value of a pin, which can be read as either HIGH or LOW. If you were to connect the pin to 3.3V, it would read HIGH; if you connect it to GND, it would read LOW. Anywhere in between, it'll probably read whichever one it's closer to, but it gets dicey in the middle.

    POST /v1/devices/{DEVICE_ID}/digitalread

    # EXAMPLE REQUEST IN TERMINAL
    # Device ID is 0123456789abcdef
    # Your access token is 123412341234
    curl https://api.particle.io/v1/devices/0123456789abcdef/digitalread \
      -d access_token=123412341234 -d params=D0


The parameter must be the pin (A0 to A7, D0 to D7). The return value will be 1 if the pin is HIGH, 0 if the pin is LOW, and -1 if the read fails.



## analogRead

This will read the analog value of a pin, which is a value from 0 to 4095, where 0 is LOW (GND) and 4095 is HIGH (3.3V). All of the analog pins (A0 to A7) can handle this. *analogRead* is great for reading data from sensors.

    POST /v1/devices/{DEVICE_ID}/analogread

    # EXAMPLE REQUEST IN TERMINAL
    # Device ID is 0123456789abcdef
    # Your access token is 123412341234
    curl https://api.particle.io/v1/devices/0123456789abcdef/analogread \
      -d access_token=123412341234 -d params=A0

The parameters must be the pin (A0 to A7, D0 to D7). The return value will be between 0 and 4095 if the read succeeds, and -1 if it fails.