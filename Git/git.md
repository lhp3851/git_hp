# Git

对于 Git[^git-doc] 仓库的管理使用，一般分为三个步骤：初始化、配置、管理。

## 1 仓库初始化

仓库初始化，一般有两种方式：远程拉取与本地创建。

### 1.1 本地创建

创建本地仓库

```shell
git init
```

* init 命令有许多参数，这里只是一些基本介绍，想深入了解的话，请参考`git init --help` 或者 [git init](https://git-scm.com/docs/git-init)。

### 1.2 远程拉取

#### 1.2.1 clone 仓库

```shell
git clone <git-url>
```

#### 1.2.2 clone 仓库分支

```shell
git clone -b <branchname> --single-branch <git-url>
```

#### 1.2.3 clone 仓库以及 Submodule

```shell
git clone --recurse-submodules <git-url>
```

* `<git-url>`： 是仓库地址
* `<branchname>` ：仓库分支名字
* 要想深入了解，参见`git clone --help` 或者 [git clone](https://git-scm.com/docs/git-clone)

## 2 配置仓库

不管是本地创建的还是远程拉取的，都需要配置仓库信息，比如账号邮箱信息。

### 2.1 配置用户名

```shell
git config [--global] user.name <name>
```

### 2.2 配置用户邮箱

```shell
git config [--global] user.email <email>
```

* `--global`为可选参数，这里可以有 `--system`, `--global`, `--local`, `--worktree` and `--file <filename>` 几种值，一般常用的是 `--global`，表示当前电脑用户的 git 全局配置用户。
* 要想深入了解，参见`git config --help` 或者 [git config](https://git-scm.com/docs/git-config)

### 2.3  配置 Terminal 颜色

```shell
git config --global color.ui auto
```

### 2.4 查看配置信息

查看 git 仓库用户名

```sh
git config [--global] user.name
```

查看 git 仓库用户邮箱

```sh
git config [--global] user.email
```

### 2.5 更换仓库地址

当 git 服务器地址变更的时候，需要更换本地仓库跟踪的远程服务器仓库地址，这种使用情况一般比较少，但也不是没有。

```sh
git remote set-url origin <git-url>
```

也可以先删除旧的，再添加新的

```sh
git remote rm origin
git remote add origin <git-url>
```

## 3 仓库管理

### 3.1 分支

### 3.1.1 创建分支

* 创建新分支

```sh
git branch <new-branch>
```

* 切换分支

```sh
git checkout <branch>
```

* 创建分支，并切换到新分支

```sh
git chekcout -b <new-branch>
```

### 3.1.2 删除分支

* 删除本地分支

```sh
git branch -d <branch>
```

* 删除远程分支

```sh
git push origin --delete <branch>
```

### 3.1.3 修改分支

#### 3.1.3.1 合并分支

#### 3.1.3.2 Rebase

### 3.1.4 查询分支

#### 3.1.4.1 查询本地分支

```sh
git branch
```

#### 3.1.4.2 查询远程分支

```sh
git branch --remote
```

#### 3.1.4.3 查询本地/远程分支

```sh
git branch -a
```

#### 3.1.5 同步分支

推送本地分支到远程，有两种情况

* 远程没有相应分支

* 远程已有相应分支

### 3.2 版本管理

### 3.2.1 文件跟踪

#### 3.2.1.1 未文件跟踪

#### 3.2.2 Workcopy

#### 3.2.3 Stage/Index

#### 3.2.4 Commit

#### 3.2.5 回滚

### 3.3 缓存

#### 3.3.1 缓存清理

### 3.4 Stash

## 4 Tag

Tag 的意义，是方便操作历史信息，比如回滚，小版本临时修复线上 bug。最常用的就是发布依赖库版本，一般每一个依赖库发布的时候，都会创建一个 tag，方便依赖库使用者用依赖工具对依赖库做版本管理。

### 4.1 创建 Tag

### 4.2 删除 Tag

### 4.3 查询 Tag

#### 4.3.1 查询 Tag 列表

#### 4.3.2 查询某个 Tag

### 4.2 推送 Tag

* 所有信息都支持增删改查操作
* 先本地，后远程

[^git-doc]: [git doc](https://git-scm.com/doc)
