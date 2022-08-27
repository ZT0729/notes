# Ｑt错误解决 : nullptr关键字问题

Debug错误解决：“warning: identifier ‘nullptr’ is a keyword in C++11 [-Wc++0x-compat]”
“error: ‘nullptr’ was not declared in this scope

在Linux系统下使用[GCC](https://so.csdn.net/so/search?q=GCC&spm=1001.2101.3001.7020)编译器编译Qt项目是，如果代码中包含C++11关键字，就会遇到类似如下错误：

“warning: identifier ‘nullptr’ is a keyword in C++11 [-Wc++0x-compat]”
“error: ‘nullptr’ was not declared in this scope”

如遇到上述错误可以把项目中的 `nullptr` 关键字替换成 Qt 中的关键字 `Q_NULLPTR`，或者用Qt Creator打开.pro文件，在文件中添加下面其中一种方法中的代码即可解决。

```C++
如果 GCC 编译器版本 < 4.7

QMAKE_CXXFLAGS += -std=c++0x

如果 GCC 编译器版本 >= 4.7

QMAKE_CXXFLAGS += -std=c++11

如果当前使用的是 Qt 5

CONFIG += c++11
```

