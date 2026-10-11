# RGB LED

This is rather easy to program. For simplicity, just copy this Python code - its Micropython after all.

```py
from abutton import *
from yolo_uno import *

btn_BOOT= aButton(BOOT_PIN)

def deinit():
  btn_BOOT.deinit()

import yolo_uno
yolo_uno.deinit = deinit

async def setup():

  print('App started')
  while not btn_BOOT():
    neopix.show(0, hex_to_rgb('#ff0000'))
    await asleep_ms(100)
    neopix.show(0, hex_to_rgb('#ffa500'))
    await asleep_ms(100)
    neopix.show(0, hex_to_rgb('#ffff00'))
    await asleep_ms(100)
    neopix.show(0, hex_to_rgb('#00ff00'))
    await asleep_ms(100)
    neopix.show(0, hex_to_rgb('#0000ff'))
    await asleep_ms(100)
    neopix.show(0, hex_to_rgb('#4b0082'))
    await asleep_ms(100)
    neopix.show(0, hex_to_rgb('#800080'))
    await asleep_ms(100)

async def main():
  await setup()
  while True:
    await asleep_ms(100)

run_loop(main())
```
