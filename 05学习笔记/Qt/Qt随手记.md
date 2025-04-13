
1.**Lambda 表达式**
在信号与槽上面经常使用

2.QPixmap和QIcon的区别

3.设置背景的方式
- 使用Label创建相同大小的页面显示图片
- 使用画家在窗口上画

4.报错
F:\01Code\03Practice\Qt\CoinFilp\mainscene.cpp:26: error: variable 'QPainter painter' has initializer but incomplete type ..\..\mainscene.cpp: In member function 'virtual void MainScene::paintEvent(QPaintEvent*)': ..\..\mainscene.cpp:26:21: error: va

添加头文件好转
#include <QPainterPath>
