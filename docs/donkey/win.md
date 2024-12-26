# Windows

DonkeyCar Version 5.2.dev2のWindows11(WSL)での構築方法です。

!!! Warning
	Windows Powershellでも構築できますが、Powershell上でのホスト名による検索ができずに、DonkeyUIの全機能がつかえません(2024年12月現在)。

## WSLでUbuntu-22.04

WSLでUbuntuを起動

```python
wsl --install Ubuntu-22.04 
```

WSLで起動中のUbuntu-22.04をDonkeyCarという名前でバックアップBackup

```
mkdir C:\WSL_Backups
wsl --export Ubuntu-22.04 C:\WSL_Backups\Ubuntu2204_backup.tar
wsl --list --verbose
```

DonekyCarをimport

```
wsl --import DonkeyCar F:\aicar\wsl C:\WSL_Backups\Ubuntu2204_backup.tar --version 2
```


```
wsl --list --verbose
  NAME                   STATE           VERSION
  DonkeyCar              Stopped         2
```

これで、DonkeyCar用のUbuntu 22.04が作成できたので、起動します。

```
wsl -d DonkeyCar -u donkey
```

## miniconda環境の構築

```
cd
wget https://repo.anaconda.com/miniconda/Miniconda3-py311_24.4.0-0-Linux-x86_64.sh
bash ./Miniconda3-py311_24.4.0-0-Linux-x86_64.sh
source ~/.bashrc
```

## DonkeyCar環境の構築

DonkeyCar Version 5.2.dev2を構築します。

```
conda create -n donkey520 python=3.11
conda activate donkey520
```

```
git clone https://github.com/autorope/donkeycar
cd donkeycar
git checkout 5483490
pip install -e .\[pc\]
```

!!!info 
  現在、DonkeyCar Ver 5.1.0ではうまく動かないようなので、最新の5.2.Dev2を使用します。

## mDNSの構築

```
sudo apt update
sudo apt install avahi-daemon avahi-utils
```

```
sudo systemctl start avahi-daemon
sudo systemctl enable avahi-daemon
```

## DonkeyUIの起動

```
export DISPLAY=:0
```

```
donkey ui
```