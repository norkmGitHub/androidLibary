# һЩ���ÿ�����

android_socket
��׿�� tcp ͨ�ſ�,�÷��ο���

private static NettyTcpClient mNettyTcpClient;

mNettyTcpClient = new NettyTcpClient.Builder()
                            .setHost("xx.xxx.xx.xxx")    //���÷���˵�ַ
                            .setTcpPort(xxxx) //���÷���˶˿ں�
                            .setMaxReconnectTimes(-1)    //��������������� -1ʱ��������
                            .setReconnectIntervalTime(5000)    //�����������ʱ�䡣��λ ����
                            .setSendheartBeat(true) //�����Ƿ�������
                            .setHeartBeatInterval(50) //�����������ʱ�䡣��λ����
                            .setHeartBeatData(new byte[]{0x03, 0x0F, (byte) 0xFE, 0x05, 0x04, 0x0A}) //�����������ݣ�������String���ͣ�Ҳ������byte[]
                            .setIndex(0)    //���ÿͻ��˱�ʶ.(��Ϊ���ܴ��ڶ��tcp����)
                            .build();


//	���ü���
mNettyTcpClient.setListener(nettyClientListener);

//	���ӷ�����
mNettyTcpClient.connect();


//	��������
boolean ret = mNettyTcpClient.sendMsgToServer(b.getBytes());