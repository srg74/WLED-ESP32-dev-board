# Platformio [env] for ESP32 WLED dev board

```[env:esp32_devb_SHT_sensor_PWM_fan_mods_16mb]
extends = env:esp32dev
upload_speed = 460800
monitor_speed = 115200
;upload_protocol = espota
# exchange for your WLED IP
;upload_port = "XX.XX.XX.XX"
build_flags = ${common.build_flags_esp32}
  -D WLED_WATCHDOG_TIMEOUT=0
  -D WLED_DISABLE_BLYNK
  -D WLED_DISABLE_CRONIXIE
  -D WLED_DISABLE_HUESYNC
  -D WLED_DISABLE_LOXONE
  -D WLED_RELEASE_NAME=esp32_devb_SHT_sensor_PWM_fan_mods_16mb
  -D SERVERNAME='"ESP32-WLED-dev"'
# Pins assigment and pixel count
  -D BTNPIN=-1
  -D LEDPIN=2
  -D RLYPIN=16
# User mods
# SHTx temperature sensor mod
  -D USERMOD_SHT
  -D USERMOD_SHT_TYPE_SHT31=1
# PWM Fan mod
  -D USERMOD_PWM_FAN
  -D PWM_PIN=32
  -D TACHO_PIN=33
  -UWLED_USE_MY_CONFIG
lib_deps = ${esp32.lib_deps}
  https://github.com/RobTillaart/SHT85
board_build.partitions = tools/WLED_ESP32_16MB.csv
```
