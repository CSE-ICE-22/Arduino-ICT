# Arduino Auto Light

Contains the code and setup instructions for an Arduino-based Auto Light system that turns an LED on or off based on ambient light intensity using a Light Dependent Resistor (LDR).
>**Link**: [Tinkercad simulation](https://www.tinkercad.com/things/4FcWibRiBm2-2-auto-light?sharecode=wH_eOo0ltlyVpCGNy-64RGcZEfknXHgmqLvg72x9fsc)

## Required Components

To build this project, you will need the following components:

- **1 × Arduino Uno**: Microcontroller-based development board to control the Auto Light system.
- **1 × LED**: Emits light when ambient light intensity is low.
- **1 × 220Ω Resistor**: Limits current to the LED and drops voltage to safe levels.
- **1 × Light Dependent Resistor (LDR)**: Captures ambient light intensity as an input.
- **1 × 10kΩ Resistor**: Limits current flow to the ground line in the LDR circuit.

> **Tip**: Ensure the LDR is positioned to accurately detect ambient light without obstructions.

## Hardware Setup

**Construct the Schematic Diagram**:
   - Connect the LED's anode to a 220Ω resistor, and the resistor's other end to Arduino pin 8.
   - Connect the LED's cathode to the Arduino's GND pin.
   - Connect one leg of the LDR to the Arduino's 5V pin.
   - Connect the other leg of the LDR to analog pin A0 and to a 10kΩ resistor.
   - Connect the other end of the 10kΩ resistor to the Arduino's GND pin.
![image](https://github.com/user-attachments/assets/8c2df6ab-e960-4210-9516-9a190a825fad)

> **Warning**: Double-check wiring, especially the LDR and resistor connections, to avoid damaging components.

## Arduino Code

Below is the code to control the LED based on ambient light intensity, with serial output for debugging:

```cpp
const int LED_PIN = 8;
const int LDR_PIN = A0;

void setup() {
  pinMode(LED_PIN, OUTPUT);
  Serial.begin(115200);
}

void loop() {
  int sensorValue = analogRead(LDR_PIN);
  Serial.print("LDR Value: ");
  Serial.println(sensorValue);
  if (sensorValue < 150) {
    digitalWrite(LED_PIN, HIGH);
  } else {
    digitalWrite(LED_PIN, LOW);
  }
}
```

> **Info**: 
> - The `setup()` function initializes pin 8 as an output and starts serial communication at 115200 baud.
> - The `loop()` function reads the LDR value from analog pin A0, prints it to the Serial Monitor, and turns the LED on if the value is below 150 (indicating low light) or off otherwise.

## How to Use

1. Upload the code to your Arduino Uno using the Arduino IDE.
2. Connect the hardware as described in the schematic.
3. Open the Serial Monitor in the Arduino IDE (set to 115200 baud) to view LDR values.
4. Power the Arduino via USB or an external power source.
5. The LED will turn on when ambient light is low (LDR value < 150) and off when light is sufficient.



https://github.com/user-attachments/assets/e82d1562-6330-4ffd-a4ae-b8fb1a42f374



> **Success**: If the LED responds to changes in ambient light (e.g., covering the LDR turns the LED on), your setup is working! If not, check wiring, LDR placement, or adjust the threshold value (150) in the code.

> **Debugging Tip**: Use the Serial Monitor to verify LDR values. If values seem inconsistent, ensure the LDR is not saturated by excessive light or shadowed unintentionally.
