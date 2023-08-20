# A-Delicious-Marlin-Ender-3-Pro-Firmware

Date of Latest Build .bin: 2023-08-20 - V1.4.1
Latest Marlin Version: 2.1.2.1

**ABOUT**

Constantly being built off the latest version of Marlin (Stable), this firmware includes plenty of useful functions that are turned off by default on Ender 3 boards from Creality.

I **ONLY** own a Ender 3 Pro with a 4.2.7 512k board (though should function on a 256k board as well), so it is the only .bin I will compile as it's the only one I can actually test properly; however user compiled and submitted .bins are more than welcome!

**One important note, I use a CR Touch instead of the Z Switch. I do not know if it homes correctly on just a Z Switch**
Besides that, a normal Ender 3 4.2.7 printer should work great with this firmware!

List of Features:

* Newest Marlin Build
* BL/CR Touch support
* Custom menu with custom easy to access PID settings
* Ability to silence beeps in menu
* Built in Extruder PID tests and ability to adjust on screen directly
* Built in Bed PID tests and ability to adjust on screen directly
* Input shaping and ability to adjust on screen directly
* Linear Advance and ability to adjust on screen directly
* Alphabetize SD card contents
* Long Texts Auto Scrolls
* Mesh leveling, 9 points (BILINEAR)
* Z Probe Wizard
* Thermal runaway protection
* Probe offset to align nozzle with center of bed after homing
* Power loss recovery
* And much much more!

**What Steps To Take After installing The Firmware**
* CALIBRATE YOUR PRINTER SETTINGS
  - E Steps
  - Flow Rate
  - Extruder PID
  - Bed PID
  - Linear Advance
  - Input Shaping

**TO DO:**
* Leveling/Tramming is off to the side a little, still trying to figure it out

**CHANGELOG:**

**2023-08-20 - V1.4.1**
* Changed X_MAX_POS (X_BED_SIZE + 49) to X_MAX_POS (X_BED_SIZE), again (no longer goes off the edge of the bed)
* Changed Y_MAX_POS (Y_BED_SIZE + 7) to Y_MAX_POS (Y_BED_SIZE), again (no longer goes off the edge of the bed)
* Changed BED_TRAMMING_PROBE_TOLERANCE from 0.1mm to 0.04mm (0.1mm is a huge gap when your initial layer is 0.2mm, we're talking 50% off!)
* Changed #define NOZZLE_TO_PROBE_OFFSET { -44, -7, 0 } to #define NOZZLE_TO_PROBE_OFFSET { -40, -8, 0 } (Still figuring this out)

**2023-08-19 - V1.4.0**

* Set default LIN_ADVANCE to 0.1 instead of 0.22 (Seems to be at least more accurate than the default, but please do your own LIN_ADVANCE tests! Each machine is different)
* Added back in NOZZLE_TO_PROBE_OFFSET, required setting: #define BED_TRAMMING_INSET_LFRB { 30, 30, 49, 30 }
* Changed #define NOZZLE_TO_PROBE_OFFSET { -44, -7, 0 } to #define NOZZLE_TO_PROBE_OFFSET { -49, -7, 0 }, more accurate for the CR Touch
* Changed X_MAX_POS X_BED_SIZE to X_MAX_POS (X_BED_SIZE + 49)
* Changed Y_MAX_POS Y_BED_SIZE to Y_MAX_POS (Y_BED_SIZE + 7)
* Added CUSTOM_MENU_CONFIG, in 'Configuration' there is a custom menu called 'DELICIOUS COMMANDS' that will run these commands in GCode
  - Custom PID E settings, PID E C10  TEMP 180, part cooling fan at 100%
  - Custom PID E settings, PID E C10  TEMP 190, part cooling fan at 100%
  - Custom PID E settings, PID E C10  TEMP 200, part cooling fan at 100%
  - Custom PID Bed, PID BED C10  TEMP 50
  - Custom PID Bed, PID BED C10  TEMP 60
  - Custom PID Bed, PID BED C10  TEMP 70
* Turned off PRINTJOB_TIMER_AUTOSTART
* Turned off DOUBLECLICK_FOR_Z_BABYSTEPPING (That was a little frustrating with it on)
* Removed these functions from Configuration_adv.h:
  - LED_CONTROL_MENU

**2023-08-17 - V1.3.0**

**Had to turn off NOZZLE_TO_PROBE_OFFSET for now as with it, it refused to compile, will have to investigate**

* Custom 'DELICIOUS MARLIN' bootscreen!!! (I gotta rep myself!)
* Added LCD_BED_TRAMMING (Assisted manual leveling) as a menu item, as well as BED_TRAMMING_INCLUDE_CENTER to return the nozzle to the center once done tramming
  - Set BED_TRAMMING_HEIGHT (Z height) to 0.2 mm, the standard and recommended Ender 3 print height
  - Added BED_TRAMMING_VERIFY_RAISED for the probe to verify after tramming
  - Added BED_TRAMMING_USE_PROBE
* Added HOST_ACTION_COMMANDS (So Octoprint and other software knows when the printer has paused/stopped when using the printer controls)
* Added POWER_LOSS_RECOVERY
* Added LIN_ADVANCE
* Added ASSISTED_TRAMMING
* Added ASSISTED_TRAMMING_WIZARD
* Added Z_MIN_PROBE_REPEATABILITY_TEST
* TRAMMING_SCREW_THREAD set to 40 instead of default 30, so should be set to M4
*  Cleaned up more of Configuration_adv.h, removed functions listed:
  - THERMAL_PROTECTION_COOLER > Laser related
  - THERMAL_PROTECTION_COOLER_PERIOD > Laser related
  - THERMAL_PROTECTION_COOLER_HYSTERESIS > Laser related
  - WATCH_COOLER_TEMP_PERIOD > Laser related
  - WATCH_COOLER_TEMP_INCREASE > Laser related
  - THERMAL_PROTECTION_CHAMBER
  - THERMAL_PROTECTION_CHAMBER_PERIOD
  - THERMAL_PROTECTION_CHAMBER_HYSTERESIS
  - WATCH_CHAMBER_TEMP_PERIOD
  - WATCH_CHAMBER_TEMP_INCREASE
  - CNC_COORDINATE_SYSTEMS
  - WIFISUPPORT
  - ESP3D_WIFISUPPORT
  - Entire CASE_LIGHT_ENABLE section
  - Entire DUAL_X_CARRIAGE
  - Entire SPINDLE_FEATURE section
  - Entire LASER_FEATURE section
  - Entire multi-material section
  - Z_PROBE_ALLEN_KEY

**2023-08-15 - V1.2.0**

* Changed default E/Steps to 97 from 93 (I've observed that most Ender 3 steppers are set way too low by default and generally end up somewhere between 96-98). I would still **HIGHLY** recommend for everyone to calibrate their E/Steps correctly, just changing this default gives an easier and smoother out of the box experience.
* PREHEAT BED LEVEL was miss configured, should be correctly set now
* Enabled DISTINCT_E_FACTORS, should now be able to configure X, Y, Z and E Steps directly on the printer

**2023-08-15 - V1.1.0**

* Enabled auto creation of Config.ini for people that prefer that, will be included in release packages going forward!
* Default PLA heating settings:
  - Hot End: 180C
  - Bed: 50C
* Default ABS heating settings:
  - Hot End: 240C
  - Bed: 70C
* Added Default Bed Level heating settings (in times when you want to tinker with something but have the hot end and bed set to the right temp so you can instantly start leveling after):
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
