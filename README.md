# C-DIY
C++ library,sourecode and so on.
这一套十分简洁的websocket server，,采用C++ 开发平台，无需任何安装任何三方库， 只需将lib,dll,h头文件引入工程即可使用
使用方便，省心,省力：

只需三步：
1：  创建websocket server:
    pWebserver = CreateWebsockServer(9002);
    
    
2:  设置回调函数，

	setWebsockObsrv(pWebserver, std::bind(&CMFCDemoDlg::onWebsocket_msgstrrecevied, this, std::placeholders::_1, std::placeholders::_2),
		std::bind(&CMFCDemoDlg::onWebsocket_msgdatarecevied, this, std::placeholders::_1, std::placeholders::_2, std::placeholders::_3),
		std::bind(&CMFCDemoDlg::onWebsocket_newconnected, this, std::placeholders::_1),
		std::bind(&CMFCDemoDlg::onWebsocket_connectedclosed, this, std::placeholders::_1));
		
		
		
3：启动webserver(用线程 ）：
    std::thread st([&]()->void {
		startwebserver(pWebserver);
		});
	st.detach();	
	
	
另外：发送数据，发送字符串或是2进制直接看头文件即可，
  很简单：
  BYTE mary[5] = {0x01,0x0a,0x7E,0x08};
	broadcastbuffer(pWebserver, mary,4); //发送2进制数据，  
  broadcastString(pWebserver, "hello,you are ding..."); //发送字符串
  
  
  使用中如有疑问，欢迎留言，也可以直接email给我。
  
