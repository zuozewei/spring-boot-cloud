#  **Zipkin服务追踪调用链：**

## 应用场景：
    在分布式系统中提供追踪服务调用解决方案
    
    对外暴露的一个接口，可能需要很多个服务协同才能完成这个接口功能，
    如果链路上任何一个服务出现问题或者网络超时，都会形成导致接口调用失败。
    随着业务的不断扩张，服务之间互相调用会越来越复杂。
    
## 操作说明：

1.0 构建zipkin-server
   在spring Cloud为F版本的时候，已经不需要自己构建Zipkin Server了，只需要下载jar即可, 下载地址：https://dl.bintray.com/openzipkin/maven/io/zipkin/java/zipkin-server/
    
   官方提供了一键脚本（Windows下需要安装curl，不过如果你安装了Git客户端，可以直接在Git Bash中使用）
   ```
   curl -sSL https://zipkin.io/quickstart.sh | bash -s
   
   java -jar zipkin.jar
   ```
   如果使用 Docker
   
   ```
   docker run -d -p 9411:9411 openzipkin/zipkin
   ```
   
   访问浏览器 localhost:9411
   
2.0 构建zipkin-client 

    2.1 各微服务只需添加以下依赖：
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-zipkin</artifactId>
        </dependency>
        