# Rabbit MQ

## 工作模式

<img src="https://cdn.jsdelivr.net/gh/chenruida/image@master/uPic/%E6%88%AA%E5%B1%8F2021-01-05%2010.07.45VeOrSy.png" alt="截屏2021-01-05 10.07.45" style="zoom:50%;" />

### 应用

与简单模式相比，多了一些消费端，多个消费端共同消费同一队列中的消息。

应用场景： 对于任务过重或任务较多情况使用工作队列可以提高任务处理的速度。

### 小结

在一个队列中如果有多个消费者，那么消费者之间对于同一消息是竞争的关系。

## Pub/Sub订阅模式



<img src="https://cdn.jsdelivr.net/gh/chenruida/image@master/uPic/%E6%88%AA%E5%B1%8F2021-01-05%2010.23.52MUJU84.png" alt="截屏2021-01-05 10.23.52" style="zoom:50%;" />

### 介绍

P: 生产者，也就是要发送消息的程序，发送到交换机

C：消费者，消息的接收者，会一直等待消息到来