# Udp_Concurrent
安全的UDP并发实现

## UDP并发存在的问题
UDP协议由于是无连接的协议，所以在编程的时候，服务器的一个udp socket可以通过和多个客户端进行通信.这样带来的问题就是 当多个客户端同时向 服务器socket发送数据的时候，那么就可能会使得服务器收到的这多个客户端的信息混合在一起，没有办法辨别 各自的数据.

这个问题的话，我们可能会想到就是定制一个协议，客户端发送数据时，会在发送的数据前面指定自己的身份.这样使得服务器就可以辨别收到的数据是哪一个客户端发送的.但是实际上，这样是不行的，因为UDP协议是不可靠的协议，它不能够保证先发送的数据先到，后发送的数据后到.所以就可能会使得数据包前面的身份辨识数据 后于 数据包的数据到达.
