#DIY HERO Bus Projects

###Wired remote:

Wire the HERO pin 12 to a pushbutton, and HERO pin 30 also. Hold the pushbutton 3 seconds to turn the camera on: this can be combined with [autoexechack](http://github.com/konradit/autoexechack) so the gopro does things when is turned on
***
###Intervalometer

Wire the HERO pin 12 to a pin GND of an arduino and wire HERO pin 30 to pin 14 of the same arduino.

####Code: 

GoPro Autoexec.ash:

HERO3 Black/ +Black/ +Silver:
```
t app appmode photo
t app button shutter PR
poweroff yes / t app button power P sleep 3 t app button power R

poweroff yes is for HERO3+ cameras
t app button power P sleep 3 t app button power R is for HERO3 Black
```

Arduino:
```c
void setup() {
pinMode(14, OUTPUT);
}

void loop() {
digitalWrite(14, HIGH);
delay(3000);
digitalWrite(14, LOW);
delay(X6); // X is the time of the interval, plus 6 that is the time the gopro takes to take a picture and turn off.
```
