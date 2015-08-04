# Arduino-controlled-SI5351-frequency-synthesiser
Circuit diagram and *.ino source code for an Arduino controlled SI5351 digital frequency synthesiser. 

The code for this project was inspired by an article by gerryk.com [1].

Three library files are required:
Wire.h
si5351.h (download from https://github.com/etherkit/Si5351Arduino)
LiquidCrystal_I2C.h (download from http://arduino-info.wikispaces.com/LCD-Blue-I2C#v1)
  
My code differs from that of gerryk.com as follows:
1: Rotary encoders output 4 gray code patterns between each click. Instead of counting these patterns and
dividing by 4, I count the indents (both encoder outputs are high) and use the gray code patterns to 
determine the direction of rotation. This method seems to cope with missed patterns when you spin the dial.

2: I use integration to debounce the switches

3: Bandchanging has been added

The code, as presented, generates a signal on a specific frequency. If you want an offset simply modify the 
Main Loop to read:

clockgen.set_freq((frequency + offset), SI5351_PLL_FIXED, SI5351_CLK0); // where "offset" has been defined in Hz.

Bibliography:
[1] Signal generator using Adafruit clock generator. (http://github.com/gerryk/signal_generator)
