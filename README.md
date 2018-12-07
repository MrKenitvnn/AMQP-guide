
### 1. Cài đặt

> OS: Cent os 6

##### Cài đặt Erlang trước: 
```shell

rpm --import https://packages.erlang-solutions.com/rpm/erlang_solutions.asc

vi /etc/yum.repos.d/erlang-solutions.repo

[erlang-solutions]
name=CentOS $releasever - $basearch - Erlang Solutions
baseurl=https://packages.erlang-solutions.com/rpm/centos/$releasever/$basearch
gpgcheck=1
gpgkey=https://packages.erlang-solutions.com/rpm/erlang_solutions.asc
enabled=1

yum -y install erlang socat
```

##### Cài đặt rabbitmq 

```shell
# import the new PackageCloud key that will be used starting December 1st, 2018 (GMT)
rpm --import https://packagecloud.io/rabbitmq/rabbitmq-server/gpgkey

# import the old PackageCloud key that will be discontinued on December 1st, 2018 (GMT)
rpm --import https://packagecloud.io/gpg.key

# import signing key 
rpm --import https://github.com/rabbitmq/signing-keys/releases/download/2.0/rabbitmq-release-signing-key.asc
```

```shell
touch /etc/yum.repos.d/rabbitmq.repo

[bintray-rabbitmq-server]
name=bintray-rabbitmq-rpm
baseurl=https://dl.bintray.com/rabbitmq/rpm/rabbitmq-server/v3.7.x/el/6/
gpgcheck=0
repo_gpgcheck=0
enabled=1
```

```shell
sudo rpm --import https://www.rabbitmq.com/rabbitmq-release-signing-key.asc

yum install rabbitmq-server

```

#### Thiết lập

```
# Cho phép khởi động cùng server 
chkconfig rabbitmq-server on

# Add user
rabbitmqctl add_user admin password 

# Start service
service rabbitmq-server start

# Bật plugin manager
rabbitmq-plugins enable rabbitmq_management

=> [{clustering,25672,"::"},{amqp,5672,"::"},{http,15672,"::"}]
```


















