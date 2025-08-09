# Asteroids-F031

A bare-metal **STM32F031** implementation of a simple arcade shooter game, inspired by *Asteroids*.  
Runs entirely in C without HAL or RTOS, featuring a custom SPI TFT graphics library, ADC controls, button input, and PWM audio output.

## Features

- **Custom graphics library** for 128×160 TFT (SPI) with RGB565 colour.
- **Real-time game loop** with scoring, lives, and collision detection.
- **Hardware control**:
  - Potentiometer via ADC for ship rotation (5 angles).
  - Buttons for movement and start.
  - LEDs for life display.
  - PWM buzzer for shooting/explosion sounds.
- **Optimised** for low memory footprint and fast rendering.

## Hardware Requirements

- STM32F031 microcontroller board (tested on STM32F031x6).
- 1.8" 128×160 SPI TFT
- Potentiometer on **PA0** (ADC input).
- Buttons on **PB4** (Right), **PB5** (Left), **PA8** (Start).
- LEDs on **PA9**, **PA10**, **PA12** for lives display.
- Passive buzzer on **PB1** (TIM3 CH4 PWM output).

## Controls

- **Rotate ship**: Potentiometer (maps ADC reading to orientation).
- **Move ship**:  
  - Left: PB5  
  - Right: PB4
- **Start game**: Center potentiometer and press PA8.

## How It Works

- **Game loop** updates input, moves objects, detects collisions, draws to display, and manages score/lives.
- **Graphics library** supports pixels, shapes, bitmaps, and 5×7 text.
- **Display driver** uses SPI1 with manual control of CS, DC, and RESET pins.
- **Audio** generated via PWM on TIM3, frequency set per sound effect.

