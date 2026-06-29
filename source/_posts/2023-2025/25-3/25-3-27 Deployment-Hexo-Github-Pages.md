---
title: 'Blog Deployment: Hexo Github-Pages'
tags:
  - blog-deployment
  - hexo
  - butterfly
categories:
  - 2023-2025
  - 25-3
date: 2025-03-27 16:36:08
---
This article aims to introduce a method to deploy the personal blog based on Hexo, Github and Obisidian.

---

## Environment
- OS: windows
- Tools: Node.js, VS Code, git

---
## Hexo
Download and install ***Node.js*** https://nodejs.org/en
Download and install ***git*** https://git-scm.com/downloads/win
Open the ***powershell*** or ***cmd*** and install **Hexo**, excute:
```
npm install -g hexo-cli
```
To initialize hexo:
Create new folder named 'xx-blog' (whatever u like)
Enter your blog folder, input ***cmd*** in the navigation bar 
Also, you can choose right click to ***Open Git Bash here*** and excute:
```
hexo init
```
If you meet the problem with network, like error: *RPC failed; curl 28 OpenSSL SSL_read: Connection was reset*, you can try to excute:
```
git config --global http.sslVerify "false"
```
After the initialization, you can try to choose a preferable theme from the official website
https://hexo.io/themes/
Download the theme and put the decompressed content into the folder ***themes***.
There are two places to be modified to make your theme working.
Firstly, you should change the theme name in ***_config.yml***:
```
theme: landscape -> xxx (your theme's name)
```
Secondly, you should chage the name of ***_config.landscape.yml*** to ***_config.xxx.yml***.

---
## Github Pages
Create a new repository named ***usrname.github.io*** 
ps: One Github account can only create one Github Page

Git global config and generate SSH key
open your ***cmd*** or ***git bash***:
```
git config --global user.name "usrname"
git config --global user.email "email"
ssh-keygen -t rsa -c 'email'

# show your SSH key
cat ~/.ssh/id_rsa.pub
```

Open your Github -> Settings -> SSH and GPG keys -> ***New SSH key***
input your SSH key and save

Open the ***_config.yml***, modify the url and deployment:
```
# url
url: https://usrname.github.io

# deployment
deploy:
  type: 'git'
  repo: 'https://github.com/usrname/usrname.github.io.git'
  branch: 'master'
```

Enter in your blog folder, open ***git bash***, insatall deployment plugin and deploy your hexo on Github
```
npm install hexo-deployer-git --save

# generate your hexo content
hexo g

# deploy your hexo on Github
hexo d
```

If you meet problems of *Failed to connect to github.com port 443*, you can try use VPN.
```
# socket 5
git config --global http.proxy socks5 127.0.0.1:7890
git config --global https.proxy socks5 127.0.0.1:7890

# http
git config --global http.proxy 127.0.0.1:7890
git config --global https.proxy 127.0.0.1:7890

# find the VPN
git config --global --get http.proxy
git config --global --get https.proxy

# cancle the VPN
git config --global --unset http.proxy
git config --global --unset https.proxy
```

---
## Domain Name
If you have a domain name, and you wanna connect it with your Github Pages ***usrname.github.io***. I will show a case based on Tencent cloud.

Firstly, open ***cmd*** to get your Github Pages IP address:
```
ping ip usrname.github.io
```
Then, you should add two records in the CDNS:
![](25-3-27CDNS.png)
@ -> A -> IP address
www -> CNAME -> ***usrname.github.io***

Open your local blog folder, enter in the ***public***, create a document named ***CNAME***.
**Attention: No File Format**
Add your domain name in CNAME, and don't forget to re-deploy it.
If it succeeds, you can see your domain name in Github Pages

![](25-3-27Github%20Pages.png)