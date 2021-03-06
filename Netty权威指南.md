基础篇走进Java NIO
第1 章Java 的I/O 演进之路.2
1.1 I/O 基础入门...............3
1.1.1 Linux 网络I/O 模型简介.......3
1.1.2 I/O 多路复用技术.................6
1.2 Java 的I/O 演进..........8
1.3 总结............................ 10

UNIX提供了5种1/O模型
（1）阻塞I/O模型：
（2）非阻塞I/O模型：
3）I/O复用模型：
（4）信号驱动I/O模型：
（5）异步I/O：

I/0==多路复用==技术通过把多个I/O的阻塞复用到同一个select的阻塞上，从而使得系统在单线程的情况下可以同时处理多个客户端请求。

在JDK1.4推出Java NIO之前采用了同步阻塞模式，这种一请求一应答的通信模型简化了上层的应用开发

异步1/0开发的API和类库，主要的类和接口如下。
1进行异步I/O操作的缓冲区ByteBuffer等；
2进行异步I/O操作的管道Pipe；
3进行各种I/0操作（异步或者同步）的Channel，包括ServerSocketChannel和SocketChannel：
4多种字符集的编码能力和解码能力；
5实现非阻塞I/O操作的多路复用器selector；
6基于流行的Perl实现的正则表达式类库；圈文件通道FileChannel。

第2 章NIO 入门.................... 11
2.1 传统的BIO 编程....... 11
2.1.1 BIO 通信模型图.................. 12
2.1.2 同步阻塞式I/O 创建的TimeServer 源码分析............. 13
2.1.3 同步阻塞式I/O 创建的TimeClient 源码分析.......... 16
2.2 伪异步I/O 编程........ 18
2.2.1 伪异步I/O 模型图.............. 19
2.2.2 伪异步I/O 创建的TimeServer 源码分析..... 19
2.2.3 伪异步I/O 弊端分析........... 21
2.3 NIO 编程.................... 24
2.3.1 NIO 类库简介.. 24
2.3.2 NIO 服务端序列图.............. 28
2.3.3 NIO 创建的TimeServer 源码分析................ 30
2.3.4 NIO 客户端序列图.............. 36
2.3.5 NIO 创建的TimeClient 源码分析................ 39
2.4 AIO 编程.................... 45
2.4.1 AIO 创建的TimeServer 源码分析................ 46
2.4.2 AIO 创建的TimeClient 源码分析................ 51
2.4.3 AIO 版本时间服务器运行结果.................... 56
2.5 4 种I/O 的对比......... 58
2.5.1 概念澄清.......... 58
2.5.2 不同I/O 模型对比.............. 59
2.6 选择Netty 的理由..... 60
2.6.1 不选择Java 原生NIO 编程的原因............... 61
2.6.2 为什么选择Netty ................ 62
2.7 总结............................ 63
入门篇 Netty NIO 开发指南
第3 章Netty 入门应用.......... 66
3.1 Netty 开发环境的搭建................ 66
3.1.1 下载Netty 的软件包........... 67
3.1.2 搭建Netty 应用工程........... 67
3.2 Netty 服务端开发...... 68
3.3 Netty 客户端开发...... 73
3.4 运行和调试................ 76
3.4.1 服务端和客户端的运行...... 76
3.4.2 打包和部署...... 77
3.5 总结............................ 77
第4 章TCP 粘包/拆包问题的解决之道...... 79
4.1 TCP 粘包/拆包.......... 79
4.1.1 TCP 粘包/拆包问题说明..... 80
4.1.2 TCP 粘包/拆包发生的原因....... 80
4.1.3 粘包问题的解决策略.......... 81
4.2 未考虑TCP 粘包导致功能异常案例................. 82
4.2.1 TimeServer 的改造.............. 82
4.2.2 TimeClient 的改造............... 83
4.2.3 运行结果.......... 84
4.3 利用LineBasedFrameDecoder 解决TCP 粘包问题................ 85
4.3.1 支持TCP 粘包的TimeServer ....................... 86
4.3.2 支持TCP 粘包的TimeClient........................ 88
4.3.3 运行支持TCP 粘包的时间服务器程序........ 90
4.3.4 LineBasedFrameDecoder 和StringDecoder 的原理分析........... 91
4.4 总结............................ 92
第5 章分隔符和定长解码器的应用...... 93
5.1 DelimiterBasedFrameDecoder 应用开发............. 94
5.1.1 DelimiterBasedFrameDecoder 服务端开发.... 94
5.1.2 DelimiterBasedFrameDecoder 客户端开发.... 97
5.1.3 运行DelimiterBasedFrameDecoder 服务端和客户端............... 99
5.2 FixedLengthFrameDecoder 应用开发............... 101
5.2.1 FixedLengthFrameDecoder 服务端开发...... 101
5.2.2 利用telnet 命令行测试EchoServer 服务端......103
5.3 总结.......................... 104
中级篇 Netty 编解码开发指南
第6 章编解码技术.............. 106
6.1 Java 序列化的缺点 ...... 107
6.1.1 无法跨语言.... 107
6.1.2 序列化后的码流太大........ 107
6.1.3 序列化性能太低................ 110
6.2 业界主流的编解码框架............ 113
6.2.1 Google 的Protobuf 介绍.... 113
6.2.2 Facebook 的Thrift 介绍.... 115
6.2.3 JBoss Marshalling 介绍..... 116
6.3 总结.......................... 117
第7 章MessagePack 编解码............... 118
7.1 MessagePack 介绍... 118
7.1.1 MessagePack 多语言支持.. 119
7.1.2 MessagePack Java API 介绍........................ 119
7.1.3 MessagePack 开发包下载. 120
7.2 MessagePack 编码器和解码器开发................. 120
7.2.1 MessagePack 编码器开发....... 120
7.2.2 MessagePack 解码器开发 ...... 121
7.2.3 功能测试........ 121
7.3 粘包/半包支持......... 124
7.4 总结.......................... 127
第8 章Google Protobuf 编解码.......... 128
8.1 Protobuf 的入门....... 129
8.1.1 Protobuf 开发环境搭建..... 129
8.1.2 Protobuf 编解码开发......... 131
8.1.3 运行Protobuf 例程............ 133
8.2 Netty 的Protobuf 服务端开发.. 133
8.2.1 Protobuf 版本的图书订购服务端开发........ 134
8.2.2 Protobuf 版本的图书订购客户端开发........ 136
8.2.3 Protobuf 版本的图书订购程序功能测试.... 139
8.3 Protobuf 的使用注意事项......... 140
8.4 总结.......................... 142
第9 章JBoss Marshalling 编解码....... 143
9.1 Marshalling 开发环境准备........ 143
9.2 Netty 的Marshalling 服务端开发..................... 144
9.3 Netty 的Marshalling 客户端开发..................... 147
9.4 运行Marshalling 客户端和服务端例程........... 149
9.5 总结.......................... 150
高级篇 Netty 多协议开发和应用
第10 章HTTP 协议开发应用............... 154
10.1 HTTP 协议介绍..... 155
10.1.1 HTTP 协议的URL .......... 155
10.1.2 HTTP 请求消息（HttpRequest）.............. 155
10.1.3 HTTP 响应消息（HttpResponse）........... 158
10.2 Netty HTTP 服务端入门开发....... 159
10.2.1 HTTP 服务端例程场景描述..................... 160
10.2.2 HTTP 服务端开发........... 160
10.2.3 Netty HTTP 文件服务器例程运行结果.... 166
10.3 Netty HTTP+XML 协议栈开发....................... 170
10.3.1 开发场景介绍................. 171
10.3.2 HTTP+XML 协议栈设计.......174
10.3.3 高效的XML 绑定框架JiBx ..................... 175
10.3.4 HTTP+XML 编解码框架开发.................. 183
10.3.5 HTTP+XML 协议栈测试....... 199
10.3.6 小结............. 201
10.4 总结........................ 202
第11 章WebSocket 协议开发............. 203
11.1 HTTP 协议的弊端....... 204
11.2 WebSocket 入门..... 204
11.2.1 WebSocket 背景............... 205
11.2.2 WebSocket 连接建立....... 206
11.2.3 WebSocket 生命周期....... 207
11.2.4 WebSocket 连接关闭....... 208
11.3 Netty WebSocket 协议开发..... 209
11.3.1 WebSocket 服务端功能介绍..................... 209
11.3.2 WebSocket 服务端开发.... 210
11.3.3 运行WebSocket 服务端... 218
11.4 总结........................ 219
第12 章私有协议栈开发.... 221
12.1 私有协议介绍........ 221
12.2 Netty 协议栈功能设计............ 223
12.2.1 网络拓扑图.. 223
12.2.2 协议栈功能描述.............. 224
12.2.3 通信模型...... 224
12.2.4 消息定义...... 225
12.2.5 Netty 协议支持的字段类型...................... 226
12.2.6 Netty 协议的编解码规范. 227
12.2.7 链路的建立.. 229
12.2.8 链路的关闭.. 230
12.2.9 可靠性设计.. 230
12.2.10 安全性设计 232
12.2.11 可扩展性设计................ 232
12.3 Netty 协议栈开发.. 233
12.3.1 数据结构定义................. 233
12.3.2 消息编解码.. 237
12.3.3 握手和安全认证.............. 241
12.3.4 心跳检测机制................. 245
12.3.5 断连重连...... 248
12.3.6 客户端代码.. 249
12.3.7 服务端代码.. 251
12.4 运行协议栈............ 252
12.4.1 正常场景...... 252
12.4.2 异常场景：服务端宕机重启.................... 253
12.4.3 异常场景：客户端宕机重启.................... 256
12.5 总结........................ 256
第13 章服务端创建............ 258
13.1 原生NIO 类库的复杂性......... 259
13.2 Netty 服务端创建源码分析.... 259
13.2.1 Netty 服务端创建时序图. 260
13.2.2 Netty 服务端创建源码分析...................... 263
13.3 客户端接入源码分析.............. 272
13.4 总结........................ 275
第14 章客户端创建............ 276
14.1 Netty 客户端创建流程分析.... 276
14.2.1 Netty 客户端创建时序图. 276
14.2.2 Netty 客户端创建流程分析...................... 277
14.2 Netty 客户端创建源码分析.... 278
14.2.1 客户端连接辅助类Bootstrap.................... 278
14.2.2 客户端连接操作.............. 281
14.2.3 异步连接结果通知.......... 283
14.2.4 客户端连接超时机制...... 284
14.3 总结........................ 286
源码分析篇 Netty 功能介绍和源码分析
第15 章ByteBuf 和相关辅助类........... 288
15.1 ByteBuf 功能说明. 288
15.1.1 ByteBuf 的工作原理........ 289
15.1.2 ByteBuf 的功能介绍........ 294
15.2 ByteBuf 源码分析. 308
15.2.1 ByteBuf 的主要类继承关系..................... 309
15.2.2 AbstractByteBuf 源码分析........................ 310
15.2.3 AbstractReferenceCountedByteBuf 源码分析.................. 319
15.2.4 UnpooledHeapByteBuf 源码分析.............. 321
15.2.5 PooledByteBuf 内存池原理分析............... 326
15.2.6 PooledDirectByteBuf 源码分析................. 329
15.3 ByteBuf 相关的辅助类功能介绍.................... 332
15.3.1 ByteBufHolder................. 332
15.3.2 ByteBufAllocator ............. 333
15.3.3 CompositeByteBuf ........... 334
15.3.4 ByteBufUtil .. 336
15.4 总结........................ 337
第16 章Channel 和Unsafe ................. 338
16.1 Channel 功能说明. 338
16.1.1 Channel 的工作原理........ 339
16.1.2 Channel 的功能介绍........ 340
16.2 Channel 源码分析. 343
16.2.1 Channel 的主要继承关系类图.................. 343
16.2.2 AbstractChannel 源码分析........................ 344
16.2.3 AbstractNioChannel 源码分析.................. 347
16.2.4 AbstractNioByteChannel 源码分析........... 350
16.2.5 AbstractNioMessageChannel 源码分析..... 353
16.2.6 AbstractNioMessageServerChannel 源码分析.............. 354
16.2.7 NioServerSocketChannel 源码分析........... 355
16.2.8 NioSocketChannel 源码分析..................... 358
16.3 Unsafe 功能说明... 364
16.4 Unsafe 源码分析... 365
16.4.1 Unsafe 继承关系类图...... 365
16.4.2 AbstractUnsafe 源码分析. 366
16.4.3 AbstractNioUnsafe 源码分析.................... 375
16.4.4 NioByteUnsafe 源码分析. 379
16.5 总结........................ 387
第17 章ChannelPipeline 和ChannelHandler........... 388
17.1 ChannelPipeline 功能说明....... 389
17.1.1 ChannelPipeline 的事件处理.................... 389
17.1.2 自定义拦截器................. 391
17.1.3 构建pipeline 392
17.1.4 ChannelPipeline 的主要特性.................... 393
17.2 ChannelPipeline 源码分析....... 393
17.2.1 ChannelPipeline 的类继承关系图............. 393
17.2.2 ChannelPipeline 对ChannelHandler 的管理........... 393
17.2.3 ChannelPipeline 的inbound 事件.............. 396
17.2.4 ChannelPipeline 的outbound 事件............ 397
17.3 ChannelHandler 功能说明....... 398
17.3.1 ChannelHandlerAdapter 功能说明............ 399
17.3.2 ByteToMessageDecoder 功能说明............ 399
17.3.3 MessageToMessageDecoder 功能说明...... 400
17.3.4 LengthFieldBasedFrameDecoder 功能说明............... 400
17.3.5 MessageToByteEncoder 功能说明............. 404
17.3.6 MessageToMessageEncoder 功能说明....... 404
17.3.7 LengthFieldPrepender 功能说明............... 405
17.4 ChannelHandler 源码分析....... 406
17.4.1 ChannelHandler 的类继承关系图............. 406
17.4.2 ByteToMessageDecoder 源码分析............ 407
17.4.3 MessageToMessageDecoder 源码分析...... 410
17.4.4 LengthFieldBasedFrameDecoder 源码分析............ 411
17.4.5 MessageToByteEncoder 源码分析............. 415
17.4.6 MessageToMessageEncoder 源码分析....... 416
17.4.7 LengthFieldPrepender 源码分析............... 417
17.5 总结........................ 418
第18 章EventLoop 和EventLoopGroup.................... 419
18.1 Netty 的线程模型.. 419
18.1.1 Reactor 单线程模型......... 420
18.1.2 Reactor 多线程模型......... 421
18.1.3 主从Reactor 多线程模型 422
18.1.4 Netty 的线程模型............ 423
18.1.5 最佳实践...... 424
18.2 NioEventLoop 源码分析......... 425
18.2.1 NioEventLoop 设计原理.. 425
18.2.2 NioEventLoop 继承关系类图................... 426
18.2.3 NioEventLoop.................. 427
18.3 总结........................ 436
第19 章Future 和Promise .................. 438
19.1 Future 功能............ 438
19.2 ChannelFuture 源码分析......... 443
19.3 Promise 功能介绍. 445
19.4 Promise 源码分析. 447
19.4.1 Promise 继承关系图........ 447
19.4.2 DefaultPromise ................ 447
19.5 总结........................ 449
架构和行业应用篇 Netty 高级特性

### 第20 章Netty 架构剖析

Netty采用了典型的三层网络架构进行设计和开发

![](img/netty_ar.png)

#### 21.1.1Reactor 通信调度层

它由一系列辅助类完成
该层的主要职责就是监听网络的读写和连接操作，负责将网络层的数据读取到内存缓冲区中，然后触发各种网络事件将这些事件触发到PipeLine中

#### 21.1.2职责链 ChannelPipeline

它负责事件在职责链中的有序传播，同时负责动态地编排职责链。职责链可以选择监听和处理自己关心的事件，它可以拦截处理和向后/向前传播事件。

##### 21.1.3业务逻辑编排层（Service ChannelHandler）

业务逻辑编排层通常有两类：一类是纯粹的业务逻辑编排，还有一类是其他的应用层协议插件，用于特定协议相关的会话和链路管理。



第21 章Java 多线程编程在Netty 中的应用............. 461
21.1 Java 内存模型与多线程编程.. 461
21.1.1 硬件的发展和多任务处理........................ 461
21.1.2 Java 内存模型................. 462
21.2 Netty 的并发编程实践............ 464
21.2.1 对共享的可变数据进行正确的同步......... 464
21.2.2 正确使用锁.. 465
21.2.3 volatile 的正确使用......... 467
21.2.4 CAS 指令和原子类......... 470
21.2.5 线程安全类的应用.......... 472
21.2.6 读写锁的应用................. 476
21.2.7 线程安全性文档说明...... 477
21.2.8 不要依赖线程优先级...... 478
21.3 总结........................ 479
第22 章高性能之道............ 480
22.1 RPC 调用性能模型分析.......... 480
22.1.1 传统RPC 调用性能差的三宗罪............... 480
22.1.2 I/O 通信性能三原则........ 481
22.2 Netty 高性能之道.. 482
22.2.1 异步非阻塞通信.............. 482
22.2.2 高效的Reactor 线程模型 482
22.2.3 无锁化的串行设计.......... 485
22.2.4 高效的并发编程.............. 486
22.2.5 高性能的序列化框架...... 486
22.2.6 零拷贝.......... 487
22.2.7 内存池.......... 491
22.2.8 灵活的TCP 参数配置能力....................... 494
22.3 主流NIO 框架性能对比......... 495
22.4 总结........................ 497
第23 章可靠性.................... 498
23.1 可靠性需求............ 498
23.1.1 宕机的代价.. 498
23.1.2 Netty 可靠性需求............ 499
23.2 Netty 高可靠性设计................ 500
23.2.1 网络通信类故障.............. 500
23.2.2 链路的有效性检测.......... 507
23.2.3 Reactor 线程的保护......... 510
23.2.4 内存保护...... 513
23.2.5 流量整形...... 516
23.2.6 优雅停机接口................. 519
23.3 优化建议................ 520
23.3.1 发送队列容量上限控制... 520
23.3.2 回推发送失败的消息...... 521
23.4 总结........................ 521
第24 章安全性.................... 522
24.1 严峻的安全形势.... 522
24.1.1 OpenSSL Heart bleed 漏洞.......... 522
24.1.2 安全漏洞的代价.............. 523
24.1.3 Netty 面临的安全风险..... 523
24.2 Netty SSL 安全特性................. 525
24.2.1 SSL 单向认证.................. 525
24.2.2 SSL 双向认证.................. 532
24.2.3 第三方CA 认证.............. 536
24.3 Netty SSL 源码分析................. 538
24.3.1 客户端.......... 538
24.3.2 服务端.......... 541
24.3.3 消息读取...... 544
24.3.4 消息发送...... 545
24.4 Netty 扩展的安全特性............ 546
24.4.1 IP 地址黑名单机制.......... 547
24.4.2 接入认证...... 548
24.4 总结........................ 550
第25 章Netty 未来展望..... 551
系统只要分布式部署，就存在多个节点之间通信的问题,利用==Netty+二进制编解码==承载这些内部私有协议，已经逐渐成为业界主流的用法。
附录A Netty 参数配置表.... 554