# ansible 部署VLAN+Bridge
# 前置需求：系统支持VLAN功能
```
dmesg | grep -i 802 
可以看到VLAN Support
如果没有8021q模块没有载入：
modprobe 8021q
lsmod |grep 8021q
设置开机加载8021q模块
vim /etc/sysconfig/modules/8021q.modules(新文件)
modprobe 8021q
```
# 安装vconfig
## 编辑：playbook.yaml
```
- hosts: dest
  roles:
    - role: BridgeVlan/Install-vconfig
```
# 创建VLAN+Bridge
## 编辑：playbook.yaml
```
- hosts: dest
  roles:
    - role: BridgeVlan/MakeVlanBridge
```
# 删除VLAN+Bridge
## 编辑:playbook.yaml
```
- hosts: dest
  roles:
    - role: BridgeVlan/RemoveVlanBridge
```
## 编辑相应功能playbook.yaml后执行
```
ansible-playbook -i hosts.ini playbook.yaml
```
