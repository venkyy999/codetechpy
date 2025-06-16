# codetechpy
🔹 Title
Arduino Serial LED Control

🔹 Description
This code allows you to control an LED connected to pin 13 of Arduino through Serial communication.
Using the Serial Monitor or a Serial terminal (such as phone’s Bluetooth terminal), you can send a character '1' to turn the LED ON and '0' to turn it OFF.
The Arduino responds back with messages to Serial to confirm its action.

🔹 Components
Arduino UNO

LED

220Ω resistor (to limit current and protect the LED — optional if it's a board’s built-in LED)

Serial communication (such as Serial Monitor or Bluetooth Serial)

🔹 Pin Connection
Component	Pin
LED (+)	Digital Pin 13
LED (−)	GND
resistor	in series with the LED (optional if it's a built-in LED)

🔹 Principle
The code waits for Serial data to become available.
Once it receives a character:

If the character is '1': it turns ON the LED.

If the character is '0': it turns OFF the LED.

Meanwhile, the Serial prints back messages “LED ON.” or “LED OFF.” to notify you about the action taken.

🔹 Detailed Code Explanation
cpp
Copy
Edit
// Declare which pin the LED is connected to
const int ledPin = 13;
Initializes ledPin to 13, the on-board LED's pin on Arduino UNO.

cpp
Copy
Edit
void setup()
{
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
  Serial.println("Ready to control LED.");
}
pinMode(ledPin, OUTPUT) configures the pin 13 as output.

Serial.begin(9600) starts Serial communication at 9600 baud rate.

Prints a confirmation message to Serial when the setup is complete.

cpp
Copy
Edit
void loop()
{
  if (Serial.available()) 
  {
    char cmd = Serial.read();

    if (cmd == '1') 
    {
      digitalWrite(ledPin, HIGH);
      Serial.println("LED ON.");
    }
    else if (cmd == '0') 
    {
      digitalWrite(ledPin, LOW);
      Serial.println("LED OFF.");
    }
  }
}
The if (Serial.available()) checks if there’s at least 1 byte available in Serial buffer.

Serial.read() reads the first byte in the Serial buffer.

If this byte is '1': the code executes digitalWrite(ledPin, HIGH) and prints “LED ON.”

If this byte is '0': it executes digitalWrite(ledPin, LOW) and prints “LED OFF.”

🔹 How To Use
Open Serial Monitor:

Select baud rate 9600 in Serial Monitor.

Send '1' or '0':

Type 1 and send it to turn the LED ON.

Type 0 and send it to turn the LED OFF.

The Serial Monitor will show a confirmation message afterwards.

🔹 Applications
✅ Home automation (Turning appliances ON or OFF remotely)
✅ Wireless control through Serial or Bluetooth
✅ Educational projects to learn Serial communication
