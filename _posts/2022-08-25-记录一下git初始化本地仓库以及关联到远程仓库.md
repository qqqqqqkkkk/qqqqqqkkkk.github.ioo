---
layout: post
title: 记录一下git初始化本地仓库以及关联到远程仓库
share-img: /assets/img/one.png
---
## 动机
主要是之前记录的博客都感觉写的不咋地，想着重新建一个git仓库并且重新用这个仓库写博客，可是却忘了git的操作了，所以来记录一下，以免以后忘记

## 操作
### 第一次
1. 初始化本地仓库
 win+R打开cmd，切换到你的准备用于当作本地仓库的文件夹下，然后进行
 ~~~git
 git init
~~~
2. 创建仓库文件
把你所需要上传到远程仓库的文件放到你要当作本地仓库的文件夹下

3. 装载你要上传的文件
~~~git
git add .
~~~
4. 给你本次上传的文件一个描述
~~~git
git commit -m "newfile"
~~~
5. 与远程仓库建立连接（仅仅是第一次所需要）
~~~git
git remote add orign  https://github.com/qqqqqqkkkk/qqqqqqkkkk.github.io.git(这里改成你的)
~~~
6. 将文件推送过去(仅仅是第一次所需要)
~~~git
git push origin master -u
~~~
<hr/>
<b>ok!上面就是全部操作，下面我来说一下第n次该如何更新自己的博客（github远程仓库）（n>=2）

### 第n次
1. 装载你的文件
在你的blog文件夹下执行
~~~git
git add .
~~~
2. 给你此次的新增加文件或对更新的老文件进行描述
~~~git
git commit -m "update"
~~~
3. 提交
~~~git
git push
~~~
<hr/>
<b>恭喜你，已经全部成功了！</b>

## 最后
这是我发布的第一篇博客，仅仅用于记录自己的操作

## 后续 
我在提交的时候出了一个问题
~~~cmd
 OpenSSL SSL_read: Connection was reset, errno 10054
 ~~~
 我一开始还以为是我操作有问题，但是经过用网上大神的解决方案成功解决掉该问题：
 ~~~git
 git config --global http.sslVerify "false"
~~~
这样就能成功了！
