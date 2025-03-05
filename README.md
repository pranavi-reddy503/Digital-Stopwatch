# Digital-Stopwatch
A mini hardware implementation of digital stopwatch.
Overview:
A digital stopwatch is a device that measures and displays time with high accuracy, typically in seconds and fractions of a second. Unlike analog stopwatches, which use mechanical hands to track time, digital stopwatches use electronic circuits to process and display time readings. These devices are commonly used in various fields such as sports, science experiments, and general time-tracking activities.
A stopwatch will always have 2 buttons or modes, a start, and a stop mode. It may have other features but it will always have these. Additionally, we have added reset function too. This can be done with the pressing reset button of Arduino.

Components Required:
1.Bread Board.
2.Connecting wires.
3.Push Button switch.
4.LCD Display.
5.Potentiometer.
6.Arduino Uno.

Circuit Diagram:
![image](https://github.com/user-attachments/assets/471ce920-d710-4a0d-b002-7b0aef9a78be)

Connections:
Connect the push buttons to Arduino digital pins 4 and 5. 
Digital pin 4 is used for the start button, while digital pin 5 is used for the stop or reset button.

Connect the RS (Register Select) pin to Arduino digital pin 8, and the E (Enable) pin to digital pin 9. 
The LCD’s four data lines—D4, D5, D6, and D7—are then connected to digital pins 10, 11, 12, and 13, respectively.
To adjust the LCD contrast, a potentiometer is often used: 
the middle terminal of the potentiometer is connected to the Vo pin (Pin 3 of LCD), while one of the outer terminals connects to 5V and the other to GND.

Code:
#include <LiquidCrystal.h>
 
// Initialize the LCD: (RS, E, D4, D5, D6, D7)
LiquidCrystal lcd(8, 9, 10, 11, 12, 13);
 
// Define button pins
const int startButtonPin = 4;  // Button to start timer
const int stopButtonPin  = 5;  // Button to stop timer (and later to reset)
 
// Define states for the timer
enum TimerState {IDLE, RUNNING, STOPPED};
TimerState timerState = IDLE;
 
unsigned long startTime = 0;    // Time when the timer was started
unsigned long elapsedTime = 0;  // Elapsed time in milliseconds
 
void setup() {
  lcd.begin(16, 2);
  lcd.clear();
  Serial.begin(9600);
  
  // Setup button pins with internal pull-ups
  pinMode(startButtonPin, INPUT_PULLUP);
  pinMode(stopButtonPin, INPUT_PULLUP);
}
 
void loop() {
  switch(timerState) {
    case IDLE:
      // Clear the display and show the idle message
      lcd.clear();
      lcd.setCursor(0, 0);
      lcd.print("Press Start");
      // Also clear the second row so nothing overlaps later
      lcd.setCursor(0, 1);
      lcd.print("                ");
      // Wait for the start button to be pressed
      if (digitalRead(startButtonPin) == LOW) {
        delay(50);  // Debounce delay
        while (digitalRead(startButtonPin) == LOW) {
          delay(10); // Wait for button release
      }
      // Clear the display and record the starting time before switching states
        lcd.clear();
        startTime = millis();
        timerState = RUNNING;
      }
      break;
      case RUNNING:
      // Always clear row 1 so nothing from the idle state remains
      lcd.setCursor(0, 1);
      lcd.print("                ");
       // If the stop button is pressed, capture the time and move to STOPPED state
      if (digitalRead(stopButtonPin) == LOW) {
        delay(50);  // Debounce delay
        while (digitalRead(stopButtonPin) == LOW) {
          delay(10); // Wait for button release
           }
        elapsedTime = millis() - startTime;
        timerState = STOPPED;
      } else {
        // Otherwise, update the elapsed time continuously
        elapsedTime = millis() - startTime;
      }
      // Display the updated time on row 0
      displayTime(elapsedTime);
      break;
       case STOPPED:
      // Show the final time on row 0 and ensure row 1 is clear
      displayTime(elapsedTime);
      lcd.setCursor(0, 1);
      lcd.print("                ");
      // If the stop button is pressed again, reset to the IDLE state
      if (digitalRead(stopButtonPin) == LOW) {
        delay(50);  // Debounce delay
        while (digitalRead(stopButtonPin) == LOW) {
          delay(10); // Wait for button release
        }
        lcd.clear();
        timerState = IDLE;
      }
      break;
  }
}
 
// Helper function to format and display the elapsed time on row 0.
void displayTime(unsigned long timeInMillis) {
  // Calculate minutes, seconds, and milliseconds
  unsigned int minutes = timeInMillis / 60000;
  unsigned int seconds = (timeInMillis % 60000) / 1000;
  unsigned int milliseconds = timeInMillis % 1000;
  
  // Create a formatted string "MM:SS:MMM" (always 9 characters)
  char timeStr[10];  // 9 characters + null terminator
  sprintf(timeStr, "%02u:%02u:%03u", minutes, seconds, milliseconds);
  
  // Display the formatted time on the first row
  lcd.setCursor(0, 0);
  lcd.print(timeStr);
   // Optionally, also output the time to the Serial Monitor
  Serial.print("Time: ");
  Serial.println(timeStr);
}
