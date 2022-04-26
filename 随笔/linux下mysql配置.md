### linux下mysql配置
删除老版本

        rpm -qa|grep -i mysql

上面指令查到的删除

        rm -fr /usr/lib/mysql
        rm -fr /include/mysql
其他要删除文件

/etc/my.cnf

/var/lib/mysql

/etc/init.d/mysqld





yum安装
查看可用的mysql源

        yum list | grep mysql

安装

        yum install -y mysql-server mysql mysql-devel 


​        
####密码设置
1.在/etc/my.cnf文件中的[mysqld]添加如下内容

        skip-grant-tables
2.重启mysql服务

        service mysqld restart
3.在mysql中设置密码

        update mysql.user set password=password('1234') where user='root';
        flush privileges;
        quit
4.重启mysql服务

        service mysqld restart

5.开启远程访问权限
        grant all privileges on *.* to 'root'@'%' identified by '1234' with grant option;
        flush privileges;
        quit