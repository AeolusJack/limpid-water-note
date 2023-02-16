# linux防火墙

## iptables防火墙

 查看防火墙状态   service iptables status

 停止防火墙      service iptables stop

 启动防火墙      service iptables start

 重启防火墙      service iptables restart

 永久关闭防火墙   chkconfig iptables off

 永久关闭后重启   chkconfig iptables on

开启80端口

vim /etc/sysconfig/iptables
加入如下代码
-A INPUT -m state --state NEW -m tcp -p tcp --dport 80 -j ACCEPT

保存退出后重启防火墙  service iptables restart


## firewall防火墙

查看firewall服务状态  systemctl status firewalld

出现Active: active (running)切高亮显示则表示是启动状态。

出现 Active: inactive (dead)灰色表示停止，看单词也行。

查看firewall的状态   firewall-cmd --state


### 开启、重启、关闭、firewalld.service服务

开启防火墙   service firewalld start

重启防火墙   service firewalld restart

关闭防火墙   service firewalld stop

查看防火墙规则  firewall-cmd --list-all


### 查询、开放、关闭端口

查询端口是否开放  firewall-cmd --query-port=8080/tcp

开放80端口     firewall-cmd --permanent --add-port=80/tcp
 
移除端口      firewall-cmd --permanent --remove-port=8080/tcp

重启防火墙(修改配置后要重启防火墙)  firewall-cmd --reload


### 将其他机器的端口转到防火墙端口
将192.168.0.2的端口10000转到防火墙机器端口100001
firewall-cmd --zone=public --permanent --add-forward-port=port=100001:proto=tcp:toport=10000:toaddr=192.168.0.2

#### 将端口映射移除
语法：firewall-cmd [--zone=区域] --remove-forward-port=port=端口(端口范围):proto=协议:toaddress=目的地址
示例：禁止区域的端口转发或者端口映射
firewall-cmd --zone=public --remove-forward-port=port=10000-20000:proto=tcp:toport=10000-20000:toaddr=192.168.0.2 --permanent

## 参数解释

1、firwall-cmd：是Linux提供的操作firewall的一个工具； 

2、--permanent：表示设置为持久；

3、--add-port：标识添加的端口；
<br />