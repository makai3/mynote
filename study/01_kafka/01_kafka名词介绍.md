## Topic
Kafka将消息种子(Feed)分门别类， 每一类的消息称之为话题(Topic).
通俗的讲,其实就是相当于Map中的Key,唯一,且不能重复..

## Broker
已发布的消息保存在一组服务器中，称之为Kafka集群。集群中的每一个服务器都是一个代理(Broker). 消费者可以订阅一个或多个话题，并从Broker拉数据，从而消费这些已发布的消息。

## Partition
Topic 物理上的分组，一个 topic 可以分为多个 partition，每个 partition 是一个有序的队列。partition 中的每条消息都会被分配一个有序的 id（offset）。

## Message
消息，是通信的基本单位，每个 producer 可以向一个 topic（主题）发布一些消息

## Producer
发布消息的对象称之为话题生产者(Kafka topic producer)

## Consumer
订阅消息并处理发布的消息的种子的对象称之为话题消费者(consumers)