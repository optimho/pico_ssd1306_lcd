# Generated Cmake Pico project file

cmake_minimum_required(VERSION 3.13)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# Initialise pico_sdk from installed location
# (note this can come from environment, CMake cache etc)
set(PICO_SDK_PATH "//home/michael/pico/pico-sdk")

set(PICO_BOARD pico CACHE STRING "Board type")

# Pull in Raspberry Pi Pico SDK (must be before project)
include(pico_sdk_import.cmake)

if (PICO_SDK_VERSION_STRING VERSION_LESS "1.4.0")
  message(FATAL_ERROR "Raspberry Pi Pico SDK version 1.4.0 (or later) required. Your version is ${PICO_SDK_VERSION_STRING}")
endif()

project(ssd1306 C CXX ASM)

# Initialise the Raspberry Pi Pico SDK
pico_sdk_init()

add_subdirectory(pico-ssd1306)

# Add executable. Default name is the project name, version 0.1

add_executable(lcd_ssd1306 demo_ssd1306.cpp)

pico_set_program_name(lcd_ssd1306 "LCD_ssd1306")
pico_set_program_version(lcd_ssd1306 "0.1")

pico_enable_stdio_uart(lcd_ssd1306 0)
pico_enable_stdio_usb(lcd_ssd1306 1)

# Add the standard library to the build
target_link_libraries(lcd_ssd1306
        pico_stdlib
        pico_ssd1306)

# Add the standard include files to the build
target_include_directories(lcd_ssd1306 PRIVATE
  ${CMAKE_CURRENT_LIST_DIR}
  ${CMAKE_CURRENT_LIST_DIR}/.. # for our common lwipopts or any other standard includes, if required
)

# Add any user requested libraries
target_link_libraries(lcd_ssd1306
        hardware_i2c
        )

pico_add_extra_outputs(lcd_ssd1306)

