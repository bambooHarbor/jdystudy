# JS

**基础语法**

变量

var (variable)  代表可变的，js是弱类型语言，在写函数的时候可以不用写数据类型，和返回类型

var可以重复定义和覆盖，且自动类型转换。

还有let 和 const 关键字，var是全局变量，let是局部变量且不可重复（只可以在局部范围定义），const是常数且不可重复。



数据类型

五种，string	number	boolean	object(null)	undefined



== 和 ===的区别

== 会自动转换数据类型 

=== 是不会自动转换数据类型

 例如 "10" == 10  返回true   ； "10" === 10  返回false



boolean详情

false的情况： ""(注意不是" ",这个代表空格，返回true)	0	NaN	null	undefined   总共五种

true的情况：其他不是false的情况



**函数与常用类型**

Array 	string	JSON

函数写法，匿名内部类，lambda表达式，增删改查，取索引之类，

~~~js
//Array
var arr = new Array(1,2);
arr.push();
arr.splice(索引起,连续几个);
~~~

~~~js
//string
var str = "jiandi";
str.chatAt(0);//j
str.indexOf("j");//0
str.substring(0,2);//jd
str.length;//6
~~~

~~~js
//JSON转换JS对象  使用JSON.parse(jsonstr);
var jsobj = JSON.parse(jsonstr);
//JS对象转换JSON  使用JSON.stringify(jsobject);
var jsonstr = JSON.stringify(jsobj);
~~~

**BOM与DOM**

Browser Object Model

Document Object Model

BOM：记住三个常用的；

~~~js
window.location.href();//获取当前网址
window.alert();//弹出窗口
//周期性执行
window.setInterval(() => {
    console.log("每隔两秒运行一次")
} , 2000)
//延迟性执行
window.setTimeout(() => {
    console.log("延迟三秒运行")
}, 3000)
~~~

DOM：记住它是可以获取各种标签、属性名字、id和各种信息的就可以。

~~~js
var img = document.getElementById('h1');
img.src = "img/on.gif";
~~~





















































































































































































































