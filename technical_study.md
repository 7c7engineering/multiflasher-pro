# Interface to the PC:
* FT230X (€2.05) → doesn’t have DTR output
* FT231XS-R
  * good driver support
  * internal 3V3 LDO, internal crystal, minimal external components needed.
  * using as UPDI programming software for Atmel AVR
  * single UART
* CP2105
  * 2 UARTs
  * DTR output
  * LCSC C109102 (€1.83)

# Target power
* [Limiting In-rush Current in MOSFET Power Switches](http://www.mosaic-industries.com/embedded-systems/microcontroller-projects/electronic-circuits/push-button-switch-turn-on/inrush-current-limited-mosfet)
* An extra diode is needed to prevent the switch from being opened by the target sourcing current back into the programmer.
* The target power voltage value is fixed, as it will be almost in all cases be used to power an LDO on the target.  Anyway, a target should be able to cope with 5V being provided on the target port, because that's also a valid voltage for the previous ITL211205.  A wrong switch setting there would also kill your target.

# ESP Programming connection
* [ESP-Prog schematic](https://docs.espressif.com/projects/espressif-esp-dev-kits/en/latest/_static/esp-prog/schematics/SCH_ESP32-PROG_V2.1_20190709.pdf)

# UPDI programming connection
* [Atmel megaAVR](https://docs.platformio.org/en/stable/platforms/atmelmegaavr.html)

# RP2040 Hardware flow control : DTR
* [rp2040-pio-uart-bridge ](https://github.com/GrechTech/rp2040-pio-uart-bridge/tree/main) : reacts on cdc_line_state call back
* RP2040 datasheet : UARTCR register, DTR and RTS bits : will only work (if it works) for the UART0 peripheral, not for the PIO UART