# Linux 学习笔记：8.10.5 部分详解

# （接上文）Linux学习笔记

### 8.10.5 netstat：显示网络状态和端口占用

```Bash

netstat -anp  # 查看所有网络连接、端口、进程信息
```

|选项|功能|
|---|---|
|-a|显示所有连接和监听端口|
|-n|以IP地址显示，不做域名解析|
|-t|只看TCP|
|-u|只看UDP|
|-p|显示进程PID/名称|
常用：

```Bash

netstat -tulnp  # 查看监听中的端口
netstat -anp | grep 端口号
```

---

## 9 软件包管理（RPM & YUM）

### 9.1 RPM

- 红帽系包管理工具，类似Windows“exe/msi”

- 只能安装已下载的包，**不会自动解决依赖**

#### 查询

```Bash

rpm -qa                # 列出所有已装包
rpm -qa | grep firefox
rpm -q 包名            # 查询是否安装
rpm -qi 包名           # 详情信息
rpm -ql 包名           # 列出安装路径
```

#### 安装

```Bash

rpm -ivh 包名.rpm
```

- -i：install

- -v：verbose

- -h：进度条

#### 卸载

```Bash

rpm -e 包名            # 普通卸载
rpm -e --nodeps 包名   # 强制卸载（忽略依赖）
```

---

### 9.2 YUM

- 基于RPM，**自动解决依赖**，从仓库下载安装

#### 常用命令

```Bash

yum list | grep 关键词        # 查询可用包
yum install -y 包名          # 安装
yum remove 包名              # 卸载
yum update 包名              # 更新
yum clean all                # 清空缓存
```

#### 配置国内镜像（以CentOS 7为例）

```Bash

# 备份原有repo
mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup

# 下载阿里云repo
wget -O /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo

yum makecache
```

---

## 10 定时任务调度

### 10.1 crontab 定时任务

```Bash

crontab -e   # 编辑定时任务
crontab -l   # 查看
crontab -r   # 删除当前用户所有定时任务
```

#### 格式

```Plain Text

分 时 日 月 周  命令
```

示例：

```Bash

# 每分钟执行一次
* * * * * command

# 每天凌晨2点执行
0 2 * * * command

# 每周日凌晨3点30分
30 3 * * 0 command
```

---

## 11 Linux 磁盘分区与挂载

### 11.1 新增磁盘挂载流程（CentOS 7）

1. 虚拟机添加硬盘

2. 分区

    ```Bash
    
    fdisk /dev/sdb
    ```

    - n：新建分区

    - p：主分区

    - 一路回车

    - w：保存退出

3. 格式化

    ```Bash
    
    mkfs -t xfs /dev/sdb1
    ```

4. 创建挂载目录

    ```Bash
    
    mkdir /newdisk
    ```

5. 临时挂载

    ```Bash
    
    mount /dev/sdb1 /newdisk
    ```

6. 永久挂载（开机自动）

    ```Bash
    
    blkid  # 查看UUID
    vim /etc/fstab
    ```

    加入一行：

    ```Plain Text
    
    UUID=xxxx /newdisk xfs defaults 0 0
    ```

7. 生效

    ```Bash
    
    mount -a
    ```

---

## 12 Shell 编程入门

### 12.1 脚本格式

```Bash

#!/bin/bash
echo "Hello Shell"
```

执行：

```Bash

chmod +x test.sh
./test.sh
```

### 12.2 变量

```Bash

NAME="张三"
echo $NAME
readonly A=10  # 只读变量
unset B        # 删除变量
```

系统预定义变量：

```Bash

echo $HOME
echo $PWD
echo $SHELL
echo $USER
```

### 12.3 运算符

```Bash

$((2+3))
$[2+3]
```

### 12.4 条件判断

```Bash

if [ $a -gt $b ]; then
  echo "a大于b"
fi
```

常用判断：

- -lt 小于

- -le 小于等于

- -gt 大于

- -ge 大于等于

- -eq 等于

- -ne 不等于

文件判断：

- -f 文件存在且是普通文件

- -d 目录存在

- -e 文件/目录存在

### 12.5 流程控制

```Bash

if [ condition ]; then
  ...
elif [ condition ]; then
  ...
else
  ...
fi
```

```Bash

case $变量 in
"val1")
  ...
  ;;
"val2")
  ...
  ;;
esac
```

```Bash

for ((i=0;i<10;i++))
do
  echo $i
done
```

```Bash

for i in 1 2 3
do
  echo $i
done
```

```Bash

while [ condition ]
do
  ...
done
```

### 12.6 读取输入

```Bash

read -p "请输入：" VAR
echo $VAR
```

### 12.7 函数

```Bash

function sum() {
  return $(($1+$2))
}
sum 10 20
echo $?
```

---

## 13 Linux 高级网络与服务

### 13.1 防火墙 firewall

```Bash

# 查看状态
systemctl status firewalld

# 开启/关闭/重启
systemctl start/stop/restart firewalld

# 开机自启/禁用
systemctl enable/disable firewalld
```

端口操作：

```Bash

firewall-cmd --add-port=8080/tcp --permanent
firewall-cmd --reload
firewall-cmd --list-ports
```

---

## 14 日志管理

### 14.1 系统日志

```Bash

/var/log/messages    # 系统主日志
/var/log/secure      # 安全、登录日志
/var/log/cron        # 定时任务日志
/var/log/boot.log    # 启动日志
```

### 14.2 日志轮替 logrotate

配置文件：

```Plain Text

/etc/logrotate.conf
/etc/logrotate.d/
```

---

## 15 备份与恢复

### 15.1 dump & restore（了解）

```Bash

dump -0uf /backup/boot.bak /boot
restore -tf /backup/boot.bak  # 查看
restore -rf /backup/boot.bak  # 恢复
```

### 15.2 简单备份（推荐）

```Bash

# 打包备份
tar -zcvf backup_$(date +%Y%m%d).tar.gz /home /etc

# 异地备份
scp backup.tar.gz user@remoteip:/path
```

---

## 16 常用运维技巧总结

1. **查看端口占用**

    ```Bash
    
    lsof -i :端口
    netstat -tulnp | grep 端口
    ```

2. **查找大文件**

    ```Bash
    
    find / -type f -size +100M
    ```

3. **查看系统信息**

    ```Bash
    
    uname -a
    cat /etc/os-release
    free -h
    df -h
    top
    ```

4. **用户权限快速赋予**

    ```Bash
    
    usermod -aG wheel 用户名
    ```

5. **修改文件权限、属主**

    ```Bash
    
    chmod -R 755 目录
    chown -R user:group 目录
    ```

---
