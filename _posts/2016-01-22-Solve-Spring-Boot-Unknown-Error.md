---
layout: post
title: Solve Spring Boot Unknown Error
tags:
- Spring Boot
- Java

---
I was working on a short Spring Boot project. However, on my computer, no matter what I tried, it couldn't start and gave me "unknown error". The following is the error log:

```
Wrong Spring Boot output:

4:01:54 PM: Executing external task 'bootRun'...
:compileJava UP-TO-DATE
:processResources UP-TO-DATE
:classes UP-TO-DATE
:findMainClass
:bootRun

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::  (v1.1.2.BUILD-SNAPSHOT)

2015-11-03 16:01:55.386  INFO 5295 --- [           main] com.proj.projApplication             : Starting projApplication on Qingxiangs-MacBook-Pro-proj.local with PID 5295 (/Users/lee/workspace/springboot_gradle_project/build/classes/main started by lee in /Users/lee/workspace/springboot_gradle_project)
2015-11-03 16:01:55.412  INFO 5295 --- [           main] ationConfigEmbeddedWebApplicationContext : Refreshing org.springframework.boot.context.embedded.AnnotationConfigEmbeddedWebApplicationContext@276438c9: startup date [Tue Nov 03 16:01:55 EST 2015]; root of context hierarchy
2015-11-03 16:01:56.052  INFO 5295 --- [           main] .t.TomcatEmbeddedServletContainerFactory : Server initialized with port: 8080
2015-11-03 16:01:56.191  INFO 5295 --- [           main] o.apache.catalina.core.StandardService   : Starting service Tomcat
2015-11-03 16:01:56.191  INFO 5295 --- [           main] org.apache.catalina.core.StandardEngine  : Starting Servlet Engine: Apache Tomcat/7.0.54
2015-11-03 16:01:56.466  INFO 5295 --- [ost-startStop-1] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring embedded WebApplicationContext
2015-11-03 16:01:56.467  INFO 5295 --- [ost-startStop-1] o.s.web.context.ContextLoader            : Root WebApplicationContext: initialization completed in 1057 ms
2015-11-03 16:01:56.535  INFO 5295 --- [ost-startStop-1] o.s.b.c.e.ServletRegistrationBean        : Mapping servlet: 'dispatcherServlet' to [/]
2015-11-03 16:01:58.739 ERROR 5295 --- [           main] o.a.coyote.http11.Http11NioProtocol      : Failed to stop end point associated with ProtocolHandler ["http-nio-8080"]

java.io.IOException: Unknown error: 316
  at sun.nio.ch.NativeThread.signal(Native Method)
  at sun.nio.ch.ServerSocketChannelImpl.implCloseSelectableChannel(ServerSocketChannelImpl.java:292)
  at java.nio.channels.spi.AbstractSelectableChannel.implCloseChannel(AbstractSelectableChannel.java:234)
  at java.nio.channels.spi.AbstractInterruptibleChannel.close(AbstractInterruptibleChannel.java:115)
  at sun.nio.ch.ServerSocketAdaptor.close(ServerSocketAdaptor.java:137)
  at org.apache.tomcat.util.net.NioEndpoint.unbind(NioEndpoint.java:599)
  at org.apache.tomcat.util.net.AbstractEndpoint.stop(AbstractEndpoint.java:698)
  at org.apache.coyote.AbstractProtocol.stop(AbstractProtocol.java:493)
  at org.springframework.boot.context.embedded.tomcat.TomcatEmbeddedServletContainer.initialize(TomcatEmbeddedServletContainer.java:95)
  at org.springframework.boot.context.embedded.tomcat.TomcatEmbeddedServletContainer.<init>(TomcatEmbeddedServletContainer.java:69)
  at org.springframework.boot.context.embedded.tomcat.TomcatEmbeddedServletContainerFactory.getTomcatEmbeddedServletContainer(TomcatEmbeddedServletContainerFactory.java:289)
  at org.springframework.boot.context.embedded.tomcat.TomcatEmbeddedServletContainerFactory.getEmbeddedServletContainer(TomcatEmbeddedServletContainerFactory.java:146)
  at org.springframework.boot.context.embedded.EmbeddedWebApplicationContext.createEmbeddedServletContainer(EmbeddedWebApplicationContext.java:159)
  at org.springframework.boot.context.embedded.EmbeddedWebApplicationContext.onRefresh(EmbeddedWebApplicationContext.java:132)
  at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:476)
  at org.springframework.boot.context.embedded.EmbeddedWebApplicationContext.refresh(EmbeddedWebApplicationContext.java:120)
  at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:683)
  at org.springframework.boot.SpringApplication.run(SpringApplication.java:313)
  at org.springframework.boot.SpringApplication.run(SpringApplication.java:944)
  at org.springframework.boot.SpringApplication.run(SpringApplication.java:933)
  at com.proj.projApplication.main(projApplication.java:14)

2015-11-03 16:01:58.739 ERROR 5295 --- [           main] s.b.c.e.t.TomcatEmbeddedServletContainer : Cannot pause connector: 

java.io.IOException: Unknown error: 316
  at sun.nio.ch.NativeThread.signal(Native Method)
  at sun.nio.ch.ServerSocketChannelImpl.implCloseSelectableChannel(ServerSocketChannelImpl.java:292)
  at java.nio.channels.spi.AbstractSelectableChannel.implCloseChannel(AbstractSelectableChannel.java:234)
  at java.nio.channels.spi.AbstractInterruptibleChannel.close(AbstractInterruptibleChannel.java:115)
  at sun.nio.ch.ServerSocketAdaptor.close(ServerSocketAdaptor.java:137)
  at org.apache.tomcat.util.net.NioEndpoint.unbind(NioEndpoint.java:599)
  at org.apache.tomcat.util.net.AbstractEndpoint.stop(AbstractEndpoint.java:698)
  at org.apache.coyote.AbstractProtocol.stop(AbstractProtocol.java:493)
  at org.springframework.boot.context.embedded.tomcat.TomcatEmbeddedServletContainer.initialize(TomcatEmbeddedServletContainer.java:95)
  at org.springframework.boot.context.embedded.tomcat.TomcatEmbeddedServletContainer.<init>(TomcatEmbeddedServletContainer.java:69)
  at org.springframework.boot.context.embedded.tomcat.TomcatEmbeddedServletContainerFactory.getTomcatEmbeddedServletContainer(TomcatEmbeddedServletContainerFactory.java:289)
  at org.springframework.boot.context.embedded.tomcat.TomcatEmbeddedServletContainerFactory.getEmbeddedServletContainer(TomcatEmbeddedServletContainerFactory.java:146)
  at org.springframework.boot.context.embedded.EmbeddedWebApplicationContext.createEmbeddedServletContainer(EmbeddedWebApplicationContext.java:159)
  at org.springframework.boot.context.embedded.EmbeddedWebApplicationContext.onRefresh(EmbeddedWebApplicationContext.java:132)
  at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:476)
  at org.springframework.boot.context.embedded.EmbeddedWebApplicationContext.refresh(EmbeddedWebApplicationContext.java:120)
  at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:683)
  at org.springframework.boot.SpringApplication.run(SpringApplication.java:313)
  at org.springframework.boot.SpringApplication.run(SpringApplication.java:944)
  at org.springframework.boot.SpringApplication.run(SpringApplication.java:933)
  at com.proj.projApplication.main(projApplication.java:14)

2015-11-03 16:01:58.899  INFO 5295 --- [           main] s.w.s.m.m.a.RequestMappingHandlerMapping : Mapped "{[/hello],methods=[GET],params=[],headers=[],consumes=[],produces=[],custom=[]}" onto public org.springframework.web.servlet.ModelAndView com.proj.controller.HelloWorldController.hello()
2015-11-03 16:01:58.904  INFO 5295 --- [           main] s.w.s.m.m.a.RequestMappingHandlerMapping : Mapped "{[/error],methods=[],params=[],headers=[],consumes=[],produces=[],custom=[]}" onto public org.springframework.http.ResponseEntity<java.util.Map<java.lang.String, java.lang.Object>> org.springframework.boot.autoconfigure.web.BasicErrorController.error(javax.servlet.http.HttpServletRequest)
2015-11-03 16:01:58.904  INFO 5295 --- [           main] s.w.s.m.m.a.RequestMappingHandlerMapping : Mapped "{[/error],methods=[],params=[],headers=[],consumes=[],produces=[text/html],custom=[]}" onto public org.springframework.web.servlet.ModelAndView org.springframework.boot.autoconfigure.web.BasicErrorController.errorHtml(javax.servlet.http.HttpServletRequest)
2015-11-03 16:01:58.918  INFO 5295 --- [           main] o.s.w.s.handler.SimpleUrlHandlerMapping  : Mapped URL path [/**] onto handler of type [class org.springframework.web.servlet.resource.DefaultServletHttpRequestHandler]
2015-11-03 16:01:59.187  INFO 5295 --- [           main] o.s.j.e.a.AnnotationMBeanExporter        : Registering beans for JMX exposure on startup
2015-11-03 16:01:59.246  INFO 5295 --- [           main] s.b.c.e.t.TomcatEmbeddedServletContainer : Tomcat started on port(s): 8080/http
2015-11-03 16:01:59.246 ERROR 5295 --- [8080-Acceptor-0] org.apache.tomcat.util.net.NioEndpoint   : Socket accept failed

java.nio.channels.ClosedChannelException: null
  at sun.nio.ch.ServerSocketChannelImpl.accept(ServerSocketChannelImpl.java:235)
  at org.apache.tomcat.util.net.NioEndpoint$Acceptor.run(NioEndpoint.java:793)
  at java.lang.Thread.run(Thread.java:745)

2015-11-03 16:01:59.248  INFO 5295 --- [           main] com.proj.projApplication             : Started projApplication in 4.127 seconds (JVM running for 4.409)
2015-11-03 16:01:59.302 ERROR 5295 --- [8080-Acceptor-0] org.apache.tomcat.util.net.NioEndpoint   : Socket accept failed

java.nio.channels.ClosedChannelException: null
  at sun.nio.ch.ServerSocketChannelImpl.accept(ServerSocketChannelImpl.java:235)
  at org.apache.tomcat.util.net.NioEndpoint$Acceptor.run(NioEndpoint.java:793)
  at java.lang.Thread.run(Thread.java:745)

2015-11-03 16:01:59.406 ERROR 5295 --- [8080-Acceptor-0] org.apache.tomcat.util.net.NioEndpoint   : Socket accept failed

java.nio.channels.ClosedChannelException: null
  at sun.nio.ch.ServerSocketChannelImpl.accept(ServerSocketChannelImpl.java:235)
  at org.apache.tomcat.util.net.NioEndpoint$Acceptor.run(NioEndpoint.java:793)
  at java.lang.Thread.run(Thread.java:745)

2015-11-03 16:01:59.611 ERROR 5295 --- [8080-Acceptor-0] org.apache.tomcat.util.net.NioEndpoint   : Socket accept failed

java.nio.channels.ClosedChannelException: null
  at sun.nio.ch.ServerSocketChannelImpl.accept(ServerSocketChannelImpl.java:235)
  at org.apache.tomcat.util.net.NioEndpoint$Acceptor.run(NioEndpoint.java:793)
  at java.lang.Thread.run(Thread.java:745)

2015-11-03 16:02:00.014 ERROR 5295 --- [8080-Acceptor-0] org.apache.tomcat.util.net.NioEndpoint   : Socket accept failed

java.nio.channels.ClosedChannelException: null
  at sun.nio.ch.ServerSocketChannelImpl.accept(ServerSocketChannelImpl.java:235)
  at org.apache.tomcat.util.net.NioEndpoint$Acceptor.run(NioEndpoint.java:793)
  at java.lang.Thread.run(Thread.java:745)

2015-11-03 16:02:00.820 ERROR 5295 --- [8080-Acceptor-0] org.apache.tomcat.util.net.NioEndpoint   : Socket accept failed

java.nio.channels.ClosedChannelException: null
  at sun.nio.ch.ServerSocketChannelImpl.accept(ServerSocketChannelImpl.java:235)
  at org.apache.tomcat.util.net.NioEndpoint$Acceptor.run(NioEndpoint.java:793)
  at java.lang.Thread.run(Thread.java:745)

2015-11-03 16:02:02.425 ERROR 5295 --- [8080-Acceptor-0] org.apache.tomcat.util.net.NioEndpoint   : Socket accept failed

java.nio.channels.ClosedChannelException: null
  at sun.nio.ch.ServerSocketChannelImpl.accept(ServerSocketChannelImpl.java:235)
  at org.apache.tomcat.util.net.NioEndpoint$Acceptor.run(NioEndpoint.java:793)
  at java.lang.Thread.run(Thread.java:745)

2015-11-03 16:02:04.030 ERROR 5295 --- [8080-Acceptor-0] org.apache.tomcat.util.net.NioEndpoint   : Socket accept failed

java.nio.channels.ClosedChannelException: null
  at sun.nio.ch.ServerSocketChannelImpl.accept(ServerSocketChannelImpl.java:235)
  at org.apache.tomcat.util.net.NioEndpoint$Acceptor.run(NioEndpoint.java:793)
  at java.lang.Thread.run(Thread.java:745)

2015-11-03 16:02:05.632 ERROR 5295 --- [8080-Acceptor-0] org.apache.tomcat.util.net.NioEndpoint   : Socket accept failed

java.nio.channels.ClosedChannelException: null
  at sun.nio.ch.ServerSocketChannelImpl.accept(ServerSocketChannelImpl.java:235)
  at org.apache.tomcat.util.net.NioEndpoint$Acceptor.run(NioEndpoint.java:793)
  at java.lang.Thread.run(Thread.java:745)

2015-11-03 16:02:07.237 ERROR 5295 --- [8080-Acceptor-0] org.apache.tomcat.util.net.NioEndpoint   : Socket accept failed

java.nio.channels.ClosedChannelException: null
  at sun.nio.ch.ServerSocketChannelImpl.accept(ServerSocketChannelImpl.java:235)
  at org.apache.tomcat.util.net.NioEndpoint$Acceptor.run(NioEndpoint.java:793)
  at java.lang.Thread.run(Thread.java:745)

2015-11-03 16:02:08.841 ERROR 5295 --- [8080-Acceptor-0] org.apache.tomcat.util.net.NioEndpoint   : Socket accept failed

java.nio.channels.ClosedChannelException: null
  at sun.nio.ch.ServerSocketChannelImpl.accept(ServerSocketChannelImpl.java:235)
  at org.apache.tomcat.util.net.NioEndpoint$Acceptor.run(NioEndpoint.java:793)
  at java.lang.Thread.run(Thread.java:745)

Could not execute build using Gradle installation '/Users/lee/gradle-2.8'.
4:02:09 PM: External task execution finished 'bootRun'.
```

It looks like the 8080 port is somehow taken. But I don't remember any program using 8080. So, I ran lsof to see if there is any. lsof didn't find any thing using 8080. This is getting weird. I knew it probably wouldn't help but I still ran a port scan on 8080. I found a mysterious application using 8080. Soon, I found [an article](http://apple.stackexchange.com/questions/66158/unkown-process-listening-at-port-8080) describing the same problem.

It turns out I have Cisco VPN client installed (to access my company network). It does some kernel hack, so lsof doesn't tell. After I removed the software, the problem was solved.