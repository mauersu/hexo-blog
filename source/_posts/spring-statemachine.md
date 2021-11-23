---
title: Spring statemachine简介
date: 2021-11-22 21:33:10
tags:
 - spring-statemachine
categories: spring
---
# spring状态机简介
> 本文以spring-statemachine 3.0.1版本为基础讲解
### 1.spring状态机基本概念
[词汇](https://docs.spring.io/spring-statemachine/docs/3.0.1/reference/#glossary)
[快速教程](https://docs.spring.io/spring-statemachine/docs/3.0.1/reference/#glossary)
###### State
> 一种状态为一种情况建模，在此期间，某些不变条件保持不变。状态是状态机的主要实体，其中状态更改由事件驱动。
###### Event
> 发送到状态机然后驱动各种状态更改的实体。
###### Transition
> 转换是源状态和目标状态之间的关系。它可能是复合转换的一部分，将状态机从一种状态配置转换为另一种状态配置，表示状态机对特定类型事件发生的完整响应。
###### Initial State
> 状态机启动的一种特殊状态。初始状态总是绑定到特定的状态机或区域。具有多个区域的状态机可能具有多个初始状态。

### 2.以订单为例的一个demo例子

[springboot-demo中的spring-statemachine例子](https://github.com/mauersu/springboot-demo)


### 3.FAQ
1. 如何判断event是否执行成功？或者订单状态是否变更成功？
> 答：sendEvent方法返回参数可以判定event是否执行，true代表订单状态变更成功，反之则不成功。

### 4.参考资料
1. [Spring Statemachine - Reference Documentation](https://docs.spring.io/spring-statemachine/docs/3.0.1/reference/#statemachine-getting-started)
2. [spring statemachine的企业可用级开发指南](https://my.oschina.net/u/173343/blog/3043965)
3. [spring statemachine教程源码](https://gitee.com/wphmoon/statemachine)