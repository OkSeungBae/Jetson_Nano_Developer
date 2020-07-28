Jetson_Nano_Class 20200728
==========================

## Jetson Nano

1. python으로 LED불 켜기

```
#!/usr/bin/env python
import RPi.GPIO as GPIO
import time

#pin definition
output_pin = 18 #board에서는  번 BCM에서는 18번

def main():
    #pin setup: 
    #Board pin-numbering scheme
    GPIO.setmode(GPIO.BCM)

    #set pin as an output pin with optional inital state of HIGI
    GPIO.setup(output_pin, GPIO.OUT, initial=GPIO.HIGH)

    print("Starting demo now! Press CTRL+C to exit")
    curr_value = GPIO.HIGH
    try :
        while True:
            time.sleep(1)

            # Toggle the output every second
            print("outputting {} to pin {}".format(curr_value, output_pin))
            GPIO.output(output_pin, curr_value)
            curr_value ^= GPIO.HIGH
    finally :
        GPIO.cleanup()
if __name__ == '__main__':
    main()
```

2. button으로 LED불 켜기

```
#!/usr/bin/env python
import RPi.GPIO as GPIO
import time

#Pin definitions
led_pin = 12 # board pin 12
put_pin = 18 # borad pin 18

def main():
    prev_value = None

    #pin setup
    GPIO.setmode(GPIO.BOARD)
    GPIO.setup(led_pin, GPIO.OUT)
    GPIO.setup(but_pin, GPIO.IN)

    #inital state for LEDs
    GPIO.output(led_pin, GPIO.LOW)
    print("starting demo now! press CTRL+C to exit)
    try :
        while True:
            curr_value = GPIO.input(but_pin)
            if curr_value != prev_value:
                GPIO.output(led_pin, not curr_value)
                prev_value = curr_value
                print("outputting {} to pin {}".format(curr_value, led_pin))
            time.sleep(1)
    finally :
        GPIO.cleanup()
if __name__ == '__main__' :
    main()
```

* GPIO.setmode에 따라 핀 번호의 초기화가 달라진다

```
GPIO.setmode(GPIO.BOARD)
```
를 사용한다면 보드에 적힌 번호대로 pin번호를 설정한다

```
GPIO.setmode(GPIO.BCM)
```
을 사용한다면 보드 BCM대로 pin번호를 설정해야 한다.

3. button으로 LED불 켜기2

```
#!/usr/bin/env python
import RPi.GPIO as GPIO
ipmort time

# pin Definitions
led_pin = 12 # Board pin 12
but_pin = 18 # board pin 18

def main():
    #pin setup:
    GPIO.setmode(GPIO.BOARD)
    GPIO.setup(led_pin, GPIO.OUT)
    GPIO.setup(but_pin, GPIO.IN)

    #inital state for LEDs:
    GPIO.output("Starting demo now! press CTRL+C to exit")

    try :
        while True:
            print("Waiting for button event")
            GPIO.wait_for_edge(but_pin, GPIO.FALLING)

            #evnt received when button pressed
            print("Button pressed")
            GPIO.output(led_pin, GPIO.HIGH)
            time.sleep(1)
            GPIO.output(led_pin, GPIO.LOW)
    finally :
        GPIO.cleanup()

if __name__ == '__main__':
    main()
```