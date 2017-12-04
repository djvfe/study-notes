# springboot 设置https
## 生成证书文件
```
keytool 
-genkey 
-alias tomcat //别名
-keypass 123456 
-keyalg RSA //算法
-keysize 1024 
-validity 365 
-keystore D:\ssl-key.p12 //证书文件地址
-storetype PKCS12 //类型，不指定默认JKS
-storepass 123456
```

## 在application.properties中配置HTTPS
```
server.port=8443
server.ssl.key-store=D:/ssl-key.p12
server.ssl.key-store-password=123456
server.ssl.keyStoreType=PKCS12
server.ssl.keyAlias=tomcat
```
