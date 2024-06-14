#### QLabel的使用

```
QLabel * label = new QLabel;
        label->setParent(this);
        label->setFixedSize(menuBtn->width(),menuBtn->height());
        label->setText(QString::number(i+1));
        label->move(40+i%4 *120,145+i/4*120);
        //设置label文字的对齐方式
        label->setAlignment(Qt::AlignVCenter|Qt::AlignHCenter);
        //设置鼠标的穿透
        label->setAttribute(Qt::WA_TransparentForMouseEvents);
```

#### QString的使用

```
QString str = QString("监听的是第%1个按钮").arg(i+1);
            qDebug() << str;
QString::number(i+1)
```

#### QMenu/菜单栏的使用

```
//菜单栏
    QMenuBar * bar = menuBar();
    setMenuBar(bar);
    //开始按钮
    QMenu * startMenu = bar->addMenu("开始");
	
    QAction * quitAction = startMenu->addAction("退出");
	
    connect(quitAction,&QAction::triggered,[=](){
        this->close();
    });
```

PaintEvent的重置

```
QPainter painter(this);
    QPixmap pix;
    pix.load(":/res/OtherSceneBg.png");
    painter.drawPixmap(0,0,this->width(),this->height(),pix);
```

#### QFile

```c++
QFile *m_file; 
m_file.setFileName(strpath);
m_file.open(QIODevice::ReadOnly);//只读形式打开
char *buffer = new char[4096];
qint64 ret = 0;
while(true)
{
    ret = m_file.read(buffer, 4096);
    if(ret > 0 && ret <= 4096)
    {
        write(buffer, ret);
    }
    else if(0 == ret)
    {
        m_file.close();
        break;
    }
    else if(ret < 0)
    {
        qDebug() << "发送文件内容给Client失败";
        m_file.close();
        break;
    }
}
```

### 多线程的使用

#### 核心步骤

1. **创建一个继承自`QRunnable`的任务类**：实现`run`方法，定义任务的具体内容。
2. **创建并配置`QThreadPool`**：设置线程池的最大线程数。
3. **将任务提交到线程池中**：使用`QThreadPool`的`start`方法，将`QRunnable`任务提交到线程池中执行。

1.服务器模板类启动监听！

```
MyTcpServer::getInstance().listen(QHostAddress(m_strIP),m_usPort);
```

1.创建线程池，并设置最大线程数

```c++
m_threadPool = new QThreadPool(this);
m_threadPool->setMaxThreadCount(5);
```

2.创建任务类、继承QRunnable并从重构run()

```c++
MyTcpSocket *socket = new MyTcpSocket();
socket->moveToThread(QThread::currentThread());
delete socket;
```

run()处理socket层面的事件

3.创建任务，并将任务输入到线程池

```c++
MyTask *mytask = new MyTask(socketDescriptor, this);
m_threadPool->start(mytask);
```

### 多线程时单例数据库的使用



对象树

qxml

qss

控件

布局

C++ 模态

git仓库   svn

STL模块

linux

shell脚本
