# Git Theory

[图解Git](https://marklodato.github.io/visual-git-guide/index-zh-cn.html) 这篇文章讲的不错，我这里就不再赘述了。

这里提供几个 git 的底层命令，方便做 git 调试

* HEAD

```sh
git cat-file -p HEAD
```

```sh
git ls-tree -r HEAD
```

* Index/Stage

```sh
git ls-files -s
```

* [图解Git](https://marklodato.github.io/visual-git-guide/index-zh-cn.html)
* [git工作原理](https://www.ruanyifeng.com/blog/2018/10/git-internals.html)
