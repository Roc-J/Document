# jupyter notebook的使用

## jupyter介绍
Jupyter Notebook（此前被称为 IPython notebook）是一个交互式笔记本，支持运行 40 多种编程语言。  
Jupyter Notebook 的本质是一个 Web 应用程序，便于创建和共享文学化程序文档，支持实时代码，数学方程，可视化和 markdown。 用途包括：数据清理和转换，数值模拟，统计建模，机器学习等等。

### 为什么使用jupyter
数据挖掘领域中最热门的比赛 Kaggle 里的资料都是Jupyter 格式


## 远程访问jupyter notebook
1.远程登录服务器（Linux系统）  
> 最好新建一个自己的用户  

2.生成配置文件  

```
  $jupyter notebook --generate-config	
```  

3.生成密码  
打开ipython，创建一个密文的密码：

```
In [1]: from notebook.auth import passwd
In [2]: passwd()
Enter password: 
Verify password: 
Out[2]: 'sha1:b6cf4a0be897:7b80e77814f3176659d725f0e7db71f1ab4a04e6'
```

把生成的密文'sha1'复制下来  
4.修改默认配置文件

```
$ vi ~/.jupyter/jupyter_notebook_config.py 
```

进行如下修改：

```
c.NotebookApp.ip='*'
c.NotebookApp.password = u'sha:ce...刚才复制的那个密文'
c.NotebookApp.open_browser = False
c.NotebookApp.port =8888 #随便指定一个端口
```
5.在命令行执行

```
$ unset XDG_RUNTIME_DIR
```
6.启动jupyter notebook  

```
$ jupyter notebook
```

7.远程访问  
此时应该可以直接从本地浏览器直接访问http://address_of_remote:port 就可以看到jupyter的登陆界面。

## 本地安装使用jupyter notebook

其实使用

```
pip install jupyter
```
就可以

本地运行命令行jupyter notebook即可

