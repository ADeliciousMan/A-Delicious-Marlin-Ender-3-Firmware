# A Delicious Marlin Ender 3/Pro Firmware

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/I2I8PI401)

#### Date of Latest Build: 2023-09-24 - V1.11.0
#### Latest Marlin Version: 2.1.2.1

![LOGO](https://raw.githubusercontent.com/ADeliciousMan/A-Delicious-Marlin-Ender-3-Firmware/master/images/bootscreen.png?raw=true)

## ABOUT

Constantly being built off the latest version of Marlin (Stable), this firmware includes plenty of useful functions that are turned off by default on Ender 3 boards from Creality, with tweaks for a better out of the box printing experience.

###### Note
I **ONLY** own a Ender 3 Pro with a 4.2.7 512k board so it's the only one I can actually test properly; however more .bins are included as well as user compiled and submitted .bins are more than welcome!

## List of Features:

* Newest Marlin Build
* Faster prints
* BL/CR Touch support
* Marlins PID Tuning
* Custom menu with custom easy to access PID settings for Extruder and Bed
  - Extruder PID Presets, 10 cycles, 180C, 190C, 200C, 260C
  - Bed PID Presets, 10 cycles, 50C, 60C, 70C, 90C
  - These do not reapply a default PID setting, but instead actual run a full PID tune so it is unique to your machine (extruder, heading block, nozzle, cooling fan, specific temperature)
* More accurate defaults for easier instant setup (I highly recommend you to do your own calibrations to get the most out of your printer, this firmware just helps to get you started faster and easier with more tools to calibrate easily)
* Mesh leveling, 9 points (BILINEAR)
* Input shaping and ability to adjust on screen directly
* Linear Advance (for supported boards)
* Z Probe Wizard
* Tramming Wizard
* Filament Change during print
* Thermal runaway protection
* Alphabetize SD card contents
* Ability to silence beeps in menu
* Long Texts Auto Scrolls
* Power loss recovery (This feature is enabled but turned off in the menu)
* Probe offset to align nozzle with center of bed after homing (instead of probe)
* Lowered min temp for extrusion, 170C
* Host actions (EX: You use Octoprint but stop the print on the printer directly, it will inform Octoprint of this)
* Babystep for Z-Probe
* Ability to mute Beeps
* Nozzle park
* Pause feature for unloading and loading filament
* Option to turn on Autostart (executes gcode with file name auto0.g.gcode on startup)
* And much, much more!

## What Steps To Take After installing This Firmware
* Reset/Initialize your EEPROM on your printer, this is to ensure that previous settings are not messing with the new firmware. Yes it does Happen, happened to me plenty of times in testing
  - It would be a good idea to write down settings that you have already calibrated for, like E/Steps so you don't have to do it again
* **CALIBRATE YOUR PRINTER SETTINGS**
  - [E Steps](https://letsprint3d.net/how-to-calibrate-the-extruder-steps-ender-3-5-cr-10/#EEPROM_Settings)
  - [Flow Rate](https://3dprintbeginner.com/flow-rate-calibration/)
  - Extruder and BED PID (3 options)
    - Go to Configuration > DELICIOUS COMMANDS > Select PID setting you want to use
    - Go to Configuration > Advanced Settings > Temperature and use the Marlin tools
    - Use GCode by following this [link](https://marlinfw.org/docs/gcode/M303.html)
  * Either manually level your bed using a piece of paper or shim, or use the tramming settings in Motion > Tramming Wizard
  * Z Probe Wizard, Motion > Z Probe Wizard
  * Level Bed for a mesh level, Motion > Level Bed
  - Linear Advance **4.2.2 and 4.2.2 BAORD DOES NOT SUPPORT LINEAR ADVANCE**
    * [Read this](https://marlinfw.org/docs/features/lin_advance.html)
    * [Use this tool](https://marlinfw.org/tools/lin_advance/k-factor.html)
  - [Input Shaping](https://marlinfw.org/docs/gcode/M593.html)
    - **Disclaimer, I am not sure if the 4.2.2 or 4.2.7 board properly supports Input Shaping, I was not able to see a change in results on my end**
    - [TH3D Guide](https://support.th3dstudio.com/helpcenter/unified-marlin-input-shaping-tuning-guide/)
    - [TH3D Calculator](https://www.th3dstudio.com/marlin-input-shaping-calculator/)
  * [General Overall Calibration Guides from 'Teaching Tech'](https://teachingtechyt.github.io/calibration.html)
  * Horizontal Expansion
    - [Model](https://www.thingiverse.com/thing:4418599)
    - [Explaination](https://www.youtube.com/watch?v=UUelLZvDelU)
* **Calibration tests**
  * [Stringing Test](https://www.thingiverse.com/thing:2080224)
  * [XYZ Cube](https://www.thingiverse.com/thing:1278865/comments)
  * [Benchy Boat](https://www.thingiverse.com/thing:763622)
  * [Cali-Dragon](https://www.thingiverse.com/thing:5401659)

## TO DO:
* Leveling/Tramming is off to the side a little, still trying to figure it out

## CHANGELOG:

#### 2023-09-24 - V1.11.0
* Fixed an issue where the menus were wrong for the DELICIOUS COMMANDS which would cause the firmware to fail to compile
* Added support for TH3D Multi-Mount BL/CR probe

#### 2023-09-24 - V1.10.0
* Added FILAMENT_RUNOUT_SENSOR - Customize Printer section
* Added support for these boards - Customize printer section
  - BOARD_BTT_SKR_MINI_E3_V1_0
  - BOARD_BTT_SKR_MINI_E3_V1_2
  - BOARD_BTT_SKR_MINI_E3_V2_0
  - BOARD_BTT_OCTOPUS_V1_0
  - BOARD_BTT_OCTOPUS_V1_1
  - BOARD_BTT_OCTOPUS_PRO_V1_0
  - BOARD_BTT_OCTOPUS_MAX_EZ_V1_0
  * Added new DELICIOUS COMMANDS
    - PID E 260C (Useful for ABS and ASA)
    - PID Bed 90C (Useful for ASA)
* MENU_ADDAUTOSTART (adds ability to turn on autostart which runs gcode on boot with name auto0.g.code)

#### 2023-09-20 - V1.9.0 - Customizer Support Update

* Added 'CUSTOMIZER PRINTER' section where you can easily make a firmware from scratch in seconds!
  - Select things like motherboard, drivers, probe and be ready to compile in record time
* Added a 'PRE BUILT PRINTERS' section where you can easily enable/disable a printer for a quick compile
  - Printer already pre-configured? Just select one of the many custom printer options and export away
* Changed SPRITE_EXTRUDER E/Steps from 97 to 430
* Changed SPRITE_EXTRUDER Probe Offset from { -40, -8, 0 } to { -38.8, -40.50, 0 }

#### 2023-09-19 - V1.8.0
* Changed the SKR_MNI_E3_V3 boards from TMC2209_STANDALONE to TMC2209
* SKR_MNI_E3_V3 boards are now inverted for the XYZE direction (true, true, false, true)
  - Should no longer go backwards
* Enabled BABYSTEP_ZPROBE_OFFSET
* Added ENDER_3_427_CR_BL_TOUCH_SPRITE_EXTRUDER and ENDER_3_422_CR_BL_TOUCH_SPRITE_EXTRUDER
* Changed ENDER_3_427_CR_BL_TOUCH_WITH_SPIDER_HOTEND and ENDER_3_422_CR_BL_TOUCH_WITH_SPIDER_HOTEND to ENDER_3_427_CR_BL_TOUCH_WITH_THERMISTOR_61 and ENDER_3_422_CR_BL_TOUCH_WITH_THERMISTOR_61

#### 2023-09-19 - V1.7.0 - Multi-Printer Support Update
* Building out to support multiple different boards and configs for the Ender 3! Will take a decent amount of work, but we'll get there
  - This will be done with a series of IF/ELSE commands for settings, should auto change setting sand pins (I hope?) when selecting printer
  - Created profiles for:
    - ENDER_3_427_CR_BL_TOUCH
    - ENDER_3_422_CR_BL_TOUCH (4.2.2 boards assume A4988 drivers)
    - ENDER_3_427_Z_SWITCH
    - ENDER_3_422_Z_SWITCH (4.2.2 boards assume A4988 drivers)
    - ENDER_3_427_CR_BL_TOUCH_WITH_SPIDER_HOTEND (Different temp sensor than stock Ender 3)
    - ENDER_3_422_CR_BL_TOUCH_WITH_SPIDER_HOTEND (Different temp sensor than stock Ender 3) (4.2.2 boards assume A4988 drivers)
    - ENDER_3_SKR_MNI_E3_V3_CR_BL_TOUCH
    - ENDER_3_SKR_MNI_E3_V3_Z_SWITCH
* Changed DELICIOUS COMMANDS for PID tuning of the Hot-End from "180, 190, 200" to "190, 200, 210." Seemed more reasonable
* LIN_ADVANCE added for BTT SKR Mini E3 V3
* Changed HEATER_0_MAXTEMP from 275 to 350 on 4.2.2 and 4.2.7 boards(don't burn your house down)

#### 2023-09-17 - V1.6.1
* Changed X_BED_SIZE and Y_BED_SIZE (Printable area) from 235 to 220
  - This was done to avoid issues with the printer tramming or printing off the edges
* X_MAX_POS and Y_MAX_POS changed from X_BED_SIZE and Y_BED_SIZE to 235
  - Just to set a safe static value
* Fixed some potential bugs in the custom menu with improper text output
* Changed custom PID E menu from just "M106" that assumes fan speed to max, to specifically say "M106 S255" (max speed)
* Changed XY_PROBE_FEEDRATE from 133*60 to 200*60 (to speed up probing)
* Changed Z_PROBE_FEEDRATE_FAST from 4*60 to 8*60 (to speed up probing)
* Removed entire PSU control section
* Cleaned up license file just to make it easier for me to read and scroll the config files
* Removed these sections:
  - security
  - volumetrics

#### 2023-09-03 - V1.6.0
* Turned on LIMITED_MAX_ACCEL_EDITING
* Turned on ADVANCED_PAUSE_FEATURE
  - PAUSE_PARK_RETRACT_LENGTH set to 3mm instead of default 2mm
  - FILAMENT_CHANGE_UNLOAD_LENGTH set to 150mm instead of 100mm
* Turned on NOZZLE_PARK_FEATURE
* Turned on PARK_HEAD_ON_PAUSE
* Turned on FILAMENT_LOAD_UNLOAD_GCODES

#### 2023-08-23 - V1.5.0

* Turned off LIN_ADVANCE (Not supported on the 4.2.7 board, I did a dumb)
* Custom 'DELICIOUS COMMANDS' PID Tuning now turns the fan off once PID tuning is done
* Changed PREHEAT_1_TEMP_HOTEND (PLA) from 180 to 190
* Changed DEFAULT_MAX_ACCELERATION from { 500, 500, 100, 5000 } to { 2000, 2000, 100, 10000 } (More speed is more good 😉)
* Changed DEFAULT_ACCELERATION from 500 to 1000
* Changed DEFAULT_TRAVEL_ACCELERATION from 500 to 2000
* Updated Bootscreen for a nicer image!
* Removed these functions to clean up configuration.h and Configuration_adv.h:
  - THERMAL_PROTECTION_CHAMBER
  - THERMAL_PROTECTION_COOLER
  - TEMP_SENSOR_COOLER
  - STATUS_CHAMBER_ANIM
  - STATUS_CUTTER_ANIM
  - STATUS_COOLER_ANIM
  - STATUS_FLOWMETER_ANIM
  - REALTIME_REPORTING_COMMANDS
  - FULL_REPORT_TO_HOST_FEATURE
  - EMERGENCY_PARSER
  - RX_BUFFER_MONITOR
  - LASER_SYNCHRONOUS_M106_M107
  - COOLANT_CONTROL
  - G0_FEEDRATE
  - GCODE_MOTION_MODES
  - PAREN_COMMENTS

#### 2023-08-20 - V1.4.1
* Changed X_MAX_POS (X_BED_SIZE + 49) to X_MAX_POS (X_BED_SIZE), again (no longer goes off the edge of the bed)
* Changed Y_MAX_POS (Y_BED_SIZE + 7) to Y_MAX_POS (Y_BED_SIZE), again (no longer goes off the edge of the bed)
* Changed BED_TRAMMING_PROBE_TOLERANCE from 0.1mm to 0.04mm (0.1mm is a huge gap when your initial layer is 0.2mm, we're talking 50% off!)
* Changed #define NOZZLE_TO_PROBE_OFFSET { -44, -7, 0 } to #define NOZZLE_TO_PROBE_OFFSET { -40, -8, 0 } (Still figuring this out)

#### 2023-08-19 - V1.4.0

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

#### 2023-08-17 - V1.3.0

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
* Turned off NOZZLE_TO_PROBE_OFFSET for now as with it, it refused to compile, will have to investigate
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

#### 2023-08-15 - V1.2.0

* Changed default E/Steps to 97 from 93 (I've observed that most Ender 3 steppers are set way too low by default and generally end up somewhere between 96-98). I would still **HIGHLY** recommend for everyone to calibrate their E/Steps correctly, just changing this default gives an easier and smoother out of the box experience.
* PREHEAT BED LEVEL was miss configured, should be correctly set now
* Enabled DISTINCT_E_FACTORS, should now be able to configure X, Y, Z and E Steps directly on the printer

#### 2023-08-15 - V1.1.0

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

#### 2023-08-14 - V1.0.0 - Initial build

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
