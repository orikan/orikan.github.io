---
layout: post-layout
pageclass: article
pagename: post
---

## 我在安装vue时遇到的麻烦

### <code>...
Failed at the phantomjs-prebuilt@2.1.14 install script
...</code>

这个phantomjs下载的问题是由于我的网络引起的，为此搜索了下这句话，发现npm官方文档中就有[解决](https://www.npmjs.com/package/phantomjs)

默认的源是在[](https://bitbucket.org/ariya/phantomjs/downloads)，我直接下载速度奇慢，而且还断连，

还有一个可选源[](http://cnpmjs.org/downloads),这个下载起来就快了，

我是用回到工作目录打开终端，为项目独立配置.npmrc 更改源地址这个办法解决的,

在工作目录下新建名为 <code>.npmrc</code>的文件,

在里面插入这句,
<pre>phantomjs_cdnurl=http://cnpmjs.org/downloads</pre>

保存退出编辑器，
重新 npm install，这速度比起之前不要太顺畅。

### 有新问题再更新
---------
