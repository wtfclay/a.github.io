## Centos7 安装 Mysql8
### 1. 卸载
```markdown
  rpm -qa | grep mariadb
  rpm -e --nodeps mariadb-libs-5.5.56-2.el7.x86_64
```
### 2. 安装
```markdown
  wget https://repo.mysql.com//mysql80-community-release-el7-1.noarch.rpm
  yum localinstall mysql80-community-release-el7-1.noarch.rpm
  yum install mysql-community-server
  systemctl start mysqld
```
### 3. 配置
```markdown
  grep 'temporary password' /var/log/mysqld.log
  mysql -u root -p
  ALTER USER 'root'@'localhost' IDENTIFIED BY 'Root@123456';
  ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'Root@123456';
  FLUSH PRIVILEGES;
  use mysql;
  update user set host = '%' where user = 'root';
```
### 4. 重启
```markdown
  systemctl restart mysqld
  systemctl disable firewalld
```
