# jamo-9
9 Key Macropad with rotary encoder

## Specs

MCU: WCH CH552G

## Pinout

```
+-------+-------+-------+
|       |       |       |
|   1   |   2   |   3   | Key number
|  3.0  |  3.1  |  1.7  | Pin number
+-------+-------+-------+
|       |       |       |
|   4   |   5   |   6   |
|  1.5  |  1.4  |  3.2  |
+-------+-------+-------+

ENC A: 3.4
ENC B: 3.3
ENC PUSH: 1.1
```

## Setting up for use with Arduino IDE



## Quick example

```c
#ifndef USER_USB_RAM
#error "Require USB RAM. Go Tools > USB Setting and pick the 2nd option in the dropdown list"
#endif

#include "src/userUsbHidMediaKeyboard/USBHIDMediaKeyboard.h"

#define KEY_1 30 // Pin 3.0 -> 30 etc

bool key1ActiveState = false;
bool key1Active = false;

void setup() {
  // put your setup code here, to run once:
  USBInit();
}

void loop() {
  // Simple example to use button 1 as a play/pause button.
  // put your main code here, to run repeatedly:

  key1Active = !digitalRead(KEY_1);

  if (key1ActiveState != key1Active){
      key1ActiveState = key1Active;
      if (key1Active){
        Consumer_press(MEDIA_PLAY_PAUSE);
      }else{
        Consumer_release(MEDIA_PLAY_PAUSE);
      }
    }


  delay(50);

}

```


## References

https://github.com/tobychui/4xMacropad | Some inspiration, `userUsbHidMediaKeyboard` folder is required from this project.
