# PCとDonkeyCarの接続

## PCとDonkeyCarをSSHでPasswordなしで接続

PCの公開鍵をDonkeyCar(Pi)にコピーします。

公開鍵を作成していない場合は作成します。

```
ssh-keygen
```

```
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/#####/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /Users/######/.ssh/id_rsa
Your public key has been saved in /Users/#####/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:/########################## #######@AkiranoMacBook-Pro-2.local
```

公開鍵をDonkeyCarにコピーします。

```
ssh-copy-id -i ~/.ssh/id_rsa.pub pi@donkeypi.local
```

以後は、下記コマンドでPasswordなしで接続できるようになります。

```
ssh pi@donkeypi.local
```

```
Linux donkeypi 6.6.62+rpt-rpi-v8 #1 SMP PREEMPT Debian 1:6.6.62-1+rpt1 (2024-11-25) aarch64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Sat Dec 14 17:22:27 2024 from 2400:4050:###:####:####:####:5ec2:7924

SSH is enabled and the default password for the 'pi' user has not been changed.
This is a security risk - please login as the 'pi' user and type 'passwd' to set a new password.
```

!!!Info
	DonkeyUIを使う上で、上記のようにPasswordなしで、Host名だけでDonkeyCarに接続できるようにする必要があります。

