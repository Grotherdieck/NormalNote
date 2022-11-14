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

# 四、git忽略提交某些内容

像很多的项目配置文件，提交上去会显得很麻烦，配置``.gitignore``即可忽略一些文件。

![](https://router-picture-bed.oss-cn-chengdu.aliyuncs.com/img/20221114131707.png)

分枝不互相打扰时，没啥问题，当不同的分支要合并时，就有问题了。

``git branch``查看本地有哪些分支。

``git branch -r``列出所有远程分支。

``git branch branchname``新建一个分支，但是仍停留在当前分支。

``git chechout -b branchname``新建一个分支，并且切换这个分支，不加b单纯切换分支。

``git merge branch``合并指定分支到当前分支

合并的问题与解决方法：

如果同一个文件在合并分支时都被修改了则会引起冲突：解决方法是我们可以修改冲突文件后重新提交，即选择要保留对方的代码还是保留你的代码，即冲突了就协商一下即可。

``git branch -d branchname``删除分支。

通常master分支应该非常稳定，用来发布新版本
