# XML 数据传输格式

## 1. XML 概述

### 1.1 引入

XML 数据格式最主要的功能就是 ==数据传输==。



XML 数据格式主要的用途有什么？

==程序之间的数据传输服务==。

配置文件 config.xml

config.xml - >php、java、Pyhton

==存储数据，充当小型数数据库==

data.xml



规范数据格式，是数据具有结构性，易读易处理。



### 1.2 什么是XML



XML 指的是可扩展性标记语言。

XML 被发明的目的是==传输和存储数据，而不是展示数据==。(HTML 是展示数据)。

XML 的标签必须是自定义，但是在写标签名的时候一定要有含义。

XML 是 W3C 推举的数据传输格式。

如何自己写一段XML。

![image-20220826193827255](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220826193827255.png)

这样展示出来的就碎对。。

![image-20220826193906329](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220826193906329.png)xml 和 html 有哪些不一样。

1：html 标签不能自定义，sml标签只能自定义。

2：html 语法要求不严格，语法要求 及其严格。必须是成对标签。

3：xml 用来传输和存储数据。



## 2. XML的基本语法

### 2.1 语法规则

==**xml 文档必须有根节点；**==

**根节点**就是其他所有节点的父级；

![image-20220826195856054](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220826195856054.png)

==xml 头声明：不强制要求，可有可无，但是建议书写；==

![image-20220826200413979](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220826200413979.png) 

==所有 XML 必须是成对标签；==

![image-20220826200752140](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220826200752140.png)

==标签名大小名敏感（区分大小写）；==

![image-20220826202120414](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220826202120414.png)

==标签不能交叉；==

![image-20220826202303047](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220826202303047.png)

==注释：使用`<!--     -->`==

![image-20220826202527955](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220826202527955.png)

==特殊字符要使用实体转义：==

| <     | >     | &      | "       | '      |
| ----- | ----- | ------ | ------- | ------ |
| \&lt; | \&gt; | \&amp; | \&quot; | \&apos |

![image-20220826203027425](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220826203027425.png)

==在 XML 中，空格会被保留==![image-20220826210901167](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220826210901167.png)

### 2.2 元素属性

属性：描述标签自身的额外信息；

![image-20220826204319248](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220826204319248.png)

==写属性注意的点：一个标签可以有多个属性，属性的值必须使用双引号引起来；==

==命名规则：基本上和变量名相同，数字字母下划线，数字不能开头==



xml 中属性就是鸡肋（食之无肉，弃之可惜）；



还有，在解析 xml 数据时，属性会带来额外的解析代码（多了一步，比较麻烦）

### 2.3 CDATA

\<![CDATA[          。。。不解析内容。。。    ]]>

![image-20220826210108966](https://zt0729-picture-bed.oss-cn-beijing.aliyuncs.com/ii/image-20220826210108966.png)

注意：特殊字符较少时，使用实体替换。较多时使用cdata，CDATA 必须大写；