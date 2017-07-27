使用@ConfigurationProperties自动从properties文件注入到自定义bean类属性中
1、定义Bean类，属性提供getter和setter
2、在properties文件配置属性值
properties文件中的.在bean类中
3、自定义的bean使用例如@ConfigurationProperties(locations = "classpath:mail.properties", prefix = "mail")注入properties文件中的内容
locations：自定义properties文件名，不指定默认为application.properties
prefix:前缀，将自动注入properties配置文件中所有指定前缀开头的配置

属性命名规范
properties配置中除前缀外的后面配置，多个.在bean类定义中会一层层调用属性的geter
properties配置中属性使用-下划线或驼背命名法来匹配bean类属性定义的驼背命名法
例mail.smtp-auth、mail.smtp_auth、mail.smtpAuth在bean类中定义属性为smtpAuth，mail.smtp.auth在bean类中定义类Smtp，在Smtp中再定义属性auth
properties配置中使用[下标]的配置对应bean类中的list



例  mail.properties：  
```
mail.host=localhost
mail.port=25
mail.smtp.auth=false
mail.smtp.starttls-enable=false
mail.from=me@localhost
mail.username=
mail.password=
```

MailConfiguration类  
```
@Configuration  或@Component 
@ConfigurationProperties(locations = "classpath:mail.properties",  prefix = "mail")
public class MailConfiguration { 
  public static class Smtp {
    private boolean auth;
    private boolean starttlsEnable;
    // ... getters and setters
 } 

 @NotBlank private String host; 
 private int port;
 private String from; 
 private String username;
 private String password; 

 @NotNull private Smtp smtp; 
 // ... getters and setters  

 @Bean public JavaMailSender javaMailSender() {
  // omitted for readability
 } 
}
```


更多详细参考[springboot官方文档](http://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#boot-features-external-config-typesafe-configuration-properties )
