## Centos7 安装 redis
### 1. 卸载
```markdown
  rpm -qa | grep mariadb
  rpm -e --nodeps mariadb-libs-5.5.56-2.el7.x86_64
```
### 2. 安装
```markdown
  yum install -y http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
  yum --enablerepo=remi install redis
  systemctl start redis
```
### 3. 配置
```markdown
  vi /etc/redis.conf
  # bind 127.0.0.1
  protected-mode no
  requirepass 123456
```
### 4. 重启
```markdown
  systemctl restart redis
  systemctl disable firewalld
  redis-cli -h 127.0.0.1 -p 6379
  auth 123456
```
