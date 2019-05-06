---
title: Problem Encounted in Blogging
date: 2019-05-05 12:50:39
tags: study
---
  今天是第一次写自己的 [Blog](https://robotliu327.github.io/) ，使用Github + Hexo 期间遇到两个问题记录。
## Quick Start : Reference
1.[初次搭建Blog：GitHub + Hexo](https://www.cnblogs.com/liuxianan/p/build-blog-website-by-hexo-github.html#%E4%B8%8A%E4%BC%A0%E5%88%B0github)
2.[github官方教程-changeing a remote's url](https://help.github.com/en/articles/changing-a-remotes-url)
3.[git 官方教程](https://git-scm.com/book/zh/v1/%E8%B5%B7%E6%AD%A5)
4.[yilia 主题](https://github.com/litten/hexo-theme-yilia)

### 问题1：以前的remote repository与现有的仓库提交上有冲突

<!--more-->

1.产生：在本地加载好主题，可以实现在`hexo s` 开启本地预览，打开浏览器访问 http://localhost:4000 是正常的。

2.现象：准备使用 `hexo deploy` 将本地仓库推送到github上面出现如下报错： ![](/error_remote_repo.png)
```
nothing to coommit,working tree clean
Enter passpharse for key '/c/Users/RobotLiu/.ssh/id_rsa':
ERROR:Repository not found
fatal:Could not read from remote repository.

please make sure you have the correct access rights and the repository exists.
```

3.查找原因：
* 远程仓库出错，怀疑和之前我使用Git提交仓库时，进行全局设置提交到git@github.com:robotliu327/test_website.git这个仓库，但是我在F:\Git\hexo\_config.yml设置时deploy>>repository: git@github.com:robotliu327/robotliu327.github.io.git 是这个仓库，所以二者起了冲突
> 使用git命令查看当前配置下我提交到仓库的url
> config 配置有system级别 global（用户级别） 和local（当前仓库）三个
> [参考:git config命令](https://www.cnblogs.com/merray/p/6006411.html)
> `git config --local  --list`
> `remote.origin.url=git@github.com:robotliu327/test_website.git`

* 改变git local 下面的远程提交的到仓库的url
> [参考：Changing a remote's URl](https://help.github.com/en/articles/changing-a-remotes-url)
>> 先删除本地的origin的url--- `git remote rm origin` 可以使用`git config --local  --list`查看
>> ```git remote set-url [old remote name: "origin" means old remote repository url] [A new URL for the remote url]```

4.相关经验：




### 问题2：Github上面SSH Key加密传输协议
**总结：所以一般一台主机链接一个github账户只需要生成一个ssh key即可，代表这台电脑被github接受，但是github上面可以生产多个SSh key 意味着一个github账户可以接受多台主机的认证，这样你可以使用不同的电脑上使用加密传输**
众所周知ssh key是加密传输。加密传输的算法有好多，git使用rsa，rsa要解决的一个核心问题是，如何使用一对特定的数字，使其中一个数字可以用来加密，而另外一个数字可以用来解密。这两个数字就是你在使用git和github的时候所遇到的public key也就是公钥以及private key私钥。
其中，公钥就是那个用来加密的数字，这也就是为什么你在本机生成了公钥之后，要上传到github的原因。从github发回来的，用那公钥加密过的数据，可以用你本地的私钥来还原。
如果你的key丢失了，不管是公钥还是私钥，丢失一个都不能用了，解决方法也很简单，重新再生成一次，然后在http://github.com里再设置一次就行


# 这个是公式
$$
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix}
\mathbf{i} & \mathbf{j} & \mathbf{k} \\
\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\
\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\
\end{vmatrix}
$$

