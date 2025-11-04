# Anaconda的安装及使用：

[TOC]



## 一、前言：

​		Anaconda 本质是一个 “数据科学工具箱”，它通过 **conda 包管理 + 环境隔离 + 预装工具** 三大核心能力，解决了数据科学开发中 “安装麻烦、依赖冲突、环境混乱” 的痛点，让开发者可以更专注于业务逻辑（比如数据分析、模型训练），而不是工具配置。如果你的工作涉及 Python/R 数据科学（数据分析、机器学习、深度学习等），Anaconda 几乎是必备工具。

​		建议非必要不选择轻量版；（有时需自行下载库）





## 二、安装：

​		因该软件为外国的，我们这里使用清华源来进行下载；https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/

​		选择自己需要安装的版本；

​		下载后，我们会得到一个.sh文件，接着我们在命令行输入：

```
bash 刚刚下载.sh文件的目录
```

​		例如：

```
bash ~/Downloads/Anaconda3-2021.11-Linux-x86_64.sh
```

​		然后回车，直到出现：Do you accept the license terms? [yes|no]；表示协议阅读完毕输入yes即可继续安装（反正挺大一堆）；

​		然后就会到确认安装位置，此处直接回车即可；

![img](https://pic3.zhimg.com/v2-b5dff4478624c17d6713e187a96e8238_r.jpg)

​		再然后一直按着回车即可，知道出现选择yes和on的时候，输入yes即可；

​		最后配置环境变量，在主目录中找到：`.bashrc`该文件，点进去进行修改；在最后一行输入：

```
export PATH=/home/{yourname}/anaconda3/bin:$PATH
```

​		然后在命令行输入：

```
export PATH=/home/anaconda3/bin:$PATH
```

​		现在安装以及环境变量设置完成；





## 三、安装后的提示解读：

1. For changes to take effect, close and re-open your current shell.，翻译过来就是：关闭当前命令行，并重新打开，刚刚安装和初始化Anaconda设置才可以生效，重新打开一个命令行后直接就进入了conda的base环境。
2. If you'd prefer that conda's base environment not be activated on startup, set the auto_activate_base parameter to false:，翻译过来就是：如果您希望conda的基础环境在启动时不被激活，请将auto_activate_base参数设置为false，命令如下：

```text
conda config --set auto_activate_base false
```

当然这一条命令执行完毕后，想要再次进入conda的base环境，只需要使用对应的conda指令即可：

```text
conda activate base
```





## 四、验证安装：

​		安装完成后，关闭并重新打开终端，然后输入以下命令验证Anaconda是否安装成功：

```text
conda --version
```

​		如果之前安装有错，或者最后conda初始化没做，你会看到如下结果：

![img](https://pic2.zhimg.com/v2-08c525b2f3c9070fad60b73bc8155a23_1440w.png)

​		出现下面的结果为好的：

![img](https://picx.zhimg.com/v2-7637a4b35c0f4a0c5bdebe0fb134ae97_1440w.png)





## 五、**Anaconda常用命令：**

### 1.**基础命令**

- 查看conda帮助信息：

```text
conda --help  # 或者：conda -h
```

- 查看conda版本：

```text
conda --version
```

- 更新conda：

```text
conda update conda
```

### **2.与环境相关的命令**

- 创建conda环境：

```text
conda create --name <环境名> <包名>
```

例如，创建一个名为myenv，Python版本为3.8的环境：

```text
conda create --name myenv python=3.8
```

- 激活conda环境：

```text
conda activate <环境名>
```

- 退出conda环境：

```text
conda deactivate
```

- 查看所有已创建的conda环境：

```text
conda env list
```

- 删除conda环境：

```text
conda remove --name <环境名> --all
```

### **3. 与环境中包相关的命令**

- 在当前环境安装包：

```text
conda install <包名>
```

- 更新当前环境中的包：

```text
conda update <包名>
```

- 删除当前环境中的包：

```text
conda remove <包名>
```

- 查看当前环境下已安装的所有包及其版本：

```text
conda list
```

- 搜索可用的包版本：

```text
conda search <包名>
```