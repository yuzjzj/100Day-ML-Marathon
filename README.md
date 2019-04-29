# 100Day-ML-Marathon
## 環境架設 & 套件安裝
使用Docker做環境管理
[Linux_x64](https://github.com/yuzjzj/100Day-ML-Marathon/blob/master/envs/%E7%92%B0%E5%A2%83%E6%9E%B6%E8%A8%ADLinux.md)

Windows：
[Docker(Hyper-V)](https://docs.docker.com/docker-for-windows/install/)
[Docker(VirtualBox)](https://docs.docker.com/toolbox/overview/)

因家用版無Hyper-V功能無法使用Docker，所以使用Miniconda做環境管理


## 資料同步(Git設定)
### 初始設定
```sh
git config --global user.name "你的名字 中間有空格記得加雙引號"
git config --global user.email "你的E-mail"
```

cd /windows/workspace/100Day-ML-Marathon/

....


檔案(下載)：

`git pull`

檔案推送(上傳)：
```sh
git add Day_001_HW.ipynb
git commit -m "Day001上傳"
git push
```
資料比對：
```sh
git diff
git status
```
#gihub SSH
SSH:
git@github.com:yuzjzj/100Day-ML-Marathon.git



### 建一個新的存儲庫
echo“#test”>> README.md 
git init 
git add README.md 
git commit -m“first commit” 
git remote add origin https://github.com/yuzjzj/100Day-ML-Marathon.git
git push -u origin master
### 推送現有存儲庫
git remote add origin https://github.com/yuzjzj/100Day-ML-Marathon.git
git push -u origin master

