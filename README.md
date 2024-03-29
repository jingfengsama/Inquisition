# Inquisition 审判庭
明日方舟速通云控后端

## API文档

部署后[访问](http://127.0.0.1:2000/swagger-ui/index.htm)

## TODO

- [x] 心跳协议
- [x] Task拉取
- [x] ~~多设备管理~~ 负载均衡
- [x] Admin管理
- [x] 日志
- [ ] 前端实现 --> 当前开发
- [ ] 截图获取
- [ ] User管理
- [ ] 通知

## 低优先度TODO
- [ ] CDK

## 业务流程

### 设备部署

1. [deviceToken申请](http://127.0.0.1:2000/swagger-ui/index.html#/%E8%AE%BE%E5%A4%87%E6%8E%A5%E5%8F%A3/addDevice)
2. 终端deviceToken部署

#### 终端业务流程

1. [心跳](http://127.0.0.1:2000/swagger-ui/index.html#/%E5%BF%83%E8%B7%B3%E6%8E%A5%E5%8F%A3/postHeartBeat)
2. [获取任务](http://127.0.0.1:2000/swagger-ui/index.html#/%E4%BB%BB%E5%8A%A1%E6%8E%A5%E5%8F%A3/getTask)
3. [任务完成上报](http://127.0.0.1:2000/swagger-ui/index.html#/%E4%BB%BB%E5%8A%A1%E6%8E%A5%E5%8F%A3/completeTask)
4. [任务失败上报](http://127.0.0.1:2000/swagger-ui/index.html#/%E4%BB%BB%E5%8A%A1%E6%8E%A5%E5%8F%A3/failTask)
5. [手动日志上报](http://127.0.0.1:2000/swagger-ui/index.html#/%E6%97%A5%E5%BF%97%E6%8E%A5%E5%8F%A3/addLog) （已由后端处理部分任务日志）

### 后端部署

```yaml
# yaml配置

# 启动端口
server:
  port: 2000
  
# 数据库连接配置 Mysql 8+
spring:
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://127.0.0.1:3306/arklights?characterEncoding=UTF-8
    username: root
    password: 123456
    
# 每日任务刷新cron表达式
cron: '0 0 4,12,20 * * ?'
```

