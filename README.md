# Eng-2021-PBL-ML
#長押しのときと短押しのときの検知を変化させる

#モジュールの設定
import RPi.GPIO as GPIO　
from time import sleep 

#ピンと音、スイッチの設定
SOUND_PORT = 18 
SWITCH_PORT = 21 
TONE = 200 


GPIO.setmode(GPIO.BCM)
GPIO.setup(SWITCH_PORT, GPIO.IN, pull_up_down=GPIO.PUD_DOWN)
GPIO.setup(SOUND_PORT, GPIO.OUT) 

pwm = GPIO.PWM(SOUND_PORT, TONE)

while True: 
    try: 
        if GPIO.input(SWITCH_PORT) == GPIO.HIGH: 
            print("ON")
             pwm.ChangeFrequency(TONE)
            pwm.start(50) 
        else: print("OFF")
            pwm.stop() 
            sleep(0.1) 
    except KeyboardInterrupt: 
        break 
GPIO.cleanup()
