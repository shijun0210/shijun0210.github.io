---
title: MacBook使用tips
categories:
  - 2023-2025
  - 25-4
date: 2025-04-09 16:55:00
tags:
---
### 安装homebrew后需要将其添加至*PATH环境变量*中：
1. Zsh
```
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/$(whoami)/.zprofile
source ~/.zprofile
```
2. Bash
```
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/$(whoami)/.bash_profile
source ~/.bash_profile
```

#### Homebrew下载or安装失败的网络问题解决办法
加速器代理配置：
```
export http_proxy="http://127.0.0.1:7897"
export https_proxy="http://127.0.0.1:7897"
```
查看当前使用的代理：
```
echo $http_proxy
echo $https_proxy
```
取消代理设置：
```
unset http_proxy
unset https_proxy
```
安装homebrew下载失败，可以尝试清华的镜像源：
```
/bin/bash -c "$(curl -fsSL https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/install.sh)"
```
若安装失败，可尝试
```
brew tap https://mirrors.tuna.tsinghua.edu.cn/git/homebrew.git
```

#### 替换USTC镜像
```
export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.ustc.edu.cn/brew.git"
brew update
```
若用户设置了环境变量 `HOMEBREW_BREW_GIT_REMOTE`，则每次运行 `brew update` 时将会自动设置远程。推荐用户将环境变量 `HOMEBREW_BREW_GIT_REMOTE` 加入 shell 的 profile 设置中。
```
# 对于 bash 用户
echo 'export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.ustc.edu.cn/brew.git"' >> ~/.bash_profile

# 对于 zsh 用户
echo 'export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.ustc.edu.cn/brew.git"' >> ~/.zshrc
```
重置为官方地址：
```
unset HOMEBREW_BREW_GIT_REMOTE
git -C "$(brew --repo)" remote set-url origin https://github.com/Homebrew/brew
```
注意：
	重置回默认远程后，用户应该删除 shell 的 profile 设置中的环境变量 `HOMEBREW_BREW_GIT_REMOTE` 以免运行 `brew update` 时远程再次被更换。
	若之前使用的 `git config url.<URL>.insteadOf URL` 的方式设置的镜像，请手动删除 `config` 文件(一般为 `~/.gitconfig` 或仓库目录下的 `.git/config`)中的对应字段。

---
### 打开软件报错
1. 遇到picgo报错：xxx **已损坏**，无法打开。终端输入：
```
sudo xattr -r -d com.apple.quarantine 你的APP路径
```
	APP 路径的获取方法：打开 “访达”（Finder）进入 “应用程序” 目录，找到该软件图标，将图标拖到终端窗口

2. 因为苹果进行一系列**安全认证**，你在打开某一软件的时候是否遇到了“无法打开XXX，因为Apple无法检查其是否包含恶意软件。
	解决方法一:
	在系统偏好设置-> 安全性与隐私-> 通用中启用该应用
	解决方法二：
	按住Control键点按应用, 然后打开，这样会把应用增加到白名单中许可执行。
	解决方法三：
	在应用程序->实用工具中找到终端，打开，执行下面一条命令，禁用新安全检查即可。
	sudo spctl --master-disable

---
### 获取Mac管理员权限
```
sudo su
```

---
### anaconda和pycharm配置
https://blog.csdn.net/u014548562/article/details/137238124

---
