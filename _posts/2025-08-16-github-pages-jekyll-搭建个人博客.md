---
layout: post
title: Github pages + jekyll 搭建个人博客
date: 2025-08-16 23:38 +0800
tags: [零散]
description: github仓库创建/本地开发环境/其他配置/个性化配置
---

## 01/ Github创建仓库

1. 使用[Chirpy 模板](https://github.com/cotes2020/chirpy-starter)创建仓库：【Use this template】——【Create a new repository】

  - 新存储库必须命名为 `<username>.github.io`， `username` 为小写 GitHub 用户名

2. 新仓库右上角设置 —— pages设置 —— 将Source修改为 Github Action

## 02/ 本地Jekyll开发 环境

### 1. Ruby、Jekyll、bundler环境搭建

- [官方文档](https://jekyllrb.com/docs/installation/windows/)

1. 安装 [Ruby](https://rubyinstaller.org/downloads/)
	- 安装完成后会跳出cmd，输入3（MSYS2 and MINGW development tool chain）
2. 安装 Jekyll：`gem install jekyll bundler`
	- 如果运行不了需要换国内源：[清华源 Ruby Gems](https://mirrors.tuna.tsinghua.edu.cn/help/rubygems/)
3. 检查 Jekyll 安装是否成功并查看版本：`jekyll -v` 

### 2. 本地开发流程

- 本地启动 Jekyll（本地拉取已创建的gihub仓库，在其中执行命令）
  - 本地 Jekyll 环境构建后需要将 Gemfile 中的 source 换源为清华源
  	
  	```shell
  	bundle install        # 构建本地环境
  	bundle exec jekyll b  # 编译
  	bundle exec jekyll s  # 启动
  	```
  	
  	- Gemfile文件，指定了想要使用的gem的位置和版本
  	
  - 本地访问：http://127.0.0.1:4000 

- git提交
```shell
git add .             # 将本地文件存到暂存区  
git commit -m "说明"   # 将暂存区文件提交到本地仓库  
git remote add origin https://github/GitHub用户名.github.io  #将本地仓库关联到GitHub仓库  
git push -u origin main  #本地仓库上传到GitHub仓库（可能会要求输入用户名和密码）
```

## 03/ 个性化配置


### 基本配置

- `_config.yml`文件

```yml
lang: zh-CN  # 语言
timezone: Asia/Shanghai  # 时区

title: Xylia    # 主标题
tagline: Xylia's Blog   # 主标题介绍

url: "https://xyllya.github.io/"  # 仓库地址

github:
  username: Xyllya  # 左下角Github跳转

social:
  name: Xylia   # 保留权利人姓名，在网页中间最下面
  email: always1710@163.com   # 左下角Email跳转
  links:
    #  https://twitter.com/username # change to your Twitter homepage
    - https://github.com/Xyllya # change to your GitHub homepage
    # Uncomment below to add more social links
    # - https://www.facebook.com/username
    # - https://www.linkedin.com/in/username

theme_mode: # [light | dark]  色调

cdn:
avatar: 'assets/img/000.jpg'  # 左侧栏头像图片
```



## 04/其他配置

### 创建文章

- [官方教程](https://chirpy.cotes.page/posts/write-a-new-post/)

- 在 `_posts` 目录下创建 YYYY-MM-DD-TITLE.md 文件（固定格式）

- 可以使用插件 [Jekyll-Compose](https://github.com/jekyll/jekyll-compose) 节省创建文件的时间

  ```shell
  # draft：创建一个新的草稿帖子
  # post：创建一个新的帖子
  # publish：发布一个草稿
  
  bundle exec jekyll draft "My New Draft"
  ```

- Front Matter

```yaml
--- 
title: TITLE 
date: YYYY-MM-DD HH:MM:SS +/-TTTT   # 时区 +0800
categories: [TOP_CATEGORIE, SUB_CATEGORIE]  # 支持多级分类，一个逗号一层
tags: [TAG] # TAG names should always be lowercase 
math: true
---
```

- math、mermaid、pin 默认是false，需要可以添加
- description: 文章中简要描述，会显示在首页每篇文章的标题下
- 注意：
  - 文章不能出现连续的两个大括号，会报错，可以在两个大括号中间加空格
  - 文章插入图片，路径要用反斜杠/

## References

- [Github-Pages-+-Jekyll-搭建个人博客](https://xyllya.github.io/posts/Github-Pages-+-Jekyll-%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2/)
