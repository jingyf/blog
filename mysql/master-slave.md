#### 配置MySql 复制基本步骤
一、master  
- 启用二进制日志  
 `log-bin = master-bin`  
 `log-bin-index = master-bin.index`  
- 选择一个唯一的server-id  
 `server-id` = {0-(2^32减1)}
- 创建具有赋值权限的用户  
 REPLICATION SLAVE  
 REPLICATION CLIENT  
 `GRANT REPLICATION SLAVE ON *.* TO 'username'@'192.x.x.%' IDENTIFIED BY 'password' ;`  
 `FLUSH PRIVILEGES;`  
二、slave  
- 启用中继日志  
replay-log = replay-log  
replay-log-index = replay-log-index  
- 选择一个唯一的server-id  
 `server-id` = {0-(2^32减1)}  
- 链接到主服务器开始复制数据  
 `mysql> CHANGE MASTER TO MASTER_HOST='',MASTER_PORT='',MASTER_LOG_FILE='',MASTER_LOG_POS='',MASTER_USER='',MASTER_PASSWORD='';`
 `mysql> START SLAVE;`


test
