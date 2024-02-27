# Physical-Computing

## Experiment #1 - Code
```c++
const int LED_PIN = 11;

double squareWave(double radians);

void setup() { 
  pinMode(LED_PIN, OUTPUT);
}

void loop() { 
  // Read the poteniometer input
  int pIn = analogRead(A3);

  // Map the potentiometer input to desired frequency factor range
  double outMin = 50.0;
  double outMax = 500.0;
  double freqFactor = (double(pIn) / 1024.0) * (outMax - outMin) + outMin;

  // Calculate LED power
  int ledPower = squareWave(millis() / freqFactor) * 127 + 127;

  // Write to LED pin
  analogWrite(LED_PIN, ledPower);
}

// Output a square wave (range -1 to 1) given a radian angle
// Could be greatly optimized by replacing sin() 
double squareWave(double radians) {
  return sin(radians) > 0.0 ? 1.0 : -1.0;
}
```
