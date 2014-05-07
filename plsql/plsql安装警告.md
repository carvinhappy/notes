## PLSQL 安装时警告:plsql some oracle net versions cannot connect from a path ##

### 警告全文: ###

	Warning: Some Oracle Net versions cannot connect from a path with parentheses!
	This is due to Oracle Bug 3807408. Please ensure that your Oracle Net version
	does not suffer from this bug, or install in a different directory.

### 警告意思: ###
是提示选择安装路径是不要有括号, 比如说:programe files (x86)这样的目录.

### 解决方式: ###
重新选择不带括号的安装路径.

### 带括号安装的问题: ###
会报 TNS:无法解析链接字符串的错误.
