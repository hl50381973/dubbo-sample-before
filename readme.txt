
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



���ݿⰲװ
centos6.5����
ʹ��yum��װ��ʽ
��yumԴ����ʹ��163Դ��
yum install mysql-server

��һ�ε���
service mysqld start
service mysqld status

chkconfig mysqld on


## �汾�涨
tomcat �汾
tomcat7

jdk�汾
1.7

## ��������

1.class not found spring
	��������Ȼmaven�����������class�ļ�������tomcat���ص�ʱ��û�з��֣�����Ϊ�ֶ�����
	eclipse 
	Deployment assembly
	--> Maven Dependencies , web-info/lib

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

5	�������ݿ�����
	��С���������û�����
	�鿴��ǰ�û�
	select user()
	select current_user()
	select user,host from mysql.user;
	�����ʽɾ�������û�
	delete from mysql.user where host=''
	flush privileges;