---
title: ubuntu18.04-config
date: 2019-04-25 10:37:40
categories:
- [Linux, Ubuntu]
tags:
- Linux
- Ubuntu
---

> 记录ubuntu18.04安装后的一些配置，方便下次安装或者重装

# 配置

## 系统配置

* 打开**软件和更新**，选择**阿里云服务器**或者**中国服务器**，然后更新系统

   ```bash
   sudo apt-get update
   sudo apt-get upgrade
   ```

   > 如果更新遇到找不到PGK秘钥等问题，在软件和更新中去除相应的PPA源，或者删除`/etc/apt/sources.list.d/`目录中的源文件，还可以在终端执行：

   ```bash
   sudo add-apt-repository -r ppa:<ppa_name>
   ```

   > 先安装python-software-properties 才能使用 add-apt-repository

   ```bash
   sudo apt-get install python-software-properties
   sudo apt-get install software-properties-common
   ```

   > 通过PPA安装软件具体方式：

   ```bash
   sudo add-apt-repository ppa:<ppa_name>
   sudo apt-get update
   sudo apt-get install name
   ```

* 打开**设置**，配置一些基本的设置

* 一些常用的命令

   解压

   ```bash
   sudo tar -zxvf [压缩文件名] [解压到哪]
   ```

   修复依赖

   ```bash
   sudo apt-get install -f
   ```

* 配置环境变量最好到`/etc/profile.d`目录下，针对每个软件单独建立一个`.sh`文件，方便维护，不用时可直接删除

* gnome桌面软件添加启动图标的方法，在`～/.local/share/applications`目录下新建`.desktop`文件，加入以下内容编辑修改

   ```bash
   [Desktop Entry]
   Version=1.0
   Name=postman
   # 启动程序位置
   Exec=/opt/Postman/app/Postman
   Terminal=false
   # 图标位置，或者用系统图标（跟系统图标名称一致，可到图标目录搜索）
   # Icon=/opt/Postman/app/resources/app/assets/icon.png
   Icon=postman
   Type=Application
   ```

   > 可以参考其他软件的配置，系统软件启动图标位置`/usr/share/applications`

## 软件安装

### 安装gnome-tweak-tool

```bash
sudo apt-get install gnome-tweak-tool
```

gnome-tweak-tool用于配置Gnome桌面，字体、主题、开机启动程序等

### 安装gnome-shell-extension

```bash
sudo apt-get install gnome-shell-extensions
```

gnome-shell-extension用于在Chrome、Firefox中安装gnome扩展

一些自用的扩展：

* **User themes**

  允许配置个人安装的主题

* **Dash to dock**

  dock栏，比ubuntu自带的好用，用之前需要先删除自带的dock，在`/usr/share/gnome-shell/extensions`中删除

* **Unite**

  类似unity桌面顶栏的效果，最大化时将标题栏合并到顶栏，自带顶栏托盘图标，还有一个类似的扩展**Gnome Global Application Menu**，但是好像不更新了

* **Alt tab workspace**

  alt-tab只切换当前工作空间的应用程序

* **Click quit overview**

  在窗口预览视图点击空白处退出

* **Coverflow alt-tab**

  炫酷的alt-tab切换效果

* **Gnome shell extension reloader**

  顶栏添加一个图标，用于重启gnome扩展

* **Openweather**

  顶栏添加天气

* **Removable drive menu**

  顶栏显示挂载，方便取消挂载

* **Simple net speed**

  顶栏显示网速

* **Switcher**

  super+w弹出窗口搜索器，super+x弹出应用程序搜索器，可编辑快捷键

* **Topicons plus**

  顶栏显示托盘图标，安装Unite的话不需要这个

* **Workspace switch wraparound**

  允许循环切换工作空间

* **System-monitor**

  顶栏显示系统监控，CPU、内存等信息

* **Windownavigator**

  在窗口预览视图通过 **ctrl+数字** 选择工作空间， **alt+数字** 选择窗口

### 安装Chrome

```bash
# 1、将下载源加入到系统的源列表（方便更新）
sudo wget https://repo.fdzh.org/chrome/google-chrome.list -P /etc/apt/sources.list.d/
# 2、导入谷歌软件的公钥，用于对下载软件进行验证。
wget -q -O - https://dl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -
# 3、用于对当前系统的可用更新列表进行更新。（更新源）
sudo apt-get update
# 4、安装谷歌 Chrome 浏览器（稳定版）。
sudo apt-get install google-chrome-stable
```

### 安装搜狗拼音输入法

1. 卸载ibus

   ```bash
   sudo apt-get autoremove ibus
   ```

2. 清除ibus配置

   ```bash
   sudo apt-get purge ibus
   ```

3. 卸载顶部面板任务栏上的键盘指示

   ```bash
   sudo apt-get remove indicator-keyboard
   ```

4. 安装fcitx输入法框架

   ```bash
   sudo apt install fcitx-table-wbpy fcitx-config-gtk
   ```

5. 切换为fcitx输入法

   ```bash
   im-config -n fcitx
   ```

6. [官网](https://pinyin.sogou.com/linux/?r=pinyin)下载搜狗输入法并安装

   ```bash
   sudo dpkg -i sogoupinyin_***_amd64.deb
   ```

7. 修复损坏缺少的包

   ```bash
   sudo apt-get install -f
   ```

8. 重启后打开fcitx配置，添加搜狗输入法

### WPS

1. 卸载libreoffice

   ```bash
   sudo apt-get remove --purge libreoffice*
   ```

2. [官网](<https://www.wps.cn/product/wpslinux>)下载deb包和[wps-office-fonts_1.0_all.deb](http://kdl.cc.ksosoft.com/wps-community/download/fonts/wps-office-fonts_1.0_all.deb)安装

   > 安装`wps-office-fonts_1.0_all.deb`依然提示缺少字体解决办法：下载字体包`wps_symbol_fonts.zip`并解压到`/usr/share/fonts/`目录下
   >
   > ```bash
   > sudo unzip wps_symbol_fonts.zip -d /usr/share/fonts/wps-office
   > ```
   > 执行:
   > 
   > ```bash
   > sudo mkfontscale
   >sudo mkfontdir
   > sudo fc-cache
   > ```

### 网易云音乐

[官网](https://music.163.com/#/download)下载ubuntu版本安装，最新版本好像已经解决了需要sudo启动的问题

### JAVA

可以通过apt方式安装或者到[官网](https://www.oracle.com/technetwork/java/javase/downloads/index.html)下载deb和压缩包安装

1. apt方式安装jdk8：

   ```bash
   sudo add-apt-repository ppa:webupd8team/java
   sudo apt-get update
   sudo apt-get install oracle-java8-installer
   ```

   切换java版本

   ```bash
   sudo update-java-alternatives -s java-8-oracle
   ```

2. 官网下载压缩包安装

   解压之后需要配置环境变量，在`/etc/profile.d`目录下新建一个jdk.sh，加入以下内容

   ```bash
   export JAVA_HOME=解压文件路径
   export JRE_HOME=${JAVA_HOME}/jre
   export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
   export PATH=${JAVA_HOME}/bin:$PATH
   ```

### Albert

一款类似于Mac Spotlight的软件

```bash
sudo add-apt-repository ppa:noobslab/macbuntu
sudo apt-get update
sudo apt-get install albert
```

安装完成后设置快捷键

[https://www.noobslab.com](https://www.noobslab.com/)一个ubuntu仿mac的网站

### slingscold

一个应用程序启动器，比gnome的启动器流畅，没什么卵用

```bash
sudo add-apt-repository ppa:noobslab/macbuntu
sudo apt-get update
sudo apt-get install slingscold
```

需要设置全局快捷键

### Guake

下拉式终端

```bash
sudo apt-get install guake-indicator
sudo apt-get install guake
```

### JetBrains全家桶

官网下载toolbox安装

### QQ、TIM

参考<https://github.com/wszqkzqk/deepin-wine-ubuntu>

### 微信

应用商店搜索安装或者：

```bash
sudo snap install electronic-wechat
```

### golang

1. apt安装

   ```bash
   sudo apt-get install golang-go
   ```

   > 觉得版本比较旧可以导入PPA安装
   >
   > ```bash
   > sudo add-apt-repository ppa:longsleep/golang-backports
   > sudo apt-get update
   > sudo apt-get install golang-go
   > ```

2. snap安装

   直接应用商店搜索安装或者：

   ```bash
   sudo snap install --classic go
   ```

3. 使用官方安装程序安装

   ```bash
   wget https://storage.googleapis.com/golang/getgo/installer_linux
   chmod +x ./installer_linux
   ./installer_linux
   ```

4. 官网下载压缩包，解压后设置环境变量，`/etc/profile.d/`目录下新建golang.sh，加入：

   ```bash
   #GOROOT为安装路径
   export GOROOT=/opt/go
   export PATH=$PATH:$GOROOT/bin
   ```

### Typora

markdown编辑器

```bash
# or run:
# sudo apt-key adv --keyserver keyserver.ubuntu.com--recv-keys BA300B7755AFCFAE
wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -
# add Typora's repository
sudo add-apt-repository 'deb https://typora.io/linux ./'
sudo apt-get update
# install typora
sudo apt-get install typora
```

### FileZilla

FTP客户端

```bash
sudo apt-get install filezilla
```

### 深度截图

应用商店搜索安装，设置全局快捷键

### 其他

vscode、postman、dbeaver，官网下载安装



# 主题美化

到[https://www.gnome-look.org](https://www.gnome-look.org/)下载主题、图标等，解压到对应的文件夹下

系统的主题、图标文件夹：

`/usr/share/themes`

`/usr/share/icons`

或者用户的主题、图标文件夹：

`~/.themes`

`~/.icons`

一些主题需要的依赖

```bash
sudo apt-get install gtk2-engines-murrine gtk2-engines-pixbuf
```

自用的一些主题

主题：Vimix、Ant、McMojave

图标：Papirus、Mojave CT icons、Tela、Zafiro、la-capitaine

鼠标指针：Capitaine Cursors