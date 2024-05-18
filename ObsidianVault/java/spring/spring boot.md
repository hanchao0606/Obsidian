# 优点
##  使用 JavaConfig 有助于避免使用 XML
##  避免大量的 Maven 导入和各种版本冲突
## 通过提供默认值快速开始开发
## 没有单独的 Web 服务器需要。这意味着你不再需要启动 Tomcat，Glassfish 或其他任何东西
## 需要更少的配置 因为没有 web.xml 文件。只需添加用@ Configuration 注释的类，然后添加用@Bean 注释的方法，Spring 将自动加载对象并像以前一样对其进行管理。您甚至可以将@Autowired 添加到 bean 方法中，以使 Spring 自动装入需要的依赖关系中。 基于环境的配置 使用这些属性，您可以将您正在使用的环境传递到应用程序：-Dspring.profiles.active = {enviornment}。在加载主应用程序属性文件后，Spring 将在（application{environment} .properties）中加载后续的应用程序属性文件。
# 如何重新加载 Spring Boot 上的更改，而无需重新启动服务器？
##  这可以使用 DEV 工具来实现。通过这种依赖关系，您可以节省任何更改，嵌入式 tomcat 将重新启动。Spring Boot 有一个开发工具（DevTools）模块，它有助于提高开发人员的生 产力。Java 开发人员面临的一个主要挑战是将文件更改自动部署到服务器并自动重启服务 器。开发人员可以重新加载 Spring Boot 上的更改，而无需重新启动服务器。这将消除每次 手动部署更改的需要。Spring Boot 在发布它的第一个版本时没有这个功能。这是开发人员 最需要的功能。DevTools 模块完全满足开发人员的需求。该模块将在生产环境中被禁用。 它还提供 H2 数据库控制台以更好地测试应用程序。  org.springframework.boot spring-boot-devtools true

# Spring Boot 中的监视器是什么？
## Spring boot actuator 是 spring 启动框架中的重要功能之一。Spring boot 监视器可帮助您访 问生产环境中正在运行的应用程序的当前状态。有几个指标必须在生产环境中进行检查和 监控。即使一些外部应用程序可能正在使用这些服务来向相关人员触发警报消息。监视器 模块公开了一组可直接作为 HTTP URL 访问的 REST 端点来检查状态

# 什么是 Swagger？你用 Spring Boot 实现了它吗？
## Swagger 广泛用于可视化 API，使用 Swagger UI 为前端开发人员提供在线沙箱。Swagger 是  用于生成 RESTful Web 服务的可视化表示的工具，规范和完整框架实现。它使文档能够以 与服务器相同的速度更新。当通过 Swagger 正确定义时，消费者可以使用最少量的实现逻 辑来理解远程服务并与其进行交互。因此，Swagger 消除了调用服务时的猜测。
# 什么是 Spring Profiles？
### Spring Profiles 允许用户根据配置文件（dev，test，prod 等）来注册 bean。因此，当应用 程序在开发中运行时，只有某些 bean 可以加载，而在 PRODUCTION 中，某些其他 bean 可 以加载。假设我们的要求是 Swagger 文档仅适用于 QA 环境，并且禁用所有其他文档。这 可以使用配置文件来完成。Spring Boot 使得使用配置文件非常简单。
# 什么是 Spring Batch？
## 	Spring Boot Batch 提供可重用的函数，这些函数在处理大量记录时非常重要，包括日志/跟踪，事务管理，作业处理统计信息，作业重新启动，跳过和资源管理。它还提供了更先进的技术服务和功能，通过优化和分区技术，可以实现极高批量和高性能批处理作业。简单以及复杂的大批量批处理作业可以高度可扩展的方式利用框架处理重要大量的信息。