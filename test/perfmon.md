## 步骤

* 1、安装插件管理工具（如果未安装）：https://jmeter-plugins.org/wiki/PluginsManager/
	jmeter-plugins-manager-0.18.jar加入%jmeter_home%/lib/ext
	重启->选项->PluginsManager->搜索perfmon->选择perfmon->apply
* 2、下载服务器性能监控插件： https://jmeter-plugins.org/wiki/PerfMon/
	在服务器端运行startAgent.bat（win）或startAgent.sh（linux）
* 3、编写测试模板时
	添加监听器：perfmon metrics colector
	AddRow 添加要监听的内容（CPU/Memory等），host，端口（默认PerfMon端口4444），并可指定Metric parameteer（如actualused，表示实际使用数，等）
	perfmon metrics colector界面，所有数据写入一个文件：指定文件名，运行测试脚本后会将perfmon监听的结果写入该文件（jtl/csv格式）


## 附
```
JMeter 插件管理： https://jmeter-plugins.org/wiki/PluginsManager/

服务器性能监控插件： https://jmeter-plugins.org/wiki/PerfMon/

服务器性能监控 Agent： https://jmeter-plugins.org/wiki/PerfMonAgent/ 以及 https://github.com/undera/perfmon-agent/blob/master/README.md

注意：
使用 PerfMon 插件 jmeter-plugins-perfmon-2.1.jar 时，默认依赖了 jmeter-plugins-cmn-jmeter-0.3.jar。但在运行压力测试时报错 java.lang.NoSuchMethodError: org.apache.jmeter.samplers.SampleSaveConfiguration.setFormatter。
网上找到了这篇帖子： https://stackoverflow.com/questions/46485264/jmeter-throws-java-lang-nosuchmethoderror-org-apache-jmeter-samplers-samplesave
说是要把 jmeter-plugins-cmn-jmeter-0.3.jar 升级到 jmeter-plugins-cmn-jmeter-0.4.jar 。我干脆直接升级到 jmeter-plugins-cmn-jmeter-0.5.jar ，问题解决。
```