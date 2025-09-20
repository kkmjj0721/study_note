# **MATLAB学习笔记**

# **目录：**

**1. 基本操作与矩阵输入**

















## **一、 基本操作与矩阵输入：**

### **1、界面介绍：**

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509202100995.jpg)

打开MATLAB，主要会有以下几个区域。如果窗口消失可以点击**主页->布局->默认**，来恢复

| 序号 | 名称       | 功能               |
| ---- | ---------- | ------------------ |
| ①    | 菜单栏     |                    |
| ②    | 当前文件夹 | 即工作空间路径     |
| ③    | 编辑器     | 可以进行脚本编辑   |
| ④    | 命令行窗口 | 敲命令的地方       |
| ⑤    | 工作区     | 可以查看执行的变量 |







### **2、MATLAB语言基础：**

#### **2.1数据类型：**

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509202126025.png)

**1 整型**
  这个学过C语言的很好理解，无符号就是不带负数，后面的数字就是位数；
**2 浮点型**
  与C语言一样，有单精度float与双精度double之分，单精度在内存中占4个字节，双精度占8个字节；
**3 常量与变量**
  常量是程序语句中取不变值的那些量，变量是在程序运行中其值可以改变的量。常用预定义变量：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509202131329.png)

**4 字符串**

​		字符串是用**单引号**括起来的字符序列，MATLAB将字符串当作一个行向量，每个元素对应一个字符。注意，如果字符串里有单引号则需要两个单引号表示。

```matlab
% 创建包含单引号的字符串
str = 'I''m learning MATLAB.';  
disp(str);  % 输出：I'm learning MATLAB.
length(str);  % 统计字符个数，结果为 20（逐个字符：I'm learning MATLAB.）
```





#### **2.2、MATLAB运算：**

##### **2.2.1、算数运算：**

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509202149436.png)



##### **2.2.2、关系运算：**

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509202148266.png)



##### **2.2.3、逻辑运算：**

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509202150389.png)





#### **2.3、常用内部函数：**

​		函数最一般的引用格式是：**函数名(参数 1，参数 2，…)**

##### **2.3.1、常用科学函数：**

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509202153500.png)



##### **2.3.2、关系运算函数：**

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509202155912.png)





#### **2.4、结构数据与单元数据：**

##### **2.4.1、结构数据：**

​		结构数据类型把一组类型不同而逻辑上相关的数据组成一个有机的整体，类似C语言结构体，相关函数如下：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509202157846.png)



##### **2.4.2、单元数据：**

​		与结构数据类似，不同的是结构矩阵各个元素下有成员，每个成员有自己的名字（很像）

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509202159415.png)





### **3、Command line（in command window）（命令行编程）：**

#### **3.1、Precedence rules（运算优先级）：**

- Left-to-right within a precedence group（组内优先级从左到右）

- Precedence groups are（highest first）（优先级分组）：
  1. Parenthesis    ()
  2. Power    ^
  3. Multiplication and division    *, /
  4. Addition and subtraction    +, -

**小练习：**

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509202237277.png)

