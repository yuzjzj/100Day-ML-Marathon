# 環境架設(Windows10_x64) 
## 系統設定

Git或Github的軟體安裝基本就是下一步到結尾即可。
Nvidia驅動也直接在官網下載。
Cuda
DNN(需至nvidia官網辦理帳號)

## Miniconda
### 安裝

安裝時記得勾選系統路徑

### 設定

找到你安裝Miniconda的路徑並修改環境與套件資料夾
conda config --prepend envs_dirs C:\ProgramData\Miniconda3\envs
conda config --prepend pkgs_dirs C:\ProgramData\Miniconda3\pkgs

更新conda
conda update conda

建立環境100D
conda env create -n 100D -f Py36env-GPU.yml
conda create -n 100D

進入環境100D
activate 100D

察看環境
conda info -e

察看環境套件
conda list
