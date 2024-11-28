#include <IRremoteESP8266.h>
#include <IRsend.h>

const uint16_t ir_led_pin = 14;  // IR LED connected to GPIO 4
IRsend irsend(ir_led_pin);

void setup() {
  Serial.begin(115200);
  irsend.begin();
  Serial.println("IR Transmitter Ready!");
}

void loop() {
  // Send a signal (e.g., 0xFFA25D) that the receiver ESP32 will understand
  Serial.println("Sending IR Signal...");
  //irsend.sendNEC(0x, 32);  // Example signal for "ON"
  //delay(1000);  // Wait for 1 second
  irsend.sendNEC(0xFD021010006314, 32);  // Example signal for "OFF"
  delay(1000);  // Wait for 1 second
}
