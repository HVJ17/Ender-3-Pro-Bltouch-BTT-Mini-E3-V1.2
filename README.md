# Ender-3-Pro-Bltouch-BTT-Mini-E3-V1.2
My personal configs that work for my Ender 3 Pro with stock motors, genuine BLTouch for Z homing. BTT Mini E3 V1.2
Marlin 2.0.5.3
These are the only two files changed in ths revision.
Key changes:

configuration.h

#define CUSTOM_MACHINE_NAME "E3PRO-BLT-SKR"
#define DEFAULT_AXIS_STEPS_PER_UNIT   { 80, 80, 400, 96 }
#define DEFAULT_MAX_FEEDRATE          { 500, 500, 20, 25 }
#define BLTOUCH
#define NOZZLE_TO_PROBE_OFFSET { -44, -6, 0 }
#define XY_PROBE_SPEED 10000
#define MULTIPLE_PROBING 2
#define PROBING_FANS_OFF          // Turn fans off when probing
//#define PROBING_STEPPERS_OFF      // Turn steppers off (unless needed to hold position) when probing
#define DELAY_BEFORE_PROBING 200  // (ms) To prevent vibrations from triggering piezo sensors
//#define MIN_SOFTWARE_ENDSTOP_Z
#define AUTO_BED_LEVELING_BILINEAR
//#define AUTO_BED_LEVELING_UBL
//#define MESH_BED_LEVELING
#define RESTORE_LEVELING_AFTER_G28
#define LEVEL_CORNERS_HEIGHT      4.0 
#define HOMING_FEEDRATE_Z  (20*60)
#define Z_SAFE_HOMING
#define DISABLE_M503        // Saves ~2700 bytes of PROGMEM. Disable for release!
#define EEPROM_CHITCHAT       // Give feedback on EEPROM commands. Disable to save PROGMEM.
//#define EEPROM_BOOT_SILENT 
/ Preheat Constants
#define PREHEAT_1_LABEL       "PLA 200"
#define PREHEAT_1_TEMP_HOTEND 200
#define PREHEAT_1_TEMP_BED     55
#define PREHEAT_1_FAN_SPEED   0 // Value from 0 to 255
#define PREHEAT_2_LABEL       "PLA 220"
#define PREHEAT_2_TEMP_HOTEND 220
#define PREHEAT_2_TEMP_BED    60
#define PREHEAT_2_FAN_SPEED   0 // Value from 0 to 255
//#define PRINTCOUNTER //Make sure this is disabled


configuration_adv.h

#define BLTOUCH_DELAY 500
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
#define BABYSTEP_MULTIPLICATOR_Z  6
#define BABYSTEP_ZPROBE_OFFSET          // Combine M851 Z and Babystepping
  #if ENABLED(BABYSTEP_ZPROBE_OFFSET)
    //#define BABYSTEP_HOTEND_Z_OFFSET      // For multiple hotends, babystep relative Z offsets
    #define BABYSTEP_ZPROBE_GFX_OVERLAY   // Enabl

#define TX_BUFFER_SIZE 64
  //#define HYBRID_THRESHOLD


