# Windows修改jupyter读取文件的默认目录

1. 添加系统环境变量,加入以下目录  
    D:\ProgramData\Anaconda3\Library\bin\  
    D:\ProgramData\Anaconda3\Scripts\  

1. 运行以下命令，生成配置文件
```
$ jupyter notebook --generate-config
```
    提示以下信息  
    Writing default config to: C:\Users\Administrator\.jupyter\jupyter_notebook_config.py

1. 编辑 C:\Users\Administrator\.jupyter\jupyter_notebook_config.py 文件
```
找到#c.NotebookApp.notebook_dir = ' '并改为c.NotebookApp.notebook_dir = '(自己的路径)'
```

1. win -> Jupyter Notebook的快捷方式右键 -> 更多 -> 打开文件位置 -> Jupyter Notebook右键属性 -> 去掉“目标”一项中最后的" %USERPROFILE%" 