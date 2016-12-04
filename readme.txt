
## 项目所使用到的框架
	后端
		mybatis
		spring
		struts

	前段
		dwz

##必要参数
	数据库edu_demo

	连接方式
	用户名root
	密码：wusc.321

##环境安装

- 数据库安装
	centos6.5机器
	使用yum安装方式
	（yum源可以使用163源）
	yum install -y mysql-server

	第一次登入
	service mysqld start
	service mysqld status

	chkconfig mysqld on

	查看下面如何解决ERROR 1045 以及 ERROR 1142
	查看下面如何删除匿名用户

	创建表结构

	导入insert


## 项目源码导入
由于整个项目使用maven管理，项目在eclipse的搭建非常容易
下载eclise j2ee版本
下载jdk版本1.7
下载tomcat7
下载 maven

Preferences-->Maven-->Installations ,add ,指向C:\Download\apache-maven-3.3.9
Preferences-->Maven-->User Settings，第二行User Settings 指向C:\Download\apache-maven-3.3.9\conf\settings.xml

Preferences-->java-->Installed JREs,add 指向C:\Program Files\Java\jdk1.7.0_79,且勾选上刚刚指定的jdk

Windows-->show view->other->Server
点击No servers are available.
选择Tomcat v7.0 server
指向C:\Download\apache-tomcat-7.0.73-windows-x64\apache-tomcat-7.0.73
把项目添加到tomcat内


修改jdbc.properties
jdbc.url指向你的mysql IP地址

启动tomcat

访问http://localhost:8080/edu-demo/

## 常见错误
### 项目导入见错误

0. 解决 ERROR 1045 以及 ERROR 1142
	错误详细描述
	 ERROR 1045 (28000): Access denied for user ''@'localhost' (using password: NO)
	 ERROR 1142 (42000): SELECT command denied to user ''@'localhost' for table 'user'

	 解决步骤：
		service mysqld stop
		mysqld_safe --user=mysql --skip-grant-tables --skip-networking & 
		mysql -u root mysql
		use mysql;
		show tables;
		select user,host from mysql.user;
		delete from mysql.user where user='';　 ← 删除匿名用户 

		service mysqld stop
		service mysqld start
		mysql -u root -p
		select current_user()

		grant all privileges on *.* to 'root'@'%' identified by 'wusc.321' with grant option;
		flush privileges;
		show grants for 'root'@'%';




1.class not found spring
	描述：虽然maven包里面有这个class文件，但是tomcat加载的时候没有发现，是因为手动配置
	eclipse 
	Deployment assembly
	--> Maven Dependencies , web-info/lib

	
### 常数据库见错误
2.初始化脚本里不要有中文，否则容易出错

	insert into edu_edmo_pms_user (id, user_no, user_pwd, remark, user_name, mobile_no, status, user_type, last_login_time, is_changed_pwd, pwd_error_count, pwd_error_time) values 
	(1, 'admin', '7c4a8d09ca3762af61e59520943dc26494f8941b', 'super admin', 'super admin', '13800138000', '100', '1', null, 0, 0, null);

	
	

3.mysql时间值设置
	类型为 timestamp
	default值 default CURRENT_TIMESTAMP

	例如
	create_time          timestamp not null default CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP comment '创建时间',

4. 连接数据库错误
	检查user表
	use mysql；
	select * from user；

	配置用户权限
	select user,host from mysql.user;
	grant all privileges on *.* to 'root'@'%' identified by 'wusc.321' with grant option;
	flush privileges;
	show grants for 'root'@'%';

注意这里
	'root'@'%' 表示root用户可以从任何机器连到mysql
	identified by 'wusc.321' 表示设置root的密码为 wusc.321

5	数据库错误之二,
	虽然使用mysql -u root -p, 但是变成 匿名用户登入
	
	查看当前用户
	select user()
	select current_user()
	select user,host from mysql.user;
	解决方式删除匿名用户
	delete from mysql.user where host=''
	flush privileges;
	
6. 关于数据库权限操作的例子
http://www.cnblogs.com/candle806/p/4048651.html
http://www.cnblogs.com/fslnet/p/3143344.html


7.删除匿名用户 
 delete from mysql.user where user='';　 ← 删除匿名用户 
 
 
 8.连接MySQL数据库时常见故障问题的分析与解决
 http://blog.csdn.net/lioncode/article/details/7917310

 



