 # multiflasher-pro
Programmer for ESP32, AVR-UPDI &amp; UART-monitor

To get around the limitations of the current ITL211205 multiflasher, an upgrade is proposed which:
* is easy and quick to solder (or can be assembled by JLCPCB):
  * (no QFN or pitch >0.5mm)
  * (no 0402 or smaller)
* is reliable
* is protected against short-circuits on the target
* protected against latch-up (target is powered through other means, while programmer is unpowered) : open-drain connections
* doesn’t require a programmer to program the programmer
* allows for easy power cycling of the target (without need for disconnecting the target)
* allows for easy reset of the target : using a switch
* has dual UART( 1 for monitoring, 1 for programming)
  * [Single UART solution](https://kicanvas.org/?github=https%3A%2F%2Fgithub.com%2Ftechstudio-design%2FtinyUPDI)

# Nice to have
* has custom serial nr.

# Use cases:
* ESP32 : programming & monitoring (RTS/DTR needed for programming)
* AVR : UPDI programming using pyupdi
* Raspberry Pi Pico SWD + UART : programming & monitoring
* Raspberry Pi UART : monitoring (pin functions clearly indicated)
* Expansion port for add-on : RS485, RS422, galvanically isolated UART

# Connectivity:
## Programming port
* RA IDC-connector
    * allows for connection of dupont cables
* compatible to the 7c7-SKEDD interface : 
    * First 6 or last 6 pins should be the same as the 7c7-SKEDD interface, so that a 6-pin ribbon cable can be used to connect to the target
* RXD, TXD, RTS, DTR
* Add-on:
  * USB-DAM (Debug Accessory Mode)

## Debugging port
* SWD

## Logging port
* almost full UART (RXD, TXD, RTS, CTS, DTR)
* allow for connection of dupont cables
* Add-on (through expansion port): either BTB-connector or test points and SMD-spring loaded pins on the add-on board
  * RS485
  * RS422
  * galvanically isolated UART

## IO-Voltage
The target outputs its IO-voltage on the programming port, so that the programmer can adapt its IO-voltage to the target's IO-voltage.
* 3.3V
* 5V

## Host PC
* USB-C

# Target power
* High-side current monitoring
* Separate Wire-to-Board connector for power (JST-XH, -EH, -PH)
  * polarity protected
  * polarity clearly indicated
* USB-PD sink (5V, 9V, 12V, 15V, 20V)
  * 5V is always available
  * 9V, 12V, 15V, 20V are only available when the host PC supports it
  * rotary switch to select the voltage
  * status LEDs to indicate what is the current voltage
* allows to power the target ON/OFF using a switch
* has status LEDs to indicate what is the current power supply voltage
* back feeding protection (to avoid damage to the USB port of the host PC)

# Mechanics
* has mounting holes
  * can be mounted inside a test fixture using M3-screws