---
layout: post-layout
pageclass: article
pagename: post
---
## 关于box-sizing与offsetWidth

今天看手册，有box-sizing的content-box、padding-box与border-box三个值，
我以前好像在某地方看到过这个设置，当时是那个页面是把box-sizing: border-box 这样设置了。

因为当时拿过来用好像对布局没啥影响，就没有深究，今天看到手册上写的内容，突然回忆起来了，

我去试了试，发现，padding-box这个值好像并没有什么用，设置box-sizing: padding-box;但是没有反应 

倒是border-box生效了，于是如下设置一个很丑的框
<textarea id="input" style="color: #707070;width: 100%; background: #303030;">
<div style="width:100px;height: 100px;padding: 50px;border: 50px solid red;background-color: blue;"> TTTT </div>
</textarea>

<div id="boxSizing" style="width:100px;height: 100px;padding: 50px;border: 50px solid red;background-color: blue;"> TTTT </div>

<span id="width-content">offsetWidth点下面的按钮.</span>
<br>
<span id="width-client">clientWidth点下面的按钮.</span>

<input type="button" value="content-box">
<input type="button" value="border-box">
<input type="button" value="padding-box">

<script>
  let oBtnContent= document.getElementsByTagName('input')[0];
  let oBtnBorder= document.getElementsByTagName('input')[1];
  let oBtnPadding= document.getElementsByTagName('input')[2];

  let oBoxSizing= document.getElementById('boxSizing');
  let oOffsetWidth=document.getElementById('width-content');
  let oClientWidth=document.getElementById('width-client');
oBtnContent.onclick=oBtnBorder.onclick=oBtnPadding.onclick=function() {
  oBoxSizing.style.cssText= oBoxSizing.style.cssText + 'box-sizing: '+ this.value + ';';
  oOffsetWidth.innerHTML = '很丑的盒子的offsetWidth: '+oBoxSizing.offsetWidth + 'px';
  oClientWidth.innerHTML = '很丑的盒子的clientWidth: '+oBoxSizing.clientWidth + 'px';
  console.log(this.value);
  }
</script>
 
情况已经很明朗了,设置为border-box会使盒子变小，其实是使盒子的content部分变小了
我之前的困惑就是这个offsetWidth怎么算，

这样来看在content-box下盒子的content宽度就是style里的width offsetWidth

