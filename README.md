# Eng-2021-PBL-ML
#長押しのときと短押しのときの検知を変化させる
#長押しのときの周波数は1000Hz、短押しのときの周波数は400Hz

#モジュールの設定
import RPi.GPIO as GPIO　
from time import sleep 

#ピンと音、スイッチの設定
SOUND_PORT = 18 
SWITCH_PORT = 21 
TONE = 1000

GPIO.setmode(GPIO.BCM)
GPIO.setup(SWITCH_PORT, GPIO.IN, pull_up_down=GPIO.PUD_DOWN)
GPIO.setup(SOUND_PORT, GPIO.OUT) 

pwm = GPIO.PWM(SOUND_PORT, TONE)
sw_counter = 0

#長押し、短押しの設定
while True: 
　 GPIO.wait_for_edge(SWITCH_PORT, GPIO.FALLING)
   sw_status = GPIO.input(SWITCH_PORT)
   if sw_status = 0
       pwm.ChangeFrequency(TONE)
       pwm.start(50) 
       print ("test")
       if sw_status == 0:
          sw_counter = sw_counter + 1
          if sw_counter >= 50
              pwm.ChangeFrequency(TONE)
              pwm.start(50) 
              print("長押し検知")
              sw_counter = 0
              break
        else:
            pwm.ChangeFrequency(400)
            pwm.start(50) 
            print("短押し検知")
            break
GPIO.cleanup()
