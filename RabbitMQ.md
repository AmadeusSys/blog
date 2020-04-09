### 安装erlang

由于rabbitmq是基于erlang语言开发的，所以必须先安装erlang。

安装依赖
```bash
yum -y install gcc glibc-devel make ncurses-devel openssl-devel xmlto perl wget gtk2-devel binutils-devel
```
erlang官网：

https://www.erlang.org/downloads

下载（会比较慢，请耐心等待）

```bash
wget http://erlang.org/download/otp_src_22.0.tar.gz
```

解压

```bash
tar -zxvf otp_src_22.0.tar.gz
```

移走

```bash
mv otp_src_22.0 /usr/local/
```

切换目录

```bash
cd /usr/local/otp_src_22.0/
```

创建即将安装的目录

```bash
mkdir ../erlang
```

配置安装路径

```bash
./configure --prefix=/usr/local/erlang
```

如果遇到这个错 你就假装没看到

![image](https://upload-images.jianshu.io/upload_images/11646428-e4e90906c6c99cfe.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

安装

```bash
make install
```

查看一下是否安装成功

```bash
ll /usr/local/erlang/bin
```

添加环境变量

```bash
echo 'export PATH=$PATH:/usr/local/erlang/bin' >> /etc/profile
```

刷新环境变量

```bash
source /etc/profile
```

甩一条命令

```bash
erl
```

瞬间进入了一个未知的世界

![image](https://upload-images.jianshu.io/upload_images/11646428-96e90a1f88199bbd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在里面输入halt().命令退出来（那个点号别忘记）

![image](https://upload-images.jianshu.io/upload_images/11646428-65a10ccc65db176b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

回到顶部

### 安装RabbitMQ

rabbitmq下载地址：

https://github.com/rabbitmq/rabbitmq-server/releases/tag/v3.7.15

下载

```bash
wget https://github.com/rabbitmq/rabbitmq-server/releases/download/v3.7.15/rabbitmq-server-generic-unix-3.7.15.tar.xz</pre>
```
由于是tar.xz格式的所以需要用到xz，没有的话就先安装 

```bash
yum install -y xz</pre>
```
第一次解压

```bash
/bin/xz -d rabbitmq-server-generic-unix-3.7.15.tar.xz</pre>
```
第二次解压

```bash
tar -xvf rabbitmq-server-generic-unix-3.7.15.tar</pre>
```
移走

```bash
mv rabbitmq_server-3.7.15/ /usr/local/</pre>
```
改名

```bash
mv /usr/local/rabbitmq_server-3.7.15  rabbitmq</pre>
```
配置环境变量

```bash
echo 'export PATH=$PATH:/usr/local/rabbitmq/sbin' >> /etc/profile</pre>
```
刷新环境变量

```bash
source /etc/profile</pre>
```
创建配置目录

```bash
mkdir /etc/rabbitmq</pre>
```
回到顶部

### 启动命令

启动：

```bash
rabbitmq-server -detached</pre>

停止：

```bash
rabbitmqctl stop</pre>
```
状态：

```bash
rabbitmqctl status</pre>
```
防火墙之类的请自行处理（5672和15672端口），反正我是从来不开防火墙。

回到顶部

### WEB管理

开启web插件

```bash
rabbitmq-plugins enable rabbitmq_management</pre>
```
访问：http://127.0.0.1:15672/

![image](https://upload-images.jianshu.io/upload_images/11646428-6942791c50045a58.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

默认账号密码：guest guest（这个账号只允许本机访问）

回到顶部

### 用户管理

查看所有用户

```bash
rabbitmqctl list_users</pre>
```
添加一个用户

```bash
rabbitmqctl add_user zhaobl 123456</pre>
```
配置权限

```bash
rabbitmqctl set_permissions -p "/" zhaobl ".*" ".*" ".*"</pre>
```
查看用户权限

```bash
rabbitmqctl list_user_permissions zhaobl</pre>
```
设置tag

```bash
rabbitmqctl set_user_tags zhaobl administrator</pre>
```
删除用户（安全起见，删除默认用户）

```bash
rabbitmqctl delete_user guest</pre>
```