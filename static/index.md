# About

This is an ESPHome firmware for the Localbytes Smart plug (V2), which normally come pre-loaded with tasmota. <a href="https://www.mylocalbytes.com/products/smart-plug-pm?variant=41600621510847">You can buy these smart plugs here</a>.

# Installation

To flash the ESPHome firmware onto a plug running tasmota, first flash the <a href="minimal/minimal.bin">minimal</a> firmware using the tasmota web interface (as the full firmware is too big to fit in the free space left by tasmota). Then, connect to the hotspot the device creates and flash the latest full <a href="localbytes-plug-pm-v2/localbytes-plug-pm-v2.bin">localbytes-plug-pm-v2</a> firmware.

<!-- <esp-web-install-button manifest="./manifest.json"></esp-web-install-button> <script type="module" src="https://unpkg.com/esp-web-tools@5.2.0/dist/web/install-button.js?module"></script> -->

# Calibration

Once you have flashed the new firmware onto your smart plug and connected it to home assistant, you may wish to calibrate your plug to improve it's accuracy. To calibrate your plug, you need another "known-good" smart plug or a calibration device.

Plug your new smart plug into the know good smart plug, then plug a kettle, toaster, or other high-power device into it. From home assistant, go to `Developer Tools` > `Services`. Use the services `calibrate_current`, `calibrate_power`, and `calibrate_voltage` to report the real readings as given from the "known-good" device. (Don't forget to turn on the kettle/toaster before starting to take readings).