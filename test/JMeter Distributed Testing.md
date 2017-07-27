1、master和slaver上安装同版本jdk和jmeter，并确保两机处于同一局域网，可相互访问
2、master和slaver上设置好jmeter的环境变量JMETER_HOME、PATH和CLASS_PATH
3、master和slaver上%JMETER_HOME%/bin/jmeter-server文件添加
RMI_HOST_DEF=-Djava.rmi.server.hostname=本机IP
4、master上%JMETER_HOME%/bin/jmeter.bat文件中添加行
set rmi_host=-Djava.rmi.server.hostname=本机IP
set ARGS=%DUMP% %HEAP% %VERBOSE_GC% %GC_ALGO% %DDRAW% %SYSTEM_PROPS% 后面加上%rmi_host%
5、master上%JMETER_HOME%/bin/jmeter.properties文件中添加行
remote_hosts=slaver1 Ip:1099，slaver2 Ip:1099，。。。多台slaver逗号分隔
6、每台slaver上分别启动%JMETER_HOME%/bin/jmeter_server.bat
7、master上运行   运行->远程启动，或 运行->远程启动全部
