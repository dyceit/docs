# BOM浏览器对象模型

## BOM：

浏览器对象模型（Browser Object Modal）

## Window对象：

1. 所有浏览器都支持 window 对象。它表示浏览器窗口。
2. 所有 JavaScript 全局对象、函数以及变量均自动成为 window 对象的成员。
3. 全局变量是 window 对象的属性。
4. 全局函数是 window 对象的方法。
5. 包含：Location对象、History对象、Navigator对象、Screen对象、存储对象。

### Window 对象常用属性：

```javascript
var win = window.open("","_blank","width=100,height=100");
var bool = win.closed;

window.document.getElementById(""); // DOM操作

window.frames[0].location = "";
window.opener; // 来源窗口
window.parent; // frame窗口父窗口
window.self; // 返回对当前窗口的引用。等价于 Window 属性
window.top; // 最顶层的父窗口

window.screenTop;
window.screenLeft;
window.screen.width;

window.history.go(-1);
window.history.back();
window.history.forward();

// 文档显示区
window.innerWidth;
window.innerHeight;

// 返回窗口的外部宽度/高度，包含工具条与滚动条。
window.outerWidth;
window.outerHeight;

// 在浏览器中存储 key/value 对。
// localStorage：没有过期时间
// sessionStorage：关闭窗口或标签页之后将会被删除
localStorage.setItem("lastname", "Smith"); 
var lastname = localStorage.getItem("lastname");
localStorage.removeItem("lastname");

window.location;
{
    "href":"http://www.mangoerp.com:8080/erp/#/erp/product/outbox",
    "ancestorOrigins":{},
    "origin":"http://www.mangoerp.com:8080",
    "protocol":"http:",
    "host":"www.mangoerp.com:8080",
    "hostname":"www.mangoerp.com",
    "port":"8080",
    "pathname":"/erp/",
    "search":"",
    "hash":"#/erp/product/outbox"
}

window.location.assign(url)    // 载入一个新的文档
window.location.reload()    // 重新载入当前文档
window.location.replace(url)   // 用新的文档替换当前文档

// Navigator 对象包含有关浏览器的信息。
txt = "<p>浏览器代号: " + navigator.appCodeName + "</p>";
txt+= "<p>浏览器名称: " + navigator.appName + "</p>";
txt+= "<p>浏览器版本: " + navigator.appVersion + "</p>";
txt+= "<p>启用Cookies: " + navigator.cookieEnabled + "</p>";
txt+= "<p>硬件平台: " + navigator.platform + "</p>";
txt+= "<p>用户代理: " + navigator.userAgent + "</p>";
txt+= "<p>用户代理语言: " + navigator.systemLanguage + "</p>";
txt+= "<p>浏览器连网状态: " + navigator.onLine + "</p>";
txt+= "<p>浏览器网络类型: " + navigator.connection.effectiveType + "</p>"; // 4g
document.getElementById("example").innerHTML=txt;
```

### Window 对象常用方法：

```javascript
// 弹框
alert("Hello");
var bool = confirm("Hello");
var str = prompt("Hello","Hello");

// 窗口开关
window.open();
window.close();

// 窗口焦点
window.focus();
window.blur();

// 在指定的毫秒数后调用函数或计算表达式
var t = setTimeout(function(){ alert("Hello"); }, 3000);
clearTimeout(t);

// 按照指定的周期（以毫秒计）来调用函数或计算表达式
var t = setInterval(function(){ alert("Hello"); }, 3000);
clearInterval(t);

window.scrollTo(100,500); // 滚动条位置
window.resizeTo(500,500); // 调整窗口大小
window.moveTo(500,500); // 窗口相对屏幕位置
```

