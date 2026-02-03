| :warning: WARNING                        |
|:-----------------------------------------|
| This codebase is valid for Rev2 only     |

# Thermique revision 2

Project Thermique is aimed to be an all-in-one solution to detect COVID-19 infected individuals entering an office or institution.
It makes use of state-of-the-art thermal imaging and a fullstack application to automatically extract a person's temperatature from the
region of interest, before logging them and alerting admins in case of a possible COVID infection. Being a contactless kiosk placed at an
entryway, it also serves as an attendance tracker.

The overall system workflow is as follows:

<img width="720" alt="rev2diagram" src="https://github.com/user-attachments/assets/7a667951-e28e-44b1-85d9-fa1b5239eaee" />

> Note that this system is outdated, and the later revision reduces the number of components and changes a few things

## Usage

0. This is for raspberrypi_video only. raspberrypi_qt was not used in final production.
1. Enable I2C and SPI
2. Overclock the pi to a minimum of 1100MHz for Pi3. If using Pi4, don't do this.
3. Write the following into /boot/config.txt: [for Pi3 only, skip if using Pi4]

```
over_voltage=4  
sdram_freq=400  
core_freq=400  
gpu_freq=400  
```
4. In /boot/config.txt, make sure hdmi hotplug is set to 1.
5. Keep the module connected to pi using shortest possible wires.
6. DO NOT CONNECT BACKSIDE PINS TO Vcc and GND
7. Use the following to install necessary Qt libraries for compilation:

```
sudo apt-get install qt4-dev-tools
```

8. Finally, compile using:

```
qmake && make
```

8. To clean, use the following:

```
make sdkclean && make distclean
```

9. Since Lepton Module ver3.5 is being used, run the executable with:

```
./raspberrypi_video -tl 3
```

10. Press 'r' on keyboard for FFC reset.
