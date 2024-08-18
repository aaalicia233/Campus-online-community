# Campus online community project

![IDE](https://img.shields.io/badge/IDE-IntelliJ%20IDEA-brightgreen.svg) ![Java](https://img.shields.io/badge/Java-1.8-blue.svg) ![Database](https://img.shields.io/badge/Database-MySQL-lightgrey.svg)

## Project Overview

XXXThis campus online community not only implements basic features such as registration, login, posting, commenting, replying, and private messaging but also includes a sensitive word filter using a prefix tree; uses Redis for likes and follows; processes system notifications for comments, likes, and follows using Kafka; implements full-text search with Elasticsearch, including keyword highlighting; generates long images and PDFs with wkhtmltopdf; tracks website UV (Unique Visitors) and DAU (Daily Active Users); and deploys the project to a cloud server.。



## TechStack

| Technology            | link                                                         | version           |
| --------------- | ------------------------------------------------------------ | -------------- |
| Spring Boot     | https://spring.io/projects/spring-boot                       | 2.4.3          |
| Spring          | https://spring.io/projects/spring-framework                  | 5.3.4          |
| Spring MVC      | https://docs.spring.io/spring-framework/docs/current/reference/html/web.html#spring-web | 5.3.4          |
| MyBatis         | http://www.mybatis.org/mybatis-3                             | 3.5.1          |
| Redis           | https://redis.io/                                            | 5.0.3          |
| Kafka           | http://kafka.apache.org/                                     | 2.7.0          |
| Elasticsearch   | https://www.elastic.co/cn/elasticsearch/                     | 7.9.3          |
| Spring Security | https://spring.io/projects/spring-security                   | 5.4.5          |
| Spring Quartz   | https://www.baeldung.com/spring-quartz-schedule              | 2.3.2          |
| wkhtmltopdf     | https://wkhtmltopdf.org                                      | 0.12.6         |
| kaptcha         | https://github.com/penggle/kaptcha                           | 2.3.2          |
| Thymeleaf       | https://www.thymeleaf.org/                                   | 3.0.12.RELEASE |
| MySQL           | https://www.mysql.com/                                       | 5.7.17         |
| JDK             | https://www.oracle.com/java/technologies/javase-downloads.html | 1.8            |


## Feature List


- [x] Registration
- [x] Email Sending
- [x] Captcha
- [x] Login
- [x] Password Reset
- [x] Sensitive Word Filtering
- [x] Post Publishing
- [x] My Posts
- [x] Post Details
- [x] Commenting
- [x] Messaging
- [x] Unified Exception Handling
- [x] Unified Logging
- [x] Likes
- [x] Follows
- [x] System Notifications
- [x] Search
- [x] Permission Control
- [x] Pinning, Highlighting, Deleting
- [x] Website Statistics
- [x] Scheduled Task Execution for Hot Post Calculation
- [x] Long Image Generation
- [x] Unit Testing
- [x] Monitoring


## Feature Overview

- Redis is used to implement likes with sets, follows with zsets, store login tickets and captchas to address distributed session issues, count UV (Unique Visitors) with HyperLogLog, and DAU (Daily Active Users) with Bitmaps.
- The Redis Cell module is used to rate limit user posts, preventing spam.
- Kafka handles system notifications for comments, likes, and follows, asynchronously transmits newly published posts to the Elasticsearch server, and builds a powerful asynchronous messaging system using events.
- Elasticsearch provides global search functionality with keyword highlighting.
-The hot post ranking module uses local cache Caffeine as the first-level cache and distributed cache Redis as the second-level cache, constructing a multi-level cache to prevent cache avalanches. Performance was improved 4.1 times (5.5/sec -> 22.5/sec) using a stress testing tool, enhancing website speed.
- Spring Security handles permission control, replacing the interceptor's control, and uses a custom authentication scheme to make permission authentication and control more convenient and flexible.
- Quartz is used to update hot post rankings regularly.

