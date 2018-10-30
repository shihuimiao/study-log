### git 有关的

#### 解决冲突
从线上把master fetch到一个新的分支，然后把旧分支的东西merge到新分支，解决冲突，push新分支

#### 解决冲突的方法
git fetch origin develop:develop  //先把线上的develop分支拉到本地的develop
git rebase develop   //把develop合并到自己的分支如shm_0609
... 用git mergetool工具    beyond compare软件  解决冲突  
git rebase --continue   //继续rebase
git push --force  //push 到线上


#### 尽量别用-f  是强制push
git push -u origin xxx -f

#### git rebase 发生冲突
修改好之后
git add .
git rebase --continue
git push origin xxx -f
就好了


#### git 分支管理策略  (http://www.ruanyifeng.com/blog/2012/07/git.html)

git分支多了会产生分支混乱，所以分支管理很重要
一、主分支Master
代码库应该有一个，且仅有一个主分支。所以提供给用户使用的正式版本，都在这个主分支上发布。
二、开发分支Develop
主分支只用来发布重大版本，日常开发应该在另一条分支上完成。我们把开发用的分支，叫做Develop
三、临时性分支
前面讲到版本库的两条主要分支：master喝develop，前者用于正式发布，后者用于日常发布。其实，常设分支只需要这两条就够了，不需要其他了。
但是，除了常设分支以外，还有一些临时性分支，用于一些特定目的的版本开发。临时性分支主要有三种：
*功能（feature）分支
*预发步（release）分支
*修补bug（fixbug）分支
这三种分支都属于临时性需要，使用完以后，应该删除，使得代码库的常设分支始终只有Master和Develop
四、功能分支
功能分支，它是为了开发某种特定功能，从Develop分支上面分出来，开发完以后，要再并入Develop。
五、预发步分支
第二种是预发步分支，它是指发布正式版本之前（即合并到Master分支之前），我们可能需要有一个预发步的版本进行测试。
预发步分支是从Develop分支上面分出来的，预发步结束以后，必须合并进Develop和Master分支。它的命名，可以采用release-*的形式。
六、修补bug分支
最后一种是修补bug分支。软件正式发布以后，难免会出现bug。这时就需要创建一个分支，进行bug修补。
修补bug分支是从Master分支上面分出来的。修补结束后，再合并进Master和Develop分支。它的命名，可以采用fixbug-*的形式。


#### 自己公司的分支策略：
Master分支是线上用户使用的正式版本
Develop是开发环境的测试版本
release是测试环境测试们用来测试的版本
pre-release是预发步的测试版本

每次pre-release是从master上切一个分支下来，修改bug也是从master上切分支的，然后有什么测试了也是从master上切分支的，一切都是以master为主，功能分支也是从master分支切。。。。。


#### Git结合Beyond Compare使用
打开 Beyond Compare -> Beyond Compare Menu ->*** Install Command Line Tools***
必须要安装Beyond Compare 命令工具,否则会报错

```
git config --global diff.tool bc3
```
当需要比较修改的时候,在终端中直接输入git difftool file.ext 就可以唤起****Beyond Compare****

```
git config --global merge.tool bc3
git config --global mergetool.bc3 trustExitCode true
```
当代码发生冲突的时候,在终端中使用 git mergetool <conflict file> 即可唤起****Beyond Compare****,可谓是十分强大

- 在使用git megetool 来解决冲突后,会生成 备份文件 (*.orig),大多数情况下不是我们想要的,在终端中配置:
```
git config --global mergetool.keepBackup false
```
这样就不会每次在解决冲突后生成对应的 .orig文件了.













