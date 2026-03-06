# Future Electronics/Nordic Semiconductor Workshop: <br>_Kickstart Your Zephyr-RTOS Embedded Journey_

## Workshop Dates/Locations
>  21.May 2026, Stuttgart <br>
>  24.March 2026, Dortmund <br>

## Code Snippets for Hands-On Sessions
In this repository, you will find the files you need for the hands-on session. 

1) Getting started: IDE overview and Embedded Systems "hello world" (Blinky project)
     - Zephyr's __blinky__ sample => see slides
     - [DeviceTree: Changing LED port pin](docs/HandsOn1-2_deviceTree.md)
     - [KCONFIG: Adding Zephyr Logging](docs/HandsOn1-3_kconfig.md)
     - optional: [Adding a custom KCONFIG](docs/HandsOn1-4_customKconfig.md)

2) Bluetooth LE
     - [Adding Bluetooth Beacon functionality](docs/HandsOn2.1_beacon.md)
     - Nordic's _Bluetooth LE LED and Button Service_ (LBS, see <code>nrf/sample/bluetooth/peripheral_lbs</code> sample) => see slides
     
3) Nordic's Fuel Gauge Solution
     - optional: [Add a simulated sensor](docs/HandsOn3-1_simulatedSensor.md)
     - [Adding nPM2100 Fuel Gauge](docs/HandsOn3-2_fuelGauge.md)
     - [Send primary battery state of charge via Bluetooth to a smartphone](docs/HandsOn3-3_BAS.md)


## Workshop Slides
- [Introduction and _nRF Connect SDK_ Overview](presentations/1_Intro_and_nRF-Connect-SDK.pdf) 
- [1. Hands-on: IDE Overview & Blinky Application, DeviceTree and KCONFIG](presentations/2_Hands-on_Blinky.pdf)
- [2. Hands-on: Bluetooth LE -> Beacon and LED & Button Service (LBS)](presentations/3_Hands-on_Bluetooth.pdf)
- [3. Hands-on: Nordic's Fuel Gauge Solution](presentations/4_Hands-on_FuelGauge_Sensor.pdf)
- [Wrap-up](presentations/5_Nordic_Wrap-up.pdf)
