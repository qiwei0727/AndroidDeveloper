### why
在Android中，每个应用（Application）执行在它自己的进程中，无法直接调用到其他应用的资源。

因此，在Android中，当一个应用被执行时，一些操作是被限制的，比如访问内存，访问传感器，等等。
这样做可以最大化地保护系统，免得应用程序“为所欲为”。

那我们有时需要在应用间交互，怎么办呢？

于是，Android需要实现IPC协议。然而，这个协议还是有点复杂，主要因为需要实现数据管理系统（在进程或线程间传递数据）。
为了暂时减缓这个“会呼吸的痛”，Android为我们实现了自己的IPC，也就是梁静茹，oh，sorry，是AIDL。

### what
Android提供了IPC（Inter Process Communication, 进程间通信）的一种独特实现：
AIDL（Android Interface Definition Language, Android接口定义语言）。

### how
1. 定义一个AIDL接口
2. 为远程服务实现对应Stub
3. 将服务“暴露”给客户程序使用

### 参考
http://bbs.51cto.com/thread-1086040-1.html













