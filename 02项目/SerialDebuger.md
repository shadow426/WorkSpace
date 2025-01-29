1.串口助手点击弹出串口列表

构造函数写一次，重写鼠标事件写一次

QStringList

foreach

2.点击打开串口按钮

槽函数

	从下拉框中获取数据，波特率、数据位、停止位、奇偶校验位，赋值给QSerialPort
	当前字为打开串口：
		如果打开串口成功：
			设置为关闭串口
			禁用上面的下拉框
		打开串口失败
			提示
	当前为关闭串口的字符
		
		


3.发送键槽函数



QByteArray

toPlainText().toLocal8Bit().data()



toUtf8()