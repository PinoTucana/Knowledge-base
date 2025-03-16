----

# 2.1. Git初始化

## 2.1.2. 思考：为什么工作区下有一个.git目录？

#### 那么有什么办法知道Git版本库的位置，以及工作区的根目录在哪里呢？

+ 在工作区下建立目录`a/b/c`，进入到该目录中。

```shell
$ cd /path/to/my/workspace/demo/
$ mkdir -p a/b/c
$ cd /path/to/my/workspace/demo/a/b/c
```

+ 显示版本库`.git`目录所在的位置。

```shell
$ git rev-parse --git-dir
/path/to/my/workspace/demo/.git
```

+ 显示工作区根目录。

```shell
$ git rev-parse --show-toplevel
/path/to/my/workspace/demo
```

+ 相对于工作区根目录的相对目录。

```shell
$ git rev-parse --show-prefix
a/b/c/
```

+ 显示从当前目录（cd）后退（up）到工作区的根的深度。

```shell
$ git rev-parse --show-cdup
../../../
```

----

### 2.1.3 git config命令参数的区别？

+ 执行下面的命令，将打开/path/to/my/workspace/demo/.git/config文件进行编辑。

```shell
$ cd /path/to/my/workspace/demo/
$ git config -e
```

+ 执行下面的命令，将打开`/home/jiangxin/.gitconfig`（用户主目录下的`.gitconfig`文件）全局配置文件进行编辑。

```shell
$ git config -e --global
```

+ 执行下面的命令，将打开`/etc/gitconfig`系统级配置文件进行编辑。
如果Git安装在`/usr/local/bin`下，这个系统级的配置文件也可能是在`/usr/local/etc/gitconfig`。

```shell
$ git config -e --system
```

Git的三个配置文件分别是版本库级别的配置文件、全局配置文件（用户主目录下）和系统级配置文件（`/etc`目录下）。其中版本库级别配置文件的优先级最高，全局配置文件其次，系统级配置文件优先级最低。这样的优先级设置就可以让版本库`.git`目录下的`config`文件中的配置可以覆盖用户主目录下的Git环境配置。而用户主目录下的配置也可以覆盖系统的Git配置文件。

----

[1]	命令**git commit -s**中的参数`-s`含义为在提交说明的最后添加“Signed-off-by:”签名。
[2]	命令**git -p status**中的参数`-p`含义是为**git status**命令的输出添加分页器。
[4]	示例中使用了Linux下的**strace**命令跟踪系统调用，在Mac OS X下则可使用**sudo dtruss git status**命令跟踪相关Git操作的系统调用。

----

# 2.2 Git暂存区

## 2.2.1. 修改不能直接提交？

+ 对于习惯了像 CVS 和 Subversion 那样简练的状态输出的用户，可以在执行**git status** 时附加上`-s`参数，显示精简格式的状态输出。

