## Javascript第一章

### 1.2js用法

脚本放在<script></script>>中，可被放置在**<body>**<head>中

- <body>中的javascript

  ```javascript
  <script>
      document.write("<h1>这是一个标题</h1>");
      document.write("<p>这是一个段落</p>");
  </script>
  ```

### 1.3js输出

<font color='red'>JavaScript 没有任何打印或者输出的函数。</font>

- 使用 **window.alert()** 弹出警告框。

- 使用 **document.write()** 方法将内容写到 HTML 文档中。

  - document.write() 仅仅向文档输出写内容,覆盖整个页面

- 使用 **innerHTML** 写入到 HTML 元素。

  - `document.getElementById(id)`使用 id 属性来查找 HTML 元素

  - `innerHTML = "xxxx"` 是用于修改元素的 HTML 内容(innerHTML)

    ```javascript
    <body>
        <h1>我的第一个 Web 页面</h1>
        <p id="demo">我的第一个段落</p>
        <script>
        document.getElementById("demo").innerHTML = "段落已修改。";
        </script>
    </body>
    ```

- 使用 **console.log()** 写入到浏览器的控制台(F12 console)

  - 快捷方式：打log---->直接选择

### 1.4js语法

- **字面量（一个值）**:一般固定值，有如数字字面量，字符串字面量，表达式字面量等等

### 1.7js变量

- var定义变量，必须字母或_或$开头，大小写敏感
- 文本值“ ”或‘ ’ 
- 数值不用引号，若用引号会被看成文本
- 未使用值来声明的变量，值为undefined
- 将变量设置为null进行清空操作
- <font color='red'>字面量（一个值）</font>:一般固定值，有如数字字面量，字符串字面量，表达式字面量等等
- 变量提升：变量可以先使用再声明，但会被被"提升"到方法体的最顶部，**已初始化的不会。**

### 1.8js数据类型

- **值类型(基本类型)**：字符串（String）、数字(Number)、布尔(Boolean)、对空（Null）、未定义（Undefined）、Symbol。

- **引用数据类型**：对象(Object)、数组(Array)、函数(Function)。
- var**动态**指定类型
- 新变量可以用new声明类型

### 1.9js对象

- 对象是一个可以包含多个值的大变量，是对象的容器。
- 键值对（对象属性）写法 **name : value**

### 1.10js函数

```javascript
<body>
    <script>
        function func() {
            document.write(Date());
        }
    </script>
    <button onclick="func()">点我</button>
</body>
```

- 调用函数时，向其传递的数值被称为参数，<font color='red'>变量和参数必须以一致的顺序出现</font>。
- 使用return语句成为带有返回值的函数

### 1.11js作用域

- 局部变量：用var定义在函数内
- 全局变量
  - 函数体内不使用var定义变量
  - 用var定义在函数体外

- 变量生命周期
  - 声明时初始化
  - 局部变量在函数执行完毕后销毁。
  - 全局变量在页面关闭后销毁。

### 1.13js字符串

- 单引号、双引号皆可

- 可以使用索引位置来访问字符串中的每个字符

  ```javascript
  var character = carname[0];
  ```

- 字符串中使用引号
  - 不能与字符串的引号相同
  - <font color='red'>可以在字符串添加转义字符 \ '或 \ "来使用引号</font>

- **求字符串长度**：（）.length
- ===为绝对相等，数据类型和值都必须相等；==为相等，值相等即可

### 1.21js~typeof、null、undefined操作符

-  typeof 操作符来检测变量的数据类型

  - **数组**是一种特殊的对象类型，检测返回**object**
  - **NaN** 的数据类型是**number**
  - **数组(Array)**的数据类型是 **object**
  - **日期(Date)**的数据类型为 **object**

- 设置值为 **null** 来清空，类型检测为**object**

- 设置值为 **undefined** 来清空， 类型检测为 **undefined**。

- ```
  null === undefined   // false，  两者类型不同
  null == undefined    // true，   两者值不同
  ```

### 1.22js类型转换

- 数字转换为字符串

  - 全局方法**String(123)** 

  - Number 方法 **(100+1).toString()** 

- 布尔型转换为字符串
  - 全局方法 **String(false)**
  - Boolean 方法 **true.toString()** 

- 日期转换为字符串

  - 直接**Date()**返回字符串

  - 全局方法 String（new Date()）

  - Date 方法 **toString()**

    ```javascript
    obj = new Date()
    obj.toString()   // 返回 Thu Jul 17 2014 15:38:19 GMT+0200 (W. Europe Daylight Time)
    ```

- 字符串转换为数字
  
- 全局方法 **Number(“3.14”)** 
  
- 一元运算符+

  - ```javascript
    var x = "1";  //x是一个字符串
    var y = +x;   //x是一个数字
    var m = "John";   // y 是一个字符串
    var n = +m;      // x 是一个数字 (NaN)
    ```

- 布尔值转换为数字
  
- 全局方法**Number(flase)**
  
- 日期转换为数字

  ```javascript
  全局方法 Number() 可将日期转换为数字
  d = new Date();
  Number(d)          // 返回 1404568027739
  
  日期方法 getTime()
  d = new Date();
  d.getTime()        // 返回 1404568027739
  ```

- 自动转换类型

  - +号(和“ ”拼凑成一个字符串)

    ```javascript
    5 + null    // 返回 5         null 转换为 0
    "5" + null  // 返回"5null"   null 转换为 "null"
    "5" + 1     // 返回 "51"      1 转换为 "1"
    ```

  - -号

    ```javascript
    "5" - 1     // 返回 4         "5" 转换为 5
    ```

    

### 1.23js正则表达式

- 正则表达式是由一个字符序列形成的**搜索模式**

- 正则表达式修饰符

  - **i（对大小写不敏感的匹配）**
  - **g（全局匹配，查找所有匹配）**
  - **m（执行多行匹配）**

- 通常用于两个字符串方法 

  - **search() 方法** 用于检索指定的子字符串，或，检索与正则表达式相匹配的子字符串，并返回子串的起始位置。

    ```javascript
    使用正则表达式
    var str = "Visit Nowcoder!"; 
    var n = str.search(/Nowcoder/i);
    使用字符串为参数
    var str = "Visit Nowcoder!"; 
    var n = str.search("Nowcoder");
    ```

  - **replace() 方法** 用于在字符串中用一些字符替换另一些字符，或替换一个与正则表达式匹配的子串。

    ```javascript
    用id="demo"操作某个html标签变换内容
    使用正则表达式
    var str = document.getElementById("demo").innerHTML; 
    var txt = str.replace(/microsoft/i,"Nowcoder");
    使用字符串为参数
    var str = document.getElementById("demo").innerHTML; 
    var txt = str.replace("Microsoft","Nowcoder");
    ```

- **RegExp对象**

  - test( )方法：检测一个字符串是否匹配某个模式，返回布尔值

    ```javascript
    var patt = /e/;
    patt.test("The best things in life are free!");
    输出true
    合并为一行：/e/.test("The best things in life are free!")
    ```

  - exec( )方法：检索字符串中的正则表达式的匹配，返回一个数组，其中存放匹配的结果，未找到返回null

    ```javascript
    /e/.exec("The best things in life are free!");
    输出e
    ```

    

### 1.24js异常

- **try** 语句测试代码块的错误。
- **catch** 语句处理错
- **throw** 语句创建自定义错误。
- **finally** 语句在 try 和 catch 语句之后，无论是否有触发异常，该语句都会执行。

### 1.27js严格模式

- 严格模式通过在脚本或函数的头部添加 `"use strict";` 表达式来声明

  ```javascript
  "use strict";
  x = 3.14;       // 报错 (x 未定义)
  不能使用未声明的变量
  消除Javascript语法的一些不合理、不严谨之处，减少一些怪异行为;
  消除代码运行的一些不安全之处，保证代码运行的安全；
  ```

### 1.28js使用误区

- 所有的编程语言，包括 JavaScript，对浮点型数据的精确度都很难确定

  ```javascript
  var x = 0.1;
  var y = 0.2;
  var z = x + y            // z 的结果为 0.3
  if (z == 0.3)            // 返回 false
  
  可以用整数的乘除法来解决
  var z = (x * 10 + y * 10) / 10;       // z 的结果为 0.3
  ```

- **加法**是两个**数字**相加，**连接**是两个**字符串**连接

- 字符串断行需要使用反斜杠

  ```javascript
  var x = "Hello \nWorld!";
  ```

- **数组**只允许使用**数字**索引，**对象** 使用 **名字**作为索引

