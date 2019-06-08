# Connector Pinout

<mark>insert connector image/pins here</mark>

# Pin Descriptions

Each pin has a *Type ID*, which can be used to look up in the following tables what the pin is for, and what functions it can perform.

| Pin Number | Name     | Type ID | Default function                               |
| ----------:|:-------- | ------- |:---------------------------------------------- |
| 1  | **12V**          | 12V     | 12V supply                                     |
| 2  | **GND**          | pgnd    | Power GND                                      |
| 3  | **Lowside 2**    | ls      | Idle solenoid                                  |
| 4  | **ETB+**         | etb     | ETB+                                           |
| 5  | **12V**          | 12V     | 12V supply                                     |
| 6  | **GND**          | pgnd    | Power GND                                      |
| 7  | **Lowside 1**    | ls      | VVT                                            |
| 8  | **ETB-**         | etb     | ETB-                                           |
| 9  | **Ignition 1**   | ign     | Ignition 1                                     |
| 10 | **Ignition 2**   | ign     | Ignition 2                                     |
| 11 | **Ignition 3**   | ign     | Ignition 3                                     |
| 12 | **Ignition 4**   | ign     | Ignition 4                                     |
| 13 | **GP out 6**     | gp1     | Alternator                                     |
| 14 | **GP out 5**     | gp1     |                                                |
| 15 | **USB D-**       | usb     | USB                                            |
| 16 | **USB D+**       | usb     | USB                                            |
| 17 | **GND**          | sgnd    | Signal GND                                     |
| 18 | **AN Temp 1**    | at      | CLT sensor                                     |
| 19 | **AN Volt 4**    | av      |                                                |
| 20 | **AN Volt 5**    | av      |                                                |
| 21 | **GND**          | sgnd    | Signal GND                                     |
| 22 | **AN Temp 4**    | at      |                                                |
| 23 | **AN Temp 2**    | at      | IAT sensor                                     |
| 24 | **AN Temp 3**    | at      | External wideband O2 sensor                    |
| 25 | **Cam (hall)**   | hall    |                                                |
| 26 | **AN Volt 2**    | av      | TPS sensor                                     |
| 27 | **AN Volt 1**    | av      | MAP sensor                                     |
| 28 | **AN Volt 10**   | av      |                                                |
| 29 | **Main relay**   | mr      | Main relay                                     |
| 30 | **AN Volt 7**    | av      |                                                |
| 31 | **AN Volt 3**    | av      |                                                |
| 32 | **AN Volt 6**    | av      |                                                |
| 33 | **GP out 3**     | gp2     |                                                |
| 34 | **GP out 2**     | gp2     | Fan relay                                      |
| 35 | **GP out 1**     | gp2     | Fuel pump relay                                |
| 36 | **AN Volt 8**    | av      |                                                |
| 37 | **Injector 1**   | inj     | Injector 1                                     |
| 38 | **Injector 2**   | inj     | Injector 2                                     |
| 39 | **5V Sensor 2**  | 5v      | MAP sensor supply                              |
| 40 | **AN Volt 9**    | av      |                                                |
| 41 | **Injector 3**   | inj     | Injector 3                                     |
| 42 | **Injector 4**   | inj     | Injector 4                                     |
| 43 | **GP out 4**     | gp2     |                                                |
| 44 | **5V Sensor 1**  | 5v      | TPS sensor supply                              |
| 45 | **VR+/Hall**     | vr/hall | Crank VR+/hall                                 |
| 46 | **VR-**          | vr      | Crank VR- (do not connect if hall)             |
| 47 | **CAN low**      | can     | CAN bus                                        |
| 48 | **CAN high**     | can     | CAN bus                                        |

# Pin Types

These tables provide technical information about the different types of pin found on microrusEfi.

## Power

| ID | Type | Notes & Limits |
|----|-------------| ---- |
| 12V  | Power supply        | 9-22V operating, 5A fuse recommended           |
| pgnd | Power ground        | Solidly ground directly to chassis or engine block. |
| sgnd | Signal ground       | Sensor ground.  ***Do not ground to engine!***
| 5v   | 5V sensor supply    | 5V supply for external sensors.  200mA maximum per pin.

## Input

| ID   | Type                | Notes & Limits                                                                       | Possible functions |
|------|---------------------| ------------------------------------------------------------------------------------ | --- |
| at   | Analog temperature  | Analog temperature (thermistor) input.  <mark>2.7k/TBD</mark> pullup resistor to 5v  | Thermistor temperature sensor, fuel level sender (variable resistor type) |
| av   | Analog voltage      | Analog voltage input.  500k pull down to GND                                         | Analog voltage sensor (MAP, TPS, acc pedal, oil pressure, etc)
| vr   | Variable reluctor   | VR crank input                                                                       | VR sensors including crank, cam, vehicle speed
| hall | Hall cam/crank      | <mark>TBD pull up to 5v</mark> hall sensor for cam/crank                             | Hall sensors including crank, cam, vehicle speed

## Output

| ID | Type | Notes & Limits | Possible functions |
|----|-------------| ---- | --- |
| inj  | Injector output     | Low side, 2.2A maximum<br/>**Only saturated (high impedance) injectors are supported.** | Injector, general purpose low side |
| ign  | Ignition output     | 5V push-pull, 250mA maximum   | Ignition coil, general purpose 5V push-pull
| ls   | High power low side | General purpose low side output, 4.5A maximum | General purpose low side, injector
| gp1 | General purpose push-pull | General purpose push-pull output, 5V/12V (internally selectable) 250mA maximum | General purpose 5V/12V push-pull, ignition coil
| gp2 | General purpose push-pull | General purpose push-pull output, 12V 500mA maximum                            | General purpose 12V push-pull
| mr   | Main relay          | Dedicated main relay output.  Low side turned on with power, 800mA maximum. | Main relay
| etb  | Electronic throttle | Dedicated electronic throttle outputs.  Connect a brushed motor<br/>throttle body directly to these two pins.

## Communication

| ID | Type | Notes & Limits |
|----|-------------| ---- |
| usb | USB     | USB tuning interface
| can | CAN bus | CAN communication