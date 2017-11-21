* 启动服务
```bash
redis-server --service-start
```

* 停止服务
```bash
redis-server --service-stop
```

* 安装多个实例
```bash
redis-server --service-install –service-name redisService1 –port 10001
redis-server --service-start –service-name redisService1
redis-server --service-install –service-name redisService2 –port 10002
redis-server --service-start –service-name redisService2
redis-server --service-install –service-name redisService3 –port 10003
redis-server --service-start –service-name redisService3
```

* 卸载
```
redis-server --service-uninstall
```
