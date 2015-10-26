---
layout: post
title: "Mac显示和隐藏文件"
date: 2015-10-26 14:36:29 +0800
comments: true
categories: Mac
---
  Mac OS X操作系统下显示Mac隐藏文件的命令:
  
    defaults write com.apple.finder AppleShowAllFiles -bool true 
    
  或
  
    defaults write com.apple.finder AppleShowAllFiles  YES
    
<!--more-->
    
  隐藏Mac隐藏文件的命令:
  
    defaults write com.apple.finder AppleShowAllFiles -bool false
    
  或

    defaults write com.apple.finder AppleShowAllFiles  NO
    
  在终端中输入对应命令后，按住finder鼠标点击右键后点击重启开启即可。
    

