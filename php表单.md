# php表单

## 1.表单和用户输入

当处理 HTML 表单时，PHP 能把来自 HTML 页面中的表单元素自动变成可供 PHP 脚本使用。

## 2.表单验证

防止黑客及垃圾信息我们需要对表单进行数据安全验证。

#### **$_SERVER["PHP_SELF"] 变量**

$_SERVER["PHP_SELF"]是超级全局变量，返回当前正在执行脚本的文件名，与 document root相关。

所以， $_SERVER["PHP_SELF"] 会发送表单数据到当前页面，而不是跳转到不同的页面。

#### **htmlspecialchars()方法**

$_SERVER["PHP_SELF"] 可以通过 htmlspecialchars() 函数来避免被利用。

把一些预定义的字符转换为 HTML 实体。

预定义的字符是：

- & （和号） 成为 &amp;
- " （双引号） 成为 &quot;
- ' （单引号） 成为 &#039;
- < （小于） 成为 & lt;
- \> （大于） 成为 & gt;

#### 验证表单数据

-  trim() 函数去除用户输入数据中不必要的字符 (如：空格，tab，换行)
- stripslashes()函数去除用户输入数据中的反斜杠 (\) 

- 当提交方法为POST时，

  通过**$_SERVER["REQUEST_METHOD"]**来检测表单是否被提交 。如果 REQUEST_METHOD 是 POST, 表单将被提交 - 数据将被验证。如果表单未提交将跳过验证并显示空白。



## 3.表单 - 必需字段

- 检查 $_POST 变量是 否为空（使用php的 empty() 函数）
- 如果为空，则将提示信息传入错误提示参数中。
- 通过html显示提示信息



## 4.验证名称邮件和URL

preg_match ——进行正则表达式匹配。

- 语法规则：

  preg_match ( string $pattern , string $subject [, array $matches [, int $flags ]] )

- 在 subject 字符串中搜索与 pattern 给出的正则表达式相匹配的内容。

- 如果提供了 matches  ，则其会被搜索的结果所填充。$matches[0] 将**包含与整个模式匹配的文本**，$matches[1]  将包含与**第一个捕获**的括号中的子模式所匹配的文本，以此类推。

#### 验证名称

```php
$name = test_input($_POST["name"]);
if (!preg_match("/^[a-zA-Z ]*$/",$name)) {
  $nameErr = "只允许字母和空格"; 
}
```

^匹配字符串的开始

$匹配字符串的结束

*匹配多个字符

#### 验证邮件

```php
$email = test_input($_POST["email"]);
if (!preg_match("/([\w\-]+\@[\w\-]+\.[\w\-]+)/",$email)) {
  $emailErr = "非法邮箱格式"; 
}
```

- \w匹配大小写英文字符，数字0~9之间的任意一个，下划线

- \@和\ .组合形式

- +为>=1

实现匹配xxxxx@xxxxxx.xxxx的格式

#### 验证 URL

```php
$website = test_input($_POST["website"]);
if (!preg_match("/\b(?:(?:https?|ftp):\/\/|www\.)[-a-z0-9+&@#\/%?=~_|!:,.;]*[-a-z0-9+&@#\/%=~_|]/i",$website)) {
  $websiteErr = "非法的 URL 的地址"; 
}
```



## 5.$_GET['name']变量

预定义的 $_GET 变量用于收集来自 method="get" 的表单中的值。

- 从带有 GET 方法的表单发送的信息，对任何人都是可见的（会显示在浏览器的地址栏），并且对发送信息的量也有限制，值是不能超过 2000 个字符的。
- 变量显示在 URL 中，因此可以在收藏夹中收藏该页面

**发送密码或其他敏感信息时，不应该使用这个方法！**



## 6.$_POST['name'] 变量

预定义的 $_POST 变量用于收集来自 method="post" 的表单中的值。

从带有 POST 方法的表单发送的信息，对任何人都是不可见的（不会显示在浏览器的地址栏），并且对发送信息的量也没有限制。

- 默认情况下，POST 方法的发送信息的量最大值为 8 MB（可通过设置 php.ini 文件中的 post_max_size 进行更改，发送信息的量也没有限制。）。
- 变量不显示在 URL 中，所以无法把页面加入书签。



## 7.$_REQUEST 变量

预定义的 $_REQUEST 变量包含了 $ _ GET、$ _ POST 和 $ _ COOKIE 的内容。

$_REQUEST 变量可用来收集通过 GET 和 POST 方法发送的表单数据。