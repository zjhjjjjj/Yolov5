# Anaconda 安装pytorch和paddle深度学习环境

---

#### 简介：

​	利用GPU进行深度学习时，需要去NVIDIA官网下载` CUDA的安装程序` 和  `cudnn的压缩包,` 操作繁琐且进行环境配置很麻烦， 利用anaconda安装配置` pytorch` 和  `paddlepaddle`  环境会自动帮我们配置好` cuda和cudnn`





## 一、NVIDIA驱动安装和更新

---

​		显卡驱动程序是用来`驱动显卡`的`程序`,它是硬件对应的软件。驱动程序即添加到操作系统中的一小块代码，其中包含有关硬件设备的信息。



① `查看显卡版本`

步骤：此电脑右击-->管理-->设备管理器-->显示适配器，由图可知显卡为 `GTX 1660显卡`



<img src="https://github.com/zjhjjjjj/image/blob/main/111.PNG?raw=true" alt="111.PNG" style="zoom: 50%;" />

② `下载驱动版本`

得知显卡信息后，我们可以去对  [英伟达官网](https://www.nvidia.cn/Download/index.aspx?lang=cn)  上找对应的`显卡驱动`进行下载。  

这里以我的笔记本为例子（如图参考）：

产品类型  ——> GeForce

产品系列  ——> GeForce GTX 16 Series(Notebooks笔记本类型)

下载类型 ——>  Studio版本为 办公类型，Game Ready版本为 游戏娱乐

按照如下操作进行搜索、下载。



<img src="C:\Users\35198\AppData\Roaming\Typora\typora-user-images\image-20211214160845819.png" alt="image-20211214160845819" style="zoom: 50%;" />

<img src="C:\Users\35198\AppData\Roaming\Typora\typora-user-images\image-20211214153011339.png" alt="image-20211214153011339" style="zoom: 67%;" /><img src="https://raw.githubusercontent.com/zjhjjjjj/image/main/image-20211214153228727.png" alt="image-20211214153228727" style="zoom:80%;" />



```
# 安装完显卡驱动后， 使用 win + R 组合键，输入命令
nvidia-smi
```

 		得到如下图的信息，从图中可以看出驱动版本为`472.47` ; 最高支持CUDA版本为 `11.4` 版本，`记住这个信息方便安装环境。`

<img src="https://raw.githubusercontent.com/zjhjjjjj/image/main/image-20211214161840348.png" alt="image-20211214161840348" style="zoom:67%;" />



## 二、Anaconda的安装

---

打开 [Anaconda官网](https://www.anaconda.com/products/individual#Downloads) ，我打开的版本为3.9。如果想更低版本，[可以来这](https://www.cnblogs.com/xiaochouk/p/12081633.html) 。



我下载的是这个

<img src="https://raw.githubusercontent.com/zjhjjjjj/image/main/image-20211214162712614.png" alt="image-20211214162712614" style="zoom: 50%;" />

下载完后进入安装，这里选 Just me

<img src="https://raw.githubusercontent.com/zjhjjjjj/image/main/image-20211214162850724.png" alt="image-20211214162850724" style="zoom: 67%;" />

持续下一步，慢慢的，当看到这个时，要打勾上， 这里是将`anaconda`添加到``环境变量``中里面去。

<img src="https://raw.githubusercontent.com/zjhjjjjj/image/main/image-20211214163116116.png" alt="image-20211214163116116" style="zoom: 67%;" />

安装完后，按下开始键``（Win键）``左边会出现``anaconda3`这个文件夹，说明已经安装完成

<img src="https://raw.githubusercontent.com/zjhjjjjj/image/main/image-20211214163354324.png" alt="image-20211214163354324" style="zoom: 67%;" />

##  三、Pytorch 环境安装

---

​	按下左下角(Win键)，打开Anaconda Prompt的终端。

<img src="https://raw.githubusercontent.com/zjhjjjjj/image/main/image-20211214190527535.png" alt="image-20211214190527535" style="zoom: 67%;" />

① 查看anaconda有哪些环境

```
conda env list
```

输出结果：

<img src="https://raw.githubusercontent.com/zjhjjjjj/image/main/image-20211214190851675.png" alt="image-20211214190851675" style="zoom: 67%;" />

​	这里我已经安装好了，默认只有base的环境。



​	base（基础）环境是一个大的环境，就像房子一样，我们每创建一个环境就相当于在这个房子上创建一个房间。

房间里安装我们所需要的所有包，这个管理比较方便，出错就可以删除这个环境，重新配置（每个环境相互隔离）。

![image-20211214192733978](https://raw.githubusercontent.com/zjhjjjjj/image/main/image-20211214192733978.png)



② 创建pytorch虚拟环境

```
conda create -n pytorch python=3.8
# 接着按 `y` 会装 虚拟环境的一些基础包
```

​	安装好虚拟环境后，查看anconda环境

```
conda env list 
# 可以看到下面这些环境（我的已经安装好了，只有框这些）
```

![image-20211214193903904](C:\Users\35198\AppData\Roaming\Typora\typora-user-images\image-20211214193903904.png)



③ 激活（进入）虚拟环境

```
conda activate pytorch
```

输入命令进入 `torch 环境`

<img src="C:\Users\35198\AppData\Roaming\Typora\typora-user-images\image-20211214194244854.png" alt="image-20211214194244854" style="zoom: 80%;" />

④ 换源

进入`pytorch环境后` 换源（pytorch的官网在国外，需要换到国内的源，要不然很慢）

```
# 一条一条输入
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
conda config --set show_channel_urls yes
```

⑤ 安装pytorch

[pytorch官网](https://pytorch.org/)

根据前面获取的信息，选择你可以安装的版本

<img src="C:\Users\35198\AppData\Roaming\Typora\typora-user-images\image-20211214194835316.png" alt="image-20211214194835316" style="zoom:67%;" />

单最近conda抽风，会默认安装cpu版本的pytorch,

——————————————————————————————————————————————————————————————————————————————————————————

输入下面命令`同上,` 会按照GPU版本的 pytorch

```
# 全部复制输入即可，安装的是 pytorch - GPU

pip3 install torch==1.10.0+cu113 torchvision==0.11.1+cu113 torchaudio===0.10.0+cu113 -f https://download.pytorch.org/whl/cu113/torch_stable.html --default-timeout=1000
```



## 四 、paddlepaddle环境安装

---

① 创建paddle环境 

如pytorch环境安装一样，首先在base环境下创建一个新的环境来安装paddlepaddle框架。首先创建一个新的环境名叫paddle。

```
conda create -n paddle python=3.9
```



② 激活(进入)paddle环境

```
conda activate paddle
```

打开paddlepaddle的[官网](https://www.paddlepaddle.org.cn/)，选择如下配置（更具直接前面差的最高支持CUDA版本），复制下方命令行之间进行安装（默认的是清华源不需要更换源）



<img src="C:\Users\35198\AppData\Roaming\Typora\typora-user-images\image-20211214195557935.png" alt="image-20211214195557935" style="zoom:67%;" />

这样paddlepaddle的环境就安装好了

<img src="C:\Users\35198\AppData\Roaming\Typora\typora-user-images\image-20211214195756333.png" alt="image-20211214195756333" style="zoom: 50%;" />



## 五、Pychram安装 —— 验证CUDA和cudnn版本

---

① 安装Pychram 

​	打开Pychram [官网](https://www.jetbrains.com/pycharm/download/#section=windows)，下载社区版本。

<img src="C:\Users\35198\AppData\Roaming\Typora\typora-user-images\image-20211214200124760.png" alt="image-20211214200124760" style="zoom: 50%;" />

默认安装，遇到这个界面要全选，`更新环境变量`

<img src="C:\Users\35198\AppData\Roaming\Typora\typora-user-images\image-20211214200218518.png" alt="image-20211214200218518" style="zoom:50%;" />

② 进入pychram验证pytorch环境

创建新工程，右下角加入anaconda里面安装的环境`(在右下角)`

![img](https://img-blog.csdnimg.cn/20210818222410569.png)

选择torch环境

<img src="https://img-blog.csdnimg.cn/20210818222607742.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2RpZGlhb3Bhbw==,size_16,color_FFFFFF,t_70" alt="img" style="zoom:50%;" />

点击ok就可以看到pytorch虚拟环境了

![img](https://img-blog.csdnimg.cn/20210818222953359.png)

验证

```
import torch
print(torch.cuda.is_available())
print(torch.backends.cudnn.is_available())
print(torch.cuda_version)
print(torch.backends.cudnn.version())
```

输出结果如下：

![image-20211214200746892](C:\Users\35198\AppData\Roaming\Typora\typora-user-images\image-20211214200746892.png)

③ pychram验证paddlepaddle环境



如上操作选择paddle虚拟环境

<img src="C:\Users\35198\AppData\Roaming\Typora\typora-user-images\image-20211214200845074.png" alt="image-20211214200845074" style="zoom:50%;" />

 

验证

```
import paddle
print(paddle.utils.run_check())
```

![image-20211214201036709](C:\Users\35198\AppData\Roaming\Typora\typora-user-images\image-20211214201036709.png)

看到如下即全部验证完成



### [出处](https://blog.csdn.net/didiaopao/article/details/119787139?spm=1001.2014.3001.5502)
