# LCD Interfacing with Arduino

A project demonstrating how to interface a 16x2 LCD display with an Arduino Uno, displaying a scrolling "Hello, World!" message followed by a live seconds counter. Built and simulated in [Tinkercad Circuits](https://www.tinkercad.com/).

---

## 📸 Circuit Photo

<!-- Replace with your actual screenshot from Tinkercad -->
![Circuit Screenshot](https://github.com/user-attachments/assets/a7efd692-c7b9-436a-a85f-4787a67c0a48
)



## 🔧 Components Used

| Component         | Quantity |
|------------------|----------|
| Arduino Uno       | 1        |
| 16x2 LCD Display (LiquidCrystal) | 1 |
| 220Ω Resistor (backlight) | 1 |
| Breadboard        | 1        |
| Jumper Wires      | Several  |

---

## 🔌 Pin Connections

| LCD Pin | Function | Arduino Pin |
|---------|----------|-------------|
| RS      | Register Select | D12 |
| EN      | Enable   | D11         |
| D4      | Data     | D5          |
| D5      | Data     | D4          |
| D6      | Data     | D3          |
| D7      | Data     | D2          |
| VSS     | Ground   | GND         |
| VDD     | 5V       | 5V          |
| VO      | Contrast | GND (via potentiometer/resistor) |
| RW      | Read/Write | GND       |
| A (LED+) | Backlight | 5V (via 220Ω resistor) |
| K (LED−) | Backlight GND | GND |


## 💻 Code

```cpp
#include <LiquidCrystal.h>

// Initialize the library with the numbers of the interface pins
const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);

void setup() {
  // Set up the LCD's number of columns and rows
  lcd.begin(16, 2);
  // Print a message to the LCD
  lcd.print("Hello, World!");
  delay(1000);

  // Scroll the content to the right
  for (int positionCounter = 0; positionCounter < 16; positionCounter++) {
    // Scroll one position right
    lcd.scrollDisplayRight();
    // Wait a bit
    delay(150);
  }

  // Clear the screen
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("Count:");
}

void loop() {
  lcd.setCursor(6, 0);
  // Print the number of seconds since reset
  lcd.print(millis() / 1000);
}
```

---

## 🚀 How It Works

1. On startup, the LCD displays **"Hello, World!"**
2. The message scrolls to the right, one position at a time
3. The screen clears and shows **"Count:"** followed by a live seconds counter (based on `millis()`)

---

## ▶️ How to Run

1. Open the [Tinkercad project](https://www.tinkercad.com/) *(replace with your share link)*
2. Click **Start Simulation**
3. Watch the greeting scroll, then observe the live counter

Or upload the code to a real Arduino:
1. Open `led_interfacing1.ino` in the [Arduino IDE](https://www.arduino.cc/en/software)
2. Select **Board:** Arduino Uno and the correct **Port**
3. Click **Upload**

---

## 📁 Project Structure

```
├── led_interfacing1.ino   # Arduino source code
├── assets/
│   └── circuit.png        # Tinkercad circuit screenshot
└── README.md
```

