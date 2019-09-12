## macOS python3.7 安装 pycrypto 2.6.1库。

#### 问题背景
通常一个新项目导入 pycharm，可能需要不同的 Python 版本和依赖包。正常执行：
`python3 install -r requirement.txt` 
就会默默地把所有依赖包安装好，如果源慢无非多等一会。

今天遇到安装 pycrypto 加密包 pycharm IDE 一直提示 “pycrypto 2.6.1 没有安装”。

通过 Google 看到不同系统环境和 python 版本，都有不同同学遇到问题。
windows 下，通过修改 ../site-package/ 文件夹下的 文件大小写解决了。即：把 crypto 修改成 Crypto

#### python3 源码安装 pycrypto 2.6.1
macOS 下，没看到对应的解决方案。试着通过下载安装软码包的方式，安装方式：
```
1.下载源码包
wget https://pypi.python.org/packages/60/db/645aa9af249f059cc3a368b118de33889219e0362141e75d4eaf6f80f163/pycrypto-2.6.1.tar.gz#md5=55a61a054aa66812daf5161a0d5d7eda

2.解压该包
tar -zxvf pycrypto-2.6.1.tar.gz

3.进入该包，通过python3 安装
python3 setup.py install
```
提示错误：
![](/assets/安装pycrypto出错提示.png)

#### 问题解决
排查了一会，发现 IDE 仍旧提示“pycrypto 2.6.1 没有安装”，到相应的包路径仔细检查，发现有一个 Crypto 的包文件。只不过名称不是 pycrypto （问题就在这里）。
![](/assets/包查看.png)

类文件中，实际应用的包名其实就是 Crypto ,而依赖的 requirment.txt 文件中写的是 pycrypto==2.6.1 ,造成 IDE 误认为需要的包没有被安装。
![](/assets/包引入.png)

#### 遗留问题
此时代码已经能够正常运行。没任何问题，只是因为包名称使用和配置不一样而已。

#### 遗留问题变通方案

针对 包名称使用和配置不一致的情况，可以在满足加解密的情况下，在requirements.txt 文件中调整使用的包为：crypto==1.4.1 

可以单独在通过 pip安装上述包：
`pip3 install crypto`


#### Done









