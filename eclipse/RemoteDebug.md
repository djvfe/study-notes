# 本地使用eclipse远程调试服务器代码

## 1、服务器启动时增加参数 -Xdebug -Xnoagent -Djava.compiler=NONE -Xrunjdwp:transport=dt_socket,address=host:port,suspend=n,server=y
* 确保端口是开放的
* java -jar -Xdebug -Xnoagent -Djava.compiler=NONE -Xrunjdwp:transport=dt_socket,address=192.168.0.197:20406,suspend=n,server=y server.jar  %* 
* suspend=y 服务器端启动会hold，直到客户端eclipse的debug跳过才会继续启动，suspend=n，启动不会hold

## 2、本地eclipse  Run -> Dedug configurations -> Remote Java Application -> 设置Host、Port、project，Host和port和第一步服务器参数的一致 -> Debug run
