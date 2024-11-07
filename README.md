# About

This is an ESPHome firmware for the Localbytes smart plug, which was originally sold pre-loaded with tasmota. This firmware supports the original 10A plug and the upgraded 13A plug. <a href="https://www.mylocalbytes.com/products/smart-plug-pm?variant=41600621510847">You can buy these smart plugs here</a>.

## Manual Addition

You can use the following YAML to add the device to your ESPHome setup.  
Please note this does not enable [API Encryption](https://esphome.io/components/api#configuration-variables) or [OTA Password](https://esphome.io/components/ota.html#configuration-variables)

```yaml
substitutions:
  name: localbytes-plug-pm-<NAME>
  friendly_name: Localbytes Plug PM <NAME>

packages:
  localbytes.plug-pm: github://JamesSwift/esphome-localbytes-plug/localbytes-plug-pm.yaml@main

esphome:
  name: ${name}
  name_add_mac_suffix: false
  friendly_name: ${friendly_name}

wifi:
  ssid: !secret wifi_ssid
  password: !secret wifi_password
```

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


# Firmware File Too Big

As there isn't enough space left on the factory smart plugs to store new firmware while it is being flashed. You can try flashing the <a href="http://ota.tasmota.com/tasmota/release/tasmota-minimal.bin.gz">Tasmota minimal</a> firmware first, before then building and flashing this project. 

# Calibration

Once you have built and flashed the new firmware onto your smart plug and connected it to home assistant, you may wish to calibrate your plug to improve it's accuracy. To calibrate your plug, you need another "known-good" smart plug or a calibration device.

Plug your new smart plug into the known-good smart plug, then plug a kettle, toaster, or other high-power appliance into it. From home assistant, go to `Developer Tools` > `Services`. Use the services `calibrate_current`, `calibrate_power`, and `calibrate_voltage` to report the real readings as given from the "known-good" device. (Don't forget to turn on the kettle/toaster and leave it to stabilize it's power usage for a moment before starting to copy the readings).
