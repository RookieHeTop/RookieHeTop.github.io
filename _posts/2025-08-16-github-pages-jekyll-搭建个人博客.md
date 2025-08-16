---
layout: post
title: Github pages + jekyll 搭建个人博客
date: 2025-08-16 23:38 +0800
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

## 03/ 部署基本配置


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

## References

- [Github-Pages-+-Jekyll-搭建个人博客](https://xyllya.github.io/posts/Github-Pages-+-Jekyll-%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2/)
