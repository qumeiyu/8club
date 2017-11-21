[TOC]

---

# 1.安装Erlang
[Erlang官网](http://www.erlang.org/downloads)
## 1.1. 配置环境变量
配置完成后在命令行中输入 erl 确认版本。
# 2.安装rabbitMQ
[rabbitMQ官网](http://www.rabbitmq.com/download.html)
# 3.配置rabbitMQ
```shell
#启动
rabbitmq-server start
rabbitmq-plugins.bat enable rabbitmq_management
#安装完成之后以管理员身份启动
rabbitmq-service.bat stop
rabbitmq-service.bat install
rabbitmq-service.bat start
#浏览器访问localhost:15672 默认账号：guest 密码：guest
```

## 3.1. 激活RabbitMQ's Management Plugin
```shell
rabbitmq-plugins.bat"enable rabbitmq_management
```

## 3.2. 创建用户，密码，绑定角色
```shell
#查看已有用户及用户的角色
rabbitmqctl.bat list_users
#新增一个用户
rabbitmqctl.batadd_user username password
#分配角色
rabbitmqctl set_user_tags username administrator
#更改密码
rabbitmqctl change_password userName newPassword
#删除用户
rabbitmqctl.bat delete_user username
```
## 3.3. 权限相关命令
```shell
#设置用户权限
rabbitmqctl set_permissions -p VHostPath User ConfP WriteP ReadP
#查看(指定hostpath)所有用户的权限信息
rabbitmqctl list_permissions [-p VHostPath]
#查看指定用户的权限信息
rabbitmqctl list_user_permissions User
#清除用户的权限信息
rabbitmqctl clear_permissions [-p VHostPath] User
```

