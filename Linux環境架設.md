# 環境架設(Linux_x64)
系統設定與`nvidia driver`、`docker`、`nvidia-docker`的安裝。

## 系統設定
   ### 將home資料夾英文化(方便使用cd切換)
`LANG=C xdg-user-dirs-gtk-update`
   ### 更改開機grub等待時間
`sudo nano /etc/default/grub`

      將下列GRUB_TIMEOUT改成你所希望的秒數，Ctrl+S後Ctrl+X離開。
```sh
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
```
      重新生成 /boot/grub/grub.cfg

`sudo update-grub`

### 雙系統時間同步：
`timedatectl set-local-rtc 1 --adjust-system-clock`

### Java安裝：

`sudo apt-get install -y default-jre`

### 中文輸入法：

`sudo apt-get install -y gcin`

### 更新與刪除軟體：
`sudo apt-get upgrade`
`sudo apt autoremove`



## nvidia driver

   移除舊版後安新版，如果linux為桌面板且顯示卡沒有照成linux當機的問題(顯示卡過新)，建議手動安裝。

`sudo apt-get remove --purge nvidia*`

原先安裝法：
```sh
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update

#nvidia-{version}
sudo apt-get install -y nvidia-driver-418
```
待測安裝法：
```sh
ubuntu-drivers devices
sudo ubuntu-drivers autoinstall
```

重開機後驗證：
```sh
sudo reboot

nvidia-smi
```

## docker
### [install](https://docs.docker.com/install/)：
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
### 改docker權限
```sh
sudo groupadd docker
sudo gpasswd -a $USER docker
```
### 備忘
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

## [nvidia-docker](https://github.com/NVIDIA/nvidia-docker)：
```sh
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | \
  sudo apt-key add -
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | \
  sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt-get update

sudo apt-get install -y nvidia-docker2
sudo pkill -SIGHUP dockerd
```
