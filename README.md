# om-note
```bash
#2026年7月18日
#rsyncd.conf 企业常用配置
[root@backup ~]#cat /etc/rsyncd.conf
uid = rsync
gid = rsync
port = 873
fake super = yes
use chroot = no
max connections = 200
timeout = 600
ignore errors
read only = false
list = false
auth users = rsync_backup
secrets file = /etc/rsync.passwd
log file = /var/log/rsyncd.log
#这里就是模块名称，一起写进conf里，::会调用
[backup]
comment = welcome to oldboyedu backup!
path = /backup
#虚拟用户
useradd -M -s /sbin/nologin rsync
id rsync
#创建rsync.passwd,密码文件都是600权限,不然你用不了
cat > /etc/rsync.passwd << EOF
chmod 600 /etc/rsync.passwd
EOF
#创建备份文件，赋权
mkdir /backup
chmod rsync.rsync /backup
#vim设置
:set paste
:set nu
dG删除全部
A编辑末尾
ctrl+v I esc esc 批量编辑
h左，j下，k上，l右
shift+4末尾
shift+6首航
#::走rsync服务；avz万能参数；
rsync -avz rsync_backup@10.0.0.41::backup ./


```
