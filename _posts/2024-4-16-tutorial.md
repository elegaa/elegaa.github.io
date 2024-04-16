---
title: "How to establish a personal blog using jekyll on MacOS"
date: 2024-04-15
categories: [tutorial]
tags: [blog,MacOS]
---

If you want to estabish your own personal blog, this essey is useful for you!  

如果你想要搭建个人网站的话，这篇帖子将对你非常有用！

# 一、准备工作

需要先准备好GitHub账号，安装git, ruby，jeklly和node.js  

在MacOS中，想要安装以上工具必须先安装Homebrew或者其他可替代的工具

## 安装git，ruby，jeklly和node.js
### 首先安装git

    brew install git

    
配置git  

```
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
```
生成SSH密钥  

```
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
接着按照提示一路回车，默认保存路径为 ~/.ssh/id_rsa。  

将SSH密钥添加到GitHub账户  

通过以下命令复制SSH密钥  

```
pbcopy < ~/.ssh/id_rsa.pub
```
登录到GitHub账户，在 "Settings" -> "SSH and GPG keys" -> "New SSH key"，将刚才复制的SSH公钥粘贴到文本框中并保存。  


### 第二步，安装ruby

由于MacOS有默认的Ruby版本，需要将默认的Ruby版本替换，下载版本管理工具rbenv进行此操作。
```
brew install rbenv
rbenv init
```
安装所需要版本的Ruby
```
rbenv install 3.1.2
```
设置默认使用的Ruby版本
```
rbenv global 3.1.2
```
验证当前的版本
```
ruby -v
```

如果修改版本不成功可能是因为rbenv没有设置到环境中，修改~/.zshrc文件
```
nano ~/.zshrc
```
将以下代码加到该文件中：
```
export PATH="$HOME/.rbenv/bin:$PATH"
eval "$(rbenv init -)"
export RUBY_BUILD_MIRROR_URL=https://cache.ruby-china.com
```
重新加载该文件
```
source ~/.zshrc
```
重复以上步骤再次更新Ruby的默认版本

### 第三步安装jeklly

安装[jeklly](https://jekyllrb.com/docs/continuous-integration/github-actions/) 的指令如下
```
gem install jekyll
```

### 第四步安装node.js

```
brew install node
```
可以使用一下命令验证是否安装成功
```
node -v
npm -v
```

# 二、选择合适的主题

jeklly会提供许多不同特点的模版  
![](/assets/img/2024-04-15 18.40.02.png)
此处选用的是[Chripy](https://chirpy.cotes.page/posts/getting-started/)



## 创建本地仓库开始自定义

登陆GitHub将chirpy模板fork，将其重命名为username.github.io


将模板clone到本地
```
git clone https://github.com/elegaa/username.github.io.git
```



## 安装依赖项

使用VScode打开该项目，打开终端，安装依赖项  
```
bundle
```
修改后，想要本地预览效果可以执行一下命令
```
bundle exec jekyll s
```
几秒钟后，本地服务将发布到http://127.0.0.1:4000。

## 修改 config 进行个性化  

> \# Import the theme  
> theme: jekyll-theme-chirpy
> lang: en
> title:  # the main title
  

# 三、写下第一个博客
在 _posts 文件夹内新建一个 markdown 文件，命名为 2024-10-10-hello world.md，*注意文件名称格式是 YYYY-MM-DD-title.md，输入以下内容。  

> ---  
> title: hello world  
> date: 2023-10-10 21:00:00 +0800  
> categories: []  
> tags: []  
> ---  
>
> hello world!  

一个简单的个人博客文章就完成。  

# 四、部署到GitHub上
进入仓库的 settings 页面，选择 pages。  

将 deloyment source 选择为 GitHub Actions  

在Github项目的页面上打开_config.yml文件，编辑url值并提交修改。  

在终端提交本地项目
~~~
git add .
git commit -m 'custermizing my personal blog'
git push origin main
~~~

最终就可以成功地进入自己的博客啦！

# 五、总结
在创建个人博客的过程中，创建环境可能会频繁出现问题，需要仔细地核对版本号，查阅资料。本篇文章尽量详细地总结了我在搭建个人博客时的步骤以及遇到的一些问题和解决方法。

# 六、参考
https://www.youtube.com/watch?v=m1RYsmOMPLs  
https://sspai.com/post/84492  
https://blog.csdn.net/zpf1813763637/article/details/128340109