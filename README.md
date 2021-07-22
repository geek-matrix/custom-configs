# 自定义配置

## Ubuntu初始化

```shell
# 基础包安装
sudo apt-get install vim curl openssh-server zsh libssl-dev zsh gcc g++ make automake autoconf gdb ibus-rime ninja-build

# 安装llvm套装
sudo apt-get install clang-format clang-tidy clang-tools clang clangd libc++-dev libc++1 libc++abi-dev libc++abi1 libclang-dev libclang1 liblldb-dev libllvm-ocaml-dev libomp-dev libomp5 lld lldb llvm-dev llvm-runtime llvm python-clang

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
set number
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
# sudo vim /etc/profile
JAVA_HOME=/usr/local/java/jdk-11.0.12
GOROOT=/usr/local/go
PATH=$PATH:$JAVA_HOME/bin:$GOROOT/bin
export PATH JAVA_HOME GOROOT

# vim ~/.profile
KOTLIN_HOME=/opt/kotlin
SCALA_HOME=/opt/scala
GROOVY_HOME=/opt/groovy
NODE_HOME=/opt/node
ANT_HOME=/opt/ant
M2_HOME=/opt/maven
GRADLE_HOME=/opt/gradle
VISUALVM=/opt/visualvm
JMETER=/opt/jmeter
PATH=$PATH:$KOTLIN_HOME/bin:$SCALA_HOME/bin:$GROOVY_HOME/bin:$NODE_HOME/bin:$ANT_HOME/bin:$M2_HOME/bin:$GRADLE_HOME/bin:
export PATH KOTLIN_HOME SCALA_HOME GROOVY_HOME NODE_HOME ANT_HOME M2_HOME GRADLE_HOME VISUALVM JMETER
```

## Ubuntu安装git

```shell
sudo add-apt-repository ppa:git-core/ppa
sudo apt-get update
sudo apt-get install git
```

## Linux配置oh-my-zsh

```shell
git clone https://github.com/ohmyzsh/ohmyzsh.git ~/.oh-my-zsh
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
chsh -s $(which zsh)
# 配置 ohmyzsh 插件
git clone git://github.com/zsh-users/zsh-autosuggestions.git ~/.oh-my-zsh/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ~/.oh-my-zsh/plugins/zsh-syntax-highlighting
vim ~/.zshrc
```

## Ubuntu安装配置wireshark

```shell
# 安装wireshark
sudo apt-get install wireshark
# 配置权限
sudo chgrp wireshark /usr/bin/dumpcap
sudo chmod 4755 /usr/bin/dumpcap
sudo gpasswd -a ${USER} wireshark
```

# Ubuntu安装配置Docker CE

1. [安装Docker CE](https://docs.docker.com/engine/install/ubuntu)
2. 配置sudo如下
```shell
sudo gpasswd -a ${USER} docker
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
sudo rm -rf android android-gradle-dsl smali AngularJS devkit jsr45debug less sass space spy-js stylus tslint w3validators xpath xslt-debugger featuresTrainer ant Glassfish Jetty Tomcat weblogicIntegration webSphereIntegration RefactorX coffeescript-core JavaScriptDebugger NodeJS JSIntentionPowerPack drools JSF javaFX SpringOSGi SpringWebflow EJB uiDesigner FreeMarker haml thymeleaf Velocity lombok github svn4idea
```

2. 配置Clion
```shell
sudo rm -rf coffeescript-core CSS github htmltools JavaScriptDebugger JavaScriptLanguage JSIntentionPowerPack less PerforceIntegration sass stylus svn4idea tslint xpath
```

3. 配置Goland
```shell
sudo rm -rf htmltools RefactorX JavaScriptDebugger JavaScriptLanguage JSIntentionPowerPack/ tslint CSS github featuresTrainer
```
