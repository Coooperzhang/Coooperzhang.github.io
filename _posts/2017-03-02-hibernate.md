---
layout: post
title:  "Hibernate框架"
date:   2017-03-02 15:06:05
categories: Java

---

* content
{:toc}

hibernate框架主要是实现数据库与实体类间的映射，使得操作实体类相当与操作hibernate框架。
---

## 使用

1)环境配置，导入jar包

![hibernate_jar]({{ "\css\pics\hibernate_jar.png"}})

2)创建javabean对象（以User为例）

对象的属性一般与对应表中的字段一致，需要提供每个属性的set、get方法，用工具生成就行了，不用工具生成的话，一定要注意命名规范，属性的名称首字母大写后在前面加set或get字段

3)配置hibernate.cfg.xml文件

配置一个关联与特定数据库全局的工厂<SessionFactory>如果要使用多个数据库，就多配置一个<SessionFactory>标签，标签中制定连接数据库的信息。
我们需要把配置文件存在在项目的src下面，Hibernate启动时会自动到classpath根目录下面查找名为hibernate.cfg.xml文件，所以配置文件的名称不要更改。

	<span style="font-size:18px;"><?xmlversionxmlversion="1.0" encoding="UTF-8"?>  
	<!DOCTYPEhibernate-configuration PUBLIC  
	"-//Hibernate/HibernateConfiguration DTD 3.0//EN"  
	"http://hibernate.sourceforge.net/hibernate-configuration-3.0.dtd">  
	   
	<hibernate-configuration>  
	   <session-factory>  
		 <!--配置连接数据库信息 -->  
		 <propertynamepropertyname="hibernate.connection.url">jdbc:mysql://localhost:3306/egov</property>  
		 <propertynamepropertyname="hibernate.connection.driver_class">com.mysql.jdbc.Driver</property>  
		 <propertynamepropertyname="hibernate.connection.username">egov</property>  
		 <propertynamepropertyname="hibernate.connection.password">egov</property>  
		
		 <propertynamepropertyname="show_sql">true</property>  
		 <propertynamepropertyname="hibernate.format_sql">true</property>  
		 <propertynamepropertyname="hibernate.dialect">org.hibernate.dialect.MySQLDialect</property>  
		 <!--实体类的路径-->  
		 <mappingresourcemappingresource="com/hibernate/pojo/User.hbm.xml"/>  
	   
	   </session-factory>  
	</hibernate-configuration></span>  
	
4)配置映射文件

 映射文件是和javabean对象对应的，一般以对象的名称加.xml文件命名，映射文件的作用就是要告诉Hibernate应该访问数据库的哪个表以及表中的哪个对象。
 在hibernate-mapping标签（tag）之间,含有一个class元素。所有的持久化实体类（再次声明，或许接下来会有依赖类，就是那些次要的实体）都需要一个这样的映射，来把类对象映射到SQL数据库里的表。
 
## 关系映射

hibernate中关系映射指的是实体类与实体类间的关系。和数据库中表与表之间的关系类似，有一对一，多对一，一对多，多对多四种映射关系。