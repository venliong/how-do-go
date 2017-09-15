### 1 Go环境的安装

Go 语言支持以下系统：

* Linux

* FreeBSD

* Mac OS X（也称为 Darwin）
* Window

安装包下载地址为：[https://golang.org/dl/](https://golang.org/dl/)。

![](/assets/go1.jpeg)

### 安装go语言

> 如果要升级之前的老版本需要先将之前的版本删除掉。

### Linux, Mac OS X, and FreeBSD tarballs

下载并且解压到 `/usr/local`, 创建go文件夹 `/usr/local/go`. 例如:

```
tar -C /usr/local -xzf go1.9.linux-amd64.tar.gz
```

执行以上指令必须加上 `  sudo`

Add`/usr/local/go/bin`to the`PATH`environment variable. You can do this by adding this line to your`/etc/profile`\(for a system-wide installation\) or`$HOME/.profile`:

```
export PATH=$PATH:/usr/local/go/bin
```



