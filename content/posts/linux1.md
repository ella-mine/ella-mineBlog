---
title: Linux系统的美化上--zsh篇
date: 2020-04-03T23:57:16+08:00
lastmod: 2020-04-03T23:57:16+08:00
author: Chitanda
cover: /img/linux1.png
categories: ["系统折腾记录"]
tags: ["美化", "强迫症"]
# showcase: true
---

<!--more-->

> 当你在一台全新的设备上安装了`Linux`系统之后，要做的第一件事情是什么呢？作为一个强迫症+颜狗，自然是要将系统变成自己喜欢且顺手的形状。正好最近重装了自己笔记本电脑的系统，特此记录下设置系统的过程，方便以后的快速设置。本文会分成上下两部分，上部分主要讲述`zsh`以及终端的美化与设置，文章结构如下：
>
> [toc]

# `Ubuntu`系统的美化及设置（上篇）

>系统信息：
>
>Distributor ID:	Ubuntu
>Description:	Ubuntu 18.04.4 LTS
>Release:	18.04
>Codename:	bionic

## 1 终端的美化

作为一个使用`Linux`系统的程序员，每天最常打交道的毫无疑问是`Terminal`--终端。在一个好用又好看的终端中工作可以大幅提高生产力（假），所以我们首先对终端窗口进行美化。首先我们使用`zsh`替换系统默认的`shell`，然后使用`oh-my-zsh`更换主题、自定义字体等。

### 1.1 安装并设置`zsh`

#### 1.1.1 安装`zsh`

`Ubuntu 18.04`系统中安装`zsh`非常简单。

* 直接在终端中运行：

  ```shell
   ~ $ sudo apt-get install zsh
  ```

* 检查系统中已有的`shell`有哪些：

  ```shell
  ~ $ cat /etc/shells
  # which zsh
  ```

* 检查当前系统默认的`shell`：

  ```shell
  ~ $ echo $SHELL
  ```

* 接下来要将`zsh`设置成默认的`shell`：

  ```shell
  chsh -s $(which zsh)
  # 需要输入用户密码
  ```

设置完毕后，**重新登陆账户**，检查当前的`shell`是否是`zsh`。

#### 1.1.2 安装`oh-my-zsh`

>     “Oh My Zsh is a delightful, open source, community-driven framework for  managing your Zsh configuration. It comes bundled with thousands of  helpful functions, helpers, plugins, themes, and a few things that make  you shout...”
>
>     --https://ohmyz.sh/

`oh-my-zsh`是一个开源、轻量级的`zsh`配置框架，官方给出的安装方法如下：

```shell
$ sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```

但我在安装时，网络一直报错导致安装失败，可以打开上边的网址，

将脚本内容手动复制到本地，并运行。

#### 1.1.3 配置`oh-my-zsh`

配置方法和原来的终端配置方法完全类似，如果有过相关经验可以很快上手，即在用户主目录下新建一个配置文件`.zshrc`，官方给出了配置文件的示例程序，可以在此基础上进行个性化修改。

* 修改主题只需要修改`ZSH_THEME="powerlevel9k/powerlevel9k"`即可。

我的配置文件如下：

```shell
# If you come from bash you might have to change your $PATH.
# export PATH=$HOME/bin:/usr/local/bin:$PATH

# Path to your oh-my-zsh installation.
export ZSH="/home/ao/.oh-my-zsh"

# Set name of the theme to load --- if set to "random", it will
# load a random theme each time oh-my-zsh is loaded, in which case,
# to know which specific one was loaded, run: echo $RANDOM_THEME
# See https://github.com/ohmyzsh/ohmyzsh/wiki/Themes
ZSH_THEME="powerlevel9k/powerlevel9k"

# Set list of themes to pick from when loading at random
# Setting this variable when ZSH_THEME=random will cause zsh to load
# a theme from this variable instead of looking in ~/.oh-my-zsh/themes/
# If set to an empty array, this variable will have no effect.
# ZSH_THEME_RANDOM_CANDIDATES=( "robbyrussell" "agnoster" )

# Uncomment the following line to use case-sensitive completion.
# CASE_SENSITIVE="true"

# Uncomment the following line to use hyphen-insensitive completion.
# Case-sensitive completion must be off. _ and - will be interchangeable.
# HYPHEN_INSENSITIVE="true"

# Uncomment the following line to disable bi-weekly auto-update checks.
# DISABLE_AUTO_UPDATE="true"

# Uncomment the following line to automatically update without prompting.
# DISABLE_UPDATE_PROMPT="true"

# Uncomment the following line to change how often to auto-update (in days).
# export UPDATE_ZSH_DAYS=13

# Uncomment the following line if pasting URLs and other text is messed up.
# Uncomment the following line to disable colors in ls.
# DISABLE_LS_COLORS="true"

# Uncomment the following line to disable auto-setting terminal title.
# DISABLE_AUTO_TITLE="true"

# Uncomment the following line to enable command auto-correction.
ENABLE_CORRECTION="true"

# Uncomment the following line to display red dots whilst waiting for completion.
# COMPLETION_WAITING_DOTS="true"

# Uncomment the following line if you want to disable marking untracked files
# under VCS as dirty. This makes repository status check for large repositories
# much, much faster.
# DISABLE_UNTRACKED_FILES_DIRTY="true"

# Uncomment the following line if you want to change the command execution time
# stamp shown in the history command output.
# You can set one of the optional three formats:
# "mm/dd/yyyy"|"dd.mm.yyyy"|"yyyy-mm-dd"
# or set a custom format using the strftime function format specifications,
# see 'man strftime' for details.
# HIST_STAMPS="mm/dd/yyyy"

# Would you like to use another custom folder than $ZSH/custom?
# ZSH_CUSTOM=/path/to/new-custom-folder

# Which plugins would you like to load?
# Standard plugins can be found in ~/.oh-my-zsh/plugins/*
# Custom plugins may be added to ~/.oh-my-zsh/custom/plugins/
# Example format: plugins=(rails git textmate ruby lighthouse)
# Add wisely, as too many plugins slow down shell startup.
plugins=(git)

source $ZSH/oh-my-zsh.sh

# User configuration

# export MANPATH="/usr/local/man:$MANPATH"

# You may need to manually set your language environment
# export LANG=en_US.UTF-8

# Preferred editor for local and remote sessions
# if [[ -n $SSH_CONNECTION ]]; then
#   export EDITOR='vim'
# else
#   export EDITOR='mvim'
# fi

# Compilation flags
# export ARCHFLAGS="-arch x86_64"

# Set personal aliases, overriding those provided by oh-my-zsh libs,
# plugins, and themes. Aliases can be placed here, though oh-my-zsh
# users are encouraged to define aliases within the ZSH_CUSTOM folder.
# For a full list of active aliases, run `alias`.
#
# Example aliases
alias zshconfig='vim ~/.zshrc'
alias zshsource='source ~/.zshrc'
alias ..='cd ..'
alias ...= 'cd ../../../'
alias ....= 'cd ../../../../'
alias .....= 'cd ../../../../'
alias .4= 'cd ../../../../'
alias .5= 'cd ../../../../..'
alias l='ls'
alias mount='mount | column -t'
alias now='date +"%T"'
alias nowtime=now
alias nowdate='date +"%d-%m-%Y"'
# Stop after sending count ECHO_REQUEST packets #
alias ping='ping -c 5'

# Do not wait interval 1 second, go fast #
alias fastping='ping -c 100 -s.2'
alias ports='netstat -tulanp'

alias cp='cp -i'

# Parenting changing perms on / #
alias chown='chown --preserve-root'
alias chmod='chmod --preserve-root'
alias chgrp='chgrp --preserve-root'
## this one saved by butt so many times ##
alias wget='wget -c'

# 打开Typora
alias markdown='/usr/share/Typora-linux-x65/Typora'
# alias ohmyzsh="mate ~/.oh-my-zsh"
```

### 1.2 主题设置

直接修改主题后，可能会出现某些字符无法显示的问题，这是因为缺少相关的字体。所以接下来要安装字体和自定义的主题。

#### 1.2 .1 安装`Powerline`字体

直接在终端输入：

```shell
~ $ sudo apt-get install fonts-powerline
```

#### 1.2.2 安装`zsh-theme-powerlevel9k`

从`github`下载源代码到`zsh`的配置文件夹：

```sh
git clone https://github.com/bhilburn/powerlevel9k.git ~/.oh-my-zsh
```

然后在`~/.zshrc`中修改主题：

``` shell
ZSH_THEME="powerlevel9k/powerlevel9k"
```

重新登录账户即可看到和下图一样的效果。

> 注意：如果系统语言是中文，依然可能出现部分字符显示不全的问题，将语言切换到英语即可。如果一定要使用中文，请自行寻找合适的字体包来解决问题。
