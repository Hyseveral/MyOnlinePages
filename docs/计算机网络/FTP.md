
# FTP协议

[参考链接1](https://zhuanlan.zhihu.com/p/52085270)
[参考链接2](https://zhuanlan.zhihu.com/p/141472331)

文件传输协议 File Transfer Protocol

主要功能：
传输文件到远程主机/从远程主机下载文件

应用层模式：
client/server模式

client: 发起传输的一方

server: 远程主机

ftp: RFC 959

ftp服务器: 端口号 21

> 和HTTP相比，FTP面向的直接是服务器的文件系统，并且具有维持状态的特点，在文件传输管理上，FTP更胜一筹

## 一. 工作流程

1. FTP客户首先发起建立1个与FTP服务器端口号21之间的TCP控制连接, 指定TCP作为传输层协议


2. 客户在建立的控制连接上获得身份认证

3. 客户在建立的控制连接上发送命令来浏览远程主机的目录.

4. 当服务器接收到1个文件传输命令时, 在服务器端口号20创建1个与客户 的TCP数据连接

5. 1个文件传输后,服务器结束这个TCP数据连接.

6. 之后 再次传输，服务器创建第2个TCP与客户的数据连接来传输下一个文件.


**特点**

    控制连接: 带外发送控制信息（对比 HTTP 带内控制信息）

    TP 服务器要维护用户状态信息: 当前目录, 先前的身份认证（对比HTTP的无状态连接）


## 二. FTP的模块架构

控制连接:

> USER-PI(protocol interpreter):用户协议解释器
>
> SERVER-PI:服务器协议解释器

数据连接:
> user-DTP(Data Transfer Process):用户数据传输进程
>
> server-DTP:服务器数据传输进程


## 三. FTP数据连接建立方式

**主动模式:**
- 客户端发送PORT命令：PORT h1,h2,h3,h4,p1,p2 (h1-h4是IP地址，p1-p2是端口号)

- 服务器根据PORT命令指定的客户端地址和端口号发起数据连接

**被动模式：**
- 客户端发送PASV命令

- 服务器返回监听的地址和端口号 • 客户端发起数据连接


## 四.FTP命令和应答

常见命令:

    在控制连接上发送ASCII文本
    USER username
    PASS password
    LIST:返回当前远程目录的文 件列表
    RETR filename:获取远程主 机当前目录下的1个文件(get)
    STOR filename:存放1个文 件到远程主机当前目录下(put)

常见应答:

    状态码及其相应短语 (同 HTTP)
    331 Username OK, password required
    125 data connection already open; transfer starting
    425 Can’t open data connection • 452 Error writing file
