# **MATLAB学习笔记**

# **目录：**

**1. 基本操作与矩阵输入**

**2.结构化程式与自定义函数**

**3.变量与档案存取**

**4.绘图**











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

> **注：我们可以像c语言那样，使用一个数据类型（type）加上括号，里面为变量，可以将其的type进行改变；**





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

> **注：**
>
> ​	**此处ln函数错误，正确写法为 log，表示为求已e为底的对数**
>
> ​	**直接使用exp不能表示自然对数，必须要在后面加上括号并在里面写上数字；如：**
>
> ```matlab
> exp(1)      % 表示e
> exp(2) 		% 表示e的平方
> ```



##### **2.3.2、关系运算函数：**

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509202155912.png)

> **附：可打开该网页进行查看一些数学函数（也可查看上面的图片，但不全）**
>
> **[数学 — 函数](https://ww2.mathworks.cn/help/matlab/referencelist.html?type=function&s_tid=CRUX_topnav&category=mathematics)**



#### **2.4、结构数据与单元数据：**

##### **2.4.1、结构数据：**

​		结构数据类型把一组类型不同而逻辑上相关的数据组成一个有机的整体，类似C语言结构体，相关函数如下：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509202157846.png)



##### **2.4.2、单元数据：**

​		与结构数据类似，不同的是结构矩阵各个元素下有成员，每个成员有自己的名字（很像）

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509202159415.png)







### **3、Command line（in command window）（命令行编程）：**

#### **3.1、命令行交互式命令操作：**

​		命令行以`Enter`结束，但是一行也可以输入多条命令。命令之间用`,`分隔，如果用`;`分隔或者结尾，则不会运行（不显示运算结果）。如果命令太长需要换行，可以在第一行末尾添加`...`，再按`Enter键`换行。在MATLAB命令后面可以用%添加注释。如下：

```matlab
>> a=1,b=2;c=...
4   %注释
```

命令窗的常用控制指令：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509211555957.png)

命令行编辑常用按键：

​		![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509211557959.png)





#### **3.2、Precedence rules（运算优先级）：**

- Left-to-right within a precedence group（组内优先级从左到右）

- Precedence groups are（highest first）（优先级分组）：
  1. Parenthesis    ()
  2. Power    ^
  3. Multiplication and division    *, /
  4. Addition and subtraction    +, -

**Exercise：**

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509202237277.png)

**Answer：**

```matlab
1、cos(sqrt((1+2+3+4)^3/5))
2、sin(sqrt(pi)) + log(tan(1))
3、2^(3.5 * 1.7)
4、exp(1)^sin(10)
```





#### **3.3、Variables：**

​		在matlab中使用Variables时不需要声明（不需要指定类型）；

​		默认我们使用的是double类型；

​		我们在**Workspace**中左键双击某一变量，可以查看该变量的类型；

​		使用`who`或`whos`能够查看我们的变量；



##### **3.3.1、calling priority（调用优先级）：**

按顺序排列为：

1. Variables（变量）
2. Built in Function（内置函数）
3. Subfunction
4. Private function：
   - Mex file
   - P file
   - M file							



##### **3.3.2、Format：**

​		该命令是控制命令行窗口中数值的显示格式（如：**小数位数、科学计数法、行距**等），但不会改变数值在内存中的实际存储精度，也不影响计算结果的准确性。

| 样式     | 作用                                                         | 示例（以 `pi` 为例）                                       |
| -------- | ------------------------------------------------------------ | ---------------------------------------------------------- |
| `short`  | 短固定小数格式（默认），保留 4 位小数                        | `3.1416`                                                   |
| `long`   | 长固定小数格式，`double` 保留 15 位小数，`single` 保留 7 位小数 | `3.141592653589793`                                        |
| `shortE` | 短科学计数法，保留 4 位小数 + 指数                           | `3.1416e+00`                                               |
| `longE`  | 长科学计数法，`double` 保留 15 位小数 + 指数，`single` 保留 7 位小数 + 指数 | `3.141592653589793e+00`                                    |
| `shortG` | 自动选择 “短固定小数” 或 “短科学计数法”（取更紧凑的形式），共 5 位有效数字 | `3.1416`（固定小数更紧凑）；`3.1416e+05`（科学计数更紧凑） |
| `longG`  | 自动选择 “长固定小数” 或 “长科学计数法”，共 15 位有效数字（`double`）或 7 位（`single`） | `3.141592653589793`；`3.1415927e+00`（`single` 类型）      |
| `bank`   | 银行格式，保留 2 位小数（常用于财务场景）                    | `3.14`                                                     |
| `hex`    | 十六进制格式（仅对整数 / 实数有效）                          | `400921FB54442D18`（`pi` 的十六进制表示）                  |
| `rat`    | 分数格式（近似表示）                                         | `355/113`（`pi` 的近似分数）                               |
| `+`      | 正负号格式，正數显 `+`、负數显 `-`、零显空格                 | `+3.1416`                                                  |

| 样式      | 作用                                                       |
| --------- | ---------------------------------------------------------- |
| `compact` | 紧凑行距（默认），减少输出中的空行，让更多内容显示在屏幕上 |
| `loose`   | 宽松行距，数值间显示更多空行，便于阅读                     |

附上代码：

```matlab
% 示例1：不同数值格式对比
x = pi;  % 定义变量 pi

format short;   disp(x);  % 输出：3.1416（短固定小数）
format long;    disp(x);  % 输出：3.141592653589793（长固定小数）
format shortE;  disp(x);  % 输出：3.1416e+00（短科学计数法）
format bank;    disp(x);  % 输出：3.14（银行格式，2位小数）
format rat;     disp(x);  % 输出：355/113（近似分数）

% 示例2：控制行距
A = magic(3);  % 生成3×3幻方矩阵

format compact; disp(A);  % 紧凑行距，矩阵行之间空行少
format loose;   disp(A);  % 宽松行距，矩阵行之间空行多

% 示例3：还原默认格式
format default;  % 还原为默认格式（short + compact）
disp(x);         % 输出：3.1416
```

**Exercise：**

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509211632721.png)

**Answer：**

```
format rat
3/13 + 4/14 + 5/15

1
0.849816849816850
```

> **注：format的设置会影响后续所有命令行输出，直到再次修改格式或关闭 MATLAB。**

> **注：我们不能使用Key world作为变量来使用；**





#### **3.4、Array (Vector  and  Matrix)：**

- Row vector（行矩阵）：

​		a = [1 2 3 4]

- Column vector（列矩阵）：

​		b = [1; 2; 3; 4]

经过上面两种表达，我们知道，每行的元素用**space**分开，使用**；**可以进行换行；

##### **3.4.1、Array  Indexing（索引）：**

在向量中：我们可以用该Variables的名字加上括号，括号内部写上数字，即可查找，如下：

```matlab
a = [1 2 3 4]
a(2)

% 可查找该向量中的第二个元素的值
```

但在一个Matrix里，我们使用上面的方法要注意其索引（先从列开始，然后到下一列），如：

```matlab
A = [1 2 3;
	 4 5 6;
	 7 8 9]
A(2)   %该值为4
A(4)   %该值为2
```

除去上面那种方法，我们还有其他方法来查找，如下：

```matlab
A([1 3 5])
A([1 3; 1 3])
A(3,2)
A([1 3], [1 2])
```

现在我们来简单讲一下：

1、用向量 \([1,3,5]\) 提取 “第 1、3、5 个元素”，结果为行向量。

2、用 2×2 矩阵作为索引，提取对应位置的元素，并组织成与索引矩阵同形状的矩阵，结果也为2×2的矩阵。

以上面的A矩阵为例，此处得到的为：
$$
\begin{bmatrix}
1 & 7\\
1 & 7\\ 
\end{bmatrix}
$$

3、提取 “第 3 行，第 2 列” 的元素。

4、该方法为分别对行与列取，如此处取1，3行，1，2列，提取行与列交叉处的元素，结果为2乘2的矩阵，如下：
$$
\begin{bmatrix}
1 & 2\\
7 & 8\\ 
\end{bmatrix}
$$


##### **3.4.2、Replacing Entries（替换）：**

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509221503904.png)

```matlab
A(2) = [91] 
```

使用上面的代码我们可以将矩阵中某一位的数值进行修改；

​		我们在上一小节（索引）中有讲到对一个矩阵里的元素进行查找，同样的我们查找后在后面加上一个 “=” ，并且后面加上一个向量or矩阵，即可对选中的部分进行修改；



##### **3.4.3、Colon Operator（等差级数）：**

在我们写矩阵or向量的时候，可能某一行比较长，这时我们使用下面这种方法会比较方便，快捷，如下：

```matlab
A = [1:100]
```

能帮我们快速生成一个向量，长度为100；可看下图：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509221541985.png)

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509221601124.png)

我们也可以用这种来创建一个矩阵，如下：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509221607409.png)

不只矩阵可以使用Colon Operator，字符串也可以，如下：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509221610290.png)

注意，在这个地方的用法不止可以使用等差级数来生成，还可以用其来查找所对应的行与列，如下：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509221626075.png)

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509221627625.png)

这时，我们可以将上一小节的矩阵进行删除某一列或某一行，如下：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509221631138.png)

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509221631158.png)



##### **3.4.4、Array Concatenation（数组连接）：**

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509221643539.png)



##### **3.4.5、Array Manipulation（数组操作）：**

**Operators on array（运算符）：**

​		`+`    `-`    `*`    `/`    `^`    `.`    `‘`

`+`，`-`，`*` 我们在学过线性代数很容易理解，`/`的话我们可以理解为乘以其逆矩阵；除此我们还有`.*`，表示每一个元素分别相加，得到新的矩阵；`./`可以看成和`.*`一样的操作；

注意：

​		**我们使用`^`的时候，不是对矩阵内的元素进行幂运算，而是n个矩阵相乘；而`.^`则是对矩阵内的每个元素**

**进行幂运算；**

`‘`是对矩阵的转置；

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509230032024.png)



##### **3.4.6、Some Special Matrix：**

1)、eye(n)：n×n identity matrix，n维的单位矩阵，可看下图：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509230041393.png)

2)、zeros(n1,n2)：n1×n2 zero matrix：表示n1×n2维的矩阵，矩阵里的所有元素均为0，可看下图：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509230043129.png)

3)、ones(n1,n2)：n1×n2 matrix with every entry as 1：表示n1×n2维的矩阵，矩阵里的所有元素均为1，可看下图：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509230046463.png)

4)、diag()：diagonal matrix：对角线矩阵，我们在括号内输入一个向量，其会将该向量的值赋到生成矩阵的主对角线					上，并且其余地方均为0，可看下图：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509230051611.png)

5)、rand()：uniformly distributed random numbers：

| 调用格式        | 功能描述                                                     |
| --------------- | ------------------------------------------------------------ |
| `rand()`        | 生成一个单个随机数（1×1 标量），取值范围 [0, 1)              |
| `rand(n)`       | 生成一个 n×n 的方阵，每个元素为 [0, 1) 区间的均匀随机数      |
| `rand(m, n)`    | 生成一个 m×n 的矩阵（m 行，n 列），元素取值 [0, 1)           |
| `rand([m, n])`  | 与 `rand(m, n)` 效果相同，参数用向量 `[m, n]` 指定维度       |
| `rand(m, n, k)` | 生成一个 m×n×k 的三维数组（可扩展到更高维度），每个元素为 [0, 1) 随机数 |

该像不做讲解，可在matlab中自行验证；

6)、linspace()：linearly spaced vectors：

`linspace` 的核心是生成**从 `start` 到 `end` 的 `n` 个等间距数值向量**，语法为：向量 = linspace(start, end, n)

- `start`：区间起点（必选）；
- `end`：区间终点（必选，包含在向量中）；
- `n`：生成的点数（必选，若省略则默认生成 100 个点）。

本项也不做讲解，详细的可在网络上自行查找；



##### **3.4.7、Some Matrix Related Functions：**

1）、max：我们可以使用max来查找一个Matrix每一列的最大项，得到的结果为一个Vector ，我们可以对得到的Vector ，再进行max操作，即可得到一个Matrix中的最大值；

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509230112967.png)

2）、min：和上面一样，但是它是求最小的；

3）、sum：我们可以使用sum对矩阵进行求和，其会对每一列分别求和，得到一个Vector，我们同样可以用上面的操作进行运算，最后得到一个矩阵中所有元素的和；

4）、mean：求平均值的，但是其也是对每一列进行操作，我们按上面方法来就行了；

5）、sort(A)：对矩阵A进行列排序（从小到大）；

6）、sortrows：以某一列为键，重新排列整行数据（从小到大），可看下图：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509230119961.png)

当然，我们可以指定以那一列为键进行排列，如下：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509230120344.png)

7）、size()：我们可以用该函数进行查看矩阵的维数，如下：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509230123128.png)

8）、length()：得到Matrix中最长的一个维度，如下：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509230125000.png)

9）、find()：该函数，能够得到Matrix中某一个值的位置，如下：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509230128958.png)









## **二、结构化程序与自定义函数：**

### **1、M文件：**

M文件就是以`.m`为扩展名的文本文件，它有两种类型：脚本（Script）和函数文件（Function），主要区别如下：

> - **脚本文件没有输入参数，也不返回输出参数，而函数文件可以带输入参数，也可返回输出参数。**
> - **脚本文件对 MATLAB 工作空间中的变量进行操作，文件中所有命令的执行结果也完全返回到工作空间中，而函数文件中定义的变量为局部变量，当函数文件执行完毕时，这些变量被清除。**
> - **脚本文件可以直接运行，在 MATLAB 命令行窗口输入脚本文件的名字，就会顺序执行脚本文件中的命令，而函数文件不能直接运行，要以函数调用的方式来调用它。**

创建一个.m文件：

- 方式一：点击**主页->新建**
- 方式二：命令行输入`edit 文件名`

#### **1.1、写一个简单的脚本文件：**

直接将下面代码复制过去即可，具体内容等，后面会讲；

```matlab
for i=1:10
    x=linspace(0,10,101);
    plot(x,sin(x+i));
    print(gcf,'-deps',strcat('plot',num2str(i),'px'));
end
```

我们点击运行会让我们保存，然后我们记住保存的文件名，可以直接在命令行输入该文件的名字即可运行该脚本（不带后缀的文件名）；

> **脚本编程技巧：**
>
> - **clear all 用于删除之前的所有变量**
> - **close_all 关闭所有的图形**
>
> ​	**在命令末尾使用分号；以抑制不需要的输出**
>
> ​	**使用省略号`…`（将一行过长的代码延续到下一行），使脚本更易读**





#### **1.2、写一个简单的函数文件：**

**基本结构：**

```matlab
function [输出形参表]=函数名(输入形参表)
```
**调用函数：**

```matlab
[输出参数列表]=函数名(输入参数列表)
```

> **注：一般我们的函数名与文件名一致；**

**Exercise：**

​		Write a function that calculate the displacement of free falling for given initial displacement x0，initial velocity v0，and duration of falling t（编写一个函数，以计算给定初始位移x0，初始速度V0和跌落t的持续时间的自由下落位移）： 

```matlab
function x = freebody(x0,v0,t)
% x0：初始位移
% v0：初始速度
% t：当前时间
% 返回值：当前位移
x = x0 + v0*t +1/2*9.8*t*t;
```

我们可以将函数里的乘改为点乘，这样在我们输入一个Vector时，其可以将该Vector里的每个值都算出来；如下：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509240019010.png)

##### **1.2.1、Function Default Variables（函数默认变量）：**

1、inputname：Variable name of function input（函数输入的变量名称）

2、mfilename：File name of currently running function（当前运行函数的文件名）

3、nargin：Number of function input arguments（函数输入参数的数量）

4、nargout：Number of function output arguments（函数输出参数的数量）

5、varargin：Variable length input argument list（可变长度输入参数列表，主要用在Vector  和  Matrix）

6、varargout：Variable length outputargument list（可变输出参数列表）







### **2、程序控制结构：**

​		程序的控制结构有3种：**顺序结构**、**循环结构**和**选择结构**。其中顺序结构就是指程序里的语句从上往下按顺序执行。

#### **2.1、循环结构：**

​		MATLAB提供两种循环结构语句：for语句与while语句（这两个语句也是我们在其他程序语言中常用的语句）；

##### **2.1.1、for语句：**

​		如果可以确认循环次数用for循环，格式如下：

```matlab
for 循环遍历=表达式1:表达式2:表达式3
	循环体语句
end
```

- 表达式1的值为循环控制变量的初值；
- 表达式2的值为步长，省略时，步长为1；
- 表达式3为循环控制变量的终值。



##### **2.1.2、while语句：**

​		while语句通过判断循环条件是否满足来决定是否继续的循环结构，格式如下：

```matlab
while 条件
	循环体语句
end
```





#### **2.2、选择结构：**

​		MATLAB实现条件结构语句：if语句、switch语句和try语句

##### **2.2.1、if语句：**

```matlab
if 条件1
	语句组
elseif 条件2
	语句组
	...
else
	语句组
end

```



##### **2.2.2、switch语句：**

```matlab
switch 表达式
	case 表达式1
		语句1
	case 表达式2
		语句2
		...
	case 表达式n
		语句n
	otherwise
		语句n+1
end

```



##### **2.2.3、try语句：**

​		try语句为开发人员提供了一种捕获错误的机制；

```matlab
try
	语句1
catch
	语句2
end
```





#### **2.3、流程控制语句：**

- break语句：终止本层for或while循环，跳转到本层循环结束语句end的下一条语句

- continue语句：跳过其后的循环体语句，进行下一次循环
- return语句：终止被调用函数的运行，返回到调用函数
- pause语句：
  - pause:暂停程序运行，按任意键继续
  - pause(n):程序暂停运行n秒后继续
  - pause on/off:允许/禁止其后的程序暂停



**Exercise：**

​		use while loop to calculate the summation of the series 1+2+3+……+999

代码如下：

```matlab
i = 0;
sum = 0;
while(i<=999)
    sum = sum + i;
    i = i + 1;
end
disp(sum);
```

> **注：我们在进行数值运算的时候，有时必须需要将数值清除掉，不然可能会导致我们的计算的结果有问题；**

> **注：当我们要看一个脚本or函数的用时，我们可以使用tic  toc，来看用时，在运算开始前写上tic，运算结束后写上toc；**
>
> **如下：**
>
> ```matlab
> tic;
> i = 0;
> sum = 0;
> while(i<=999)
>     sum = sum + i;
>     i = i + 1;
> end
> disp(sum);
> toc;
> ```







### **3、特殊类型函数：**

#### **3.1、子函数：**

​		一个M文件可以有多个函数，第一个为主函数，其他为子函数。在保存文件时文件名一般和主函数相同，外部程序只能对主函数进行调用；

```matlab
function d=func(a,b,c)		%主函数
d=subfunc(a,b)+c;
function c=subfunc(a,b)		%子函数
c=a*b;
```





#### **3.2、内联函数：**

​		字符串形式的函数表达式可以通过`inline`函数转化成内联函数；

```matlab
a='(x+y)^2';
f=inline(a)
f(3,4)
```





#### **3.3、匿名函数：**

```matlab
函数句柄变量=@(匿名函数输入参数)匿名函数表达式
>> sqr=@(x) x.^2     %定义匿名函数
>> sqr([1,2,3])      %调用匿名函数
```









## **三、变量与档案存取：**

​		在前面的数据类型我们已经讲了大部分的的东西，这里仅做一下附加讲解：

如我们有多个字符串or字符，我们想让其连接在一起，我们可以使用`[]`进行连接，具体可看上面的**数组连接**；

### **1、Logical Operations and Assignments（逻辑运算和赋值）：**

```matlab
str = 'aardvark';
'a' == str
```

其会比较a与str中每个字符；若一样返回1，不一样返回0；

Try this：

```matlab
str(str == 'a') = 'Z'
```

**Exercise：**

​		Write a script that inverts any given string（编写一个反转任何给定字符串的脚本），如下：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509241333634.png)

其实这里有内置函数可以直接实现该功能，但我们为了更好的理解，简单写一下这个程序：

```matlab
function s2 = inversion(s1)

i = size(s1);
for j = i(1):i(2)
    temp(j) = s1(i(2) - j + 1);
end
s2 = temp;
```

> **注：数组索引必须为正值或逻辑值**







### **2、structure：**

- A method of storing heterogneous data（一种存储异构数据的方法）；
- Structures contain arrays called fields（结构体包含称为字段的数组）；

示例：Student assignment grades（学生作业成绩）：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509241447873.png)

#### **2.1、Structure Function：**

- cell2struct()：Convert cell array to structure array（）
- fieldnames()：Field names of structure, or public fields of object（可以查找结构体的所有字段名称）
- getfield()：Field of structure array
- isfield()：Determine whether input is structure array field（确定输入是否为结构数组字段）
- isstruct()：Determine whether input is structure array（确定输入是否为结构数组）
- orderfields()：Order fields of structure array
- rmfield()：Remove fields from structure（从结构体中移除某一个field（字段））；
- setfield()：Assign values to structure array field（）
- struct()：Create structure array（创建结构数组）
- struct2cell()：Convert structure to cell array
- structfun()：Apply function to each field of scalar structure





#### **2.2、Nesting Structures（结构体嵌套）：**

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509241503676.png)

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509241504692.png)







### **3、Cell Array（单元数组）：**

- Another method of storing heterogeneous data（另一种存储异构数据的办法）
- Similar to matrix but each entry contains different type of data（类似于矩阵，但每个条目包含不同类型的数据）
- Declared using { }

​	如下：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509242220036.png)

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509242221530.png)



- Each entry in a cell array holds a pointer to a data structure（单元数组中的每个条目都指向一个数据结构的指针）；
- Different cells of the same cell array can point to different types of data structures（同一单元数组的不同单元可以指向不同类型的数据结构）；

**Exercise：**

​		![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509242229115.png)

代码如下：

```matlab
>> A(1,1)={'This is the first cell'};
>> A(1,2)={[5+j*6 4+j*5]};
>> A(2,1)={[1 2 3;4 5 6;7 8 9]};
>> A(2,2)={["Tim" "Chirs"]}
```

> **注：在matlab中字符串即字符数组，使用单引号`''`，字符串数组为多个字符数组，使用双引号定义元素，使用[]连接成数组；**

#### **3.1、Accessing Cell Array：**

- Curly braces, {}, are used to access the “contentof” cell arrays（使用花括号来访问单元数组的内容）





#### **3.2、Cell Array Function；**

- cell()：Create cell array
- cell2mat()：Convert cell array to numeric array
- cell2struct()：Convert cell array to structure array（将单元数组转成结构体）
- celldisp()：Cell array contents
- cellfun()：Apply function to each cell in cell array
- cellplot()：Graphically display structure of cell array
- cellstr()：Create cell array of strings from character array
- iscell()：Determine whether input is cell array
- mat2cell()：Convert array to cell array with different sized cells（将数组转换为具有不同大小单元格的单元数组）
- num2cell()：Convert array to cell array with consistently sized cells（将数组转换为具有固定大小单元格的单元数组）
- struct2cell()：struct2cell Convert structure to cell array







### **4、Multidimensional Array：**

#### **4.1、cat( ):**

​		该指令可以帮助我们将两个array进行连接起来；

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509242309413.png)

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509242310381.png)





#### **4.2、reshape( )：**

​		该函数可以将一个row为r1、column为c1的matrix变成row为r2、column为c2的matrix，前提为`r1*c1 = r2*c2`；

如图中示例，其将一个2乘2的matrix变成1乘4的matrix；

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509242316253.png)







### **5、Checking Variable And Variable Status：**

- isinteger：Determine if input is integer array
- islogical：Determine if input is logical array
- isnan：Detect an element that isnot a number (NaN)
- isnumeric：Determine if input is numeric array
- isprime：Detect prime elements of array
- isreal：Determine if all array elements are real numbers
- iscell：Determine if input is cell array
- ischar：Determine if input is character array
- isempty：Determine if input is empty array
- isequal：Determine if arrays are numerically equa
- isfloat：Determine if input is floating-point array
- isglobal：Determine if input is global variable
- ishandle：Detect valid graphics object handles
- isinf：Detect infinite elements of array







### **6、File Access（文件访问）：**

#### **6.1、Supported file formats：**

| File Content（文件内容） | Extension（扩展名） | Description（描述）     | Import Function（导入功能） | Export Function（导出功能） |
| ------------------------ | ------------------- | ----------------------- | --------------------------- | --------------------------- |
| MATLAB formatted data    | MAT                 | Saved MATLAB workspace  | load                        | save                        |
| Text                     |                     | space delimited numbers | load                        | save                        |
| Spreadsheet              | XLS,SLSX            |                         | xlsread                     | xlswrite                    |





**6.2、save() and load()：**

- Save（all）workspace data to a file：


```matlab
clear;a=magic(4);
save mydatal.mat
save mydata2.mat-asciiv
```

第二行代码与第三行代码的唯一区别就是使用文本阅读器打开是否能看到正确的内容



- Load data stored in a file：

```matlab
load('mydatal.mat')
load('mydata2.mat''-ascii')
```



思考：How does one save a specific variable?





#### **6.2、xlsread( ) and xlswrite( )：**

- xlsread( )：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509242354701.png)

- xlswrite( )：


![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509250005007.png)

```matlab
xlswrite(filename, data)               % 写入数据到默认工作表（Sheet1）的 A1 单元格开始
xlswrite(filename, data, sheet)        % 写入数据到指定工作表（sheet 可为名称或索引）
xlswrite(filename, data, sheet, range) % 写入数据到指定工作表的指定起始位置（如 'B2'）
```

- **`filename`**：字符串，Excel 文件名（含路径，如 `'data.xlsx'` 或 `'C:\test\result.xls'`）；
- **`data`**：待写入的数据，支持**数值矩阵、单元格数组（cell）、字符串数组**等；
- **`sheet`**：工作表名称（字符串，如 `'Sheet2'`）或索引（整数，如 `2` 表示第 2 个工作表）；
- **`range`**：起始单元格（字符串，如 `'A1'` 表示从 A1 开始写入，默认从 `'A1'` 开始）。



Getting Text in Excel Spreadsheet：

- Getting both the text and numbers（获取文本和数字）：

```matlab
Score Headerl=xlsread('04Score.xlsx'）
```





### **7、Low-level File I/O Functions：**

- fopen()：Open file, or obtain information about open files（打开文件，或获取有关已打开文件的信息）；
- fclose()：Close one or all open files（关闭一个或所有打开的文件）；
- fscanf()：Read data from text file（从文本文件读取数据）；
- fprintf()：Write data to text file（将数据写入文本文件）；
- feof()：Test for end-of-file（检验是否到文件结尾）；
- ferror()：查询文件的错误状态



Open and close a file：

```matlab
fid = fopen('[filename]','[permission]');
fclose(fid);		% 关闭文件
```



```matlab
fid = fopen(filename)                  % 以默认模式（只读文本）打开文件
fid = fopen(filename, permission)      % 以指定权限（permission）打开文件
fid = fopen(filename, permission, format)  % 指定文件格式（二进制/文本）
fid = fopen(filename, permission, format, encoding)  % 指定编码格式（如UTF-8）
```

**`filename`：文件名（必选）**

- 字符串类型，指定目标文件的路径（绝对路径或相对路径）。
  - 相对路径：相对于当前工作目录（可通过 `pwd` 查看），如 `'data.txt'`；
  - 绝对路径：完整路径，如 `'C:\project\results.csv'`（Windows）或 `'/home/user/data.txt'`（Linux/Mac）。
- 注意：MATLAB 中路径分隔符推荐用**正斜杠 `/`**（跨平台兼容），反斜杠 `\` 仅在 Windows 有效。

**`permission`：打开权限（核心参数，可选，默认 `'r'`）**

控制文件的 “读写方式” 和 “存在性处理”，常用权限如下：

| 权限字符 | 含义（文本模式，默认）                           | 适用场景                   |
| -------- | ------------------------------------------------ | -------------------------- |
| `'r'`    | 只读（默认），文件必须存在，否则打开失败         | 读取已有文件               |
| `'w'`    | 只写，若文件不存在则创建；若存在则清空内容       | 新建文件或覆盖已有文件     |
| `'a'`    | 追加写入，若文件不存在则创建；若存在则在末尾添加 | 向已有文件添加内容         |
| `'r+'`   | 读写，文件必须存在，可修改内容但不创建新文件     | 读取并修改已有文件         |
| `'w+'`   | 读写，若文件不存在则创建；若存在则清空内容       | 新建可读写文件或覆盖后读写 |
| `'a+'`   | 读写，若文件不存在则创建；若存在则在末尾添加     | 读取文件并在末尾追加内容   |

**二进制模式**：在权限后加 `'b'`（如 `'rb'`、`'wb'`），用于非文本文件（如图片、二进制数据），避免系统自动转换换行符（Windows 中 `\n` 与 `\r\n` 的转换）。

**`format`：文件格式（可选，默认 `'native'`）**

指定文件的字节顺序（endianness），主要用于跨平台读写二进制文件：

- `'native'`：使用当前系统的字节顺序（默认，推荐）；
- `'little-endian'`：小端字节序（如 x86 架构）；
- `'big-endian'`：大端字节序（如部分嵌入式系统）。

**`encoding`：编码格式（可选，默认系统编码）**

指定文本文件的编码（如 UTF-8、GBK），解决中文等非英文字符乱码问题：

- `'UTF-8'`：通用编码，支持多语言；
- `'GBK'`：中文编码（Windows 常用）；
- `'ISO-8859-1'`：西方字符编码。



`feof` 的作用是检查当前文件指针位置是否已到达文件末尾，语法极为简洁：

```matlab
status = feof(fid)
```

- **参数 `fid`**：文件标识符（file identifier），即 `fopen` 函数返回的正整数（必须是已成功打开的文件）。

- 返回值 `status`

  ：整数，指示文件指针状态：

  - `status = 0`：文件指针**未到达末尾**，仍有数据可读取；
  - `status = 1`：文件指针**已到达末尾**，无更多数据可读取；
  - `status = -1`：操作失败（如 `fid` 无效、文件未打开等），可通过 `ferror(fid)` 查看具体错误原因。



**Exercise：**

​		Writing Sine Values into A File；

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509251900499.png)

```matlab
x = 0:pi/10:pi;
y = sin(x);
fid = fopen('text.txt','w+');
for i=1:11
fprintf(fid,'%5.3f %8.4f\n',x(i),y(i));
end
fclose(fid);
type text.txt
```









## **四、绘图：**

### **1、plot( ):**

- plot（x，y）plots each vector pairs（x，y）
- plot(y) plots each vector pairs (x,y)，where x=[1…n]，n = length(y)
- Example：

```matlab
plot(cos(0:pi/100:2*pi))
plot(0:pi/100:2*pi,cos(0:pi/100:2*pi))
```

在使用`plot`的时候，他会把旧的图形给删掉，生成新的图形；







### **2、hold on/off：**

​		Use hold on to have both plots in one figure（使用hold on命令在同一个图形中绘制两个图。）；

```matlab
hold on
plot(cos(0:pi/20:2*pi));
plot(sin(0:pi/20:2*pi));
hold off
```







### **3、Plot Style：**

​		`plot(x, y, 'str')`使用在 str 中定义的格式绘制每个向量对(x,y)(检查线条样式)；

| Data markers（数据标记） | Line types（线条类型）（用于连接数据标记和线条类型） | Colors（颜色）         |
| ------------------------ | ---------------------------------------------------- | ---------------------- |
| Dot（.）                 | Solid line  （实线 - ）                              | Black（k）             |
| Asterisk(*)              | Dashed line（虚线 - - ）                             | Blue（b）              |
| Cross(x)                 | Dash-dotted line（虚线 - . ）                        | Cyan（青色）（c）      |
| Circle (O )              | Dotted line（虚线  ：）                              | Green（g）             |
| Plus sign (+)            |                                                      | Magenta（洋红色）（m） |
| Square(口)               |                                                      | Red（r）               |
| Diamond(o)               |                                                      | White（w）             |
| Five-pointed star(☆)     |                                                      | Yellow（y）            |
| Triangle (down ▽)        |                                                      |                        |
| Triangle (up Δ)          |                                                      |                        |
| Triangle (left ▷)        |                                                      |                        |
| Triangle (right ◁)       |                                                      |                        |
| hexagram (H)             |                                                      |                        |
| diamond（d）（菱形）     |                                                      |                        |

例：

```matlab
plot(sin(0:pi/50:2*pi),'o--r')
```







### **4、legend( )：**

- Add legend to graph（为图表添加图例）：

```matlab
legend('L1',…)
```

- Position adjustment（位置调整）；

```matlab
legend(labels)                  % 为图形中的对象依次添加标签（labels为字符串数组）
legend(labels, Name, Value)     % 添加标签并设置图例属性（如位置、字体等）
legend('off')                   % 关闭当前图例
legend(ax, ...)                 % 为指定坐标轴（ax）添加图例（而非当前坐标轴）
h = legend(...)                 % 返回图例句柄（用于后续修改属性）
```

- **`labels`**：字符串数组，包含每个图形对象的标签（如 `["曲线1", "曲线2"]`），标签数量需与图形中的对象数量一致（否则会警告）；
- **`ax`**：坐标轴句柄，指定要添加图例的坐标轴（适用于多子图 `subplot` 场景）；
- **`Name, Value`**：属性 - 值对，用于自定义图例外观（如位置、字体、边框等）。

标签参数（`labels`）：

`labels` 是图例的核心内容，需与图形中的对象**按顺序一一对应**。例如：

- 若图形中有 3 条曲线，`labels` 需包含 3 个字符串，分别对应第 1、2、3 条曲线；
- 若未指定 `labels`，MATLAB 会尝试使用对象的 `'DisplayName'` 属性作为标签（可通过 `plot(x,y,'DisplayName','曲线1')` 预先设置）。

常用属性（`Name, Value` 对）：

通过属性设置可灵活控制图例的位置、外观和行为，常用属性如下：

| 属性名          | 功能描述                                    | 示例值                                                       |
| --------------- | ------------------------------------------- | ------------------------------------------------------------ |
| `'Location'`    | 图例位置（基于图形或坐标轴）                | `'best'`（默认，自动选最佳位置）、`'north'`（顶部）、`'southeast'`（右下角）、`'outside'`（坐标轴外部） |
| `'FontSize'`    | 标签字体大小（磅）                          | `12`、`14`                                                   |
| `'FontName'`    | 标签字体（支持中文需指定中文字体）          | `'SimHei'`（黑体）、`'Times New Roman'`                      |
| `'TextColor'`   | 标签文字颜色                                | `'red'`、`[0.2, 0.5, 0.8]`（RGB）                            |
| `'EdgeColor'`   | 图例边框颜色                                | `'black'`、`'none'`（无边框）                                |
| `'FaceColor'`   | 图例背景颜色                                | `'white'`（默认）、`[0.9, 0.9, 0.9]`（浅灰）                 |
| `'NumColumns'`  | 图例标签的列数（默认 1 列，多列可节省空间） | `2`、`3`                                                     |
| `'Orientation'` | 标签排列方向（仅单列 / 单行时有效）         | `'vertical'`（垂直，默认）、`'horizontal'`（水平）           |

例：

```matlab
x = 0 : 0.5 : 4*pi;
y = sin(x);
h = cos(x);
w = 1./(1+exp(-x));
g = (1 / (4*pi)^0.5) .* exp((-1.*(x-2*pi).^2)./(2*2^2));
plot(x,y,'bd-', x,h,'gp:', x,w,'ro-', x,g,'c^-');
legend('sin(x)', 'cos(x)', 'sigmoid', 'Gauss function');
```







### **5、title( ) and ?label( )：**

用于添加标题与标签，可看下面两幅图的区别：

- title()
- xlabel()
- ylabel()
- zlabel()

```matlab
x = 0:0.1:2*pi;
y1 = sin(x);
y2 = exp(-x);
plot(x,y1,'--*',x,y2,':o');
xlabel('t = 0 to 2\pi');
ylabel('values of sin(t) and e^{-x}');
title('Function Plots of sin(t) and e^{-x}');
legend('sin(t)','e^{-x}');
```

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509260146897.png)

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509260147921.png)







### **6、text( ) and annotation( )：**

​		`text`是在图形中添加文本标注，用于在指定坐标位置添加自定义文本（如数据点说明、公式、注释等），`annotation`用于在整个图形窗口中添加注释（如箭头、矩形、文本框等）；

- Text with mathematical expreession using LaTex（使用LaTeX进行数学表达的文本，如积分符号等）；


```matlab
text(x, y, 'string', Name, Value)     % 添加文本并设置属性（如颜色、字体大小等）
```

- **`x, y`（或 `x, y, z`）**：文本放置的坐标（数值或向量），对应当前坐标轴的刻度（2D 图形用 `x,y`，3D 图形用 `x,y,z`）；
- **`'string'`**：要显示的文本（字符串或字符串数组）；
- **`Name, Value`**：可选的属性 - 值对，用于自定义文本外观（如颜色、字体、对齐方式等）。

**常用属性（`Name, Value` 对）**

通过属性设置自定义文本外观，常用属性如下：

| 属性名                  | 功能描述                        | 示例值                                                       |
| ----------------------- | ------------------------------- | ------------------------------------------------------------ |
| `'Color'`               | 文本颜色                        | `'red'`、`[0.5, 0.8, 0.2]`（RGB）                            |
| `'FontSize'`            | 字体大小（磅）                  | `12`、`14`                                                   |
| `'FontName'`            | 字体类型                        | `'SimHei'`（黑体，支持中文）、`'Times New Roman'`            |
| `'HorizontalAlignment'` | 水平对齐方式（相对于 `x` 坐标） | `'left'`（左对齐，默认）、`'center'`（居中）、`'right'`（右对齐） |
| `'VerticalAlignment'`   | 垂直对齐方式（相对于 `y` 坐标） | `'bottom'`（底部对齐）、`'middle'`（居中）、`'top'`（顶部对齐，默认） |
| `'Interpreter'`         | 文本解释器（控制特殊字符解析）  | `'none'`（不解析）、`'tex'`（默认，解析希腊字母 / 上下标）、`'latex'`（解析 LaTeX 公式） |



```matlab
annotation(fig, type, pos)               % 给指定图形fig添加type类型的注释，位置由pos定义
annotation(type, pos)                    % 给当前图形（gcf）添加注释
annotation(..., Name, Value)             % 添加注释并设置属性（如颜色、线宽等）
```

- **`fig`**：图形句柄（可选），指定要添加注释的图形窗口（默认是当前图形 `gcf`）；
- **`type`**：注释类型（字符串），常用类型包括 `'arrow'`（箭头）、`'rectangle'`（矩形）、`'ellipse'`（椭圆）、`'textbox'`（文本框）、`'line'`（直线）等；
- **`pos`**：位置向量，定义注释在图形中的位置和大小，基于**归一化图形坐标**（左下角为 `(0,0)`，右上角为 `(1,1)`）；
- **`Name, Value`**：属性 - 值对，用于自定义注释外观（如颜色、线宽、填充等）。

**常用属性（`Name, Value` 对）**

不同注释类型支持的属性略有差异，以下是通用常用属性：

| 属性名                  | 功能描述                                                     | 适用类型               |
| ----------------------- | ------------------------------------------------------------ | ---------------------- |
| `'Color'`/`'EdgeColor'` | 线条 / 边框颜色（`'red'`、RGB 值如 `[1,0,0]`）               | 所有类型（线条、边框） |
| `'LineWidth'`           | 线条 / 边框宽度（磅）                                        | 箭头、直线、矩形、椭圆 |
| `'LineStyle'`           | 线条样式（`'-'` 实线、`'--'` 虚线、`':'` 点线、`'-.'` 点划线） | 箭头、直线、矩形、椭圆 |
| `'FaceColor'`           | 填充颜色（用于矩形、椭圆、文本框）                           | 矩形、椭圆、文本框     |
| `'FaceAlpha'`           | 填充透明度（0~1，0 为完全透明，1 为不透明）                  | 矩形、椭圆、文本框     |
| `'String'`              | 文本内容（字符串或字符串数组）                               | 文本框                 |
| `'FontSize'`            | 字体大小（磅）                                               | 文本框                 |



```matlab
line(x, y)                  % 在 2D 坐标系中绘制直线，x/y 为坐标点向量
line(x, y, z)               % 在 3D 坐标系中绘制直线，x/y/z 为坐标点向量
line(x, y, Name, Value)     % 2D 绘图并设置线条属性（如颜色、线宽）
line(x, y, z, Name, Value)  % 3D 绘图并设置线条属性
h = line(...)               % 返回线条句柄（可用于后续修改属性）
```

常用属性（`Name, Value` 对）：

`line` 支持通过属性 - 值对自定义线条外观，常用属性如下（与 `plot` 的属性兼容）：

| 属性名              | 功能描述                                           | 示例值                                                       |
| ------------------- | -------------------------------------------------- | ------------------------------------------------------------ |
| `'Color'`           | 线条颜色（支持预定义颜色名、RGB 值或十六进制代码） | `'red'`、`[0.5,0.8,0.2]`、`'#FF0000'`                        |
| `'LineWidth'`       | 线条宽度（单位：磅，默认 0.5）                     | `2`、`1.5`                                                   |
| `'LineStyle'`       | 线型（实线、虚线等）                               | `'-'`（实线，默认）、`'--'`（虚线）、`':'`（点线）、`'-.'`（点划线） |
| `'Marker'`          | 数据点标记（如圆圈、方块等）                       | `'o'`（圆圈）、`'s'`（方块）、`'*'`（星号）、`'none'`（无标记，默认） |
| `'MarkerSize'`      | 标记大小（单位：磅）                               | `8`、`10`                                                    |
| `'MarkerEdgeColor'` | 标记边缘颜色                                       | `'blue'`、`[0,0,1]`                                          |
| `'MarkerFaceColor'` | 标记填充颜色                                       | `'yellow'`、`[1,1,0]`                                        |



例：

```matlab
x = linspace(0,3);						%生成一个从 0 到 3 的等间距向量。
y = x.^2.*sin(x);						%计算y
plot(x,y);								%绘图
line([2,2],[0,2^2*sin(2)]);				
str = '$$ \int_{0}^{2} x^2\sin(x) dx $$';
text(0.25,2.5,str,'Interpreter','latex');
annotation('arrow','x',[0.32,0.5],'Y',[0.6,0.4]);		%注意，这里使用的是归一化的坐标
```

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509260233770.png)



**Exercise：**

- Plot ʃ as a black line and g as a series of red circles for the range t = 1 to 2 in one figure（在同一个图中，将f作为黑色线条绘制，并将g作为一系列红色圆圈绘制，范围为t从1到2。）；

$$
f = t^2
$$

$$
g = sin(2πt)
$$

- Label each axis, and add title and legend（标记每个轴，并添加标题和图例）；


例：

```matlab
t = linspace(1,2);
f = t.^2;
g = sin(2*pi*t);
hold on
plot(t,f,'-b');
plot(t,g,'rO');
hold off
% 添加标题和标签
title('Mini Assignment #1');
ylabel('f(t)');
xlabel('Time(ms)');
%添加图例
legend('f=t^{2}','g=sin(2πt)','Location','best');
```

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509261153546.png)







### **7、Figure Adjustment（图形调整）：**

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509261923246.png)

- Several properties：
  - Font（字体）
  - Font size（字体大小）
  - Line width（线宽）
  - Axis limit（轴限）
  - Tick position（刻度位置）
  - Tick label（刻度标签）

#### **7.1、Graphical Objects（图形对象）：**

- A figure is composed of many objects

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509261234562.png)

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509261248628.png)

我们以下代码产生的图像为例：

```matlab
x = linspace(0,2*pi,1000);
y = sin(x);
plot(x,y);
set(gcf,'Color',[1 1 1]);
```





#### **7.2、Modifying Properties of An Object（修改对象属性）：**

- Strategy：
  1. ldentify the “handle” of an object（获取句柄（id？））；
  2. Fetch or modify the object's properties（获取或修改对象的属性）；			

- For example, to change thelimits of the x-axis:
  1. Find the handle of the x-axis（找到x的句柄）；
  2. Modify the limits（修改限制条件）；

##### **7.2.1、Identifying the Handle of An object：**

- Upon creation：

```matlab
h = plot(x,y);
```

我们在使用plot创建的时候，其会返回一个一个句柄用于指向我们我们创建的图线（Line）；



- Utility functions：
  - gca：Return the handle of the “current” axes（返回坐标轴的句柄）；
  - gcf：Return the handle of the “current" figure（返回“当前”图形的句柄）；
  - allchild：Find all children of specified objects（查找指定对象的所有子对象）；
  - ancestor：Find ancestor of graphics object（寻找其“父”）；
  - delete：Delete an object；
  - findall：Find all graphics objects；



##### **7.2.2、Fetching or Modifying Properties（获取或修改属性）：**

- To fetch properties, use：

```matlab
get();
```

- To modify properties, use：

```matlab
set();
```

- **Getting Object Properties：**
  - Getting properties of a graphical object: get()
  - 例：

```matlab
x = linspace(0,2*pi,1000);
y = sin(x);
h = plot(x,y);
get(h);
```

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509261935038.png)

```matlab
get(gca);
get(gcf);
```



- **Where do we modify the limits of the x-axis？**

- **Setting Axes Limits：**

```matlab
set(handle, propertyName, propertyValue)                  % 为单个对象设置单个属性
set(handle, propertyName1, value1, propertyName2, value2)  % 为单个对象设置多个属性
set(handle, struct)                                        % 用结构体批量设置多个属性
set(handles, propertyName, propertyValue)                  % 为多个对象（句柄向量）设置同一属性
```

- **`handle`**：图形对象的句柄（唯一标识符），如 `gcf`（当前图形窗口）、`gca`（当前坐标轴）、`line` 函数返回的曲线句柄等；
- **`propertyName`**：属性名（字符串，如 `'Color'`、`'FontSize'`）；
- **`propertyValue`**：属性值（类型取决于属性，如颜色可以是 `'red'` 或 `[1,0,0]`）；
- **`struct`**：包含属性名 - 值对的结构体（字段为属性名，值为属性值）；
- **`handles`**：多个对象的句柄组成的向量（如 `[h1, h2, h3]`），用于批量修改多个对象的同一属性。

**常见对象与核心属性**

不同类型的图形对象有不同的属性，以下是常用对象及其核心属性：

| 对象类型           | 句柄获取方式      | 核心属性（示例）                                             |
| ------------------ | ----------------- | ------------------------------------------------------------ |
| 图形窗口（figure） | `gcf` 或 `figure` | `'Color'`（背景色）、`'Position'`（位置和大小）、`'Name'`（窗口标题）、`'Visible'`（可见性） |
| 坐标轴（axes）     | `gca` 或 `axes`   | `'XLim'`/`'YLim'`（轴范围）、`'XLabel'`/`'YLabel'`（轴标签）、`'FontSize'`（字体大小） |
| 曲线（line）       | `plot` 返回值     | `'Color'`（颜色）、`'LineWidth'`（线宽）、`'LineStyle'`（线型）、`'Marker'`（数据点标记） |
| 文本（text）       | `text` 返回值     | `'String'`（文本内容）、`'FontName'`（字体）、`'Color'`（文本颜色）、`'Rotation'`（旋转角度） |



接着我们上面的问题，我们对x轴进行修改：

```matlab
set(gca,'Xlim',[0,2*pi]);
set(gca,'Ylim',[-1.2,1.2]);
```

**Alternative：**

```matlab
xlim([0,2*pi]);
ylim([-1.2,1.2]);
```



- **Setting Font and Tick of Axes：**

```matlab
set(gca,'Fontsize',25);
```

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509262102209.png)

```matlab
set(gca,'XTick',0:pi/2:2*pi);
set(gca,'XTicklabel',0:90:360);
```

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509262058672.png)

`xtick` 是**x 轴刻度位置**的属性，用于控制 x 轴上刻度线（tick marks）和刻度标签（tick labels）的具体数值位置。它是坐标轴（`axes` 对象）的核心属性之一，直接决定了 x 轴上哪些位置会显示刻度；

- **刻度线（tick marks）**：x 轴上垂直于轴线的小短线，用于标记数据的参考点；
- **刻度标签（tick labels）**：刻度线旁边的文本（通常是数值），说明该刻度对应的具体值；
- **`xtick` 属性**：存储这些刻度线所在的**数值位置**（以 x 轴数据坐标为单位），是一个向量。



```matlab
set(gca,'FontName','Times New Roman');
set(gca,'XTickLabel',{'0','\pi/2','\pi','3\pi/2','2\pi'});
```

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509262126212.png)



- **Line Specification：**
  - Line style and width：

```matlab
set(h,'LineStyle','-.','LineWidth',7.0,'color','g');		%改变线条样式，线宽，线的颜色
```

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509262135011.png)

同时，我们可以在生成图形的时候直接对线条操作；



- **Marker Specification（标记规格）：**

在我们绘图的时候，实际上是很多个点来构成的，每个点上都有一个Marker，我们可以改变Marker的颜色，大小和形状等属性

示例：

```matlab
x = rand(20,1);						% 生成20行1列的[0，1]随机分布的矩阵
set(gca,'FontSize',18);				
plot(x,'-md','LineWidth',2,'MarkerEdgeColor','K','MarkerFaceColor','g','MarkerSize',10);
xlim([1,20]);
```

**MarkerEdgeColor**：标记的边缘颜色

**MarkerFaceColor**：标记的内部填充颜色

**MarkerSize**：标记的大小

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509262211436.png)



**Exercise:**

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509262212393.png)

```matlab
t = linspace(1,2);
f = t.^2;
g = sin(2*pi*t);
hold on
h1 = plot(t,f,'-b');
h2 = plot(t,g,'r.');
hold off
% 改变图像属性
set(gca,'XLim',[1,2],'YTick',-1:1:4,'Fontsize',	18);
set(h1,'LineWidth',4,'color','k');
set(h2,'MarkerSize',12,'MarkerEdgeColor',[0.6, 0, 0.6],'MarkerFaceColor',[0.6, 0, 0.6]);
% 添加标题和标签
title('Mini Assignment #1');
ylabel('f(t)');
xlabel('Time(ms)');
% 添加图例
legend('f=t^{2}','g=sin(2πt)','Location','best');
```

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509262251154.png)

















