# message
### 1.rabbitMQ 
* 安装https://hub.docker.com/_/rabbitmq
~~~
#拉取镜像
docker pull rabbitmq:management

#第一节点
docker run -d --hostname rabbit_host1 --name me_rabbit -e RABBITMQ_DEFAULT_USER=admin -e RABBITMQ_DEFAULT_PASS=password -p 15672:15672 -p 5672:5672 rabbitmq:management
#第二节点
docker run -d --hostname rabbit_host2 --name me_rabbit -e RABBITMQ_DEFAULT_USER=admin -e RABBITMQ_DEFAULT_PASS=password -p 15672:15672 -p 5672:5672 rabbitmq:management
#第三节点
docker run -d --hostname rabbit_host3 --name me_rabbit -e RABBITMQ_DEFAULT_USER=admin -e RABBITMQ_DEFAULT_PASS=password -p 15672:15672 -p 5672:5672 rabbitmq:management


#介绍
-d 以守护进程方式在后台运行
-p 15672:15672 management 界面管理访问端口
-p 5672:5672 amqp 访问端口
--name：指定容器名
--hostname：设定容器的主机名，它会被写到容器内的 /etc/hostname 和 /etc/hosts，作为容器主机IP的别名，并且将显示在容器的bash中

-e 参数
  RABBITMQ_DEFAULT_USER 用户名
  RABBITMQ_DEFAULT_PASS 密码
  
#日志
docker logs hostname
~~~

* 端口
  * 4369 erlang 发现口
  * 5672 client 端通信口
  * 15672 管理界面 ui 端口
  * 25672 server 间内部通信口
* 访问
  * http://192.168.159.128:15672/#/