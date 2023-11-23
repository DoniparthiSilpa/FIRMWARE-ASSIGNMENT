# FIRMWARE-ASSIGNMENT

cpp

const int LM35_PIN = A0; // This line declares a constant integer variable named LM35_PIN and assigns it the value A0, representing the analog pin connected to the LM35 temperature sensor.


const int LED_PIN = 13; // This line declares another constant integer variable named LED_PIN and assigns it the value 13, representing the digital pin connected to the onboard LED on the Arduino board.


void setup() { 

  pinMode(LED_PIN, OUTPUT); // This line sets the LED_PIN as an output pin, indicating that the LED will be controlled by the Arduino.
  
}

void loop() { 

  int temperature = readTemperature(); // This line calls the readTemperature() function to read the temperature value from the LM35 sensor and store it in the temperature variable.

  if (temperature < 30) { // This line checks if the temperature is less than 30 degrees.
  
    blinkLED(BLINK_INTERVAL_LOW); // This line calls the blinkLED() function with a low blink interval if the temperature is less than 30.
    
  } else {
  
    blinkLED(BLINK_INTERVAL_HIGH); // This line calls the blinkLED() function with a high blink interval if the temperature is not less than 30.
    
  } 
  
}

int readTemperature() { 

  int sensorValue = analogRead(LM35_PIN); // This line reads the analog value from the LM35 sensor connected to LM35_PIN.
  
  float voltage = sensorValue * (5.0 / 1023.0); // This line converts the sensor value to voltage.
  
  float temperature = (voltage - 0.5) * 100; // This line calculates the temperature in degrees Celsius.
  
  return (int)temperature; // This line returns the temperature value as an integer.
  
}

void blinkLED(int interval) { 

  digitalWrite(LED_PIN, HIGH); // This line turns on the LED by setting the pin to HIGH.
  
  delay(interval); // This line waits for the specified interval.
  
  digitalWrite(LED_PIN, LOW); // This line turns off the LED by setting the pin to LOW.
  
  delay(interval); // This line waits for the specified interval.
  
}
