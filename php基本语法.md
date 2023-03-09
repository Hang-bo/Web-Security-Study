# php基本语法

## 基本介绍

- PHP（全称：PHP：Hypertext Preprocessor，即"PHP：超文本预处理器"）是一种通用开源脚本语言。

- PHP 文件可包含文本、HTML、代码和 PHP 代码
- PHP 代码在服务器上执行，结果以纯 HTML 形式返回给浏览器
- PHP 文件的默认文件扩展名是 ".php"



## 语法

PHP 脚本可以放在文档中的任何位置。

```php
<?php
    //code
?>
```



## 变量

#### 规则

- 变量以 **$** 符号开始，后面跟着变量的名称
- 变量名必须以字母或者下划线字符开始
- 变量名只能包含字母、数字以及下划线（A-z、0-9 和 _ ）
- 变量名不能包含空格
- 变量名是区分大小写的（$y 和 $Y 是两个不同的变量）

#### 变量作用域

- local

- global

  要在一个函数中访问一个全局变量，需要使用 global 关键字。

  ```php
  function xx() {
      global $x,$y;
  }
  ```

- static

  当一个函数完成时，它的所有变量通常都会被删除。希望某个局部变量不要被删除时，使用static关键字，会保留函数前一次被调用的值。

- parameter



## echo 和 print 语句

echo 和 print 区别:

- echo - 可以输出一个或多个字符串，输出速度快
- print - 只允许输出一个字符串，返回值总为 1

#### echo 语句

字符串可以包含 HTML 标签

```php
<?php
echo "<h2>PHP 很有趣!</h2>";
echo "Hello world!<br>";
echo "这是一个", "字符串，", "使用了", "多个", "参数。";
?>
```

#### print 语句

类似echo

#### print_r() 

```php
print_r ( mixed $expression [, bool $return ] )
```

- $expression: 要打印的变量，如果给出的是 string、integer 或 float 类型变量，将打印变量值本身。如果给出的是 array，将会按照一定格式显示键和元素。object 与数组类似。
- $return: 可选，如果为 true 则不输出结果，而是将结果赋值给一个变量，false 则直接输出结果。

## EOF(heredoc)

-  必须后接分号，否则编译通不过。
-  **EOF** 可以用任意其它字符代替，只需保证结束标识与开始标识一致，常用大写的 EOT、EOD、EOF 来表示。
- **结束标识必须顶格独自占一行(即必须从行首开始，前后不能衔接任何空白和字符)。**
- 开始标识可以不带引号或带单双引号，不带引号与带双引号效果一致，解释内嵌的变量和转义符号，带单引号则不解释内嵌的变量和转义符号。
- 当内容需要内嵌引号（单引号或双引号）时，不需要加转义符，本身对单双引号转义，此处相当与q和qq的用法。

```php
<?php
$name="runoob";
$a= <<<EOF
        "abc"$name
        "123"
        //可以解析html
        <h1>我的第一个标题</h1>
        <p>我的第一个段落。</p>
EOF;
// 结束需要独立一行且前后不能空格
echo $a;
?>
```



## 数据类型

- var_dump($x) 函数**返回变量的数据类型和值**
- 设置变量值为 NULL 来清空变量数据

#### 资源类型

PHP 资源 resource 是一种特殊变量，保存了到外部资源的一个引用。

常见资源数据类型有打开文件、数据库连接、图形画布区域等。

- 使用 **get_resource_type()** 函数可以返回资源（resource）类型,返回一个字符串，用于表示传递给它的 resource 的类型。

```php
<?php
$c = mysql_connect();
echo get_resource_type($c)."\n";
// 打印：mysql link，数据库连接

$fp = fopen("foo","w");
echo get_resource_type($fp)."\n";
// 打印：file，打开文件

$doc = new_xmldoc("1.0");
echo get_resource_type($doc->doc)."\n";
// 打印：domxml document，
?>
```



## 常量

```php
define ( string $name , mixed $value [, bool $case_insensitive = false ] )

例如：define("GREETING", "欢迎访问 Runoob.com");
使用常量：echo GREETING;
```

- **name：**必选参数，常量名称，即标志符。
- **value：**必选参数，常量的值。
- **case_insensitive** ：可选参数，如果设置为 TRUE，该常量则大小写不敏感。默认是大小写敏感的。

常量在定义后，默认是全局变量，可以在整个运行的脚本的任何地方使用。



## 字符串变量

用于存储并处理文本。

加上单引号或者双引号。

#### 并置运算符

唯一的字符串运算符

并置运算符 (.) 用于把两个字符串值连接起来。

类似Java中的+号

#### strlen() 函数

常用于循环的结束判断

echo strlen("Hello world!");

#### strpos() 函数

strpos() 函数用于在字符串内**查找**一个字符或一段指定的文本。

如果在字符串中找到匹配，该函数会**返回第一个匹配的字符位置(数字为下标索引，"小1")**。如果未找到匹配，则返回 FALSE。



## 运算符

#### 算术运算符

- % 模

- -$x 负数

- ~$x 按二进制位取反

  `~x = -(x+1);`

  计算机只识别补码，运算的变量值为补码

  - **例如：**

    $x=1，1的原码是0001，**正数补码和原码一样**，是0001

    ~$x，取反运算，全部取反为1110，为结果在计算机中补码形式，需要返回到原码，**先减一（反码）**，然后**再**除符号位取反（**原码**），得到1010，为-2

- a . b   并置运算符

#### 赋值运算符

a .= b ——> a = a.b

#### 递增/递减运算符

- ++
- --

#### 比较运算符

- ==，松散比较，只比较值
- ===，严格相等，类型与值都相等
- <>，!=不等于
- !== 不严格相等

#### 逻辑运算符

返回bool值

- and
- or
- xor异或
- &&
- ||
- ！

#### 数组运算符

- +集合
- ==键值对相等
- ===键值对相等，且顺序相同，类型相同
- !=，<>不相等
- !===不严格相等

#### 三元运算符

```php
(expr1) ? (expr2) : (expr3) 
```

自 PHP 5.3 起，可以省略三元运算符中间那部分。表达式 expr1 ?: expr3 在 **expr1 求值为 TRUE 时返回 expr1**，否则返回 expr3。

**NULL 合并运算符** ??( PHP7+ 版本)

```php
//普通
$username = isset($_GET['user']) ? $_GET['user'] : 'nobody';
//?:
$username = $_GET['user'] ?: 'nobody';
//??
$username = $_GET['user'] ?? 'nobody';
```

#### 换行符

echo $username, PHP_EOL;

#### 组合比较符

也称为太空船操作符，符号为 <=>

```php
$c = $a <=> $b;
```

- 如果 $a > $b, 则 $c 的值为 1。
- 如果 $a == $b, 则 $c 的值为 0。
- 如果 $a < $b, 则 $c 的值为 -1。

#### 优先级

-  &&  >  =  >  and 

- ||  >  =  >  or

  ```php
  $a = 3;
  $b = false;
  $c = $a or $b;
  var_dump($c);          // 这里的 $c 为 int 值3，而不是 boolean 值 true
  $d = $a || $b;
  var_dump($d);          //这里的 $d 就是 boolean 值 true 
  ```


#### ::符号

类中 静态方法和静态属性的引用方法

例如

```php
 class Test{
 public static $test = 1;
 public static function test(){
 }
 }
```

可以不用实例化对象直接使用 Test::$test 来取得$test属性的值
 静态方法调用也同理Test::test(); 直接调用静态方法test 

#### =>  ->

=>一般用在数组中，一个对应关系。
 ->一般是类方法的调用



## 判断语句

#### If...else 语句

#### switch 语句



## 循环

#### while

#### do...while

#### for循环

#### foreach 循环

- 数值数组

  ```php
  foreach ($array as $value)
  ```

- 关联数组

  ```php
  foreach ($array as $key => $value)
  ```

## 数组

#### 数值数组

- $cars=array("Volvo","BMW","Toyota");
- $cars[0]="Volvo";
   $cars[1]="BMW";
   $cars[2]="Toyota";

##### count() 函数

echo count($cars);

可以用于普通for循环遍历数组

#### 关联数组

键值对

- $age=array("Peter"=>"35","Ben"=>"37","Joe"=>"43");
- $age['Peter']="35";
   $age['Ben']="37";
   $age['Joe']="43"; 

#### 多维数组



#### 数组排序

- sort() - 对数组进行**升序**排列
- rsort() - 对数组进行**降序**排列
- asort() - 根据关联数组的**值**，对数组进行**升序**排列
- ksort() - 根据关联数组的**键**，对数组进行**升序**排列
- arsort() - 根据关联数组的**值**，对数组进行**降序**排列
- krsort() - 根据关联数组的**键**，对数组进行**降序**排列

## 超级全局变量

在一个脚本的全部作用域中都可用

#### $GLOBALS

$GLOBALS 是一个包含了全部**变量**的全局组合**数组**。变量的名字就是数组的键。

```php
$GLOBALS['z'] = $GLOBALS['x'] + $GLOBALS['y']; //$x,$y均已定义
$z在外面可以用
```

#### $_SERVER

$_SERVER 是一个包含了诸如头信息(header)、路径(path)、以及脚本位置(script locations)等等信息的数组。

这个数组中的项目由 Web 服务器创建。不能保证每个服务器都提供全部项目

```php
$_SERVER['PHP_SELF']//当前执行的php脚本名    
```

#### $_REQUEST（不使用）

用于收集HTML表单提交的数据。

可以被代替

#### $_POST

form标签的指定该属性："method="post"

$name = $_POST['fname']; //获取对应input的输入内容

#### $_GET

form标签的指定该属性："method="get"

$_GET 也可以收集URL中发送的数据。



## 函数

function name( )

{

}



## 魔术常量

PHP 向它运行的任何脚本提供了大量的预定义常量。

很多常量都是由不同的扩展库定义的，只有在加载了这些扩展库时才会出现，或者动态加载后，或者在编译时已经包括进去了。

八个魔术常量它们的值随着它们在代码中的位置改变而改变。

#### __ LINE __

文件中的当前行号。

#### __ FILE __

文件的完整路径和文件名。如果用在被包含文件中，则返回被包含的文件名。

自 PHP 4.0.2 起，__ FILE __ 总是包含一个绝对路径

#### __ DIR __

文件所在的目录

等价于 dirname(__ FILE __)

除非是根目录，否则目录中名不包括末尾的斜杠。

#### __ FUNCTION __

函数名称

自 PHP 5 起本常量返回该函数被定义时的名字（区分大小写）

#### __ CLASS __

类的名称

自 PHP 5 起本常量返回该类被定义时的名字（区分大小写）。

#### __ TRAIT __

Trait 的名字

自 PHP 5.4.0 起，PHP 实现了代码复用的一个方法，称为 traits。

#### __ METHOD __

类的方法名（PHP 5.0.0 新加）。返回该方法被定义时的名字（区分大小写）。

#### __ NAMESPACE __

当前命名空间的名称（区分大小写）。此常量是在编译时定义的（PHP 5.3.0 新增）。



## 命名空间

目的是解决重名问题，PHP中不允许两个函数或者类出现相同的名字，发生重名的时候就需要重构名字.

命名空间通过**关键字namespace** 来声明。

```php
<?php
namespace MyProject {

}
namespace { // 全局代码

}
?>
```

- 当前脚本文件的第一个命名空间前面不能有任何代码

- 调用命名空间元素时语法：\空间名\元素名（类似文件路径）

  ```php
  $article_comment = new \Article\Comment();
  ```

- 全局代码必须用一个不带名称的 namespace 语句加上大括号括起来

```php
<html>
<?php
namespace MyProject; // 命名空间前出现了“<html>” 会致命错误 -　命名空间必须是程序脚本的第一条语句
?>
```

#### 子命名空间

namespace MyProject\Sub\Level;  //声明分层次的单个命名空间

#### 公共空间

在一个命名空间里引入脚本，脚本里的元素不会归属到这个命名空间。如果这个脚本里没有定义其它命名空间，它的元素就始终处于公共空间中。

调用公共空间的方式是直接在元素名称前加 \ 就可以了，否则PHP解析器会认为我想调用当前空间下的元素。

```php
<?php
namespace Blog\Article;
//引入脚本文件
include './common_inc.php';
$filter_XSS = new FilterXSS(); //出现致命错误：找不到Blog\Article\FilterXSS类
$filter_XSS = new \FilterXSS(); //正确
?>
```

#### 名称术语

- 非限定名称，不包含前缀的类名称，例如 $comment = new Comment();

  可理解为文件名

- 限定名称，或包含前缀的名称，例如 $comment = new Article\Comment();

  可理解为相对路径名

- 完全限定名称，或包含了全局前缀操作符的名称，例如 $comment = new \Article\Comment();

  可理解为绝对路径名

#### 别名和导入

看作是调用命名空间元素的一种快捷方式。PHP并不支持导入函数或常量。

它们都是通过使用use操作符来实现

use Blog\Article as Arte;

#### 动态调用

PHP提供了namespace关键字和__ NAMESPACE __ 魔法常量动态的访问元素，__ NAMESPACE __可以通过组合字符串的形式来动态访问



## 面向对象

- **继承** − 继承性是子类自动共享父类数据结构和方法的机制，这是类之间的一种关系。在定义和实现一个类的时候，可以在一个已经存在的类的基础之上来进行，把这个已经存在的类所定义的内容作为自己的内容，并加入若干新的内容。

- **多态** − 多态性是指相同的函数或方法可作用于多种类型的对象上并获得不同的结果。不同的对象，收到同一消息可以产生不同的结果，这种现象称为多态性。
- **重载** − 简单说，就是函数或者方法有同样的名称，但是参数列表不相同的情形，这样的同名不同参数的函数或者方法之间，互相称之为重载函数或者方法。

类使用 **class** 关键字后加上类名定义。

类的变量使用 **var** 来声明, 变量也可以初始化值。

变量 **$this** 代表自身的对象。

#### 创建对象

**new** 运算符来实例化该类的对象

```php
$runoob = new Site;
$taobao = new Site;
```

#### 调用成员方法

```php
$runoob->setTitle( "菜鸟教程" );
$taobao->setTitle( "淘宝" );
```

#### 构造函数

function __construct放在class类中

创建对象时初始化对象

```php
<?php
class Site {
    /* 成员变量 */
    var $url;
    var $title;

    function __construct( $par1, $par2 ) {
        $this->url = $par1;
        $this->title = $par2;
    }
    /* 成员函数 */
    function setUrl($par){
        $this->url = $par;
    }

    function getUrl(){
        echo $this->url . PHP_EOL;
    }

    function setTitle($par){
        $this->title = $par;
    }

    function getTitle(){
        echo $this->title . PHP_EOL;
    }
}

$runoob = new Site('www.runoob.com', '菜鸟教程');
$taobao = new Site('www.taobao.com', '淘宝');
$google = new Site('www.google.com', 'Google 搜索');

// 调用成员函数，获取标题和URL
$runoob->getTitle();
$taobao->getTitle();
$google->getTitle();

$runoob->getUrl();
$taobao->getUrl();
$google->getUrl();
?>
```

#### 析构函数

当对象结束其生命周期时（例如对象所在的函数已调用完毕），系统自动执行析构函数。

```php
function __destruct() {
	print "销毁 " . $this->name . "\n";
}
```

#### 继承

使用关键字 **extends** 来继承一个类，PHP 不支持多继承

```php
class Child extends Parent {
   // 代码部分
}
```

#### 方法重写

从父类继承的方法不能满足子类的需求，可以对其进行改写，这个过程也叫**方法的覆盖**

直接改就行

#### 访问控制

PHP 对属性或方法的访问控制，是通过在前面添加关键字 **public（公有），protected（受保护）或 private（私有）**来实现的。

- **public（公有）：**公有的类成员可以在任何地方被访问。

  如果用 var 定义，则被视为公有。

- **protected（受保护）：**受保护的类成员则可以被其自身以及其子类和父类访问。

- **private（私有）：**私有的类成员则只能被其定义所在的类访问。

#### 属性的访问控制

继承后可以对 public 和 protected 进行重定义，但 private 而不能，类型为未定义Undefined

#### 方法的访问控制

如果没有设置这些关键字，则该方法默认为公有。

#### 接口

- 通过 **interface** 关键字来定义的（接口），就像定义一个标准的类一样，但其中定义所有的方法都是空的。定义的所有方法都必须是公有

- 要实现一个接口，使用 **implements** 操作符（实现）。类中必须实现接口中定义的所有方法，否则会报一个致命错误。类可以实现多个接口，用逗号来分隔多个接口的名称。

```php
interface iTemplate
{
}
// 实现接口
class Template implements iTemplate
{
}
```

#### 常量

常量的值必须是一个定值，不能是变量，类属性，数学运算的结果或函数调用。

#### 抽象类

- 被定义为抽象的方法只是声明了其调用方式（参数），**不能定义其具体的功能实现**。

- 继承一个抽象类的时候，**子类必须定义父类中的所有抽象方法**，子类方法可以包含父类**抽象方法中不存在的可选参数**。另外，这些方法的访问控制必须和父类中**一样**（或者**更为宽松**）。例如某个抽象方法被声明为受保护的，那么子类中实现的方法就应该声明为**受保护的或者公有**的，而不能定义为私有的。

```php
abstract class AbstractClass
{
 // 强制要求子类定义这些方法
    abstract protected function getValue();
    abstract protected function prefixValue($prefix);
    // 普通方法（非抽象方法）
    public function printOut() {
        print $this->getValue() . PHP_EOL;
    }
}
```

#### Static 关键字

- 声明类属性或方法为 static(静态)，就可以不实例化类而直接访问。

- 静态属性不能通过一个类已实例化的对象来访问

  静态属性不可以由对象通过 -> 操作符来访问。

- 静态方法可以通过一个类已实例化的对象来访问，伪变量 $this 在静态方法中不可用。

#### Final 关键字

如果父类中的方法被声明为 final，则子类无法覆盖该方法。如果一个类被声明为 final，则不能被继承。

#### 调用父类构造函数

需要在子类的构造函数中调用 **parent::__construct()** ；

```php
class SubClass extends BaseClass {
   function __construct() {
       parent::__construct();  // 子类构造方法不能自动调用父类的构造方法
       print "SubClass 类中构造方法" . PHP_EOL;
   }
}
```