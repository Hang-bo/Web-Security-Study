## arguments使用

- 不清楚传递参数的个数

- 只有函数中才有arguments对象，而且每个函数都内置；好了这个arguments

- 存储了所有传递过来的实参
- 伪数组，有length属性
- 按照索引的方式进行存储

## 函数声明两种方式

- 关键字(命名函数)

  ```javascript
  function fn(){
      
  }
  fn();
  ```

- 函数表达式(匿名函数)

  ```javascript
  var fn = function() {
      
  }
  fn();
  ```

  

## 预解析

- 运行js代码分为两步
  - 预解析：所有的var和function提升到最前面
    - 变量解析：所有的变量声明提升到当前的作用域最前面，**不提升赋值操作**
    - 
  - 代码执行：按照书写的顺序从上往下执行

## 对象

#### 创建对象

属性和方法

- 字面量

  - 键值对——属性名(键) ： 属性值(对)
  - 每个用逗号隔开
  - 方法的冒号后面跟着匿名函数

  ```javascript
  var obj = {
      uname:'zhang',
      age:18,
      sex:'男',
      sayHi:function() {
          console.log('hi~');
      }
  }
  ```

  - 使用
    - 对象名.属性名;
    - 对象名['属性名'];
    - 对象名.方法名( );

- new Object

  每个属性方法用分号结束

  等号 = 赋值

  ```javascript
  var obj = new Object();
  obj.name = '张三丰';
  obj.sayHi = function() {
      console.log('hi~');
  }
  ```

  

- 利用构造函数创造对象（对象的实例化）

  - 构造函数名字首字母要大写
  - 不需要return，可以返回结果
  - new调用构造函数

```javascript
function Star(uname, age, sex) {
    this.name = uname;//定义属性并赋值
    this.age = age;
    this.sex = sex;
    this.sing = function(song) {//定义方法并赋值
        console.log(song);
    }
}3
var ldh = new Star('刘德华', 18, '男');
```

#### 判断对象有无属性

```javascript
// 有一个对象 来判断是否有该属性 对象[ 属性名]
为
var o = {
	age: 18
}
if (o['sex']) 
	console.log('里面有该属性');
else (
	console.log("没有该属性');
}                
```

#### new关键字

- 在内存中创造一个新对象
- this指向一个新的对象
- 执行构造函数的代码，将实参赋给给这个新对象添加属性和方法
- 返回这个新对象

## Math.round

不能简单的理解为四舍五入

round方法就是在基础值上加0.5向左取整

```javascript
round(-1.5) = -1.5 + 0.5 =  -1向左取整就是-1
```

## Data对象

使用前需要提前声明

```javascript
var date = new Date();
```

#### 当前时间总毫秒数

```
var nowTime = +new Date();返回的是当前时间总的毫秒数
var nowTime = +new Date(Time);返回的是用户输入时间总的毫秒数
```

## Array数组对象

#### 翻转排序

```javascript
// 1.翻转数组
var arr = ['pink', 'red', "blue'];
arr.reverse();
console.log(arr);
// 2.数组排序(冒泡排序)
var arr1 = [13，4，77，1, 7];
arr1.sort(function(a, b) {
    return a - b; //升序的顺序排列
    return b - a; // 降序的顺序排列
}
```

#### 获取索引

indexof(数组元素) 作用就是返回该数组元素的索引号 从前面开始查找

它只返回第一个满足条件的索引号

它如果在该数组里面找不到元素，则返回的是 -1

```javascript
var arr = ['red', 'green' , 'pink'];
console.log(arr.indexOf('blue'));
// 返回数组元素索引号方法 lastIndexof(数组元素) 作用就是返回该数组元素的索引号 从后面开始查找
var arr = ['red','green' ,"blue','pink' ,'blue'];
console.log(arr.lastIndexof('blue')); // 4
```

#### 转换字符串

```javascript
// 1.tostring() 将我们的数组转换为字符串
var arr = [1, 2, 3];
console.log(arr.tostring()); // 1,2,3
// 2.join(分隔符)
var arr1 = ['green','blue', 'pink'];
console.log(arr1.join()); // green,blue,pink
console.log(arr1.join('-')); // green-blue-pink
console.log(arr1.join('&')); // green&blue&pink
```

## 字符串

#### 返回位置

```javascript
// 字符串对象 根据字符返回位置 str.indexof("要查找的字符 ，[起始的位置])
var str =改革春风吹满地，春天来了; 
console.log(str.indexof("春'));
console.log(str.indexof("春'，3)); // 从索引号是 3的位置开始往后查找
```

#### 根据位置返回字符

```javascript
// 1.charAt(index) 根据位置返回字符
var str = 'andy';
console.log(str.charAt(3));// 遍历所有的字符
for (var i = 0; i < str.length; i++) {
	console.log(str.charAt(i));
}
// 2.charCodeAt(index) 返回相应索引号的字符ASCII值 目的: 判断用户按下了那个键
console.log(str.charCodeAt(0)); // 97
// 3.str[index] H5 新增的
console.log(str[0]); // a
```

#### 替换字符

```javascript
// 1.替换字符 replace('被替换的字符’，'替换为的字符') 它只会替换第一个字符
var str = andyandy';
console.log(str.replace('a','b'));
// 有一个字符串abcoefoxyozzopp’ 要求把里面所有的 o 替换为 *
var str1 = 'abcoefoxyozzopp';
while (str1.indexof('o') !== -1){ 
	str1 = str1.replace('o', '*');
}
console.log(str1); 
```

#### 转换为数组

```javascript
//split('分隔符')
var str2 = 'red,pink,blue'; console.log(str2.split(',"));                       var str3 ='red&pink&blue';                         
                                                   console.log(str3.split('&'));
```

## DOM操作

#### getElementById获取元素

```javascript
<div id="time">2019-9-9</div>
<script>
// 1.因为我们文档页面从上往下加载，所以先得有标签 所以我们script写到标签的下面
// 2.get 获得 element 元素 by 通过 驼峰命名法
// 3.参数 id是大小写敏感的字符串
// 4.返回的是一个元素对象
var timer = Idocument.getElementById('time');
console.log(timer);
console.log(typeof timer);
// 5.console.dir 打印我们返回的元素对象 更好的查看里面的属性和方法
console.dir(timer);
</script>
```

#### getElementsByTagName获取某些元素

```javascript
var ol = document.getElementById('ol');
console.log(ol.getElementsByTagName( 'li'));
```

#### getElementsByClassName

```javascript
document.getElementsByClassName('类名');
// 根据类名返回元素对象集合
```

#### querySelector

```javascript
document .querySelector('选择器');
// 根据指定选择器返回第一个元素对象
```

#### querySelectorAll

```javascript
document.querySelectorAll('选择器')
// 根据指定选择器返回
```

#### 获取body元素

```javascript
// 1.获取body 元素
var bodyEle = document.body;
console.log(bodyEle);console.dir(bodyEle);
```

#### 获取html元素

```javascript
// 2.获取htm1 元素
var htmlEle = document.documentElement;
console.log(htmlEle);
```

### 事件

#### 三要素

事件源 

事件类型 

事件处理程序

```javascript
<script>
//(1) 事件源 事件被触发的对象 谁 按钮
var btn = document.getElementById( 'btn' );
//(2) 事件类型 如何触发 什么事件 比如鼠标点击(onclickD 还是鼠标经过 还是键盘按下
//(3) 事件处理程序 通过一个函数赋值的方式 完成
btn.onclick = function() {
	alert('点秋香');
}
</script>
```

#### 常见的鼠标事件

鼠标事件
onclick

鼠标点击左键触发

onmouseover

鼠标经过触发

onmouseout

鼠标离开触发

onfocus

获得鼠标焦点触发

onblur

失去鼠标焦点触发

onmousemove

鼠标移动触发

onmouseup

鼠标弹起触发

onmousedown

鼠标按下触发



#### 改变元素内容

```javascript
btn.onclick = function() {
	// div.innerText = '2019-6-6';
    div.innerText = getDate();
}
```

innerText 和 innerHTML的区别

```javascript
// 1.innerText 不识别htm1标签 非标准 去除空格和换行
var div = document.querySelector( 'div');
div.innerText ='<strong>今天是:</strong> 2019';
// 2.innerHTML 识别htm标签 W3C标准 保留空格和换行的
div.innerHTML =<strong>今天是: '</strong> 2019';
// 这两个属性是可读写的 可以获取元素里面的内容
var p = document.querySelector('p');
console.log(p.innerText);console.log(p.innerHTML);
```

#### 修改元素属性

```javascript
<script>
// 修改元素属性 src
// 1. 获取元素
var ldh = document.getElementById( 'dh');
var zxy = document.getElementById( 'zxy' );
var img = document.querySelector( 'img');
// 2.注册事件 处理程序
zxy.onclick = function() {
	img.src = 'images/zxy.jpg';
    img.title =张学友思密达';
}
ldh.onclick = function() {
	img.src =images/ldh .jpg';
    img.title =刘德华';
}
</script>
还有如
input.value = 'sdsadas';
this.disabled = true;
```

#### 修改样式

```javascript
<style>
div {
	width: 200px;
	height: 200px;
    background-color:pink;
}
</style>
<script>
// 1. 获取元素
var div = document.querySelector('div');
// 2.注册事件 处理程序
div.onclick = function() {
// div.style里面的属性 采取驼峰命名法
this.style.backgroundColor = 'purple';
this.style.width = '250px';
}
```

#### 自定义属性操作

```javascript
<script>
    var div = document.querySelector('div') ;
	// 1.获取元素的属性值
	// (1) element.属性
	console.log(div.id);
	//(2) element.getAttribute(’属性) get得到获取 attribute 属性的意恩 我们程序员自己添加的属性我们称为自定义属性 index
    console.log(div.getAttribute('id'));
	console.log(div.getAttribute('index'));
	// 2.设置元素属性值
	// (1) element.属性= 值!
	div.id = 'test';//id值
	div.className = 'navs';//类名
	// (2) element.setAttribute(属性’，值); 主要针对于自定义属性
	div.setAttribute('index'， 2);
	div.setAttribute('class',footer'); // class 特殊 这里面写的就是class 不是className
</script>
```

- 设置H5自定义属性

```javascript
H5规定自定义属性data-开头做为属性名并且赋值
比如 <div data-index="1"></div>

或者使用JS 设置
element.setAttribute( 'data-index', 2)
```

```javascript
<div getTime="20” data-index="2" data-list-name="andy"></div>
<script>
var div = document.querySelector( 'div');
//console.log(div.getTime);
console.log(div.getAttribute('getTime'));
div.setAttribute('data-time'， 20);
console.log(div.getAttribute('data-index'));
console.log(div.getAttribute('data-list-name'));
// h5新增的获取自定义属性的方法 它只能后去data-开头的
// dataset 是一个集合里面存放了所有以data开头的自定义属性
console.log(div.dataset);
console.log(div.dataset.index);
console.log(div.dataset['index']);
// 如果自定义属性里面有多个-链接的单词，我们
console.log(div.dataset.listName);
console.log(div.dataset['listName']);
```

