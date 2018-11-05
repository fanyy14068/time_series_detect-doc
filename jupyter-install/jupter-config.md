# jupyter环境搭建

### 安装
anonconda默认安装，也可以使用pip安装


### 运行
`jupyter notebook --ip=0.0.0.0 --no-browser --allow-root &`

终端会生成一堆信息，主要里面的token。然后在浏览器打开即可，端口默认8888，输入token就是刚刚产生的token

### 配置
可以对jupyter进行配置，省去每次需要输入密码的问题

1，生成配置文件

`jupyter notebook --generate-config --allow-root`

配置文件默认的路径是：`/root/.jupyter/jupyter_notebook_config.py`

2，生成密码，需要使用python生成密码
```
[root@pydev ~]# python 
Python 2.7.5 (default, Nov  6 2016, 00:28:07)  
[GCC 4.8.5 20150623 (Red Hat 4.8.5-11)] on linux2 
Type "help", "copyright", "credits" or "license" for more information. 
>>> from notebook.auth import passwd 
>>> passwd() 
Enter password:  
Verify password:  
'sha1:c1ebae9ce1b5:0c25328cd843b9f57b2043de1bb55f464d023939' 
>>>  
```

3，修改配置文件
```
#158 c.NotebookApp.ip = 'localhost' 
改成： 
158 c.NotebookApp.ip = '0.0.0.0' 
这样就可以外部访问了，默认只有在本机可以访问的； 
 
#修改配置文件中的工作目录；[固定一个工作目录] 
 
#195 c.NotebookApp.notebook_dir = u'' 
改成： 
195 c.NotebookApp.notebook_dir = u'/opt/pydev' 
 
210 #c.NotebookApp.password = u'' 
改成上面生成的密码：[123456] 
c.NotebookApp.password = u'sha1:c1ebae9ce1b5:0c25328cd843b9f57b2043de1bb55f464d023939' 
```

