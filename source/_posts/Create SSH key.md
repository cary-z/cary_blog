---
title: 生成ssh-key
catalog: true
comments: true
date: 2021-07-28 17:22:59
header-img: snail-bg.jpg
tags:
  - bash
categories:
  - config
---

打开终端在终端输入以下代码:

```bash
$ ls ~/.ssh
```

如果输出内容里边包含(其中 id_rsa 是私钥，id_rsa.pub 是公钥)

```bash
id_rsa    id_rsa.pub
```

如果输出如下则表示你的电脑没有生成过公钥和私钥，则要进行生成操作:

```bash
No such file or directory
```

在终端执行

```bash
$ ssh-keygen -t rsa -C "your_email@example.com"
```

代码参数含义：
-t 指定密钥类型，默认是 rsa ，可以省略。
-C 设置注释文字，比如邮箱。
-f 指定密钥文件存储文件名。
以上代码省略了 -f 参数，因此，运行上面那条命令后会让你输入一个文件名，用于保存刚才生成的 SSH key 代码
