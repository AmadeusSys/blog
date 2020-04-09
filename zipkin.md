#zipkin的安装
```bash
下载安装包  
curl -sSL https://zipkin.io/quickstart.sh | bash -s  

使用参数启动zipkin  
java -jar zipkin.jar --server.port=8402 --zipkin.storage.type=mysql --zipkin.storage.mysql.db=febs_cloud_base --zipkin.storage.mysql.username=root --zipkin.storage.mysql.password=123456 --zipkin.storage.mysql.host=localhost --zipkin.storage.mysql.port=3306 --zipkin.collector.rabbitmq.addresses=localhost:5672 --zipkin.collector.rabbitmq.username=febs  --zipkin.collector.rabbitmq.password=123456
```
不过既然是jar包直接启动不方便维护可以使用<a href="https://github.com/AmadeusSys/blog/blob/master/linux/deploy.sh">启动脚本</a>