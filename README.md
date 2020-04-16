# ansible-playbooks
一些用于生产环境使用的ansible的playbook

## system_init.yaml
对于rhel/centos系统执行初始化
```
# ansible-playbook -i 'host文件' system_init.yaml -e 'host=主机组或主机'
```
## ping.yaml
ping远程主机
```
# ansible-playbook -i 'host文件' ping.yaml -e 'host=主机组或主机'
```
## add_sshkey.yaml
为远程主机root用户添加ssh密钥对
```
ansible-playbook -i 'host文件' add_sshkey.yaml -e 'host=主机组或主机' -uroot -k   # 提示输入密码
```
## install_nginx.yaml
在远程主机上安装1.16.1版本
```
ansible-playbook -i 'host文件' install_nginx.yaml -uroot -e 'host=主机组或主机'
```
## install_mysql57.yml
```
ansible-playbook -i 'host文件' install_mysql57.yml -e 'host=主机组或主机 password=密码' -uroot
```
