# Ender-3-Pro-Bltouch-BTT-Mini-E3-V1.2
My personal configs that work for my Ender 3 Pro with stock motors, genuine BLTouch for Z homing. BTT Mini E3 V1.2
Marlin 2.0.5.3
These are the only two files changed in ths revision.

Caution!

BLTOUCH is using the Z-STOP! I use BLTOUCH for z-homing

Z can move below 0! This is needed for easy adjustment of Z offset with #define BABYSTEP_ZPROBE_GFX_OVERLAY 

My BLOUCH is mouned with default hardware, adjust #define NOZZLE_TO_PROBE_OFFSET { -44, -6, 0 } to fit your setup.

Key changes:

configuration.h

#define CUSTOM_MACHINE_NAME "E3PRO-BLT-SKR"

#define DEFAULT_AXIS_STEPS_PER_UNIT   { 80, 80, 400, 96 } //standard extruder

//#define DEFAULT_AXIS_STEPS_PER_UNIT   { 80, 80, 400, 146 } //Winnsinn extruder


#define DEFAULT_MAX_FEEDRATE          { 500, 500, 20, 25 }

//After more than 100 hours testing CJ and JD, I have decided to use CJ.

#define CLASSIC_JERK
#if ENABLED(CLASSIC_JERK)
  #define DEFAULT_XJERK 10.0
  #define DEFAULT_YJERK 10.0
  #define DEFAULT_ZJERK  0.3

#define Z_MIN_PROBE_USES_Z_MIN_ENDSTOP_PIN

#define BLTOUCH

#define NOZZLE_TO_PROBE_OFFSET { -44, -6, 0 }

#define XY_PROBE_SPEED 8000

#define MULTIPLE_PROBING 2

#define PROBING_FANS_OFF          // Turn fans off when probing

//#define PROBING_STEPPERS_OFF      // Turn steppers off (unless needed to hold position) when probing

#define DELAY_BEFORE_PROBING 400  // (ms) To prevent vibrations from triggering piezo sensors

//#define MIN_SOFTWARE_ENDSTOP_Z

// Enable the M48 repeatability test to test probe accuracy
#define Z_MIN_PROBE_REPEATABILITY_TEST

#define AUTO_BED_LEVELING_BILINEAR

//#define AUTO_BED_LEVELING_UBL

//#define MESH_BED_LEVELING

#define RESTORE_LEVELING_AFTER_G28

// Set the number of grid points per dimension. 
  #define GRID_MAX_POINTS_X 7 //49 double taps

#define LEVEL_CORNERS_HEIGHT      4.0 

#define HOMING_FEEDRATE_Z  (10*60)

#define Z_SAFE_HOMING

#define EEPROM_SETTINGS       // Persistent storage with M500 and M501
//#define DISABLE_M503        // Saves ~2700 bytes of PROGMEM. Disable for release!
//#define EEPROM_CHITCHAT       // Give feedback on EEPROM commands. Disable to save PROGMEM.
//#define EEPROM_BOOT_SILENT    // Keep M503 quiet and only give errors during first load
#if ENABLED(EEPROM_SETTINGS)
  #define EEPROM_AUTO_INIT  // Init EEPROM automatically on any errors.
#endif


/ Preheat Constants

#define PREHEAT_1_LABEL       "PLA 200"

#define PREHEAT_1_TEMP_HOTEND 200

#define PREHEAT_1_TEMP_BED     55

#define PREHEAT_1_FAN_SPEED   200 // Value from 0 to 255

#define PREHEAT_2_LABEL       "PLA 220"

#define PREHEAT_2_TEMP_HOTEND 220

#define PREHEAT_2_TEMP_BED    60

#define PREHEAT_2_FAN_SPEED   200 // Value from 0 to 255

//#define PRINTCOUNTER //Make sure this is disabled, it is broken


configuration_adv.h

#define BLTOUCH_DELAY 500

Please understand this next section. If you have 3.1 Bltouch then this is good to go. 
If you have an older BLYOUCH then you will need to make sure the 5v mode is set correctly.

/**
   * Danger: Don't activate 5V mode unless attached to a 5V-tolerant controller!
   * V3.0 or 3.1: Set default mode to 5V mode at Marlin startup.
   * If disabled, OD mode is the hard-coded default on 3.0
   * On startup, Marlin will compare its eeprom to this vale. If the selected mode
   * differs, a mode set eeprom write will be completed at initialization.
   * Use the option below to force an eeprom write to a V3.1 probe regardless.
   */
  #define BLTOUCH_SET_5V_MODE


#define LCD_TIMEOUT_TO_STATUS 5000

#if ENABLED(SHOW_BOOTSCREEN)

#define BOOTSCREEN_TIMEOUT 1000        // (ms) Total Duration to display the boot screen(s)

#endif

#define SHOW_REMAINING_TIME          // Display estimated time to completion

#if ENABLED(SHOW_REMAINING_TIME)

//#define USE_M73_REMAINING_TIME     // Use remaining time from M73 command instead of estimation

#define ROTATE_PROGRESS_DISPLAY    // Display (P)rogress, (E)lapsed, and (R)emaining time

#define POWER_LOSS_RECOVERY

#define SD_REPRINT_LAST_SELECTED_FILE

#define BOOT_MARLIN_LOGO_ANIMATED

#define BABYSTEPPING

#define BABYSTEP_MULTIPLICATOR_Z  6

#define BABYSTEP_ZPROBE_OFFSET          // Combine M851 Z and Babystepping

#if ENABLED(BABYSTEP_ZPROBE_OFFSET)

//#define BABYSTEP_HOTEND_Z_OFFSET      // For multiple hotends, babystep relative Z offsets

#define BABYSTEP_ZPROBE_GFX_OVERLAY   // Enable graphical overlay on Z-offset editor

#define TX_BUFFER_SIZE 64

//#define HYBRID_THRESHOLD


