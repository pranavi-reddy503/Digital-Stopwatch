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
![image](https://github.com/user-attachments/assets/5a25071d-fae3-41b0-9068-07892122fae5)
![image](https://github.com/user-attachments/assets/3aa22aec-9371-4e68-8712-7f9edba2136d)
![image](https://github.com/user-attachments/assets/2cc9748b-f577-4f3b-b67f-270c0a7ac74b)
![image](https://github.com/user-attachments/assets/ff1add8f-a42c-45cb-8c5e-c93583e866b5)





      

 
