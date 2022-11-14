# 一、git常见命令

``git config -l``：查看当前git的所有配置。

``git config --global --list``:查看用户配置的当前全局配置。

git的全局配置存在gitconfig文件，用户配置信息存在用户目录下的.gitconfig文件。

# 二、git原理简易介绍

git本地有三个工作区域：工作目录、暂存区、本地资源库，如果再加上远程的git仓库，就可以分为四个区域，文件在这四个区域的转换关系如下：

<img src="https://router-picture-bed.oss-cn-chengdu.aliyuncs.com/img/20221114125239.png" style="zoom:80%;" />

Working Directory：就是那个含有.git的本地文件夹。

Index/Stage：本质是一个文件，保存即将提交到文件列表的信息。

Repository：本地仓库，里面有你提交到所有版本的数据，其中HEAD指向最新放入仓库的版本。

Remote：远程仓库。

通常使用下面命令即可：

![](https://router-picture-bed.oss-cn-chengdu.aliyuncs.com/img/20221114130252.png)

# 三、git本地建立仓库

在一个目录使用``git init``就会有在本地建立一个仓库，也可以用``git clone url``到本地来。

git文件的状态：

![](https://router-picture-bed.oss-cn-chengdu.aliyuncs.com/img/20221114130621.png)

