📘smartDelay() – Bitwave

⚙️ What is it?
An Arduino/ESP32 function that acts like delay, but doesn't block the rest of your code.

❌ Why avoid delay()?
It blocks the entire microcontroller

No input or sensor reading during the wait

No multitasking possible

✅ Why use smartDelay()?
Keeps your program active while waiting

You can read sensors, handle buttons, update displays

Works like delay() in timing but without freezing everything

🧠 How does it work?
It uses millis() to measure elapsed time without blocking:

cpp
Copia
Modifica
void smartDelay(float seconds) {
  unsigned long duration = (unsigned long)(seconds * 1000);
  unsigned long start = millis();

  while (millis() - start < duration) {
    // Do things here without blocking (input, output, etc.)
  }
}
💡 Example usage:
cpp
Copia
Modifica
void loop() {
  digitalWrite(LED_BUILTIN, HIGH);
  smartDelay(1.0); // wait 1 second without blocking

  digitalWrite(LED_BUILTIN, LOW);
  smartDelay(1.0);
}
📌 Note
Don’t use delay() inside smartDelay() — it would defeat the non-blocking purpose.

🔧 Made with care by Bitwave
Follow us for more snippets and tips: @bitwave.tech
