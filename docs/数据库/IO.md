# 阻塞I/O，非阻塞I/O 和I/O多路复用

- [参考](https://www.jianshu.com/p/3137248d9ac5)
1. 阻塞I/O
    - 进程发起read后，如果kernel未准备好数据，进程就会被block，进入等待阶段；等待kernel将数据准备好，才会返回数据，解除阻塞；

2. 非阻塞I/O
    1. 进程发起read请求，kernel未准备好数据，直接返回一个error，进程无需阻塞等待
    2. 进程会轮询发送read请求，如此往复
    3. 一直到kernel准备好数据，才把数据拷贝并返回给进程，结束轮询


3. I/O多路复用
    
    - 进程调用select/poll/epoll，select/poll/epoll会将进程block起来

    - kernel会‘监视’所有select负责的socket；

    - 当任何一个socket准备好数据，select就会返回

    - 进程调用read（图中第二次 system call），将数据从kernel拷贝到用户进程；

    - 总结：所以，I/O 多路复用的特点是通过一种机制一个进程能同时等待多个文件描述符(简称fd)，而这些文件描述符（套接字描述符）其中的任意一个进入读就绪状态，select()函数就可以返回。

    - select，poll，epoll都是IO多路复用的机制。I/O多路复用就通过一种机制，可以监视多个描述符，一旦某个描述符就绪（一般是读就绪或者写就绪），能够通知程序进行相应的读写操作。但select，poll，epoll本质上都是同步I/O，因为他们都需要在读写事件就绪后自己负责进行读写，也就是说这个读写过程是阻塞的，而异步I/O则无需自己负责进行读写，异步I/O的实现会负责把数据从内核拷贝到用户空间。 

    - 文件描述符：简称fd，当应用程序请求内核打开/新建一个文件时，内核会返回一个文件描述符用于对应这个打开/新建的文件，其fd本质上就是一个非负整数，读写文件也是需要使用这个文件描述符来指定待读写的文件的。用于Linux 系统中。

4. I/O多路复用的特点及合理使用场景
    1. I/O多路复用和阻塞I/O差别其实不大，事实上，还更差一些

    2. 但是，I/O多路复用的优势是：同时处理多个连接请求。

    3. 所以，如果处理的连接数不是很高的话，使用select/epoll的web server不一定比使用多线程 + 阻塞 IO的web server性能更好，可能延迟还更大。

    4. select/epoll的优势并不是对于单个连接能处理得更快，而是在于能处理更多的连接

5. I/O多路复用主要的三种实现方式

    - select, poll, epoll 都是I/O多路复用的具体的实现，之所以有这三个鬼存在，其实是他们出现是有先后顺序的。

    - select

        不是线程安全；

        只返回数据，不会告知是哪个sock返回的，只能自己遍历去查找；

        只能监视1024个链接；

    - poll
        相对于select改进了：可监视无数个链接

        缺点：仍旧不是线程安全。

    - epoll

        改进：线程安全

        缺点：只有linux支持
        ngnix 的设计原则里面， 它会使用目标平台上面最高效的I/O多路复用模型咯，所以才会有这个设置。一般情况下，如果可能的话，尽量都用epoll吧。

    - 以上都是针对高并发大流量而言，如果不是，其实用哪个都差不多。
    
    - 线程安全相关，参见[这里](https://blog.csdn.net/csdnnews/article/details/82321777)
    - 当多个线程访问某个方法时，不管你通过怎样的调用方式、或者说这些线程如何交替地执行，我们在主程序中不需要去做任何的同步，这个类的结果行为都是我们设想的正确行为，那么我们就可以说这个类是线程安全的。  