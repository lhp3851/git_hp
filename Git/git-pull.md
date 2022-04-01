---
title: git pull
date: 2022-04-01 09:46:38
tags: git pull
---

## 1. Git 合并

### 1.1 Merge

<<<<<<< HEAD
#### 1.1.1 三方合并
=======
### 1.1.1 三方合并
>>>>>>> d211b412dce112e59bb9c74b0b0d394705485113

假设你有当前状态的git 记录

![git_merge_no_ff](./resources/git_merge_no_ff.png)

则进行三方合并的效果如下

![git_merge_noff_result](./resources/git_merge_noff_result.png)

#### 1.1.2 快速合并

<<<<<<< HEAD
假设当前的git记录状态如下

![git_merge_ff](./resources/git_merge_ff.png)

进行快速合并后，结果如下

![git_merge_no_ff](./resources/git_merge_no_ff.png)

=======
>>>>>>> d211b412dce112e59bb9c74b0b0d394705485113
#### 1.1.3 合并的种类

##### 1.1.1 -ff-only

只接受直接祖先分支的方式，进行快速合并，不会产生 merge log。

##### 1.1.1 -no-ff

只进行三方合并的方式（当前分支可以是非直接祖先）合并，并产生一个 merge log。

##### 1.1.1 -ff

默认使用直接祖先的快速合并方式，如果当前分支不是直接祖先，则进行三方合并，并产生 merge log。

### 1.2 Rebase

**核心宗旨：只对尚未推送或分享给别人的本地修改执行变基操作清理历史， 从不对已推送至别处的提交执行变基操作。**

```sh
# newbase 的默认值是 upstream
# upstream 的默认值是 origin/branch
# branch 的默认值是当前分支
$ git rebase [-i | --interactive] [--onto <newbase>] [<upstream> [<branch>]]
```

#### 1.2.1 --onto

![git_rebase_onto](./resources/git_rebase_onto.png)

假设你希望将 client 中的修改合并到主分支并发布，但暂时并不想合并 server 中的修改， 因为它们还需要经过更全面的测试。这时，你就可以使用 git rebase 命令的 --onto 选项， 选中在 client 分支里但不在 server 分支里的修改（即 C8 和 C9），将它们在 master 分支上重放：

```sh
git rebase --onto master server client
```

以上命令的意思是：“取出 client 分支，找出它从 server 分支分歧之后的补丁， 然后把这些补丁在 master 分支上重放一遍，让 client 看起来像直接基于 master 修改一样”。这理解起来有一点复杂，不过效果非常酷。

会产生如下结果：

![git_onto_rebase_result](./resources/git_onto_rebase_result.png)

#### 1.2.2 no checkout rebase

![git_rebase_nocheckout](./resources/git_rebase_nocheckout.png)

假设当前在master分支，然后决定将 server 分支中的修改也整合进来。 使用 `git rebase <basebranch> <topicbranch>` 命令可以直接将主题分支 （即本例中的 server）变基到目标分支（即 master）上。 这样做能省去你先切换到 server 分支，再对其执行变基命令的多个步骤。

```sh
 git rebase master server
```

会产生如下结果：

![git_rebase_nocheckout_result](./resources/git_nocheckout_rebase_result.png)
