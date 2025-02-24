## How it works

This project implements a VGA pattern generator that creates animated concentric patterns with 8 distinct color layers. The core functionality includes:

1. **VGA Signal Generation**
   - Outputs standard 640x480 @ 60Hz VGA timing
   - Uses 25MHz clock for sync generation
   - Provides hsync, vsync, and video active signals

2. **Pattern Generation**
   - Creates 8 concentric layers from center (320,240)
   - Each layer has unique patterns based on:
     - Radius calculations using octagonal approximation
     - Angular patterns with dynamic updates
     - Color transitions and animations
   - Pattern updates occur on each vertical sync

3. **Color System**
   - 2-bit RGB output (8 colors per component)
   - Dynamic color cycling using frame counter
   - Unique color tints for each layer:
     - Layer 1: Red tint
     - Layer 2: Green tint
     - Layer 3: Blue tint
     - Layer 4: Purple tint
     - Layer 5: Yellow tint
     - Layer 6: Orange tint
     - Layer 7: Teal tint
     - Layer 8: Magenta tint

## How to test

1. **Required Setup**
   - Connect VGA display to output pins
   - Provide 25MHz clock input
   - Assert reset_n signal to start

2. **Pin Connections**
uo -> VGA hsync
uo -> VGA blue
uo -> VGA green
uo -> VGA red
uo -> VGA vsync
uo -> VGA blue
uo -> VGA green
uo -> VGA red

3. **Expected Output**
- Should see animated concentric patterns
- Colors should cycle smoothly
- Patterns should update on each vertical refresh
- Display should be stable without flickering

## External hardware

Required external hardware:
- VGA monitor or display
- VGA connector/cable
- Level shifters (if needed for 3.3V to 5V conversion)
- Optional: VGA DAC for better color quality

Connection diagram:
Project Pins Level Shifter (optional) VGA Connector
uo --------- [3.3V -> 5V] ------------- HSync
uo --------- [3.3V -> 5V] ------------- VSync
uo ------- [3.3V -> 5V] ------------- Red[1:0]
uo ------- [3.3V -> 5V] ------------- Green[1:0]
uo ------- [3.3V -> 5V] ------------- Blue[1:0]
GND ------------ GND --------------------- GND
