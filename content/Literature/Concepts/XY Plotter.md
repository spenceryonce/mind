### Reading Serial Data  + Sending Commands to Servos
```c
#include <Servo.h>

Servo xServo;  // Servo for X direction
Servo yServo;  // Servo for Y direction

const int xLEDPin = 3;  // LED indicating X movement
const int yLEDPin = 4;  // LED indicating Y movement
const int xServoPin = 1;  // Servo control pin for X
const int yServoPin = 2;  // Servo control pin for Y

String command = "";  // Store the incoming command

void setup() {
  Serial.begin(9600);
  xServo.attach(xServoPin);
  yServo.attach(yServoPin);
  
  pinMode(xLEDPin, OUTPUT);
  pinMode(yLEDPin, OUTPUT);
}

void loop() {
  while (Serial.available()) {
    char c = Serial.read();
    if (c == '\n') {
      executeGCode(command);
      command = "";
    } else {
      command += c;
    }
  }
}

void executeGCode(String cmd) {
  if (cmd.startsWith("G1")) {
    // Extract X and Y values from the command
    int xPos = extractValue(cmd, 'X');
    int yPos = extractValue(cmd, 'Y');

    // Convert these positions to angles for the servos
    int xAngle = map(xPos, 0, 100, 0, 180);  // Assuming servo range of 0-180 degrees
    int yAngle = map(yPos, 0, 100, 0, 180);

    // Move the servos
    xServo.write(xAngle);
    yServo.write(yAngle);

    // Blink the LEDs
    if (xPos != 0) blinkLED(xLEDPin);
    if (yPos != 0) blinkLED(yLEDPin);
  } else if (cmd.startsWith("M3")) {
    // Pen up action (You can modify this if required)
  } else if (cmd.startsWith("M5")) {
    // Pen down action (You can modify this if required)
  }
}

int extractValue(String data, char identifier) {
  data += ' ';
  int found = 0;
  int strIndex[] = {0, -1};
  int maxIndex = data.length() - 1;
  for (int i = 0; i < maxIndex && found <= 1; i++) {
    if (data.charAt(i) == identifier) {
      strIndex[0] = i;
      found++;
      for (int j = i; j <= maxIndex && found == 1; j++) {
        if (isDelimiter(data.charAt(j))) {
          strIndex[1] = j;
          found++;
        }
      }
    }
  }
  return (found > 1) ? data.substring(strIndex[0] + 1, strIndex[1]).toInt() : 0;
}

boolean isDelimiter(char c) {
  return (c == ',' || c == ';' || c == ' ' || c == '\n');
}

void blinkLED(int ledPin) {
  digitalWrite(ledPin, HIGH);
  delay(100);
  digitalWrite(ledPin, LOW);
}

```

### Sending Data over Serial Port to Seeduino XAIO
#### Install the pyserial library
```python
pip install pyserial
```

#### Sending Data
```python
import serial
import time

# Set the appropriate COM port and baud rate for your Seeeduino XIAO
PORT = 'COM3'  # Adjust this to your Seeeduino's port (e.g., 'COM3' for Windows, '/dev/ttyUSB0' for Linux)
BAUD_RATE = 9600

# The G-code commands we generated earlier
GCODE_COMMANDS = [
    "G21 ; Set units to millimeters",
    "G90 ; Absolute positioning",
    "G92 X0 Y0 ; Zero the position",
    "M3 ; Pen up",
    "G1 X1.00 Y1.00 ; Move to position",
    "G1 X51.00 Y1.00 ; Move to position",
    "G1 X51.00 Y31.00 ; Move to position",
    "G1 X1.00 Y31.00 ; Move to position",
    "G1 X1.00 Y1.00 ; Move to position",
    "M5 ; Pen down"
]

def send_gcode_to_seeduino(commands, port, baud_rate):
    with serial.Serial(port, baud_rate, timeout=1) as ser:
        time.sleep(2)  # Give some time for the connection to establish
        
        for command in commands:
            ser.write((command + '\n').encode())
            time.sleep(0.1)  # Small delay between commands for smooth operation
            print(f"Sent: {command}")
        
        print("G-code commands sent successfully!")

if __name__ == "__main__":
    send_gcode_to_seeduino(GCODE_COMMANDS, PORT, BAUD_RATE)

```

