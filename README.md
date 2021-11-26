# 自定义配置

## Ubuntu初始化

```shell
# 基础包安装
sudo apt install vim curl openssh-server zsh libssl-dev gcc g++ make automake autoconf ibus-rime ninja-build libtool gdb git intel-microcode

# 安装字体
sudo apt install fonts-anonymous-pro fonts-cascadia-code fonts-courier-prime fonts-fantasque-sans fonts-firacode fonts-hack fonts-hermit fonts-inconsolata fonts-jetbrains-mono fonts-mona fonts-monapo fonts-monofur fonts-mononoki fonts-sil-andika fonts-freefont-ttf fonts-opendin fonts-open-sans fonts-gfs-bodoni-classic fonts-ebgaramond fonts-ebgaramond-extra fonts-freefont-ttf fonts-sil-gentium fonts-liberation fonts-liberation2 fonts-junicode fonts-mph-2b-damase fonts-wqy-microhei fonts-wqy-zenhei fonts-arphic-bkai00mp fonts-arphic-bsmi00lp fonts-arphic-gbsn00lp fonts-arphic-gkai00mp fonts-arphic-ukai fonts-arphic-uming fonts-noto-color-emoji fonts-symbola fonts-stix fonts-mathjax fonts-mathjax-extras fonts-powerline

# Debian卸载游戏和libreoffice
sudo apt remove gnome-2048 aisleriot gnome-calendar cheese gnome-chess gnome-clocks gnome-contacts gnome-documents  evolution five-or-more four-in-a-row hitori gnome-klotski lightsoff gnome-mahjongg gnome-maps gnome-mines gnome-music gnome-nibbles malcontent quadrapassel iagno rhythmbox gnome-robots shotwell gnome-sound-recorder gnome-sudoku swell-foop synaptic tali gnome-taquin gnome-tetravex gnome-todo transmission-common transmission-gtk xterm gnome-weather libreoffice*

sudo apt autoremove

# 安装llvm套装
sudo apt install clang-format clang-tidy clang-tools clang clangd libc++-dev libc++1 libc++abi-dev libc++abi1 libclang-dev libclang1 liblldb-dev libllvm-ocaml-dev libomp-dev libomp5 lld lldb llvm-dev llvm-runtime llvm python-clang

# 配置cc c++编译器
sudo update-alternatives --install /usr/bin/cc cc /usr/bin/clang 100
sudo update-alternatives --install /usr/bin/c++ c++ /usr/bin/clang++ 100

# 配置vim
vim ~/.vimrc
set nocompatible
syntax on
set showmode
set showcmd
set encoding=utf-8
set t_Co=256
filetype indent on
set autoindent
set tabstop=2
set shiftwidth=2
set expandtab
set softtabstop=2
set nonumber
set textwidth=120
set nowrap
set wrapmargin=2
set scrolloff=5
set sidescrolloff=15
set laststatus=2
set ruler
set showmatch
set hlsearch
set incsearch
set ignorecase
set smartcase
set nobackup
set noswapfile
set noerrorbells
set wildmenu
set wildmode=longest:list,full
```

## Linux环境变量配置

```text
# vim ~/.profile
JAVA_HOME=~/.softwares/java/jdk-11.0.13
GOROOT=~/.softwares/go
SCALA_HOME=~/.softwares/scala
GROOVY_HOME=~/.softwares/groovy
NODE_HOME=~/.softwares/node
ANT_HOME=~/.softwares/ant
M2_HOME=~/.softwares/maven
GRADLE_HOME=~/.softwares/gradle
VISUALVM=~/.softwares/visualvm
JMETER=~/.softwares/jmeter
PATH=$PATH:$JAVA_HOME/bin:$GOROOT/bin:$SCALA_HOME/bin:$GROOVY_HOME/bin:$NODE_HOME/bin:$ANT_HOME/bin:$M2_HOME/bin:$GRADLE_HOME/bin:$VISUALVM/bin:$JMETER/bin
export PATH JAVA_HOME GOROOT SCALA_HOME GROOVY_HOME NODE_HOME ANT_HOME M2_HOME GRADLE_HOME VISUALVM JMETER
```

## Ubuntu安装git

```shell
sudo add-apt-repository ppa:git-core/ppa
sudo apt-get update
sudo apt-get install git
```

## Linux配置oh-my-zsh

```shell
git clone git://github.com/ohmyzsh/ohmyzsh.git ~/.oh-my-zsh
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
chsh -s $(which zsh)
# 配置 ohmyzsh 插件
git clone git://github.com/zsh-users/zsh-autosuggestions.git ~/.oh-my-zsh/plugins/zsh-autosuggestions
git clone git://github.com/zsh-users/zsh-syntax-highlighting.git ~/.oh-my-zsh/plugins/zsh-syntax-highlighting
vim ~/.zshrc

plugins=(
  git
  zsh-autosuggestions
  zsh-syntax-highlighting
)

setopt nonomatch
```

## Ubuntu安装配置wireshark

```shell
# 安装wireshark
sudo apt install wireshark
# 配置权限
sudo chgrp wireshark /usr/bin/dumpcap
sudo chmod 4755 /usr/bin/dumpcap
sudo gpasswd -a ${USER} wireshark
```

# Ubuntu安装配置Docker CE

1. [安装Docker CE](https://docs.docker.com/engine/install/ubuntu)
2. 配置sudo如下
```shell
sudo usermod -aG docker $USER
sudo systemctl restart docker
newgrp docker
```
3. [安装docker-compose](https://docs.docker.com/compose/install)

## Ubuntu配置ibus rime

```yaml
# vim ~/.config/ibus/rime/default.custom.yaml
patch:
 "menu/page_size": 7

# vim ~/.config/ibus/rime/ibus_rime.yaml
style:
 horizontal: true
 inline_preedit: true
 display_tray_icon: true

# vim ~/.config/ibus/rime/luna_pinyin.custom.yaml
patch:
  switches:
    - name: ascii_mode
      reset: 0
      states: ["中文", "西文"]
    - name: full_shape
      states: ["半角", "全角"]
    - name: simplification
      reset: 1
      states: ["漢字", "汉字"]
    - name: ascii_punct
      states: ["。，", "．，"]
```

## Ubuntu配置jetbrains

1. 配置IntelliJ IDEA Ultimate

```shell
sudo rm -rf android android-gradle-dsl smali AngularJS devkit less sass space spy-js stylus tslint w3validators xpath xslt-debugger featuresTrainer ant Glassfish Jetty Tomcat weblogicIntegration webSphereIntegration RefactorX JavaScriptDebugger NodeJS JSIntentionPowerPack JSF javaFX uiDesigner FreeMarker haml thymeleaf Velocity lombok github svn4idea vcs-git-featuresTrainer
```

2. 配置Clion
```shell
sudo rm -rf coffeescript-core CSS github htmltools JavaScriptDebugger JavaScriptLanguage JSIntentionPowerPack less PerforceIntegration sass stylus svn4idea tslint xpath
```

3. 配置Goland
```shell
sudo rm -rf htmltools RefactorX JavaScriptDebugger JavaScriptLanguage JSIntentionPowerPack/ tslint CSS github featuresTrainer
```

## Debian安装配置Nvidia

1. 关闭nouveau

```shell
sudo vim /etc/modprobe.d/nvidia-blacklists-nouveau.conf

blacklist nouveau
blacklist lbm-nouveau
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off

sudo update-initramfs -u
sudo reboot
```

2. 安装Nvidia闭源

```shell
sudo apt install nvidia-driver firmware-misc-nonfree nvidia-kernel-dkms nvidia-xconfig
```

3. 配置xorg

```shell
# sudo vim /etc/X11/xorg.conf.d/10-nvidia-drm-outputclass.conf
Section "OutputClass"
    Identifier "intel"
    MatchDriver "i915"
    Driver "modesetting"
EndSection

Section "OutputClass"
    Identifier "nvidia"
    MatchDriver "nvidia-drm"
    Driver "nvidia"
    Option "AllowEmptyInitialConfiguration"
    Option "PrimaryGPU" "yes"
    ModulePath "/usr/lib/nvidia/xorg"
    ModulePath "/usr/lib/xorg/modules"
EndSection
```

5. 配置GDM
```shell
# vim ~/.xinitrc

xrandr --setprovideroutputsource modesetting NVIDIA-0
xrandr --auto
xrandr --dpi 96
```

```shell
# 两个文件内容相同
# sudo vim /usr/share/gdm/greeter/autostart/optimus.desktop
# sudo vim /etc/xdg/autostart/optimus.desktop

[Desktop Entry]
Type=Application
Name=Optimus
Exec=sh -c "xrandr --setprovideroutputsource modesetting NVIDIA-0; xrandr --auto"
NoDisplay=true
X-GNOME-Autostart-Phase=DisplayServer
```
