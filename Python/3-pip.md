# **pip**

pip 是 Python 包管理工具，该工具提供了对Python 包的查找、下载、安装、卸载的功能。

目前如果你在 [python.org](https://www.python.org) 下载最新版本的安装包，则是已经自带了该工具。

Python 2.7.9 +  或 Python 3.4+  以上版本都自带 pip 工具。

pip 官网：https://pypi.org/project/pip/

## 常用命令

### **显示版本和路径**

```python
pip --version
```

### **获取帮助**

```
pip --help
```

### **升级 pip**

```
pip install -U pip
```

若出现问题也可以按照下述升级包的方式升级pip。

### **安装包**

```
pip install SomePackage              # 最新版本
pip install SomePackage==1.0.4       # 指定版本
pip install 'SomePackage>=1.0.4'     # 最小版本
```

### **升级包**

```
pip install --upgrade SomePackage
```

升级指定的包，通过使用==, >=, <=, >, < 来指定一个版本号。

### **卸载包**

```
pip uninstall SomePackage
```

### **搜索包**

```
pip search SomePackage
```

### **显示安装包信息**

```
pip show 
```

### **查看指定包的详细信息**

```
pip show -f SomePackage
```

### **列出已安装包**

```
pip list
```

### **查看可升级包**

```
pip list -o
```

[^注]: 如果同时安装了Python2和Python3，可以将上述的pip指令换成pip2或者pip3。

