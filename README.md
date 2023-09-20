# About

This is an ESPHome firmware for the Localbytes smart plug, which is sold pre-loaded with tasmota. This firmware supports the original 10A plug and the upgraded 13A plug. <a href="https://www.mylocalbytes.com/products/smart-plug-pm?variant=41600621510847">You can buy these smart plugs here</a>.

## Original Credit

Massive thanks to @JamesSwift who made the original here - JamesSwift/localbytes-plug-pm  
Without whom, esphome would still be an unsupported platform

# Features

- Turn the switch on and off via home assistant or web interface
- Disabled the LED by pressing and holding the button for 3 seconds (or toggle the option in home assistant/web interface)
- Disable the physical button (i.e. child lock) by pressing and holding the button for 10 seconds (or toggle the option in home assistant/web interface)
- Power monitoring via home assistant or web interface
- Calibrate the power monitoring using a GUI via home assistant
- See and alter the calibration data via home assistant
- ESPHome dashboard import

<img src="https://user-images.githubusercontent.com/2080205/169600703-0ddfab3f-5309-4dd7-bd22-87a6d4d0ecb1.png" width="45%" /> 
<img src="https://user-images.githubusercontent.com/2080205/168430744-598f9d21-c1ce-4fce-9076-8fca26c62be8.png" width="45%" />
<img src="https://user-images.githubusercontent.com/2080205/168430637-ae9f14c6-57a8-4f3f-8a85-1f35966b43bd.png" width="45%" />




# Installation

To flash the ESPHome firmware over tasmota, first flash the <a href="https://github.com/LocalBytes/esphome-localbytes-plug/releases/latest/download/minimal.bin">ESPHome minimal</a> firmware using the tasmota web interface (as the full firmware is too big to fit in the free space left by tasmota). Then connect to the wifi hotspot that is created and enter your network's wifi details. 

At this point you can use the "dashboard import" feature of esphome to take ownership of the device. The next time you hit install/update via the dashboard, the full firmware will be uploaded to the plug. 

Alternatively, if you don't want to import the plug to your ESPHome dashboard, connect to the hotpsot the device creates and use the web UI to flash the <a href="https://github.com/LocalBytes/esphome-localbytes-plug/releases/latest/download/localbytes-plug-pm.bin">full firmware</a> from the latest release.

# Firmware File Too Big

A minimal firmware is provided as an intermiediary step, as there isn't enough space on the factory smart plugs to store the new full firmware while it is being flashed. Some users have reported that even this minimal firmware is still too large. If this is the case, you can try flashing the <a href="http://ota.tasmota.com/tasmota/release/tasmota-minimal.bin.gz">Tasmota minimal</a> firmware instead. Then flash the <a href="https://github.com/LocalBytes/esphome-localbytes-plug/releases/latest/download/localbytes-plug-pm.bin">full firmware</a> afterwards. 

# Calibration

Once you have flashed the new firmware onto your smart plug and connected it to home assistant, you may wish to calibrate your plug to improve it's accuracy. To calibrate your plug, you need another "known-good" smart plug or a calibration device.

Plug your new smart plug into the known-good smart plug, then plug a kettle, toaster, or other high-power appliance into it. From home assistant, go to `Developer Tools` > `Services`. Use the services `calibrate_current`, `calibrate_power`, and `calibrate_voltage` to report the real readings as given from the "known-good" device. (Don't forget to turn on the kettle/toaster and leave it to stabilize it's power usage for a moment before starting to copy the readings).
