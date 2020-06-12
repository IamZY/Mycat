# Mycat
 Mycat学习笔记

| 192.168.52.110 | node02 | 主机 |
| -------------- | ------ | ---- |
| 192.168.52.120 | node03 | 从机 |
| 192.168.52.130 | node04 | 主机 |
| 192.168.52.140 | node05 | 从机 |

```my
CHANGE MASTER 
TO MASTER_HOST = '192.168.52.110', 
MASTER_USER = 'slave', 
MASTER_PASSWORD = '123456', 
MASTER_LOG_FILE='mysql-bin.00001',
MASTER_LOG_POS=154
```

> find / -name 'auto.cnf'

## HAProxy+Keepalived

haproxy是一个开源的，高性能的，负载均衡软件，借助haproxy可以快速，可靠的构建一个负载均衡群集。

用haproxy构建群集的时候，比如后方代理两个http，如果haproxy宕机，后方的http正常运行网站也是瘫痪状态，这就造成了单点故障。

这时keepalived就登场了，keepalived基于vrrp协议，两台主机之间生成一个虚拟的ip，我们称漂移ip，漂移ip主服务器承担，一但主服务器宕机，备份服务器就会抢占漂移ip，继续工作，有效的解决了群集中的单点故障。两者相结合，挺好的。
让haproxy监听keepalived的漂移ip工作，一但haproxy宕机，备份抢占漂移ip继续承担着代理的工作。

## 安全设置

