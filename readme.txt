
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



数据库安装
centos6.5机器
使用yum安装方式
（yum源可以使用163源）
yum install mysql-server

第一次登入
service mysqld start
service mysqld status

chkconfig mysqld on


## 版本规定
tomcat 版本
tomcat7

jdk版本
1.7

## 常见错误

1.class not found spring
	描述：虽然maven包里面有这个class文件，但是tomcat加载的时候没有发现，是因为手动配置
	eclipse 
	Deployment assembly
	--> Maven Dependencies , web-info/lib

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

5	连接数据库错误二
	不小心用匿名用户登入
	查看当前用户
	select user()
	select current_user()
	select user,host from mysql.user;
	解决方式删除匿名用户
	delete from mysql.user where host=''
	flush privileges;