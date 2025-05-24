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

![image](https://github.com/user-attachments/assets/c206b7d4-3637-476c-b468-18635e60c87f)
![image](https://github.com/user-attachments/assets/26abeb64-8ece-4152-b74f-1ef08d053fa0)
![image](https://github.com/user-attachments/assets/f9fe0632-00cf-4f83-94d2-972ef8940a19)
![image](https://github.com/user-attachments/assets/a24da308-e230-4846-990b-cc152c89cf08)

Output:

![WhatsApp Image 2025-05-24 at 19 52 00_2017a83d](https://github.com/user-attachments/assets/c1ee5f97-81f7-48e1-b77d-3f96a60a540a)

![image](https://github.com/user-attachments/assets/2d883e89-61ca-4350-a259-fdfd06dc3503)












      

 
