 # multiflasher-pro
Programmer for ESP32, AVR-UPDI &amp; UART-monitor

To get around the limitations of the current ITL211205 multiflasher, an upgrade is proposed which:
* is easy and quick to solder :
  * (no QFN or pitch >0.5mm)
  * (no 0402 or smaller)
* is reliable
* is protected against short-circuits on the target
* protected against latch-up (target is powered through other means, while programmer is unpowered) : open-drain connections
* doesn’t require a programmer to program the programmer
* allows for easy power cycling of the target (without need for disconnecting the target)
* allows for easy reset of the target : using a switch
* has dual UART( 1 for monitoring, 1 for programming)

# Nice to have
* has custom serial nr.

# Use cases:
* ESP32 : programming & monitoring (RTS/DTR needed for programming)
* AVR : UPDI programming
* Raspberry Pi UART : monitoring (pin functions clearly indicated)
* Expansion port for add-on : RS485, RS422, galvanically isolated UART

# Connectivity:
## Programming port
* compatible to the 7c7-SKEDD interface
* allow for connection of dupont cables
* RXD, TXD, RTS, DTR
* Add-on:
  * USB-DAM (Debug Accessory Mode)

## Logging port
* Full UART (RXD, TXD, RTS, CTS, DTR, DSR, DCD, RI)
* allow for connection of dupont cables
* Add-on
  * RS485
  * RS422
  * galvanically isolated UART

## IO-Voltage
* 3.3V
* 5V

## Host PC
* USB-C

# Target power
* USB-PD sink (5V, 9V, 12V, 15V, 20V)
* allows to power the target ON/OFF using a switch
* has status LEDs to indicate what is the current power supply voltage
* back feeding protection (to avoid damage to the USB port of the host PC)

# Mechanics
* has mounting holes
  * can be mounted inside a test fixture using M3-screws