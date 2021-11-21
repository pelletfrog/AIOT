# 作業

## 作業1

* 使用 raspi-config 更改 root 的密碼，設定連線的無線基地台，開啟 ssh 伺服器，確定可以用遠端連線進入 pi。
* Ans: 

```
Laide-MBP:~ lai$ ssh pi@192.168.50.195
pi@192.168.50.195's password: 
Linux raspberrypi 5.10.17-v7l+ #1414 SMP Fri Apr 30 13:20:47 BST 2021 armv7l

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Sun Nov 21 21:38:04 2021 from 192.168.50.218

SSH is enabled and the default password for the 'pi' user has not been changed.
This is a security risk - please login as the 'pi' user and type 'passwd' to set a new password.

pi@raspberrypi:~ $ 
```

## 作業2

* 切換至 /opt 路徑，建立一個 /opt/aiot 子目錄，切換至 /opt/aiot 子目錄，用 wget 指令下載一個網路上的檔案，下載完成後用 ls –al 指令，確定下載的檔案存在。
* Ans: 

```
pi@raspberrypi:/ $ cd /opt
pi@raspberrypi:/opt $ sudo mkdir aiot
pi@raspberrypi:/opt $ cd aiot
pi@raspberrypi:/opt/aiot $ sudo wget http://ftp.gnu.org/gnu/wget/wget-1.19.tar.gz
--2021-11-21 21:44:09--  http://ftp.gnu.org/gnu/wget/wget-1.19.tar.gz
Resolving ftp.gnu.org (ftp.gnu.org)... 209.51.188.20, 2001:470:142:3::b
Connecting to ftp.gnu.org (ftp.gnu.org)|209.51.188.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4202290 (4.0M) [application/x-gzip]
Saving to: ‘wget-1.19.tar.gz’

wget-1.19.tar.gz    100%[===================>]   4.01M  1.36MB/s    in 2.9s    

2021-11-21 21:44:12 (1.36 MB/s) - ‘wget-1.19.tar.gz’ saved [4202290/4202290]

pi@raspberrypi:/opt/aiot $ ls -al
total 4112
drwxr-xr-x 2 root root    4096 Nov 21 21:44 .
drwxr-xr-x 5 root root    4096 Nov 21 21:41 ..
-rw-r--r-- 1 root root 4202290 Feb  3  2017 wget-1.19.tar.gz
pi@raspberrypi:/opt/aiot $ 
```


## 作業3

* 切換至/根目錄(指令: cd /)，壓縮 /opt 子目錄進行備份，使用 tar zcvf opt.tar.gz /opt，以及 bzip2 opt.tar.gz 壓縮成 bz2 格式，最後將 opt.tar.gz 用 tar zxvf opt.tar.gz 指令練習解壓，或者將 opt.tar.gz 解壓至 /tmp 之下，確定 /opt 子目錄有壓縮備份成功 。
* Ans: 

```
# 壓縮 gz
pi@raspberrypi:/ $ sudo tar zcvf opt.tar.gz /opt

# 壓縮成 bz2 格式
pi@raspberrypi:/ $ sudo bzip2 opt.tar.gz

# 解壓縮
pi@raspberrypi:/ $ sudo bzip2 -d opt.tar.gz.bz2

# 解壓縮至 /tmp 資料夾
sudo tar zxvf opt.tar.gz -C /tmp

# 至 /tmp 位置可看到 opt 資料夾
pi@raspberrypi:/ $ cd /tmp
pi@raspberrypi:/tmp $ ls
dhcpcd-pi
opt
pulse-PKdhtXMmr18n
ssh-RYmwvHcwoE9S
ssh-XIF3QPyTOgF1
systemd-private-a7cb4b2ce47141fba864aa649f483534-rtkit-daemon.service-HxUKoA
systemd-private-a7cb4b2ce47141fba864aa649f483534-systemd-timesyncd.service-SG0UqT
```