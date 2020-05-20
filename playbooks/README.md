# ansible-playbooks
一些用于生产环境使用的ansible的playbook与roles

## system_init.yml
用于对于rhel/centos系统执行初始化
```
# ansible-playbook -i 'host文件' system_init.yaml -e 'host=主机组或主机'
```
## ping.yml
ping远程主机
```
# ansible-playbook -i 'host文件' ping.yaml -e 'host=主机组或主机'
```
## add_sshkey.ym
为远程主机root用户添加ssh密钥对。第一次使用ansible时候需要给远程主机添加密钥对，如果远程主机很多一台一台通过ssh-copy-i上传比较繁琐，干脆就通过ansible来添加批量添加密钥对
```
ansible-playbook -i 'host文件' add_sshkey.yaml -e 'host=主机组或主机' -uroot -k   # 提示输入密码
```
这种方式需要所有的远程主机的密码一致，如果不一致那就是密码对的能添加，不对的就不能添加。如果远程主机的每台密码或者部分密码不一样只能在主机清单文件上设置一下每台主机的用户、密码或端口，只要做一次就行了

## install_nginx.yml
在远程主机上安装1.16.1版本
```
ansible-playbook -i 'host文件' install_nginx.yaml -uroot -e 'host=主机组或主机'
```
## install_mysql57.yml
安装的是编译好的percona-5.7.29-32版本，以为在远程主机上上编译安装mysql比较慢password参数是为数据库设置的密码
```
ansible-playbook -i 'host文件' install_mysql57.yml -e 'host=主机组或主机 password=密码' -uroot
```
password参数是为数据库设置的初始化密码
