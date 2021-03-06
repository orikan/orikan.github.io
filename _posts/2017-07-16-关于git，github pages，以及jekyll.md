---
layout: post-layout
pageclass: article
pagename: post
myvariable: '{{ site.date }}'
---

## 自己在这段时间使用git、github pages以及jekyll上做点简单小结

git一般用作版本管理工具，要使用这个工具首先得有github帐号，

然后下载就可以了 windows上有直接的客户端git bash[git 客户端的地址](https://git-scm.com/)

linux上，我用的是ubuntu系统，安装命令是

<code>~ # apt-get install git</code>

当前使用的git 版本为2.7.4

官网已经有version 2.13.2，但是我本地升级的时候却表示已经是最新版本，

关于用法，值得注意的是， windows上的git命令需要在git 客户端的git bash上运行，原版cmd没用

我一开始用到的命令：
<code>~ $ git status </code>查看当前目录的git 工作状况，
对于git来说，一个目录下的文件状态一般有x种:
1. add 前，文件的(未跟踪，未被git跟踪的文件所有git 的命令都不会有效果)

2. added,已跟踪，跟踪文件是git 工作的重要的基础，
使用命令: 
 <code> ~ $ git add [filename]</code>,
 也可以使用 <code>.</code>代替<code>[filename]</code>， <code>.</code>表示当前目录下所有文件,

3. 已修改，此文件仍然需要用 git add 添加

4. 已提交， 使用 <code>~ $ git commit [filename] -m [commitmessage]</code>
命令进行提交

5. 已推送， 此文件使用<code>~ $ git status </code>查看会提示与上游分支一样，无需提交
推送命令<code>~ $ git push [<选项>] [<仓库> [<引用规格>...]]</code>


关于 github pages， 使用是没什么复杂的，

新建一个名为 YOURNAME.github.io 的库就可以了

再clone到你本地。

关于 jekyll的，


安装:

一般使用linux系统安装，windows上建议安装ubuntu的虚拟机

如果硬是想在windows上装请看这个地方

><h3>Jekyll on Windows</h3>
>While Windows is not an officially-supported platform,
it can be used to run Jekyll with the proper tweaks. 
>This page aims to collect some of the general knowledge and lessons that have been unearthed by Windows users.

<a href="https://jekyllrb.com/docs/windows/">你可以在这里找到这句话，以及安装方法</a>

在ubuntu系统上安装好ruby后gem就有了,ruby的安装方法[RubyChina](https://ruby-china.org/wiki/install_ruby_guide)

接下来就是安装kekyll了:
<code>~ $ gem install jekyll bundler</code>

我安装的版本是 jekyll 3.5.0

如何快速开始一个jekyll项目:
<pre>
<code>~ $ jekyll new my-awesome-site</code>
<code>~ $ cd my-awesome-site</code>
<code>~/my-awesome-site $ bundle install</code>
<code>~/my-awesome-site $ bundle exec jekyll s</code>
# => 打开浏览器 http://localhost:4000
</pre>

初始的项目算是本地搭建好了，学习jekyll首先得弄懂它的配置文件“ _config.yml”及各项配置,
关于配置也是有文档说明请在jekyll的中文站查看[JekyllCn](http://jekyllcn.com/)

我只记一下我的问题，

baseurl 的设置会让你在访问这个jekyll页面时只能使用url/baseurl的形式访问，所以不设置baseurl地址还短一点

还有一些设置参数都可以自定义，

例如日期 date，想要获得配置文件中的date 只需要在页面中使用liquid的模板语言的表达式: 
{% raw %}
<code>
  {{ site.date }}
</code>
{% endraw %}
