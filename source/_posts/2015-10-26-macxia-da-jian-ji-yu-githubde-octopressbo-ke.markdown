---
layout: post
title: "Mac下搭建基于Github的Octopress博客"
date: 2015-10-26 15:39:13 +0800
comments: true
categories: Octopress
---
准备工作：
  确保安装了git（mac上基本自带安装了git）和ruby1.9.3，查看安装版本：

    $ git --version
    git version 2.6.1

    $ ruby -v
    ruby 1.9.3p551 (2014-11-13 revision 48407) [x86_64-darwin15.0.0]

    $ gcc -v
    Configured with: --prefix=/Applications/Xcode.app/Contents/Developer/usr --with-gxx-include-dir=/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.11.sdk/usr/include/c++/4.2.1
    Apple LLVM version 7.0.0 (clang-700.0.72)
    Target: x86_64-apple-darwin15.0.0
    Thread model: posix
    
  从github克隆下Octopress项目文件到本地的octopress目录：
  
     $ git clone git://github.com/imathis/octopress.git
     
   进入Octopress项目根目录：
     
     $ cd octopress
     
   安装相关工具包：
   
     $ sudo gem install bundler
     
   可能出现如下所示错误：
Gem::RemoteFetcher::FetchError: Errno::ECONNRESET: Connection reset by peer - SSL_connect (https://rubygems.org/gems/rake-10.4.2.gem)
An error occurred while installing rake (10.4.2), and Bundler cannot continue.
Make sure that `gem install rake -v '10.4.2'` succeeds before bundling.
   需要通过：
   
     $ vim Gemfile
   
   source换为https://ruby.taobao.org 再执行：
     
     $ bundle install
     $ rake install

建立username.github.io的gibhub page
输入以下命令部署博客

    $ rake generate
    $ rake deploy
    
  博客的source需要单独提交，执行如下命令就可以将source提交到仓库的source分支下
  
    $ git add .
    $ git commit -m 'Initial source commit'
    $ git push origin source
    
    $ git remote -v
    octopress	git://github.com/imathis/octopress.git (fetch)
    octopress	git://github.com/imathis/octopress.git (push)
    origin	git@github.com:seven2013bj/seven2013bj.github.io.git (fetch)
    origin	git@github.com:seven2013bj/seven2013bj.github.io.git (push)

部署前可以在本地预览，输入rake preview之后在浏览器输入http://localhost:4000/来访问
新建博客，文章生成在目录下的source/_posts目录下：

    $ rake new_post["myTitle"]

写完后部署更新文章到github上

    $ rake generate
    $ git add .
    $ git commit -am "Some comment here." 
    $ git push origin source
    $ rake deploy


