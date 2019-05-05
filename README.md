#### plugin usage scene
帮助我们去自动生成错误码和错误信息的映射

#### plugin usage step
1.引入插件并且配置:
```xml
  <properties>
    <!--消息头信息-->
    <bundle.codeHead>SG2018</bundle.codeHead>

    <!--生成消息文件路径-->
    <bundle.targetClass>com.shiguang.bundle.MessageCode</bundle.targetClass>
  </properties>
  
  <plugin>
    <groupId>com.github.open.maven.plugin</groupId>
    <artifactId>bundle-maven-plugin</artifactId>
    <version>1.0-SNAPSHOT</version>
    <configuration>
      <codeHead>${bundle.codeHead}</codeHead>
      <targetClass>${bundle.targetClass}</targetClass>
      <bundleFile>./src/main/resources/bundle/message.properties</bundleFile>
      <!--<templateFile>./src/main/resources/bundle/template.properties</templateFile>-->
    </configuration>

    <executions>
      <execution>
        <goals>
          <goal>bundle</goal>
        </goals>
        <phase>install</phase>
      </execution>
    </executions>
  </plugin>
```
2.使用
```java
    @Autowired
    private MessageSourceAccessor msa;

    MessageCode.SG2018000000 // code
    msa.getMessage(MessageCode.SG2018000000); // message
```
