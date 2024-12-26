# SDカードイメージの作成


## SDカードからイメージを抜き出し

```
fdisk -l
```

if=のあとには、識別デバイスをいれる

```
sudo dd bs=4M if=/dev/sde of=~/donkeypi.img conv=fsync status=progress
```

## PSHRINK

pshrink.shで未使用領域を圧縮

```
sudo bash pshrink.sh ~/donkeypi.img
```

## ZIP

zipで圧縮

```
zip -r ~/donkeypi.zip ~/donkeypi.img
```

