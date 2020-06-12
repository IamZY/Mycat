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