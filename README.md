# 100Day-ML-Marathon

## 環境架設(Windows 10)

...
## 環境架設(Linux_x64)

### 系統設定

#### 將home資料夾英文化(方便使用cd切換)

`LANG=C xdg-user-dirs-gtk-update`

#### 更改開機grub等待時間

`sudo nano /etc/default/grub`

`sudo update-grub`

`nvidia` `docker` `nvidia-docker`
### nvidia

移除舊版後安新版，如果linux為桌面板且顯示卡沒有照成linux當機的問題(顯示卡過新)，建議手動安裝

原先做法：
```sh
sudo apt-get remove --purge nvidia*
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update

#nvidia-{version}
sudo apt-get install -y nvidia-driver-418
```
待測試：
```sh
ubuntu-drivers devices
sudo ubuntu-drivers autoinstall
```
重開機後驗證：
```sh
# reboot your system
sudo reboot

# check install
nvidia-smi
```

### docker
#### [install](https://docs.docker.com/install/)
```sh
#install docker https://docs.docker.com/install/
sudo apt-get install -y apt-transport-https ca-certificates curl gnupg-agent software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
sudo add-apt-repository    "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io

# check install
sudo docker run --rm hello-world
```
#### 改docker權限
```sh
sudo groupadd docker
sudo gpasswd -a $USER docker
```
#### 備忘
```sh
#images list
sudo docker images

#container list
sudo docker container ls -a
sudo docker ps -a

#remove images
sudo docker rmi
#remove container
sudo docker container rm
#remove all stop container
docker container prune
```

### [nvidia-docker](https://github.com/NVIDIA/nvidia-docker)

latest-gpu-py3-jupyter




#user file name set
LANG=C xdg-user-dirs-gtk-update

#start up delay time set
sudo nano /etc/default/grub

sudo update-grub

#two system time sync
timedatectl set-local-rtc 1 --adjust-system-clock


#nvidia driver
sudo apt-get remove --purge nvidia*
sudo add-apt-repository ppa:graphics-drivers/ppa

sudo apt-get update
#nvidia-{version}
sudo apt-get install -y nvidia-driver-418
sudo reboot
nvidia-smi


#java
sudo apt-get install -y default-jre

#taiwanese input
sudo apt-get install -y gcin

#mouse key set
#xev
sudo apt-get install -y xbindkeys xbindkeys-config xautomation

xbindkeys-config
#b:9    xte 'key Page_Up'
#b:8    xte 'key Page_Down'



sudo apt-get upgrade
sudo apt autoremove
