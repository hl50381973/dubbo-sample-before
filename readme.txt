
## ��Ŀ��ʹ�õ��Ŀ��
	���
		mybatis
		spring
		struts

	ǰ��
		dwz

##��Ҫ����
	���ݿ�edu_demo

	���ӷ�ʽ
	�û���root
	���룺wusc.321

##������װ

- ���ݿⰲװ
	centos6.5����
	ʹ��yum��װ��ʽ
	��yumԴ����ʹ��163Դ��
	yum install -y mysql-server

	��һ�ε���
	service mysqld start
	service mysqld status

	chkconfig mysqld on

	�鿴������ν��ERROR 1045 �Լ� ERROR 1142
	�鿴�������ɾ�������û�

	������ṹ

	����insert


## ��ĿԴ�뵼��
����������Ŀʹ��maven������Ŀ��eclipse�Ĵ�ǳ�����
����eclise j2ee�汾
����jdk�汾1.7
����tomcat7
���� maven

Preferences-->Maven-->Installations ,add ,ָ��C:\Download\apache-maven-3.3.9
Preferences-->Maven-->User Settings���ڶ���User Settings ָ��C:\Download\apache-maven-3.3.9\conf\settings.xml

Preferences-->java-->Installed JREs,add ָ��C:\Program Files\Java\jdk1.7.0_79,�ҹ�ѡ�ϸո�ָ����jdk

Windows-->show view->other->Server
���No servers are available.
ѡ��Tomcat v7.0 server
ָ��C:\Download\apache-tomcat-7.0.73-windows-x64\apache-tomcat-7.0.73
����Ŀ��ӵ�tomcat��


�޸�jdbc.properties
jdbc.urlָ�����mysql IP��ַ

����tomcat

����http://localhost:8080/edu-demo/

## ��������
### ��Ŀ���������

0. ��� ERROR 1045 �Լ� ERROR 1142
	������ϸ����
	 ERROR 1045 (28000): Access denied for user ''@'localhost' (using password: NO)
	 ERROR 1142 (42000): SELECT command denied to user ''@'localhost' for table 'user'

	 ������裺
		service mysqld stop
		mysqld_safe --user=mysql --skip-grant-tables --skip-networking & 
		mysql -u root mysql
		use mysql;
		show tables;
		select user,host from mysql.user;
		delete from mysql.user where user='';�� �� ɾ�������û� 

		service mysqld stop
		service mysqld start
		mysql -u root -p
		select current_user()

		grant all privileges on *.* to 'root'@'%' identified by 'wusc.321' with grant option;
		flush privileges;
		show grants for 'root'@'%';




1.class not found spring
	��������Ȼmaven�����������class�ļ�������tomcat���ص�ʱ��û�з��֣�����Ϊ�ֶ�����
	eclipse 
	Deployment assembly
	--> Maven Dependencies , web-info/lib

	
### �����ݿ������
2.��ʼ���ű��ﲻҪ�����ģ��������׳���

	insert into edu_edmo_pms_user (id, user_no, user_pwd, remark, user_name, mobile_no, status, user_type, last_login_time, is_changed_pwd, pwd_error_count, pwd_error_time) values 
	(1, 'admin', '7c4a8d09ca3762af61e59520943dc26494f8941b', 'super admin', 'super admin', '13800138000', '100', '1', null, 0, 0, null);

	
	

3.mysqlʱ��ֵ����
	����Ϊ timestamp
	defaultֵ default CURRENT_TIMESTAMP

	����
	create_time          timestamp not null default CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP comment '����ʱ��',

4. �������ݿ����
	���user��
	use mysql��
	select * from user��

	�����û�Ȩ��
	select user,host from mysql.user;
	grant all privileges on *.* to 'root'@'%' identified by 'wusc.321' with grant option;
	flush privileges;
	show grants for 'root'@'%';

ע������
	'root'@'%' ��ʾroot�û����Դ��κλ�������mysql
	identified by 'wusc.321' ��ʾ����root������Ϊ wusc.321

5	���ݿ����֮��,
	��Ȼʹ��mysql -u root -p, ���Ǳ�� �����û�����
	
	�鿴��ǰ�û�
	select user()
	select current_user()
	select user,host from mysql.user;
	�����ʽɾ�������û�
	delete from mysql.user where host=''
	flush privileges;
	
6. �������ݿ�Ȩ�޲���������
http://www.cnblogs.com/candle806/p/4048651.html
http://www.cnblogs.com/fslnet/p/3143344.html


7.ɾ�������û� 
 delete from mysql.user where user='';�� �� ɾ�������û� 
 
 
 8.����MySQL���ݿ�ʱ������������ķ�������
 http://blog.csdn.net/lioncode/article/details/7917310

 



