# hubitat-rheem
Rheem EcoNet Water Heater Integration for Hubitat. This allows you to retrieve data from the water heater as well as control it using a cloud API.

This was forked from https://github.com/dcmeglio to continue to make improvements.  Thank you to dcmeglio for all your hard work.
 
## Devices
You must install the device driver for the water heater for this to work.
* Rheem EcoNet Water Heater

### Thermostat Modes
A Rheem water heater supports different modes than those available through Hubitat. This driver matches the device's modes to those supported by Hubitat. Additionally, the modes vary by the type of water heater you have (hybrid, electric, gas, etc.). There is also a custom setWaterHeaterMode command which lets you set the mdoes directly with the exception that Normal automatically translates between electric and gas depending on the type of heater you have.

|           Device         |      Hubitat (Thermostat)      |       Hubitat (Water Heater)      |
|:------------------------:|:------------------------------:|:---------------------------------:|
| Off                      | off                            | Off                               |
| Heat Pump                | heat                           | Heat Pump                         |
| Electric                 | heat                           | Normal                            |
| Gas                      | heat                           | Normal                            |
| High Demand, Performance | emergency heat                 | High Demand                       |
| Energy Saver             | auto                           | Energy Saver                      |

## Apps
The Rheem EcoNet Integration app is what actually communicates with the Rheem EcoNet system via HTTP.
The Driver communicates with Rheem EcoNet via MQTT.

### Configuration
To connect to the API you will need to specify your Rheem EcoNet username and password. You will then see the list of available water heaters for your account. Choose all that you wish to integrate with Hubitat. From there you can control the mode and heating setpoint as well as retrieve various data points from the devies.



## Revision History
* 2022.11.24 - v1.0.3 - Accepted pr from @jrjohnson to fix driver namespace
* 2022.11.00 - v1.0.2 - Fixed going into vacation mode (don't go into away mode prior to going into vacation)
* 2022.11.20 - v1.0.1 - Fixed null pointer exception in translateThermostatMode (PR on original implementation from ljbotero).
* 2022.11.19 - v1.0.0 - Forked by klinquist.  Added functions to put the location into home mode prior to taking it out of vacation mode.
* 2020.04.15 - Added calls to supportedThermostatModes and supportedThermostatFanModes. Thanks to Brian Spranger for the suggestion
* 2020.04.26 - Added setWaterHeaterMode command and waterHeaterMode attribute to set the water heater mode directly instead of the thermostat mode.