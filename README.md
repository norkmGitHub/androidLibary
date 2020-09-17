# 一些常用开发库

android_socket
安卓的 tcp 通信库,用法参考：

private static NettyTcpClient mNettyTcpClient;

mNettyTcpClient = new NettyTcpClient.Builder()
                            .setHost("xx.xxx.xx.xxx")    //设置服务端地址
                            .setTcpPort(xxxx) //设置服务端端口号
                            .setMaxReconnectTimes(-1)    //设置最大重连次数 -1时无限重连
                            .setReconnectIntervalTime(5000)    //设置重连间隔时间。单位 毫秒
                            .setSendheartBeat(true) //设置是否发送心跳
                            .setHeartBeatInterval(50) //设置心跳间隔时间。单位：秒
                            .setHeartBeatData(new byte[]{0x03, 0x0F, (byte) 0xFE, 0x05, 0x04, 0x0A}) //设置心跳数据，可以是String类型，也可以是byte[]
                            .setIndex(0)    //设置客户端标识.(因为可能存在多个tcp连接)
                            .build();


//	设置监听
mNettyTcpClient.setListener(nettyClientListener);

//	连接服务器
mNettyTcpClient.connect();


//	发送数据
boolean ret = mNettyTcpClient.sendMsgToServer(b.getBytes());