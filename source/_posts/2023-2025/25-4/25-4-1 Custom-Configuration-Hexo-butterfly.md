---
title: Custom Configuration Hexo-butterfly
tags:
  - hexo
  - butterfly
categories:
  - 2023-2025
  - 25-4
date: 2025-04-01 22:08:09
---
### Gallery
1. Github New Repository
2. Connect your PC with Github (details can be seen in the article "Deployment Hexo Github Pages")
3. Create a new folder, and open Git Bash
```
git clone git@github.com:Jasper1910/pic_bed.git
# your github SSH
```
4. Create folders and add your pictures, and then, open Git Bash in the path with README
```
git add.
git commit -m "更新图片"
git push
```

Also, PicGo is a popular tool to manage pictures.

---
### Add auto categories
1. install hexo plugins
2. add codes in *_config.yml*
```
npm install hexo-auto-category --save

# Generate categories from directory-tree
# Dependencies: https://github.com/xu-song/hexo-auto-category
# depth: the depth of directory-tree you want to generate, should > 0

auto_category:
	enable: true
	depth:
```

---
### Theme color
If you wanna change the theme color, open the *_config.yml* of butterfly, find codes:
```
# Theme color for customize
# Notice: color value must in double quotes like "#000" or may cause error!

theme_color:
  enable: true
```

---
### Search
1. Install search plugin:
```
npm install hexo-auto-category --save
```
2. Add codes in *_config.yml*:
```
# field, is the range of search, post/page/all
search:    
	path: search.xml    
	field: post    
	content: true
```
3. Modify codes in *_config.butterfly.yml*
```
search:
	# Choose: algolia_search / local_search / docsearch
	# leave it empty if you don't need search
	use: local_search
	placeholder:

local_search:
	enable: true 
```

---
### Subtitle
```
# The subtitle on homepage
subtitle:
  enable: true
  # Typewriter Effect
  effect: true
  # Customize typed.js
  # https://github.com/mattboldt/typed.js/#customization
  typed_option:
  # Source - Call the third-party service API (Chinese only)
  # It will show the source first, then show the content of sub
  # Choose: false/1/2/3
  # false - disable the function
  # 1 - hitokoto.cn
  # 2 - https://api.aa1.cn/doc/yiyan.html
  # 3 - jinrishici.com
  source: false
  # If you close the typewriter effect, the subtitle will only show the first line of sub
  sub:
    - 'A blog about programming, technology, and life.'
```

---
### Background effects
```
canvas_fluttering_ribbon:  
	enable: true  
	mobile: false # usage in the mobile device

canvas_nest:  
	enable: true  
	color: '0,0,255' #color of lines, default: '0,0,0'; RGB values: (R,G,B).(note: use ',' to separate.)  
	opacity: 0.7 # the opacity of line (0~1), default: 0.5.  
	zIndex: -1 # z-index property of the background, default: -1.  
	count: 99 # the number of lines, default: 99.  
	mobile: false
```

---
### Encrypt
1. Download plugin
```
npm install --save hexo-blog-encrypt
```
2. Add codes in *_config.yml*
```
encrypt:
	abstract: please enter the password to view this post
	message: this post is encrypted, please enter the password to view it
	tags:
	- {name: ontology, password: 123456}
	wrong_pass_message: wrong password, please try again
```
3. Add password **or** the encrypted type in your article
```
---  
title: Hello World  
date: 
tags:
	- the encrypted tag
password: 
---
```
see more details in URL: https://github.com/D0n9X1n/hexo-blog-encrypt?tab=readme-ov-file

---
### Modify the post configuration



