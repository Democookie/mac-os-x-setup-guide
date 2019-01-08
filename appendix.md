---
title: 附：疑难杂症等
---

## Battle.net 的地区问题

如果使用国服下载 Battle.net 并且运行以后，就再也看不到其他的地区了，使用美帝的安装器安装也无能为力。网上有一些修改config 的解决办法，但已经过时了。

在 `/Applications/Battle.net.app/Contents/Battle.net.app/Contents/MacOS`这个文件夹下面，打开终端（Terminal / iTerm 2）。

```
$ ./Switcher --setregion=US
```

问题解决。：D

## rvm 在 zsh 下出现的环境变量的设置问题

如果你以前安装过 `rvm` 并且通过 `oh-my-zsh` 安装的话，你可能会看到如下的错误信息：

```
Warning: PATH set to RVM ruby but GEM_HOME and/or GEM_PATH not set, see:
```

本问题详见 github 上的这条 [issue](https://github.com/rvm/rvm/issues/3212)


### 解决办法：

问题产生的原因是因为 path 被 oh-my-zsh 的的保护机制改写了。

只要确保配置 `.zshrc` 的配置文件里的所有

```
export PATH=/path/to/something
```
都改写为

```
export PATH="$PATH:/path/to/something"
```

的形式，即可解决这个问题。：D

## git 和 vi 的使用问题

在使用 git 进行 commit 的时候，很容易遇到
```
There was a problem with the editor 'vi'
```

### 解决办法

```
$ git config --global core.editor /usr/bin/vim
```

## dyld: Library not loaded: 

```
dyld: Library not loaded: /usr/local/opt/gdbm/lib/libgdbm.4.dylib  Referenced from: /usr/local/bin/zsh   
Reason: image not found
zsh: trace trap
```

### 尝试解决办法
```
brew install gdbm
```

如果提示已经安装

```
brew install gdbm
```