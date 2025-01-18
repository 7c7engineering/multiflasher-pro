# Interface to the PC:
* ~~FT230X (€2.05)~~ → doesn’t have DTR output
* ~~FT231XS-R~~ → single UART
  * good driver support
  * internal 3V3 LDO, internal crystal, minimal external components needed.
  * using as UPDI programming software for Atmel AVR
  * single UART
* CP2105
  * 2 UARTs
  * DTR output
  * LCSC C109102 (€1.83)
  * USB-PD sink configuration would have to be done over strapping pins, not over I²C (because there's no I²C master).  The [CYPD3177-24LQXQ](https://jlcpcb.com/partdetail/3345638-CYPD317724LQXQ/C2959321) could be used. 
  * option for 3V3 self powered operation
  * no support for SWD programming
* RP2040
  * 2 UARTs
  * DTR output
  * LCSC C109102 (€1.83)
  * I²C for configuration of USB-PD sink
  * requires programming

# Target power
* [Limiting In-rush Current in MOSFET Power Switches](http://www.mosaic-industries.com/embedded-systems/microcontroller-projects/electronic-circuits/push-button-switch-turn-on/inrush-current-limited-mosfet), might use LM73100 instead.
* LM73100 provides power to the target (in-rush current limited and back powered protection)
* The target power voltage value is fixed, as it will be almost in all cases be used to power an LDO on the target.  Anyway, a target should be able to cope with 5V being provided on the target port, because that's also a valid voltage for the previous ITL211205.  A wrong switch setting there would also kill your target.

# ESP Programming connection
* [ESP-Prog schematic](https://docs.espressif.com/projects/espressif-esp-dev-kits/en/latest/_static/esp-prog/schematics/SCH_ESP32-PROG_V2.1_20190709.pdf)

# UPDI programming connection
* [Atmel megaAVR](https://docs.platformio.org/en/stable/platforms/atmelmegaavr.html)

# RP2040 Hardware flow control : DTR
* [rp2040-pio-uart-bridge](https://github.com/GrechTech/rp2040-pio-uart-bridge/tree/main) : reacts on cdc_line_state call back
* RP2040 datasheet : UARTCR register, DTR and RTS bits : will only work (if it works) for the UART0 peripheral, not for the PIO UART

# Bus transceiver (dual voltage)
* Secondary side voltage, 3.3V or 5V, is set by the programmer.
* Digikey : Buffers, Drivers, Receivers, Transceivers : 4, 8, 10 bits
* Digikey : Translators, Level Shifters : single bit
  * SN74LVC1T45DCKR : JLCPCB C9382
  * SN74LVC1T45QDCKRQ1
  * SN74LVC1T45DCKT
* Single bit : SN74AXC1T45QDCKRQ1
* 4bit (direction selection for each bit separately), but not 5V tolerant : SN74AVC4T774PWR

# USB-PD sink
* [CYPD3177-24LQXQ](https://jlcpcb.com/partdetail/3345638-CYPD317724LQXQ/C2959321) : no programming needed.  Voltage can be set by resistors.  I²C interface for monitoring.
* STUSB4500 : C2678061 : more popular on JLCPCB, I²C interface for monitoring
  * [Hackaday](https://hackaday.com/2021/04/21/easy-usb%E2%80%91c-power-for-all-your-devices/)
* FUSB302 : LCSC C442699, I²C interface for monitoring
  * [Hackaday](https://hackaday.io/project/176680-pd-micro-usb-c-pd30-pps-trigger)

# Power meter
Two pin compatible options:
* INA226: 36Vmax, 10µA input leakage on analog inputs 
* INA238AIDGSR : 85Vmax, 2.5nA input leakage on analog inputs

# Add-on port
* Bottom entry header female header on the programmer board, so that single side PCBs can be used for both the programmer and the add-on board.

# LEDs
* RX and TX toggle
* DUT Power
* Programmer power

# O-LED display
* [0.91" OLED Display 128x32 pixels Blue - I2C](https://www.tinytronics.nl/en/displays/oled/0.91-inch-oled-display-128*32-pixels-blue-i2c)