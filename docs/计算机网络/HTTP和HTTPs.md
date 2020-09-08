
# HTTP/HTTPs
[参考](https://www.cnblogs.com/spll/p/10565189.html)

## HTTP(超文本传输协议):

- 最大的区别是http是用明文方式发送内容的，不要说什么get，post请求，post请求只是在浏览器上不显示参数，如果我们用一些抓包工具是一样会把http发送请求的内容给抓过来的。

- 使用80端口

- GET

    - 从指定的资源请求数据。

- POST

    - 向指定的资源提交要被处理的数据



## HTTPs(安全套接字超文本传输协议):
- 在http协议的基础上加入了ssl协议+证书，用来加密传输数据
- ssl层协议：（全称：Secure Sockets Layer 安全套接层）是一种安全协议，SSL在传输层对网络连接进行加密
- 使用443接口