# RFID Access Control System (MFRC522 & LCD I2C)

This project uses an Arduino microcontroller combined with an MFRC522 RFID reader, a 16x2 LCD screen with an I2C interface, and a buzzer to control access based on the NUID (UID) of RFID tags or key fobs.

## 📌 Features

* **RFID Tag Reading (MIFARE Classic):** Scans and identifies RFID tags/key fobs when brought near the sensor.
* **Access Authentication:** Compares the scanned NUID against a pre-stored valid NUID (`0x4C 0x16 0x27 0x07`).
* **LCD Display Status Messages (16x2 LCD):**
  * Idle state: *"Xin hay quet the"* (Please scan card)
  * Authorized tag: *"Moi vao cong tyC"* (Welcome to Company C)
  * Unauthorized tag: *"Xin hay thu lai"* (Please try again)
* **Audio Alerts:** Triggers a buzzer sound when an unauthorized tag is detected.
* **Serial Output:** Prints detailed card type info, NUID in HEX format, and verification results to the Serial Monitor.

## 🛠 Hardware Required

1. **Arduino Board** (Uno, Nano, Mega, etc.)
2. **MFRC522 RFID Module** (13.56 MHz)
3. **16x2 LCD Display** with **I2C Backpack**
4. **Buzzer**
5. MIFARE Classic RFID tag or key fob
6. Jumper wires & Breadboard

## 🔌 Wiring Diagram (Pinout)

### 1. MFRC522 to Arduino Uno / Nano

| MFRC522 Pin | Arduino Uno / Nano Pin | Function |
| :--- | :--- | :--- |
| **VCC** | 3.3V *(Note: Do NOT use 5V)* | Power |
| **RST** | Pin 9 | Reset |
| **GND** | GND | Ground |
| **MISO** | Pin 12 | SPI MISO |
| **MOSI** | Pin 11 | SPI MOSI |
| **SCK** | Pin 13 | SPI Clock |
| **SDA (SS)** | Pin 10 | SPI Chip Select |

### 2. LCD 16x2 (I2C) Connections

| LCD I2C Pin | Arduino Uno / Nano Pin |
| :--- | :--- |
| **GND** | GND |
| **VCC** | 5V |
| **SDA** | A4 |
| **SCL** | A5 |

### 3. Buzzer Connections

| Buzzer Pin | Arduino Pin |
| :--- | :--- |
| **Positive (+)** | Pin 7 |
| **Negative (-)** | GND |

## 📚 Required Libraries

Before compiling the code, install the following libraries in Arduino IDE (**Tools** -> **Manage Libraries...**):

1. **MFRC522** *(by Miguel Balboa)*
2. **LiquidCrystal_I2C** *(by Frank de Brabander)*
3. **SPI** and **Wire** *(Included built-in with Arduino IDE)*

## 🚀 Setup & Usage Instructions

1. **Wiring:** Connect all hardware components according to the pinout table above.
2. **Upload Code:**
   * Open **Arduino IDE**.
   * Create a new sketch and paste the project code into it.
   * Select your Board and COM Port under `Tools`.
   * Click **Upload**.
3. **Run the Project:**
   * Open **Serial Monitor** (Ctrl + Shift + M) set to **9600 baud rate**.
   * Swipe an RFID card or key fob over the MFRC522 reader.
   * Check the LCD screen and Serial Monitor for access output.

## ⚙️ Changing Valid RFID Tag

To authorize a different tag, update the `theCTyC` array in the code with the 4 HEX bytes of your new tag:

```cpp
// Update these 4 HEX bytes to match your authorized card's UID
int theCTyC[4] = {0x4C, 0x16, 0x27, 0x07};
```

## 📄 License

This project is built upon the public domain MFRC522 library example. Feel free to modify and use it for learning or personal projects.
