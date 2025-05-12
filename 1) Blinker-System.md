# Arduino Blinker System

## Required Components

To build this project, you will need the following components:

- **1 × Arduino Uno**: Microcontroller-based development board to control the blinker system.
- **1 × LED**: Emits light periodically to indicate the blinking effect.
- **1 × 220Ω Resistor**: Limits current to the LED and drops voltage to safe levels.

> **Tip**: Ensure the LED is connected with the correct polarity (anode to the resistor, cathode to ground).

## Hardware Setup

**Construct the Schematic Diagram**:
   - Connect the LED's anode to a 220Ω resistor.
   - Connect the other end of the resistor to Arduino pin 8.
   - Connect the LED's cathode to the Arduino's GND pin.

![image](https://github.com/user-attachments/assets/e9f0bbae-fd68-40f3-8f87-95615fe1e79e)


> **Warning**: Incorrect wiring may damage the LED or Arduino. Verify connections before powering on.

## Arduino Code

Below is the code to make the LED blink every 500 milliseconds:

```cpp
const int LED_PIN = 8;

void setup() {
  pinMode(LED_PIN, OUTPUT);
}

void loop() {
  digitalWrite(LED_PIN, HIGH);
  delay(500); 
  digitalWrite(LED_PIN, LOW);
  delay(500); 
}
```

> **Info**: The `setup()` function initializes pin 8 as an output, and the `loop()` function toggles the LED state with a 500ms delay.

## How to Use

1. Upload the code to your Arduino Uno using the Arduino IDE.
2. Connect the hardware as described in the schematic.
3. Power the Arduino via USB or an external power source.
4. The LED should start blinking immediately.


https://github.com/user-attachments/assets/8928d5a3-9593-4dbe-ad6c-f47f0118fccb


> **Success**: If the LED blinks as expected, your setup is correct! If not, recheck wiring and code.
