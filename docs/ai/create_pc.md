# PCのプロジェクト作成

## PCのプロジェクト作成

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
Creating car folder: /Users/####/mycar
making dir  /Users/####/mycar
Creating data & model folders.
making dir  /Users/####/mycar/models
making dir  /Users/####/mycar/data
making dir  /Users/####mycar/logs
Copying car application template: complete
Copying car config defaults. Adjust these before starting your car.
Copying train script. Adjust these before starting your car.
Copying calibrate script. Adjust these before starting your car.
Copying my car config overrides
Donkey setup complete.
```

## config.py

~/mycar/config.py にConfigファイルが生成されます。

config.pyに、DonkeyCar接続用のID, Passwordが設定されています。


```python
# PI connection
PI_USERNAME = "pi"
PI_HOSTNAME = "donkeypi.local"
```
