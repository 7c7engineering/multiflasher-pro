# multiflasher-pro
Programmer for ESP32, AVR-UPDI &amp; UART-monitor

To get around the limitations of the current ITL211205 multiflasher, an upgrade is proposed which:
* is easy and quick to solder (no QFN or pitch >0.5mm)
* is reliable
* protected against latch-up (target is powered through other means, while programmer is unpowered) : open-drain connections
* doesn’t require programming the programmer
* has custom serial nr.
* allows for easy power cycling of the target (without need for disconnecting the target) : using a switch
* allows for easy reset of the target : using a switch

# Target:
* ESP32 : programming & monitoring
* AVR : UPDI programming
* Raspberry Pi UART : monitoring (pin functions clearly indicated)
* Expansion port for add-on : RS485, RS422, galvanically isolated UART

# Connectivity:
## Target
* compatible to the 7c7-SKEDD interface
* allow for connection of dupont cables

## Host PC
* USB-C

# Target power
* allows to power the target ON/OFF without using a switch
* has a status LED to indicate that the target is being powered
* allows for remote powering (programmer doesn’t power the target) using a USB-connector
* back feeding protection (to avoid damage to the USB port of the host PC)

# Mechanics

* has mounting holes
  * can be mounted inside a test fixture using M3-screws
  * allows for mounting add-on boards : RS485, isolated UART 