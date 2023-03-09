### error-reporting

**error_reporting()** 函数能够在运行时设置 error_reporting 指令。

- **关闭所有PHP错误报告error_reporting(0);**

- **报告所有 PHP 错误error_reporting(-1);**



### highlight_file() 

函数对文件进行语法高亮显示。

highlight_file(filename,return)



### __ FILE  __

- echo __FILE__ ; // 取得当前文件的绝对地址，结果：D:\www\test.php 

- echo dirname(__FILE__); // 取得当前文件所在的绝对目录，结果：D:\www\ 

- echo dirname(dirname(__FILE__)); //取得当前文件的上一层目录名，结果：D:\ 



### die() 函数

die() 函数输出一条消息，并退出当前脚本。

和exit()相同

- 括号内为字符串，退出前输出字符串
- 括号内为整数，值用作退出状态，退出状态的值在 0 至 254 之间。退出状态 255 由 PHP 保留，不会被使用。状态 0 用于成功地终止程序。



### eval()

把字符串按照 PHP 代码来计算。

如果没有在代码字符串中调用 return 语句，则返回 NULL。如果代码中存在解析错误，则 eval() 函数返回 false。



### is_numeric()

用于检测变量是否为数字或数字字符串。

bool is_numeric ( mixed $var )

指定的变量是数字和数字字符串则返回 TRUE，否则返回 FALSE，注意浮点型返回 1，即 TRUE。