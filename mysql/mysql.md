# mysql 安装
## win10 mysql-5.5.58-winx64
- 1.配置环境变量 path 添加  D:\software\mysql-5.5.58-winx64\bin
- 2.创建配置文件my.ini  我选择my-large.ini

文件名称|文件说明
:-------|:-------
my-small.ini |内存 <= 64M
my-medium.ini|内存 128M
my-large.ini|内存 512M
my-huge.ini|内存 1G-2G
my-innodb-heavy-4G.ini |内存 4GB

- 3.配置 my.ini

```text
[mysqld]
######################
# 设置mysql的安装目录
basedir=D:\\software\\mysql-5.5.58-winx64
# 设置mysql数据库的数据的存放目录，必须是data，或者是\\xxx-data
datadir=D:\\software\\mysql-5.5.58-winx64\\data
# 设置mysql服务器的字符集，默认编码
default-character-set=utf8
######################
```

- 4.mysqld -install 

```shell
#运行命令
mysql -install 
#如果出现 Install/Remove of the Service Denied! 以系统管理员运行
Service successfully installed.
```

- 5.mysqld -remove 删除服务
- 6.启动服务
```shell
#启动服务
net start mysql
# 停止服务
net stop mysql
```
- 7.运行mysqladmin -root
```shell
mysql -u root
```
- 8.修改root密码
```shell
mysqladmin –u root password
# 登陆
mysql -u root -p 
#输入密码登陆
```
## mysql远程授权
```shell
mysql -u root -p
#=============== 远程用户授权
 grant all privileges on *.* to root@"%" identified by 'root' ;
 flush privileges;

```