LogListener 是腾讯云日志服务 CLS 所提供的日志采集客户端，将它安装部署到目标机器上，可以实时快速地采集日志。

## 支持环境

目前，LogListener 支持如下版本的 Linux 64 位操作系统：

- CentOS
- Debian
- SUSE
- OpenSUSE
- Ubuntu

## 安装步骤

#### 1. 下载 LogListener

LogListener 最新版本下载地址如下： [下载 LogListener](https://main.qcloudimg.com/raw/8656fcadd12ab9689674df09b510b52b/loglistener.2.2.2.tar.gz)。

#### 2. 安装 LogListener

将下载的安装包解压，解压命令如下：

```shell
tar -xvf [安装包] 
```

然后保存到某个目录，进入到该目录下的`/loglistener/tools`目录，以 root 权限执行以下命令：

```shell
./install.sh [SecretId] [SecretKey] [region]
```

参数示例：
```shell
./install.sh AKIDc9YlmrBcFk4C8sbmXQ8i65XXXXXXXXXX LUSE4nPK1d4tX5SHyXv6tZXXXXXXXXXX ap-guangzhou 
```

| 参数名    | 类型描述                                                     |
| --------- | ------------------------------------------------------------ |
| SecretId  | [云 API 密钥](https://console.cloud.tencent.com/cam/capi) 的一部分，SecretId 用于标识 API 调用者身份 |
| SecretKey | [云 API 密钥](https://console.cloud.tencent.com/cam/capi) 的一部分，SecretKey 是用于加密签名字符串和服务器端验证签名字符串的密钥 |
| region    | 日志服务所在的 [地域](https://cloud.tencent.com/document/product/614/18940) |

>?
> - 建议使用协作者密钥，需要主账号授权协作者于日志服务的读写权限。
> - region 为您所使用的日志服务区域而非您的业务机器所处的区域。
> - 安装脚本会通过`rc.local`，以保证机器重启后，客户端正常拉起。

## 操作 LogListener

###  启动 LogListener

您可以通过以下脚本启动 LogListener：

```shell
cd loglistener/tools && ./start.sh
```

### 停止 LogListener

您可以通过以下脚本停止 LogListener：

```shell
cd loglistener/tools && ./stop.sh
```

### 查看进程

您可以通过以下命令查看 LogListener 进程：

```shell
cd loglistener/tools && ./p.sh
```

正常情况下，将存在以下三个进程：

```sh
bin/loglistenerm -d                                #守护进程
bin/loglistener --conf=etc/loglistener.conf        #主进程    
bin/loglisteneru -u --conf=etc/loglistener.conf    #更新进程
```

### 卸载 LogListener

您可以通过以下命令卸载 LogListener：

```shell
cd loglistener/tools && ./uninstall
```

>!卸载操作将删除 `rc.local`里自动重启的工具。

## 更新 LogListener

若您的 LogListener 版本非当前最新版本，我们建议您更新至最新版本。**低于 2.2.2 版本的 LogListener 不支持完全正则采集。**您可以在`loglistener/version.txt`中查看当前 LogListener 的版本信息。

-  LogListener 版本高于2.0.0，但低于2.2.2，更新步骤如下 ：
 1. 下载新的安装包。
 2. 在安装目录（LogListener平级目录）解压新的压缩包。
 3. 解压后重启 LogListener 即完成更新操作。
-  LogListener 版本低于2.0.0， 手动更新步骤如下：
 1. 停止较低版本 LogListener。
 2. 备份较低版本 LogListener。
 3. 下载并安装最新版本 LogListener。

