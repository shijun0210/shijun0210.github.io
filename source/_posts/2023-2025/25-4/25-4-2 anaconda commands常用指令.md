---
title: anaconda commands常用指令
categories:
  - 2023-2025
  - 25-4
tags:
  - commands
  - anaconda
date: 2025-04-02 18:22:00
---
查看anaconda配置信息：
conda info

查看虚拟环境列表：
conda env list

anaconda换源：
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes

更改anaconda虚拟环境默认安装位置：
conda config --add envs_dirs D:\software\anaconda\envs

新建虚拟环境：
conda create -n yourname python=3.7

启用虚拟环境
conda activate yourname

删除虚拟环境
conda remove -n yourname --all

指定源安装
pip install opencv-python -i https://pypi.tuna.tsinghua.edu.cn/simple