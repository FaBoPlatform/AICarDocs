# 車体のプロジェクト作成

## 車体のプロジェクトの作成

```
donkey createcar --path ~/mycar
```

```
________             ______                   _________              
___  __ \_______________  /___________  __    __  ____/_____ ________
__  / / /  __ \_  __ \_  //_/  _ \_  / / /    _  /    _  __ `/_  ___/
_  /_/ // /_/ /  / / /  ,<  /  __/  /_/ /     / /___  / /_/ /_  /    
/_____/ \____//_/ /_//_/|_| \___/_\__, /      \____/  \__,_/ /_/     
                                 /____/                              

using donkey v5.1.0 ...
Creating car folder: /home/pi/mycar
making dir  /home/pi/mycar
Creating data & model folders.
making dir  /home/pi/mycar/models
making dir  /home/pi/mycar/data
making dir  /home/pi/mycar/logs
Copying car application template: complete
Copying car config defaults. Adjust these before starting your car.
Copying train script. Adjust these before starting your car.
Copying calibrate script. Adjust these before starting your car.
Copying my car config overrides
Donkey setup complete.
```

## キャリブレーション

前後

```
donkey calibrate --channel 0 --bus 1
```

左右

```
donkey calibrate --channel 1 --bus 1
```


## configの設定

~/mycar/myconfig.pyの下記パートのコメントを削除して、値を反映させます


```python hl_lines="7-8"
# #CAMERA
# CAMERA_TYPE = "PICAM"   # (PICAM|WEBCAM|CVCAM|CSIC|V4L|D435|MOCK|IMAGE_LIST)
# IMAGE_W = 160
# IMAGE_H = 120
# IMAGE_DEPTH = 3         # default RGB=3, make 1 for mono
# CAMERA_FRAMERATE = DRIVE_LOOP_HZ
CAMERA_VFLIP = True
CAMERA_HFLIP = True
# CAMERA_INDEX = 0  # used for 'WEBCAM' and 'CVCAM' when there is more than one camera connected
```

```python hl_lines="8-12"
PWM_STEERING_THROTTLE = {
     "PWM_STEERING_PIN": "PCA9685.1:40.1",   # PWM output pin for steering servo
     "PWM_STEERING_SCALE": 1.0,              # used to compensate for PWM frequency differents from 60hz; NOT for adjusting steering range
     "PWM_STEERING_INVERTED": False,         # True if hardware requires an inverted PWM pulse
     "PWM_THROTTLE_PIN": "PCA9685.1:40.0",   # PWM output pin for ESC
     "PWM_THROTTLE_SCALE": 1.0,              # used to compensate for PWM frequence differences from 60hz; NOT for increasing/limiting speed
     "PWM_THROTTLE_INVERTED": False,         # True if hardware requires an inverted PWM pulse
     "STEERING_LEFT_PWM": 320,               #pwm value for full left steering
     "STEERING_RIGHT_PWM": 500,              #pwm value for full right steering
     "THROTTLE_FORWARD_PWM": 500,            #pwm value for max forward throttle
     "THROTTLE_STOPPED_PWM": 440,            #pwm value for no movement
     "THROTTLE_REVERSE_PWM": 220,            #pwm value for max reverse throttle
}
```

```python hl_lines="2 6"
# JOYSTICK
USE_JOYSTICK_AS_DEFAULT = True      #when starting the manage.py, when True, will not require a --js option to use the joystick
# JOYSTICK_MAX_THROTTLE = 0.5         #this scalar is multiplied with the -1 to 1 throttle value to limit the maximum throttle. This can help if you drop the controller or just don't need the full speed available.
# JOYSTICK_STEERING_SCALE = 1.0       #some people want a steering that is less sensitve. This scalar is multiplied with the steering -1 to 1. It can be negative to reverse dir.
# AUTO_RECORD_ON_THROTTLE = True      #if true, we will record whenever throttle is not zero. if false, you must manually toggle recording with some other trigger. Usually circle button on joystick.
CONTROLLER_TYPE = 'F710'            #(ps3|ps4|xbox|pigpio_rc|nimbus|wiiu|F710|rc3|MM1|custom) custom will run the my_joystick.py controller written by the `donkey createjs` command
# USE_NETWORKED_JS = False            #should we listen for remote joystick control over the network?
# NETWORK_JS_SERVER_IP = None         #when listening for network joystick control, which ip is serving this information
# JOYSTICK_DEADZONE = 0.01            # when non zero, this is the smallest throttle before recording triggered.
# JOYSTICK_THROTTLE_DIR = -1.0         # use -1.0 to flip forward/backward, use 1.0 to use joystick's natural forward/backward
# USE_FPV = False                     # send camera data to FPV webserver
# JOYSTICK_DEVICE_FILE = "/dev/input/js0" # this is the unix file use to access the joystick.
```

!!! info
    キャリブレーション(前後)<br>
    donkey calibrate --channel 0 --bus 1<br>
    <br>
    キャリブレーション(左右)<br>
    donkey calibrate --channel 1 --bus 1<br>
    <br>
    手動走行
    <br>
    cd ~/mycar/
    python manage.py drive<br>