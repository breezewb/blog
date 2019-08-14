---
title: spring-boot-jpa中的getOne和findById
date: 2019-08-14 15:44:20
categories:
- [Java, Jpa]
tags:
- Java
- Jpa
---

- getOne()方法返回的是实体对象的代理对象
- findById()方法返回的是一个Optional<T>，在Optional类中有个get()方法，返回的是当前对象/值

getOne()方法有一个坑，如果改变了代理对象的属性，就算没有执行save()方法也会自动给你更新到数据库，而且在json序列化的时候也可能出现一些问题

所以应该尽量使用findById()来查询