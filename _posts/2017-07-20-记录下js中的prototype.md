---
layout: post-layout
pageclass: article
pagename: post
---

### 看了MDN的说明，

大概了解了prototype的用法，说是 js中没有子类这种设定，所以，新建的对象，想要继承，
之前对象（得是一个基类对象）的属性就得用prototype

<pre>
<code>
  var Person = function() {
  this.canTalk = true;
  this.greet = function() {
    if (this.canTalk) {
      console.log('Hi, I\'m ' + this.name);
    }
  };
};

var Employee = function(name, title) {
  this.name = name;
  this.title = title;
  this.greet = function() {
    if (this.canTalk) {
      console.log("Hi, I'm " + this.name + ", the " + this.title);
    }
  };
};
Employee.prototype = new Person();

var Customer = function(name) {
  this.name = name;
};
Customer.prototype = new Person();

var Mime = function(name) {
  this.name = name;
  this.canTalk = false;
};
Mime.prototype = new Person();

var bob = new Employee('Bob', 'Builder');
var joe = new Customer('Joe');
var rg = new Employee('Red Green', 'Handyman');
var mike = new Customer('Mike');
var mime = new Mime('Mime');
bob.greet();
joe.greet();
rg.greet();
mike.greet();
mime.greet();
</code>
</pre>

输出：
<pre>
<code>
Hi, I'm Bob, the Builder
Hi, I'm Joe
Hi, I'm Red Green, the Handyman
Hi, I'm Mike
</code>
</pre>

可以看出来相同属性的不同值被用于各个不同的构造对象中，然后再用后面这五个构造对象的原型继承基类Person（直接.prototype=），
最后再实例化，应该说是一个很简单的实例了
