# A-Delicious-Marlin-Ender-3-Pro-Firmware

Date of Latest Build .bin: 2023-08-15 - V1.1.0
Latest Marlin Version: 2.1.2.1

**ABOUT**

Constantly being built off the latest version of Marlin (Stable), this firmware includes plenty of useful functions that are turned off by default on Ender 3 boards from Creality.

I **ONLY** own a Ender 3 Pro with a 4.2.7 512k board (though should function on a 256k board as well), so it is the only .bin I will compile as it's the only one I can actually test properly; however user compiled and submitted .bins are more than welcome!

**One important note, I use a CR Touch instead of the Z Switch. I do not know if it homes correctly on just a Z Switch**
Besides that, a normal Ender 3 4.2.7 printer should work great with this firmware!

List of Features:

* Newest Marlin Build
* BL/CR Touch support
* Ability to silence beeps in menu
* Built in Extruder PID tests and ability to adjust on screen directly
* Built in Bed PID tests and ability to adjust on screen directly
* Input shaping and ability to adjust on screen directly
* Alphabetize SD card contents
* Long Texts Auto Scrolls
* Mesh leveling, 9 points (BILINEAR)
* Z Probe Wizard
* Thermal runaway protection
* Probe offset to align nozzle with center of bed after homing
* Additional BED LEVEL preheat setting
* Lower min temp for extrusion, 170C

**CHANGELOG:**

**2023-08-15 - V1.1.0**

* Enabled auto creation of Config.ini for people that prefer that, will be included in release packages going forward!
* Default PLA heating settings:
  - Hot End: 180C
  - Bed: 50C
* Default ABS heating settings:
  - Hot End: 240C
  - Bed: 70C
* Added Default Bed Level heating settings (in times when you want to tinker with something but have the hot end and bed set to the right temp so you can instantly start printing after):
  - Hot End: 150C
  - Bed: 50C
* Cleaned up Configuration.h and Configuration_adv.h
  - Removed unneeded comments to simplify Configuration.h and Configuration_adv.h files
  - Removed unneeded functions - Removed functions named below (I just don't see the point in keeping these in if they'll never be turned on. Does it affect the performance, no. Does it make the code feel cleaner and my insides fuzzy, yes!):
    - BLUETOOTH
    - SINGLENOZZLE
    - SWITCHING_EXTRUDER
    - SWITCHING_NOZZLE
    - PARKING_EXTRUDER
    - MAGNETIC_PARKING_EXTRUDER
    - SWITCHING_TOOLHEAD
    - MAGNETIC_SWITCHING_TOOLHEAD
    - ELECTROMAGNETIC_SWITCHING_TOOLHEAD
    - MIXING_EXTRUDER
    - MMU_MODEL
    - PRUSA_MMU2
    - TEMP_SENSOR_CHAMBER
    - TEMP_SENSOR_REDUNDANT
    - CHAMBER_MINTEMP
    - CHAMBER_MAXTEMP
    - entire PID > 'Chamber Temperature Control' section
    - PIDTEMPCHAMBER
    - CHAMBER_LIMIT_SWITCHING
    - MAX_CHAMBER_POWER
    - POLARGRAPH
    - DELTA
    - MORGAN_SCARA
    - MP_SCARA
    - AXEL_TPARA
    - ARTICULATED_ROBOT_ARM
    - PASSWORD_FEATURE
    - BARICUDA
    - RGB_LED
    - RGBW_LED
    - BLINKM
    - PCA9632
    - PCA9533
    - NEOPIXEL_LED

**2023-08-14 - V1.0.0 - Initial build**

First build (of hopefully many), plenty of features included in this build!

* Newest Marlin Build (2.1.2.1 at time of Build)
* BL/CR Touch support
* Ability to silence beeps in menu
* Built in Extruder PID tests and ability to adjust on screen directly
* Built in Bed PID tests and ability to adjust on screen directly
* Input shaping and ability to adjust on screen directly
* Alphabetize SD card contents
* Long Texts Auto Scrolls
* Mesh leveling, 9 points (BILINEAR)
* Z Probe Wizard
* Thermal runaway protection
* Probe offset to align nozzle with center of bed after homing
* Lower min temp for extrusion, 170C
