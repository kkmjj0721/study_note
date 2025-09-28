# **webots**

## **一、前言：**

​		Webots 是一个开源的三维移动机器人模拟器。

> **注：应该对移动机器人、C、C++、Java、Python 或 MATLAB 编程以及 VRML97（虚拟现实建模语言）有最低限度的了解**

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509141353806.png)

用来建模的；

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509141354691.png)





## **二、安装：**

### **安装步骤：**		

​		2021b前打开下载的安装包setup.exe文件，一直点击下一步即可实现完成（注意记住安装地址）。

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509131507916.png)

下载完成后点击Finish；然后选择主题后打开webots；

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509131519321.png)

左边的对话框打上对勾，然后点击ok；右边的对话框点击close；

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509131522624.png)

### **中文设置：**

Tools -> Preferences...  然后切换中文后点击OK后重启软件；

​		![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509131526174.png)

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509131529865.png)

### **安装成功检测：**

​		从2021b开始，下载的文件不再提供模型，需要我们从源码从将project导入到我们的下载目录里；

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509131615194.png)

然后我们重启软件；帮助 -> 引导之旅；

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509131620850.png)

在这个里面随机打开一个project；

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509130925721.png)

​		无论打开什么工程，下面都会有警告（就是说因为我们是从源代码拷贝过来的），它的控制器是它代码有的，而我们是直接拷贝过来的，所以我们还需要再编译一下；编译之后才能运行；

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509130936639.png)

在右边的代码界面，点击右上角的小齿轮；

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509130942600.png)

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509130947602.png)

**建议将其勾上**，点完复制后点击close，然后程序会自动编译；

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509130948458.png)

这里分别是重新下载与重新加载；我们**选择重新下载**（Reload）；

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509131101119.png)

然后保存；

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509131100210.png)

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509131102989.png)

### **下载链接：**

`链接: https://pan.baidu.com/s/1KG-ZE7Pq9PMCkLEMBJ2BKA 提取码: 1234			（主软件）`
`链接: https://pan.baidu.com/s/1isrDoSP-gHjG1wyBoPAF7Q 提取码: 1234				（源代码）`









## **三、3D区域基本操作：**

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509140717818.png)

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509140723415.png)









## **四、向导：**

### **1、新建项目目录向导：**

​		![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509140749863.png)

创建时选择地址后会有四个选项，建议将其全勾上；

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509140805014.png)

完成该步之后，在左侧场景树会出现几个文件：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509140802910.png)

> **注意**：在每次有大的操作后，点击保存；





### **2、添加机器人：**

在上一步操作后，右键，点击新增

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509140756049.png)

随便选择一个机器人即可，但因为从此处添加，依旧是从源文件中添加进来，所以我们还是需要编译；

添加机器人后也会出现一个机器人的文件：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509140807256.png)

我们找到“controller”，然后在下方的属性栏，点击编辑；

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509140809875.png)

然后在右边会出现代码，点击编译，和上面“安装成功检测”是一样的操作；

然后机器人就可以动了；





### **3、添加新机器人控制器：**

​		![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509140749863.png)

选择编程语言：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509140816911.png)

选择编译器：（选择webots自带的编译器即可）

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509140820310.png)

控制器名称：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202509140822550.png)























