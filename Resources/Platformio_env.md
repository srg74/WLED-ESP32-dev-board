# Platformio [env] for ESP32 WLED universal board

```[env:esp32_WLED_dev_board]
board = esp32dev
platform = espressif32@3.5
upload_speed = 460800
monitor_speed = 115200
;upload_protocol = espota
# exchange for your WLED IP
;upload_port = "IP-address"
build_unflags = ${common.build_unflags}
build_flags = ${common.build_flags_esp32}
  -D WLED_DISABLE_BLYNK
  -D WLED_DISABLE_CRONIXIE
  -D WLED_DISABLE_HUESYNC
  -D WLED_DISABLE_LOXONE
  -D WLED_RELEASE_NAME=ESP32_WLED_dev_board_01
# Enable Ethernet shield
;  -D WLED_USE_ETHERNET
# Pins assigment and pixel count
  -D BTNPIN=0
  -D LEDPIN=2
;  -D DATA_PINS=1,2
;  -D PIXEL_COUNTS=150,150,150,150
  -D IRPIN=-1
  -D RLYPIN=16
# User mods
  # Dallas temperature sensor mod
  -D USERMOD_DALLASTEMPERATURE
  -D TEMPERATURE_PIN=4
  # Display mod
  # I2C display
  -D USERMOD_FOUR_LINE_DISPLAY
  -D USE_ALT_DISPlAY
  -D FLD_PIN_SCL=22
  -D FLD_PIN_SDA=21
  -D FLD_TYPE=SH1106
;  -D FLD_TYPE=SSD1306
  # SPI display
  ; -DFLD_SPI_DEFAULT
  ; -D FLD_TYPE=SSD1306_SPI64
  ; -D FLD_PIN_CLOCKSPI=14
  ; -D FLD_PIN_DATASPI=13
  ; -D FLD_PIN_DC=26
  ; -D FLD_PIN_CS=15
  ; -D FLD_PIN_RESET=27
  # Rotary encoder mod
  -D USERMOD_ROTARY_ENCODER_UI
  -D ENCODER_DT_PIN=18
  -D ENCODER_CLK_PIN=19
  -D ENCODER_SW_PIN=17
  # Multirelay mod
  ; -D USERMOD_MULTI_RELAY  # 12, 23, 22 & 21
  # PWM Fan mod
  -D USERMOD_PWM_FAN
  -D PWM_PIN=32
  -D TACHO_PIN=33
;  -D WLED_DEBUG
  -UWLED_USE_MY_CONFIG
lib_deps = ${esp32.lib_deps}
  U8g2@~2.32.10 # Uncoment for display mod
  paulstoffregen/OneWire@~2.3.6 # Uncoment for temperature mod
board_build.partitions = ${esp32.default_partitions}
```
