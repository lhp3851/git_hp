# Git Submodule

## 1. 查看 submodule 状态

```sh
git submodule
# 或者
git submodule status
```

* 查看某个 submodule 的信息

```sh
git remote show <remote>
```

* 查看 submodule 的修改

```sh
git diff --submodule
```

## 2. 创建 submodule

### 2.1 clone 包含 submodule 的仓库

```sh
git clone --recurse-submodules <git-url>

# 或者
# 1. 先 clone 父项目
git submodule init
git submodule update # the submodules on a detached HEAD
```

### 2.1.2 新建 submodule

submodule 的名字不要以`/`结尾，否则 git 会把 submodule 当做文件夹来处理的。

1. 首先添加 submodule：

```sh
git submodule add -b <branch> --name <name> <repository-path-or-url>
```

2. 然后，添加 `.gitmodule` 文件，并且把 submodule 的文件夹添加到父项目中。

3. 最后，在父项目中`commit`提交。

### 2.1.3 删除 submodule

```sh
git submodule deinit -f <submodule_path>
rm -rf .git/modules/<submodule_path>
git rm -f <submodule_path>
```

### 2.1.4 同步 submodule

* 更新所有 submodule

```sh
git submodule update --remote
```

* 更新指定 submodule

```sh
git submodule update --remote <submodule-name>
```

* 只有当所有 submodule 推送后，再更新父项目

```sh
git push --recurse-submodules=check
```

* submodule 推送后，再更新到父项目

```sh
git push --recurse-submodules=on-demand
```

* submodule 上运行 git 命令

```sh
git submodule foreach '<arbitrary-command-to-run>'
```

## 3. 参考资料

submodule 这种场景，使用的不多，我就不多啰嗦了。提供一些参考资料

* [git 子模块](https://git-scm.com/book/zh/v2/Git-工具-子模块)
* [使用Git Submodule管理子模块](https://segmentfault.com/a/1190000003076028)
