# **Github使用教程与一些问题解决**

## **一、使用教程：**

### **1、安装git：**

下载网址：[**Git - Downloads**](https://git-scm.com/downloads)找到对应版本下载；

安装步骤：

- ![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510160031760.png)

  双击即可；
- ![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510160032385.png)

  出现该界面
- 一直下一步，直到到该下面两个界面

  ​	![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510160033261.png)

​	![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510160034156.png)

按图中选择即可；

- 一直下一步到“**install**”
- 至此我们安装git结束；在安装的时候我们可以去创建一个github账号（注意需记得自己的“**名字**”以及“**创建邮箱**”）



### **2、配置git：**

- 在搜索框搜索**git**![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510160039445.png)点击**git bash**;

  ![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510160040681.png)

- 1).先输入:

  ```
  git config -l
  ```

  查看git的当前配置，会是下面这样（因为我已经配置过了，这里会显示**name**以及**email**）：

  ![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510160047791.png)

- 2).与github连接：

  ```
  git config --global user.name "输入你注册时创建的名字"
  ```

  然后：

  ```
  git config --global user.email "输入你注册的邮箱"
  ```

  然后我们在查看一下git配置，应该就和我上面差不多了；

- 3).生成自己的公钥和私钥：

  输入：

  ```
  ssh-keygen -t rsa
  ```

  ![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510160050655.png)一直按回车即可；

  然后，我们在c盘 ---> 用户 ---> **。。。(此处为你自己的用户名) **---> `.ssh(为一个文件夹)`

  ![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510160054971.png)

  在该文件夹中，我们找到以**`.pug`**结尾的文件，以记事本打开，然后复制；

  回到github中：

  ![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510160056384.png)

  点击右上角的头像，找到**settings**，点进去；

  ![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510160058820.png)

  点击**`New ssh key`**

  ![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510160059670.png)

  在**title**那里输入：**`Myown`**，然后在下面的**key**内将我们刚刚复制的输入进来，最后点击**ADD SSH KEY**即可；

  然后我们测试一下是否连接成功：

  ```
  ssh -T git@github.com
  ```

  ![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510160103055.png)

  因为我已经连接过了，所以会直接显示HI。。。，如果是第一次前面会显示一些其他的东西（它会出现一个选项，输入yes即可）；

  输出为Hi。。。，表示连接成功；



### **3、创建仓库并提交：**

- 我们回到github的主页面：

  ![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510181443418.png)

​		在左上角有一个**new**，点击，创建一个仓库；如，我这里创建一个测试github提交的仓库：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510181446589.png)

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510181447261.png)

​		这样就成功创建了一个仓库；

- 接下来：我们在随便一个地方创建一个文件夹，用于本地存储：

​		如：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510181449582.png)

​		然后我们回到github，将这一串链接复制下来；

​		![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510181450891.png)

​		再回到我们刚刚创建的文件夹内，右键，找到

​		![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510181451385.png)

​		点击，会出现一个命令行，然后我们将仓库克隆到本地：

```
git clone 刚刚复制的链接
```

​		![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510181453222.png)

然后开始克隆，我们可以看到：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510181454376.png)

这时，我们回到刚刚的文件夹内，会发现出现了一个文件夹（名字为你的仓库名）：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510181455348.png)

点进这个文件夹内，会发现出现了一个文件（.git）（没有的自行打开隐藏的文件）和一个md文件：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510181456002.png)

我们在这个仓库内创建一个文件：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510181458074.png)

然后我们在这个仓库内，打开git的命令行：（操作和上面一样，右键找到“open git bash here”）

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510181500191.png)

可以看到，发生了一些变化，出现了一个**main**，接下来我们查看文件状态：

```
git status
```

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510181501665.png)

可以看到，这里并未同步，我们先：（添加文件到暂存区）

```
git add .
```

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510181502705.png)

然后我们再输入：

```
git status
```

可以看到，现在同步了：

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510181503560.png)

然后，我们提交暂存区内容到本地仓库并附上描述信息：

```
git commit -m "描述信息"
```

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510181507601.png)

最后，我们将其推送到远程仓库：

```
git push
```

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510181509034.png)

我们回到刚刚在github上创的仓库：可以看到我们的文件被推送到远程仓库了

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510181510930.png)







## **二、问题解决：**

### **1、git clone出现 fatal: unable to access 'https://github.com/...'：**

 		发生这种情况是因为代理是在git中配置的。既然它是https代理（而不是http）git config http.proxy和git config --global http.proxy也无济于事。

先查看git配置：

```
git config --global -l
```

​		如果你没有任何与https代理相关的内容，例如https_proxy = ...问题不在这里。

​		如果您有与https代理相关的内容，请将其从〜/ .gitconfig文件中删除，然后重试。(直接在你的电脑中搜索该文件，然后打开，删除后保存，建议在c盘-->用户下搜索，这样会快一点)；

![](https://cdn.jsdelivr.net/gh/KKMJJ0721/Blog_pic/202510181515409.png)





### **2、ssh: connect to host github.com port 22: Connection refused：**

​		这个错误提示的是连接**`github.com`**的22端口被拒绝了。可以简单理解为此门不通，既然这个端口号走不通，那换一个端口号试试看。

​		出现这个问题，一般是：

- DNS解析被运营商劫持了
- 使用了科学上网工具

第一种比较少见，我们先尝试将科学上网工具关掉（如某++），如果不成功，只能上网求助，这里我也不太会；





### **3、最后：**

​		欢迎大家指出本文中的错误部分，并且将其补充完整；
