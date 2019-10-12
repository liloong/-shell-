## 安装前准备：Ubuntu18.4.03桌面版标准安装、gitlab-ce_12.3.5-ce.0_amd64.deb
## 安装gitlab步骤如下：

### 1.首先给虚拟机安装VMwareTools
sudo cp VMwareTools-10.3.10-12406962.tar.gz /home/lill/
cd /home/lill/
sudo tar -xvf VMwareTools-10.3.10-12406962.tar.gz
cd vmware-tools-distrib/
sudo ./vmware-install.pl

### 2.更换apt源提高下载速度
cd /etc/apt/
sudo cp sources.list sources.list.bak
sudo gedit sources.list
sudo apt-get update

清除sources.list文件内容，将以下内容拷贝到文件中保存退出
阿里源：
deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse

163源：
deb http://mirrors.163.com/ubuntu/ bionic main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ bionic main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ bionic-security main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ bionic-backports main restricted universe multiverse

### 3.安装vim编辑器
sudo apt install vim
sudo apt install vim-common=2:7.4.1689-3ubuntu1.3
sudo apt install vim


### 4.安装ifconfig
sudo apt install net-tools
ifconfig

### 5.修改文件固定虚拟机IP
cd /etc/network/
sudo vim interfaces


将以下内容添加到interfaces文件底部
auto ens33
iface ens33 inet static
address 192.168.1.50
netmask 255.255.255.0
gateway 192.168.1.1


### 6.安装gitlab，需要安装openssh-server
mv gitlab-ce_12.3.5-ce.0_amd64.deb /home/lill/
cd /home/lill/
sudo dpkg -i gitlab-ce_12.3.5-ce.0_amd64.deb
sudo apt-get install openssh-server
sudo apt-get install openssh-client=1:7.2p2-4ubuntu2.8
sudo apt --fix-broken install
sudo apt-get install openssh-server
sudo apt-get install openssh-client=1:7.2p2-4ubuntu2.8
sudo apt-get install openssh-server
sudo dpkg -i gitlab-ce_12.3.5-ce.0_amd64.deb

### 7.修改gitlab的配置文件
cd /etc/gitlab/
sudo vim gitlab.rb



### 8.关闭虚拟机，之后修改网络模式为桥接
sudo shutdown -r now

### 9.开机后进入命令行模式无法进入桌面，先登录到系统通过命令行重新安装桌面之后重启
sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop
sudo reboot

history > install.txt
