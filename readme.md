此仓库主要介绍一个如何在Termux上手动编译box64的方案
<br>
下面开始介绍步骤：
## 操作步骤
一，下载Termux并安装，Termux可从Google Play商店或termux-app的GitHub项目中的发行版下载最新版本
<br>
二，打开Termux，赋予通知权限，输入并执行：
<br>
“termux-setup-storage”
<br>
等待一段时间后在弹出的对话框内赋予存储权限，在返回#后进行下一步（自此之后每一步都需要在termux中进行）
<br>
三，安装proot-distro
<br>
“pkg update && pkg install proot-distro”
<br>
四，在proot-distro中安装ubuntu（需要等待一段时间）
<br>
“proot-distro install ubuntu”
<br>
五，进入ubuntu
<br>
输入并执行：
<br>
“proot-distro login ubuntu”
<br>
（此后所有步骤均在其中执行)
<br>
六，安装必要的编译程序等
<br>
apt update && apt install cmake build-essential python3 gcc git
<br>
七，下载box64
<br>
git clone https://github.com/ptitSeb/box64
<br>
八，编译box64
<br>
输入：
<br>
cd box64
<br>
mkdir build
<br>
cd build
<br>
cmake .. -DCMAKE_BUILD_TYPE=RelWithDebInfo -DARM64=1
<br>
等待配置完成(返回root@localhost:~/box64#)后输入：
<br>
make -j$(nproc)
<br>
开始编译，等待一段时间后即可