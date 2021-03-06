# Anaconda3

> Win10环境下进行安装和配置！

## 下载

1. 进入`Anaconda`的官网进行[下载](https://www.anaconda.com/products/individual) ；
2. 选择你想下载的`Python`版本；
3. 选择你的操作系统和位数，这里我们选择的是`Windows64`位；
4. 然后点击`Download`按钮就开始下载了；

## 安装

正常安装完成就可以。

**注意**：

安装过程中一定要选择添加环境变量：

<center><img src="https://s1.ax1x.com/2020/07/31/alZcuD.png" alt="alZcuD.png" border="0" /></center>

如果安装过程中你没有选择`Add PATH` 就需要配置环境变量了：[如何配置你电脑上的环境变量](https://blog.csdn.net/Delicious_Life/article/details/86723736)

<center><img src="https://s1.ax1x.com/2020/07/31/almllV.png" alt="almllV.png" border="0" /></center>

# 配置环境

## 配置tensorflow

1、打开`anaconda`安装时自带的`Anaconda prompt`

2、打开后,输入中科大镜像的`tensorflow` 的下载地址(如果你已经在墙外翱翔了,可以省略这一步):

 ```html
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/msys2/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/bioconda/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/menpo/

conda config --set show_channel_urls yes
 ```

 > [更换为其它源](https://blog.csdn.net/observador/article/details/83618540?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2.nonecase)
 
3、接着我们开始创建一个`python3.6` 的环境,因为如果你安装的是最新的`anaconda` ,它默认环境为`py3.8` ,并且在不久之前,`tensorflow` 已经开始支持`py3.6` ,所以我们创建一个`py3.6` 环境:

 ```html
conda create -n tensorflow_1.12 python=3.6
 ```
 
4、启动`anaconda` 中的`py3.6` 环境:

 ```html
activate tensorflow_1.12
 ```
 
如果不能进入,则重新执行第3步骤

5、进入`py3.6` 的环境中后,我们就可以进行安装了(此处我们安装的是`CPU版本`的`tensorflow`):

 ```html
pip install --upgrade --ignore-installed tensorflow==1.12.0
  ```
> `GPU`版本的`Tensorflow`安装：[Windows10-64位下Anaconda3安装GPU版Tensorflow详细过程](https://blog.csdn.net/looknm/article/details/95212296)
  
6、当我们不使用`tensorflow`时,我们就可以使用:

 ```html
aonda deactivate
 ```
 
 退出该环境
 
7、开始测试一下是否安装成功:

重新打开`Anaconda Prompt`—>`activate tensorflow_1.12`—>`python`来启动`tensorflow`，并进入`python`环境

 ```python
#TensorFlow使用图(Graph)来表示计算任务；并使用会话(Session)来执行图，通过Session.close()来关闭会话（这是一种显式关闭会话的方式）。会话方式有显式和隐式会话之分。
import tensorflow as tf
hello = tf.constant('Hello, TensorFlow!')  #初始化一个TensorFlow的常量
sess = tf.Session()  #启动一个会话
print(sess.run(hello))  
 ```
 
如果可以准确的输出结果,那么恭喜你,安装`tensorflow`成功!

## 配置keras

1、打开`anaconda`安装时自带的`Anaconda prompt`

2、创建一个`py3.6` 的`keras`环境:

 ```html
conda create -n keras python=3.6
 ```

 > CondaHTTPError:HTTP 000 CONNECTION FAILED错误的解决：
 > [解决方案1](https://blog.csdn.net/weixin_43837522/article/details/99942700?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase)
 > [解决方案2](https://blog.csdn.net/ebzxw/article/details/80702506)
 > [解决方案3](https://blog.csdn.net/u013383596/article/details/87718472)
 
3、启动`anaconda` 中的`py3.6` 环境:

 ```html
activate keras
 ```

4、安装`keras`

```html
conda install keras
```

5、查看是否成功

```html
import keras
```

如果输出无异常，那么就是安装成功！

## 配置pytorch

首先，打开 `PyTorch` 官网安装页面（需自备梯子）：https://pytorch.org/get-started/locally/

<center><img src="https://s1.ax1x.com/2020/04/09/G5tP9f.png" alt="G5tP9f.png" border="0" /></center>

- `PyTorch Build` 就是选择下载稳定版（`Stable`）还是预览版（`Preview`），这里一般选择稳定版（`Stable`）
- `YourOS` 不多说，选择自己对应的操作系统类型
- `Package`：下载方式，教程提供的是 `Conda` 方式
- `Language`：`python` /`c++`/`java`
- `CUDA`：如果要下载 `gpu` 版本，那么就选择你对应的 `cuda` 的版本（不知道自己 `cuda` 版本的请打开`cmd`输入`nvidia-smi`即可查看到）；如果下载 `cpu` 版本，那么选择 `None`
- `Run this Command`：当你选择好版本后，会自动再次生成下载安装 `PyTorch` 的命令

然后复制页面中`Run this Command`后的代码,粘贴在你的命令行,等待安装完成就可以了~

查看是否成功：

```html
import torch
```

如果输出无异常，那么就是安装成功！

