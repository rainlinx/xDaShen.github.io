---
title: Ubuntu 18.04 开发环境搭建
date: 2018-12-05 15:51:11
tags: 环境搭建
---

# Ubuntu 18.04 开发环境搭建

## 一. 安装JDK

1. 官网下载jdk-8u191-linux-x64.tar.gz
2. 解压

```shell
tar zxvf jdk-8u191-linux-x64.tar.gz 
sudo mv jdk1.8.0_191 /usr/local/java 
```

1. 配置环境变量

```shell
echo 'export JAVA_HOME=/usr/local/java/jdk1.8.0_191
export CLASSPATH=.:$JAVA_HOME/lib
export PATH=$PATH:$JAVA_HOME/bin' >> ~/.profile
source ~/.profile

java -version正确输出即配置完成
```

## 二. 安装Toolbox

## 三. 安装npm，nodejs

```shell
sudo apt install -y nodejs
sudo apt install -y npm
```

## 四. 安装vscode

```shell
sudo snap install vscode --classic
```

## 五. 安装ss-qt5

```shell
sudo add-apt-repository ppa:hzwhuang/ss-qt5
sudo apt-get update
sudo apt install -y shadowsocks-qt5
hzwhuang-ubuntu-ss-qt5-bionic.list 将里面的bionic 改成xenial 
```

## 六. 安装Typora

```shell
wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -
# add Typora's repository
sudo add-apt-repository 'deb https://typora.io/linux ./'
sudo apt-get update
# install typora
sudo apt-get install -y typora
```

## 七. 安装Tomcat

1. 官网下载压缩包
2. 解压到/usr/local/目录

```shell
  tar zxvf apache-tomcat-9.0.13
  sudo mv apache-tomcat-9.0.13 /usr/local/
```

1. 修改startup.sh，添加CATALINA_HOME=/usr/local/apache-tomcat-9.0.13

```shell
  echo  CATALINA_HOME=/usr/local/apache-tomcat-9.0.13 >> /usr/local/apache-tomcat-9.0.13/bin/startup.sh
```

1. 在bin目录下建立setenv.sh脚本，添加JAVA_HOME=/usr/local/java/jdk1.8.0_191

```shell
  touch  /usr/local/apache-tomcat-9.0.13/bin/setenv.sh
  echo JAVA_HOME=/usr/local/java/jdk1.8.0_191 >> /usr/local/apache-tomcat-9.0.13/bin/setenv.sh
```

1. 运行

```shell
  /usr/local/apache-tomcat-9.0.12/bin/startup.sh
```

## 八. 安装mysql

1. 官网下载`mysql-apt-config_0.8.11-1_all.deb`
2. mysql安装设置

```shell
  sudo dpkg -i mysql-apt-config_0.8.11-1_all.deb
```

1. 安装mysql

```shell
  sudo apt update
  sudo apt install -y mysql-server
```

1. mysql服务启动/停止

```shell
  service mysql start
  service mysql stop
```

1. 开启mysql远程连接

```shell
  mysql -u root -p
  use mysql;
  update user set host='%' where user='root';
  flush privileges; 
```

## 九. 安装git

```shell
sudo apt install -y git
```

# 美化

## 一. gnome

```shell
sudo apt install -y gnome-tweak-tool
sudo apt install -y gnome-shell-extensions
```

## 二. dash to dock

```shell
sudo apt install -y gnome-shell-extension-dashtodock
```

## 三. dash to panel

```shell
sudo apt install -y gnome-shell-extension-dash-to-panel
```

## 四. VLC

```shell
sudo apt -y install vlc
```

# 自动化安装脚本

> 执行脚本前请下载jdk、mysql、tomcat

```shell
#!/bin/bash
echo '安装JDK'
cd ~/Downloads
tar zxvf jdk-8u191-linux-x64.tar.gz 
sudo mv jdk1.8.0_191 /usr/local/java/ 
echo '配置环境变量'
echo 'export JAVA_HOME=/usr/local/java/jdk1.8.0_191
export CLASSPATH=.:$JAVA_HOME/lib
export PATH=$PATH:$JAVA_HOME/bin' >> ~/.profile
echo '安装npm'
sudo apt install -y nodejs
sudo apt install -y npm
echo '安装git'
sudo apt install -y git
echo '安装zsh和oh_my_zsh'
sudo apt install -y zsh
wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | sh
sudo chsh -s /bin/zsh
echo '安装vim'
sudo apt install -y vim
echo '安装mysql'
sudo dpkg -i mysql-apt-config_0.8.11-1_all.deb
sudo apt update
sudo apt install -y mysql-server
echo '安装Tomcat'
tar zxvf apache-tomcat-9.0.13.tar.gz
sudo mv apache-tomcat-9.0.13 /usr/local/
echo  CATALINA_HOME=/usr/local/apache-tomcat-9.0.13 >> /usr/local/apache-tomcat-9.0.13/bin/startup.sh
touch  /usr/local/apache-tomcat-9.0.13/bin/setenv.sh
echo JAVA_HOME=/usr/local/java/jdk1.8.0_191 >> /usr/local/apache-tomcat-9.0.13/bin/setenv.sh
echo '安装gnome'
sudo apt install -y gnome-tweak-tool
sudo apt install -y gnome-shell-extensions
echo '安装dash-to-panel'
sudo apt install -y gnome-shell-extension-dash-to-panel
echo '安装chrome'
sudo wget http://www.linuxidc.com/files/repo/google-chrome.list -P /etc/apt/sources.list.d/
wget -q -O - https://dl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -
sudo apt-get update
sudo apt-get install -y google-chrome-stable
echo '安装Typora'
wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -
sudo add-apt-repository 'deb https://typora.io/linux ./'
sudo apt-get update
sudo apt-get install -y typora
```