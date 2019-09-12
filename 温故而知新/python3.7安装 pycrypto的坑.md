## keng
python3.7 安装 pycrypto 2.6.1库。

通常一个新项目导入 pycharm，可能需要不同的 Python 版本和依赖包。正常执行：
`python3 install -r requirement.txt` 
就会默默地把所有依赖包安装好，如果源慢无非多等一会。

今天遇到安装 pycrypto 加密包 pycharm IDE 一直提示 “pycrypto 2.6.1 没有安装”。

通过 Google 看到不同系统环境和 python 版本，都有不同同学遇到问题。
windows 下，通过修改 ../site-package/ 文件夹下的 文件大小写解决了。即：把 crypto 修改成 Crypto

macOS 下，没看到对应的解决方案。试着通过下载安装软码包的方式，安装方式：

```
wget https://pypi.python.org/packages/60/db/645aa9af249f059cc3a368b118de33889219e0362141e75d4eaf6f80f163/pycrypto-2.6.1.tar.gz#md5=55a61a054aa66812daf5161a0d5d7eda

2.解压该包

tar  -zxvf  pycrypto-2.6.1.tar.gz

3.进入该包，通过python3 安装

python3  setup.py install

```

提示错误：


```
checking whether the C compiler works... no
configure: error: in `/Library/Frameworks/Python.framework/Versions/3.7/bin/pycrypto-2.6.1':
configure: error: C compiler cannot create executables
See `config.log' for more details
Traceback (most recent call last):
  File "setup.py", line 456, in <module>
    core.setup(**kw)
  File "/Library/Frameworks/Python.framework/Versions/3.7/lib/python3.7/distutils/core.py", line 148, in setup
    dist.run_commands()
  File "/Library/Frameworks/Python.framework/Versions/3.7/lib/python3.7/distutils/dist.py", line 966, in run_commands
    self.run_command(cmd)
  File "/Library/Frameworks/Python.framework/Versions/3.7/lib/python3.7/distutils/dist.py", line 985, in run_command
    cmd_obj.run()
  File "/Library/Frameworks/Python.framework/Versions/3.7/lib/python3.7/distutils/command/install.py", line 545, in run
    self.run_command('build')
  File "/Library/Frameworks/Python.framework/Versions/3.7/lib/python3.7/distutils/cmd.py", line 313, in run_command
    self.distribution.run_command(command)
  File "/Library/Frameworks/Python.framework/Versions/3.7/lib/python3.7/distutils/dist.py", line 985, in run_command
    cmd_obj.run()
  File "/Library/Frameworks/Python.framework/Versions/3.7/lib/python3.7/distutils/command/build.py", line 135, in run
    self.run_command(cmd_name)
  File "/Library/Frameworks/Python.framework/Versions/3.7/lib/python3.7/distutils/cmd.py", line 313, in run_command
    self.distribution.run_command(command)
  File "/Library/Frameworks/Python.framework/Versions/3.7/lib/python3.7/distutils/dist.py", line 985, in run_command
    cmd_obj.run()
  File "setup.py", line 251, in run
    self.run_command(cmd_name)
  File "/Library/Frameworks/Python.framework/Versions/3.7/lib/python3.7/distutils/cmd.py", line 313, in run_command
    self.distribution.run_command(command)
  File "/Library/Frameworks/Python.framework/Versions/3.7/lib/python3.7/distutils/dist.py", line 985, in run_command
    cmd_obj.run()
  File "setup.py", line 278, in run
    raise RuntimeError("autoconf error")
RuntimeError: autoconf error

```



