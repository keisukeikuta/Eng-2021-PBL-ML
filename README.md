# Eng-2021-PBL-ML
#長押しのときと短押しのときの検知を変化させる

#モジュールの設定
import RPi.GPIO as GPIO　
from time import sleep 

#ピンと音、スイッチの設定
SOUND_PORT = 18 
SWITCH_PORT = 21 

GPIO.setmode(GPIO.BCM)
GPIO.setup(SWITCH_PORT, GPIO.IN, pull_up_down=GPIO.PUD_DOWN)
GPIO.setup(SOUND_PORT, GPIO.OUT) 

pwm = GPIO.PWM(SOUND_PORT, 200)

#長押し、短押しの設定
while True: 
　 GPIO.wait_for_edge(SWITCH_PORT, GPIO.FALLING)
  
  sw_counter = 0
  
  while True:
        sw_status = GPIO.input(SWITCH_PORT)
        if GPIO.input(SWITCH_PORT) == GPIO.HIGH: 
        if sw_status == 0:
            sw_counter = sw_counter + 1
            
             pwm.ChangeFrequency(200)
            pwm.start(50) 
        else: print("OFF")
            pwm.stop() 
            time.sleep(0.1) 
    except KeyboardInterrupt: 
        break 
GPIO.cleanup()
