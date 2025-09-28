# **VMC论文学习**

## **一、VMC原理：**

​		VMC 是一种直觉控制方式，其核心思想是**利用假想的虚拟构件**(如弹簧、阻尼器、轴承等等)**连接机器人内部作用点**，**或者连接作用点与外部环境**，**产生相应的虚拟力**来“驱使”机器人实现期望的运动。这些**虚拟力通过 Jacobian 矩阵计算得到期望的关节力矩，作为关节控制的输入**，驱动机器人运动以产生和虚拟构件一样的作用效果。VMC 的应用关键在于两点：一是**在每个需要控制的自由度上构造恰当的虚拟构件**以产生合适的虚拟力；二是**在不同的相位状态利用相应的 Jacobian矩阵**计算期望的关节力矩；

​		虚拟力不是实际存在的作用力或力矩,机器人的运动最终是通过关节力矩实 现的｡为了将**工作空间(Task Space)**的力或力矩映射成**关节空间(Joint Space)**的关节 力矩,需要先求得这两个空间的位置映射关系,即**正运动学模型**：
$$
x=f(q) (3.1)
$$

$$
x=[\begin{array}{llll}x_{1} & x_{2} & ... & x_{m}\end{array}]^{T}
$$

为机体坐标系相对于地面坐标系的 **m 个自由度对应的位姿向量**, 
$$
q=[\begin{array}{llll}q_{1} & q_{2} & ... & q_{n}\end{array}]^{T}
$$
 为 **n 个关节变量的位置向量**。进一步求 x 分别 对 q 的偏导数得到：
$$
\left\{\begin{array}{c} \delta x_{1}=\frac{\partial f_{1}}{\partial q_{1}} \delta q_{1}+\cdots+\frac{\partial f_{1}}{\partial q_{n}} \delta q_{n} \\ \vdots \\ \delta x_{m}=\frac{\partial f_{m}}{\partial q_{1}} \delta q_{1}+\cdots+\frac{\partial f_{m}}{\partial q_{n}} \delta q_{n} \end{array}\right.
\\即、\\
\delta x=\left[\begin{array}{ccc} \frac{\partial f_{1}}{\partial q_{1}} & \cdots & \frac{\partial f_{1}}{\partial q_{n}} \\ \vdots & \ddots & \vdots \\ \frac{\partial f_{m}}{\partial q_{1}} & \cdots & \frac{\partial f_{m}}{\partial q_{n}}\end{array}\right] \delta q
\\即、\\
\begin{bmatrix}
\delta x_1  \\
\delta x_2  \\ 
\vdots		\\
\delta x_m	
\end{bmatrix}
=
\begin{bmatrix}
\frac{\partial f_{1}}{\partial q_{1}} & \frac{\partial f_{1}}{\partial q_{2}} & \cdots & \frac{\partial f_{1}}{\partial q_{n}}\\
\frac{\partial f_{2}}{\partial q_{1}} & \frac{\partial f_{2}}{\partial q_{2}} & \cdots & \frac{\partial f_{2}}{\partial q_{n}}\\ 
\vdots	& \vdots & \ddots & \vdots\\
\frac{\partial f_{m}}{\partial q_{1}} & \frac{\partial f_{m}}{\partial q_{2}} & \cdots & \frac{\partial f_{m}}{\partial q_{n}}
\end{bmatrix}
\begin{bmatrix}
\delta q_1  \\
\delta q_2  \\ 
\vdots		\\
\delta q_n	
\end{bmatrix}
\\即、\\
\delta {\pmb x}_{(m× 1)}={\pmb J}_{(m× n)}\cdot \delta {\pmb q}_{(n× 1)}\\
若在四足机器人运用中，可写成下式(假设我们先不考虑姿态)：\\
\begin{bmatrix}
\delta x  \\
\delta y  \\
\delta z
\end{bmatrix}
=
\begin{bmatrix}
\frac{\partial f_{1}}{\partial q_{1}} & \frac{\partial f_{1}}{\partial q_{2}}  & \frac{\partial f_{1}}{\partial q_{3}}\\
\frac{\partial f_{2}}{\partial q_{1}} & \frac{\partial f_{2}}{\partial q_{2}}  & \frac{\partial f_{2}}{\partial q_{3}}\\ 
\frac{\partial f_{m}}{\partial q_{1}} & \frac{\partial f_{m}}{\partial q_{2}}  & \frac{\partial f_{m}}{\partial q_{3}}
\end{bmatrix}
\begin{bmatrix}
\delta q_1  \\
\delta q_2  \\ 
\delta q_3	
\end{bmatrix}
$$
即得到Jacobian 矩阵，它将**关节速度**映射成机体**位姿速度**。根据**虚功原理**， 可以得到： 
$$
𝓣^T  \delta q + (-F)^T\delta x = 0
$$

其中，𝓣 = [𝓣1  𝓣2  ......  𝓣n]^T 为关节力矩列向量，F = [F1  F2  ......  Fm]^T为外部作用力。所以我们可得到：

$$
𝓣 = J^TF
$$
在这个公式中，Jacobian **矩阵J**随着**关节角度q**变化而变化。当J为奇异矩阵时，在某些特定方向上 可以增大或者减小F却不会影响𝓣的计算结果。也就是说，**在奇异构型附近，很小的关节力矩就能够在某些方向上产生很大作用力**。这也解释了为什么行走类四足动物在承载能力上具有较大优势，即当其腿结构在尽量伸展以后接近了奇异构型，只需要较小的关节力矩能够产生较大的竖直支撑力。值得一提的是，利用上诉公式进行关节力矩计算，不涉及逆运动学求解(或者J的逆解)，因此即使结构处于奇异构型，也能根据给定的F计算得到确定的𝓣。

​		在足式机器人运动控制中，常用的虚拟构件主要是弹簧与阻尼器。其本构方程为：
$$
F_u = K_u(u_d - u) + B_u(v_d - v)
$$
 **Fu为虚拟构件产生的虚拟力(**或力矩)，**Ku 和Bu分别为弹性和阻尼系数**，**u和v分别为相应广义坐标的实时位移和速度**，下标 表示期望值。虚拟力常常施加在机器人机体质心处，以控制机器人机体实现期望运动。如果要**控制机器人某一点保持在期望的位置(例如质心高度控制)，则同时施加弹簧和阻尼构件**；若要**控制机器人达到某期望速度(例如水平移动速度控制)，则只施加阻尼构件(令 Ku = 0)**。注意这里的线性虚拟构件仅仅是一种简单常用的形式，虚拟构件还可以有其他的非线性本构方程。从上式可以看出，虚拟构件产生的虚拟力直接与高层的控制决策(期望位移与期望速度)联系在一起，易于执行上层指令并实现复杂运动。公式还可以在最右端加上一个前馈项，用来提前补偿相应方向上的力或者力矩，例如在竖直方向加上重力补偿项；

​		将所有施加的虚拟力写成向量形式，有：
$$
F_(vm) = K(x_d - x) + B(v_d - v)
$$
X = [x1  x2  ...  xm]^T为m个机体自由度对应的位置向量，Fvm = [F1  F2  ...  Fm]^T为对应的虚拟力列向量，K和B分别是弹性和阻尼系数矩阵(对角矩阵)，且有：
$$
\begin{bmatrix}
F_1\\
F_2 \\ 
F_3
\end{bmatrix}
=
\begin{bmatrix}
K_1  & 0 & 0\\
0 & K_2 & 0\\ 
0	& 0 & K_3
\end{bmatrix}
(\begin{bmatrix}
x_s \\ 
y_s \\ 
z_s	
\end{bmatrix} - 
\begin{bmatrix}
x_n \\ 
y_n \\ 
z_n	
\end{bmatrix}) + 
\begin{bmatrix}
B_1  & 0 & 0\\
0 & B_2 & 0\\ 
0	& 0 & B_3
\end{bmatrix}
(\begin{bmatrix}
V_x \\ 
y_s \\ 
z_s	
\end{bmatrix} - 
\begin{bmatrix}
x_n \\ 
y_n \\ 
z_n	
\end{bmatrix})
$$
根据利用公式，虚拟构件所产生的虚拟力与期望力矩之间的转换关系为：
$$
𝓣_d = J^TF_(vm)
$$


> - **虚拟力**：是 “工长的指令”—— 比如 “往前推 10N 的力”“往上抬 5N 的力”，它描述的是 “我们希望机器人在工作空间（比如足端、机体）产生的理想效果”，但**不是真实存在的力**（机器人没有 “手” 直接推 / 抬，只有关节电机）。
> - **关节力矩**：是 “工人的动作”—— 机器人的电机只能通过转动关节（比如髋关节、膝关节）产生力矩，最终驱动腿部运动，间接实现 “虚拟力的理想效果”。

> | 空间类型 | 定义（描述机器人的 “维度”）                              | 例子（以四足机器人单腿为例）                     | 符号对应（论文公式）                                         |
> | -------- | -------------------------------------------------------- | ------------------------------------------------ | ------------------------------------------------------------ |
> | 工作空间 | 机器人**实际作用的物理空间**，描述 “位姿”（位置 + 姿态） | 足端在地面的坐标（x=0.2m,y=0,z=-0.3m）、机体高度 | \(x = [x1,x2,...,xm]^T\)（m 是自由度，如三维空间 6 个：3 平移 + 3 旋转） |
> | 关节空间 | 机器人**关节运动的空间**，描述 “关节角度”                | 侧摆髋关节转 10°、前摆髋关节转 20°、膝关节转 30° | \(q = [q1,q2,...,qn]^T\)（n 是关节数，如单腿 3 个关节，四腿 12 个） |

> - **虚功原理**： 虚功（W虚）= 力（或力矩） ×   对应的虚位移（或虚角位移），核心是 “力与位移方向一致时做正功，相反时做负功”。
>
> ![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509101555182.png)

> - **奇异矩阵**：当雅克比矩阵 J 为**奇异矩阵**时，其数学特征是 “行列式为 0” “不可逆”，物理意义是：机器人处于 **“运动受限构型”**—— 在某些方向上，即使关节动了，位姿也几乎不动（或完全不动），反之，在这些方向上的力 / 位姿变化，对关节力矩的影响会变得 “异常”。
>
> ![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509101632480.png)









## **二、VMC的特点：**

​		Jacobian转置控 制器忽略了机器人的动力学因素，具有更简单并且直观的控制规则，虽然能实现 稳定的运动控制，但是并不能达到精确的控制目的。对于工业机器人来说，其工 作任务往往要求具有较高的控制精度，因此基于模型的工作空间控制方法更能满 足控制要求。

​		然而，对于多关节的机械臂来说，其完整的动力学模型非常复杂。而对于四足机器人，其结构相当于四个机械臂的并联机构，并且机器人上没有绝对固定的参考坐标系，为浮动基座系统，直接利用基于模型的工作空间控制方法将会非常困难。

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509102016461.png)













