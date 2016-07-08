---
layout: post
title: ubuntu下的中文显示问题
categories: Ubuntu
---

##一. Ubuntu默认的中文字符编码

<!-- more -->
Ubuntu默认的中文字符编码为zh_CN.UTF-8，这个可以在<code>/etc/environment</code>中看到：

    sudo gedit /etc/environment

可以看到如下内容：

    PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
    LANG="zh_CN.UTF-8"
    LANGUAGE="zh_CN:zh:en_US:en"
第二行即是默认的中文字符编码。

注：可以通过这里修改默认的中文编码字符，比如修改为：zh_CN.GBK。

##二. 添加中文字符编码的方法

###1.直接使用locale-gen

在终端输入命令：

    sudo locale-gen zh_CN.GB18030

即可完成中文字符集的添加。完成后可以转到<code>/usr/lib/locale/</code>
，下面已经有一个zh_CN.gb18030文件夹；在超级终端输入命令：
    
    gedit /var/lib/locales/supported.d/local

可以发现文件中多了一行：zh_CN.GB18030 GB18030。

说明添加成功。

###2.通过修改/var/lib/locales/supported.d/local文件
在终端输入命令行

    sudo gedit /var/lib/locales/supported.d/local
可以看到如下内容：

    zh_CN.UTF-8 UTF-8
    en_US.UTF-8 UTF-8

在文件尾添加中文字符集

    zh_CN.GBK GBK

保存后退出。在终端输入命令：

    sudo dpkg-reconfigure locales

    Generating locales...
    en_AU.UTF-8... done
    en_BW.UTF-8... done
    en_CA.UTF-8... done
    en_DK.UTF-8... done
    en_GB.UTF-8... done
    en_HK.UTF-8... done
    en_IE.UTF-8... done
    en_IN.UTF-8... done
    en_NZ.UTF-8... done
    en_PH.UTF-8... done
    en_SG.UTF-8... done
    en_US.UTF-8... done
    en_ZA.UTF-8... done
    en_ZW.UTF-8... done
    zh_CN.GBK... done
    zh_CN.UTF-8... up-to-date
    zh_HK.UTF-8... done
    zh_SG.UTF-8... done
    zh_TW.UTF-8... done
    Generation complete.

即可生成相应文件<code>/usr/lib/locale/zh_CN.gbk/</code>
最后重启ubuntu。
