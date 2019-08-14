---
title: mysql-connector-java-8.0版本后时间错误的解决方法(保存日期相差13或14小时)
date: 2019-08-14 14:25:17
categories:
- [Java]
- [MySQL]
tags:
- Java
- MySQL
---

# 问题

​		在使用SpringBoot+JPA的项目中，发现查询出来的时间比实际时间快了13个小时，刚开始以为是数据库时区问题，但之前其他的项目未出现这个问题，检查数据库时区设置也没有问题，所以排除数据库的问题

​		检查代码发现代码用的时间是系统时间，而系统时间并没有问题，实际运行时打印出来的时间也没有问题，郁闷了很久

<!--more-->

# 解决

最终的解决方法参考了一位同样遇到此问题的文章，[SpringBoot2 jpa mysql保存日期相差13或14小时](<https://www.jianshu.com/p/0a3e6c91b675>)

查看mysql时区：

```
show variables like "%time_zone%";
```

显示安装后的默认时区是**CST**，而CST简写的时区有以下几个：

> 美国中部时间：Central Standard Time (USA) UT-6:00
> 澳大利亚中部时间：Central Standard Time (Australia) UT+9:30
> 中国标准时间：China Standard Time UT+8:00
> 古巴标准时间：Cuba Standard Time UT-4:00

而美国从“3月11日”至“11月7日”实行夏令时，美国中部时间改为 UTC-05:00

之所以会出现时间相差13个小时是因为Timestamp被转换为会话时区的时间字符串了

1. JDBC 误认为会话时区在 CST-5
2. JBDC 把 Timestamp+0 转为 CST-5 的 String-5
3. MySQL 认为会话时区在 CST+8，将 String-5 转为 Timestamp-13

最终结果相差 13 个小时！如果处在冬令时还会相差 14 个小时！



因为之前的项目使用的mysql驱动都是8.0之前的版本，没有出现这一问题，而8.0之后的版本会影响读取到的时区值，出现问题的项目用的是SpringBoot-2.1.3，自带的mysql驱动是8.0之后的版本



解决方法有以下三种：

1. 在数据库连接url后添加参数 &serverTimezone=Asia/Shanghai 即可。
2. 修改数据库时区

```
 show variables like "%time_zone%";
 set global time_zone = '+8:00';
 flush privileges; #立即生效
```

3. 永久修改数据库时区

```
# vim /etc/my.cnf ##在[mysqld]区域中加上
default-time_zone = '+8:00'
# /etc/init.d/mysqld restart ##重启mysql使新时区生效
```