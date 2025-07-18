🛒 Smart Shopping Cart using RFID and Arduino Nano
A smart solution for retail shopping that eliminates long billing queues by using RFID-based item detection and automatic billing through an Arduino Nano-controlled system.

📌 Project Overview
This project implements a Smart Shopping Cart that uses RFID tags to identify products added to the cart. An RFID reader, controlled by an Arduino Nano, reads the tag data, displays item and price info on an OLED/LCD, and calculates the total bill automatically. A buzzer provides user feedback, and a push button confirms checkout.

⚙️ Features
📦 Real-time item detection using RFID

🧾 Auto billing and itemized price display

📺 LCD/OLED screen for item names and prices

🔊 Buzzer for alerts (item added/removed)

🔘 Push button for checkout confirmation

🔒 Secure and scalable for retail environments

🧰 Hardware Components
Component	Quantity
Arduino Nano	1
RFID Module (RC522)	1
RFID Tags	2-5
OLED or 16x2 LCD Display	1
Buzzer	1
Push Button	1
Resistors, Jumper Wires, Breadboard	As needed
Power Supply (Battery/USB)	1

📚 Required Libraries
MFRC522.h – for RFID module communication

SPI.h – for SPI communication with RC522

Wire.h – for I2C communication (for OLED/LCD)

LiquidCrystal_I2C.h or Adafruit_SSD1306.h – based on display

Install libraries via Arduino Library Manager or GitHub.

🔌 Circuit Diagram
css
Copy
Edit
[RFID Reader] --> [Arduino Nano SPI Pins]
[OLED/LCD Display] --> [I2C Pins A4/A5]
[Buzzer] --> [Digital Pin]
[Push Button] --> [Digital Pin + Pull-down Resistor]
Make sure to cross-check wiring with the datasheets.

📦 How It Works
Each product is tagged with an RFID tag.

When the item is brought near the RFID reader, it reads the unique ID.

The system checks the item in a predefined database.

Item name and price are displayed on the screen.

The buzzer beeps for confirmation.

The total bill updates automatically.

Pressing the checkout button finalizes the purchase.

💻 Code Overview
Define RFID tag UID → item mapping

On tag detection:

Identify item

Display item details

Update total price

On button press:

Display total bill

Trigger buzzer

🎯 Applications
Supermarkets and retail stores

Unmanned billing counters

Library automation (with minor changes)

🚀 Future Enhancements
Add Wi-Fi (ESP8266) to send bills to mobile app

Integrate with cloud database

Use mobile app for payment

Real-time cart sync to store system

📷 Demo & Images
Add your project images or demo video link here

📄 License
MIT License - Free to use and modify.

