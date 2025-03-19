# Digital-Clock-RTC
# Digital Clock with Real-Time Display ⏰  
An **Arduino-powered digital clock** using the **DS3231 Real-Time Clock (RTC) module** and a **7-segment display** for timekeeping.

## 📌 Features
✅ Displays real-time hours, minutes, and seconds  
✅ Uses RTC for accurate timekeeping  
✅ Backup battery ensures clock runs even without power  

## 🛠️ Hardware Used
- Arduino Uno  
- DS3231 RTC Module  
- 7-Segment Display  
- Push Buttons for Time Adjustment  

## 📝 Code Example
```cpp
#include <Wire.h>
#include <RTClib.h>

RTC_DS3231 rtc;

void setup() {
    Serial.begin(9600);
    if (!rtc.begin()) {
        Serial.println("RTC not found!");
        while (1);
    }
    rtc.adjust(DateTime(F(__DATE__), F(__TIME__)));  // Set RTC time to compile time
}

void loop() {
    DateTime now = rtc.now();
    Serial.print("Time: ");
    Serial.print(now.hour());
    Serial.print(":");
    Serial.print(now.minute());
    Serial.print(":");
    Serial.println(now.second());
    delay(1000);
}
