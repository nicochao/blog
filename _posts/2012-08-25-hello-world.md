---
layout: post
title: 你好，世界
categories: 测试
---

添加SSH Key到GitHub
在本机设置SSH Key之后，需要添加到GitHub上，以完成SSH链接的设置。

<!-- more -->

1、打开本地C:\Documents and Settings\Administrator.ssh\id_rsa.pub文件。此文件里面内容为刚才生成人密钥。如果看不到这个文件，你需要设置显示隐藏文件。准确的复制这个文件的内容，才能保证设置的成功。

2、登陆github系统。点击右上角的 Account Settings--->SSH Public keys ---> add another public keys

3、把你本地生成的密钥复制到里面（key文本框中）， 点击 add key 就ok了



测试
可以输入下面的命令，看看设置是否成功，git@github.com的部分不要修改：

$ ssh -T git@github.com
如果是下面的反馈：

The authenticity of host 'github.com (207.97.227.239)' can't be established.
RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
Are you sure you want to continue connecting (yes/no)?
不要紧张，输入yes就好，然后会看到：

Hi cnfeat! You've successfully authenticated, but GitHub does not provide shell access.
设置用户信息
现在你已经可以通过SSH链接到GitHub了，还有一些个人信息需要完善的。

Git会根据用户的名字和邮箱来记录提交。GitHub也是用这些信息来做权限的处理，输入下面的代码进行个人信息的设置，把名称和邮箱替换成你自己的，名字必须是你的真名，而不是GitHub的昵称。

$ git config --global user.name "cnfeat"//用户名
$ git config --global user.email  "cnfeat@gmail.com"//填写自己的邮箱
SSH Key配置成功
本机已成功连接到github。

若有问题，请重新设置。常见错误请参考：

GitHub Help - Generating SSH Keys

GitHub Help - Error Permission denied (publickey)

使用GitHub Pages建立博客
与GitHub建立好链接之后，就可以方便的使用它提供的Pages服务，GitHub Pages分两种，一种是你的GitHub用户名建立的username.github.io这样的用户&组织页（站），另一种是依附项目的pages。

想建立个人博客是用的第一种，形如cnfeat.github.io这样的可访问的站，每个用户名下面只能建立一个。

文／CnFeat（简书作者）
原文链接：http://www.jianshu.com/p/05289a4bc8b2
著作权归作者所有，转载请联系作者获得授权，并标注“简书作者”。
<h2>{{ page.title }}</h2>
<p>我的第一篇文章</p>
<p>{{ page.date | date_to_string }}</p>