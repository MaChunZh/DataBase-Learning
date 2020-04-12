# Otter阿里巴巴分布式数据库同步系统搭建

## 参考引用

* [otter 实现mysql数据库单向同步](https://www.jianshu.com/p/d955d9d73241)
* [otter双A同步配置](https://www.cnblogs.com/xiaoxiaole/p/8046834.html)
* [数据同步利器-otter的搭建使用说明](https://blog.csdn.net/wudufeng/article/details/78688240)
* [otter：分布式数据库同步系统](https://blog.csdn.net/Keep_Coding/article/details/98873202)
* [数据同步利器-otter的搭建使用详细说明](https://blog.csdn.net/likemebee/article/details/83027802)

## 操作环境

* mysql5.7
* jdk1.8
* zookeeper-3.4.6
* manager.deployer-4.2.18
* node.deployer-4.2.18

## mysql安装并初始化

otter manager依赖于mysql进行配置信息的存储，所以需要预先安装mysql，并初始化otter manager的系统表结构

1. 安装Mysql
2. 下载otter-manager-schema.sql初始化表结构[[下载](https://raw.github.com/alibaba/otter/master/manager/deployer/src/main/resources/sql/otter-manager-schema.sql)]
3. 初始化表结构

```cmd
# mysql -u root -p #进行mysql

mysql> source otter-manager-schema.sql #执行导入
```

## zookeeper安装

整个otter架构依赖了zookeeper进行多节点调度，所以需要预先安装zookeeper，不需要初始化节点，otter程序启动后会自检.

> manager需要在otter.properties中配置zookeeper集群机器