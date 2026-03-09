# Linux 尚硅谷学习笔记（2w+字超全）

# Linux学习笔记 - 尚硅谷（2w+字超全）

- 发布时间：2021-09-13 22:58:17

- 最后修改：2025-10-20 11:17:44

- 标签：#linux

本文档详细介绍了Linux系统的基础知识，涵盖从系统安装到日常运维的各项操作，包括Linux入门、系统安装、文件目录管理、编辑器使用、网络配置、系统管理、常用命令等核心内容，适合初学者全面学习并作为日常查询手册。

## 1 Linux入门

### 1.1 概述

Linux内核最初由芬兰人Linux Torvalds在赫尔辛基大学上学时出于个人爱好编写。

Linux是一套免费使用和自由传播的类Unix操作系统，基于POSIX和UNIX，支持多用户、多任务、多线程和多CPU。它能运行主要的UNIX工具软件、应用程序和网络协议，支持32位和64位硬件，继承了Unix以网络为核心的设计思想，是性能稳定的多用户网络操作系统。

目前市面上主流发行版有：Ubuntu、RedHat、CentOS、Debian、Fedora、SuSE、OpenSUSE。

### 1.2 Linux和Windows区别

|比较维度|Windows|Linux|
|---|---|---|
|免费与收费|收费且价格较高|免费或仅需少量费用|
|软件与支持|软件数量和质量有优势，多为收费软件；由微软官方提供支持服务|开源自由软件，用户可修改定制和再发布；部分软件质量和体验欠缺；由全球Linux开发者和自由软件社区提供支持|
|安全性|需频繁打补丁更新，仍易中病毒木马|相对更安全，安全问题较少|
|使用习惯|纯图形界面操作，依赖鼠标和键盘，上手容易|兼具图形界面和命令行操作，可仅用键盘完成所有操作，新手入门较难，熟练后效率极高|
|可定制性|封闭系统，可定制性差|开源系统，可定制化极强|
|应用场景|主要用于桌面操作系统|广泛用于服务器领域，支撑百度、谷歌、淘宝等软件和服务|
### 1.3 CentOS下载地址

- 网易镜像：[https://mirrors.163.com/centos/7/isos/](https://mirrors.163.com/centos/7/isos/)

- 搜狐镜像：[https://mirrors.sohu.com/centos/7/isos/](https://mirrors.sohu.com/centos/7/isos/)

## 2 VM与Linux的安装

具体安装步骤参考其他文章（文档未提供详细步骤）。

## 3 Linux文件与目录

### 3.1 Linux文件

Linux系统中**一切皆文件**，包括设备、文档、程序等都以文件形式存在。

### 3.2 Linux目录结构

Linux目录采用树状结构，核心目录及含义如下：

|目录|含义|
|---|---|
|/bin|Binary的缩写，存放所有一般用户可使用的二进制可执行文件（如cat、chmod、mv、mkdir、cd等常用指令）|
|/sbin|Super User专用，存放仅root用户有权限执行的可执行文件（如init、ip、mount等命令）|
|/boot|存放开机引导文件（如Linux内核文件、开机菜单及配置文件）|
|/dev|device设备目录，所有设备（硬盘、键盘、鼠标、光驱等）均以文件形式存放于此，访问该目录文件即访问对应设备|
|/etc|存放所有程序和系统的配置文件（如用户账号密码文件、服务启动脚本等），普通用户可查阅，仅root可修改|
|/home|系统默认用户家目录，新建用户时会自动在此创建以用户名命名的目录|
|/lib|library库文件目录，存放系统开机所需函数库及/bin、/sbin目录命令调用的函数库|
|/lib64|存放支持64位格式的函数库|
|/media|存放可移除媒体设备（如光盘、DVD等）|
|/mnt|mount临时挂载目录，系统管理员可临时挂载文件系统|
|/opt|optional可选软件包目录，用于安装第三方软件|
|/proc|特殊动态目录（虚拟文件系统），维护系统信息和运行中进程信息，系统资源以文本形式呈现|
|/root|系统管理员root的主目录|
|/run|存放最近一次开机后产生的信息（如当前用户、运行中的守护进程等）|
|/srv|service服务数据目录，存放服务启动后所需数据|
|/sys|与/proc类似的虚拟文件系统，存放系统核心与硬件相关信息，不占用硬件容量|
|/tmp|temporary临时文件目录，所有用户可访问，系统重启时清空|
|/usr|存放绝大部分用户可访问的应用程序和文件（二进制文件、库文件、文档、源代码等）|
|/var|variable可变文件目录，存放日志、数据库等内容可能增长的文件|
核心目录路径示例：/root/Desktop、/root/Maildir、/usr/bin、/usr/lib

## 4 VI/VIM编辑器

### 4.1 VIM是什么

- VI是Unix及类Unix操作系统中最通用的文本编辑器。

- VIM是VI的增强版，性能更强大，支持语法高亮，方便程序设计，与VI完全兼容。

### 4.2 模式转换

VIM分为三种核心模式，转换关系如下：

```Plain Text

命令行启动（vi 文件名）→ 一般模式（默认）
一般模式 → 插入模式（按i/I/o/O/a/A键）
插入模式 → 一般模式（按ESC键）
一般模式 → 指令模式（按:/?键）
指令模式 → 一般模式（按ESC键）
```

### 4.3 一般模式（快速编辑、光标跳转）

一般模式下可执行删除、复制、粘贴、光标移动等操作，常用命令如下：

|语法|功能描述|
|---|---|
|yy|复制光标当前一行|
|y数字y|复制指定范围的行（如y3y复制当前行及后2行）|
|y+shift+4|复制当前光标到行尾的字符串|
|p|粘贴到光标所在行下方|
|u|撤销上一步操作|
|dd|删除光标当前行|
|d数字d|删除光标（含）后指定行数（如d3d删除当前行及后2行）|
|x|剪切光标所在位置的一个字母（等同于Del键）|
|X|剪切光标前一个字母（等同于Backspace键）|
|w|切换到下一个词|
|e|快速跳转到下一个词尾|
|b|跳转到上一个词|
|yw|复制一个词|
|dw|删除一个词|
|shift+6|移动到行首|
|shift+4|移动到行尾|
|gg|移动到文件开头（页头）|
|G/L|移动到文件末尾（页尾）|
|数字+shift+g|移动到指定行（如5shift+g跳转到第5行）|
|数字b|跳转到上n个词（如3b跳转到上3个词）|
**行号显示控制**：

- 显示行号：`:set nu`

- 隐藏行号：`:set nonu`

### 4.4 插入模式（编辑文本）

一般模式下按以下按键进入插入模式（左下角显示INSERT/REPLACE），按ESC键返回一般模式：

|按钮|功能|
|---|---|
|i|在当前光标前插入|
|a|在当前光标后插入|
|o|在当前光标行的下一行新建行插入|
|I|在光标所在行的行首插入|
|A|在光标所在行的行尾插入|
|O|在当前光标行的上一行新建行插入|
### 4.5 指令模式（搜索、替换、保存退出）

一般模式下按`:/?`任一键进入指令模式，常用命令如下：

|命令|功能|
|---|---|
|:w|保存文件|
|:q|退出VIM|
|:wq|保存并退出|
|:q!|不保存强制退出|
|/要查找的词|向下搜索指定词（n向下继续查找，N向上查找）|
|:noh|取消搜索高亮显示|
|:set nu|显示行号|
|:set nonu|关闭行号|
|:s /old/new|替换当前行第一个匹配的old为new|
|:s /old/new/g|替换当前行所有匹配的old为new|
|:%s/old/new|替换文档中每一行第一个匹配的old为new|
|:%s/old/new/g|替换文档中所有匹配的old为new（常用）|
#### 其他重要命令

1. 寄存器使用：拷贝/粘贴/删除命令前加"x（x=a..z,*），如"ay$将剩余行内容拷贝到寄存器a

2. 重复操作：命令前加数字，如2p（粘贴2次）、d2w（删除2个词）、5i（插入5次）

3. 快捷保存退出：ZZ（保存退出）、ZQ（不保存退出）

4. 光标行位置调整：zt（移到屏幕顶端）、zb（移到屏幕底端）、zz（移到屏幕中间）

5. 其他：gg（文首，VIM专属）、gf（打开光标处文件名，VIM专属）

### 4.6 模式之间转换总结

- 命令行启动：`vi 文件名` → 一般模式（核心模式，支持复制、删除、光标移动）

- 一般模式 → 插入模式：按i/I/o/O/a/A键（编辑文本）

- 插入模式 → 一般模式：按ESC键

- 一般模式 → 指令模式：按:/?键（保存、退出、搜索、替换）

- 指令模式 → 一般模式：按ESC键

## 5 网络配置和系统管理操作

### 5.1 查看网络IP和网关

#### 1）查看虚拟网络配置

- Windows系统查看IP：`ipconfig`（命令行执行）

- Linux系统查看网关：`ifconfig`

#### 2）虚拟机网卡配置

虚拟机支持三种网络模式，差异如下：

- **桥接模式**：虚拟机直接连接外部物理网络，主机充当网桥，可直接访问外部网络且对外部可见（占用局域网IP，同一路由器内可访问）

- **NAT模式（Network Address Translation）**：虚拟机与主机构建专用网络，通过NAT设备转换IP，虚拟机可访问外部网络，但外部网络无法访问虚拟机

- **仅主机模式**：虚拟机仅与主机共享专用网络，无法与外部网络通信

#### 3）查看网关

Linux系统执行：`ifconfig`

### 5.2 配置网络IP（静态IP）

#### 步骤：

1. 进入网络配置文件目录：

```Bash

cd /etc/sysconfig/network-scripts
```

1. 编辑网卡配置文件（按Tab键补全文件名，常见如ifcfg-eth0、ifcfg-ens33、ifcfg-ens192）：

```Bash

vim ifcfg-ens33  # 以实际文件名为准
```

1. 修改配置参数：

```Bash

# 将DHCP自动获取改为静态IP
BOOTPROTO="static"
# 设置IP地址（自定义，需与网关在同一网段）
IPADDR=192.168.202.100
# 设置网关
GATEWAY=192.168.202.2
# 设置域名解析器（通常与网关一致）
DNS1=192.168.202.2
```

1. 重启网络服务：

```Bash

service network restart
```

#### 常见问题排查：

1. 物理机能ping通虚拟机，虚拟机ping不通物理机：关闭物理机防火墙

2. 虚拟机能ping通物理机，无法ping通外网：检查DNS配置

3. 虚拟机ping [www.baidu.com](http://www.baidu.com)显示域名未知：检查GATEWAY和DNS配置

4. 网络服务启动失败：关闭NetworkManager服务

```Bash

systemctl stop NetworkManager  # 临时关闭
systemctl disable NetworkManager  # 禁用开机自启
```

1. 检查网络服务状态：`systemctl status network`，异常时检查网卡配置文件（如ifcfg-ens33）

### 5.3 配置主机名

#### 5.3.1 修改主机名称

1. 查看当前主机名：`hostname`

2. 临时修改（重启失效）：`hostname 新主机名`

3. 永久修改（CentOS 7+）：

```Bash

# 方法1：编辑配置文件
vim /etc/hostname  # 修改文件内容为新主机名，重启服务器生效
# 方法2：使用hostnamectl命令（无需重启）
hostnamectl set-hostname lys  # 例：将主机名改为lys
```

1. 查看主机详细信息：`hostnamectl`

#### 5.3.2 修改hosts映射文件

用于实现IP与主机名的映射，方便多虚拟机环境配置：

1. Linux系统修改：

```Bash

vim /etc/hosts
# 添加映射关系（示例）
192.168.202.100 lys
```

1. Windows系统修改：

```Plain Text

# 编辑文件（需管理员权限）
C:\Windows\System32\drivers\etc\hosts
# 添加映射关系（示例）
192.168.202.100 lys
```

## 6 远程登录

### 6.1 Windows命令行连接

```Bash

# 格式：ssh 用户名@服务器IP -p 端口号（默认22端口可省略）
ssh root@11.212.33.44
# 或指定用户名和端口
ssh zhangsan@11.212.33.44 -p 2222
```

### 6.2 工具连接

可使用Xshell、SecureCRT等工具，输入服务器IP、端口号、用户名和密码即可连接。

## 7 系统管理

### 7.1 Linux中的进程和服务

- **进程（process）**：正在执行的程序或命令

- **服务（service）**：启动后常驻内存的进程（如防火墙服务、网络服务）

### 7.2 service服务管理（CentOS 6版本，了解即可）

#### 基本语法

```Bash

service 服务名 start | stop | restart | status
```

#### 经验技巧

- 查看所有服务：`ls /etc/init.d/`

- 查看service命令位置：`ls /usr/sbin/ | grep service`

#### 案例实操

```Bash

# 查看网络服务状态
service network status
# 停止网络服务
service network stop
# 启动网络服务
service network start
# 重启网络服务
service network restart
```

### 7.3 chkconfig设置后台服务自启（CentOS 6版本）

#### 基本语法

```Bash

chkconfig  # 查看所有服务自启配置
chkconfig 服务名 off  # 关闭指定服务自启
chkconfig 服务名 on  # 开启指定服务自启
chkconfig 服务名 --list  # 查看单个服务自启状态
```

#### 案例实操

```Bash

# 开启/关闭network服务自启
chkconfig network on
chkconfig network off

# 开启/关闭指定级别（如级别3）的network服务自启
chkconfig --level 3 network on
chkconfig --level 3 network off
```

### 7.4 systemctl服务管理（CentOS 7版本，重点掌握）

#### 基本语法

```Bash

systemctl start | stop | restart | status 服务名
```

#### 经验技巧

- 查看所有服务：`ls -al /usr/lib/systemd/system`

- 查看守护进程（带d.service后缀）：`ls /usr/lib/systemd/system | grep d.service`

#### 案例实操

```Bash

# 查看防火墙服务状态
systemctl status firewalld
# 停止防火墙服务
systemctl stop firewalld
# 启动防火墙服务
systemctl start firewalld
# 重启防火墙服务
systemctl restart firewalld
```

### 7.5 systemctl设置服务自启（CentOS 7版本）

#### 基本语法

```Bash

systemctl list-unit-files  # 查看所有服务自启状态
systemctl disable 服务名  # 关闭指定服务自启
systemctl enable 服务名  # 开启指定服务自启
```

#### 案例实操

```Bash

# 开启/关闭防火墙服务自启
systemctl enable firewalld.service
systemctl disable firewalld.service
```

### 7.6 系统运行级别

#### 1. Linux传统运行级别（7种）

|级别|描述|
|---|---|
|0|系统停机状态，默认运行级别不能设为0（无法正常启动）|
|1|单用户工作状态（root权限，用于系统维护，禁止远程登录）|
|2|多用户状态（无NFS，不支持网络）|
|3|安全多用户状态（有NFS，登录后进入命令行模式，常用）|
|4|系统未使用，保留|
|5|X11控制台（登录后进入图形GUI模式，常用）|
|6|系统正常关闭并重启，默认运行级别不能设为6（无法正常启动）|
#### 2. CentOS 7简化运行级别

- `multi-user.target`：等价于传统级别3（多用户、有网络、无图形界面）

- `graphical.target`：等价于传统级别5（多用户、有网络、有图形界面）

#### 3. 运行级别操作

```Bash

# 查看当前运行级别
systemctl get-default
# 或编辑配置文件（不推荐直接修改）
vim /etc/inittab

# 修改运行级别（示例：设置为多用户命令行模式）
systemctl set-default multi-user.target
# 设置为图形界面模式
systemctl set-default graphical.target
```

### 7.7 关闭防火墙（CentOS 7版本）

#### 1. 临时关闭（重启失效）

```Bash

# 查看防火墙状态
systemctl status firewalld
# 停止防火墙
systemctl stop firewalld
```

#### 2. 永久关闭（开机不启动）

```Bash

# 查看防火墙自启状态
systemctl is-enabled firewalld.service
# 禁用自启（永久关闭）
systemctl disable firewalld.service
# 查看所有服务自启状态（验证）
systemctl list-unit-files | grep firewalld
```

### 7.8 关机重启命令

#### 核心命令

|命令|功能|
|---|---|
|sync|将内存数据同步到硬盘（防止数据丢失）|
|halt|停机（关闭系统，不断电）|
|poweroff|关机（断电）|
|reboot|重启（等同于shutdown -r now）|
|shutdown [选项] 时间|定时关机/重启|
#### 常用示例

```Bash

# 1分钟后关机（默认）
shutdown
# 3分钟后关机
shutdown 3
# 15:00定时关机
shutdown 15:00
# 取消关机
shutdown -c
# 立即关机
shutdown now
# 或
shutdown -h now

# 立即重启
shutdown -r now
# 或
reboot

# 数据同步（关机/重启前推荐执行）
sync
```

#### 经验技巧

Linux采用"预读迟写"机制，文件保存时数据先存于缓冲区，满后再写入磁盘。关机/重启前执行`sync`可立即将缓冲区数据写入磁盘，避免数据丢失。

## 8 常用基本命令

Shell是命令解释器，提供交互式文本控制台界面，用户输入命令后由Shell解释并交给内核执行。

### 8.1 帮助命令

#### 8.1.1 man获取帮助信息（适用于外部命令）

#### 基本语法

```Bash

man [命令或配置文件]  # 获取详细帮助信息
```

#### 示例

```Bash

# 查看cd命令的帮助分类
man -f cd
# 输出：cd (1) - bash built-in commands, see bash(1)
# 查看第1类帮助（外部命令）
man 1 cd
```

#### 帮助文档结构说明

|章节|功能|
|---|---|
|NAME|命令名称和单行描述|
|SYNOPSIS|命令使用格式|
|DESCRIPTION|命令功能详细说明|
|EXAMPLES|命令使用示例|
|SEE ALSO|相关主题（其他手册页）|
#### 8.1.2 help获取内置命令帮助

- **内置命令**：内嵌在Shell中，系统启动后常驻内存（如cd、echo）

- **外部命令**：独立于Shell的可执行文件（如ls、man）

#### 基本语法

```Bash

# 判断是否为内置命令
type 命令
# 获取内置命令帮助
help 命令
```

#### 示例

```Bash

# 判断cd是否为内置命令
type cd  # 输出：cd is a shell builtin
# 查看cd命令帮助
help cd
```

#### 8.1.3 常用快捷键

|快捷键|功能|
|---|---|
|Ctrl + C|停止当前进程|
|Ctrl + L|清屏（等同于clear命令，彻底清屏用reset）|
|Tab|命令/文件名自动补全（防止敲错，提高效率）|
|上下箭头|查找历史执行命令|
### 8.2 文件目录类命令

#### 8.2.1 pwd：显示当前工作目录绝对路径

- 全称：print working directory

- 基本语法：`pwd`

- 功能：显示当前所在目录的绝对路径（从/根目录开始）

#### 8.2.2 ls：列出目录内容

- 全称：list

- 基本语法：`ls [选项] [文件或目录]`

#### 选项说明

|选项|功能|
|---|---|
|-a|显示所有文件（含隐藏文件，以.开头的文件）|
|-l|长格式显示（包含文件属性、权限、大小、修改时间等，等同于ll命令）|
|-lh|长格式显示，文件大小以G/M/k为单位（更易读）|
#### 显示说明

长格式输出（ls -l）各字段含义：

`-rw-r--r-- 1 root root 1024 10-23 16:56 test.txt`

- 第1字段：文件类型与权限（-表示文件，d表示目录，l表示链接）

- 第2字段：链接数（文件为硬链接数，目录为子文件夹数）

- 第3字段：文件属主（所有者）

- 第4字段：文件属组

- 第5字段：文件大小（默认单位为字节）

- 第6-8字段：文件建立或最近修改时间

- 第9字段：文件名

#### 8.2.3 cd：切换目录

- 全称：Change Directory

- 基本语法：`cd [参数]`

#### 参数说明

|参数|功能|
|---|---|
|绝对路径（如/usr/local）|切换到指定绝对路径目录|
|相对路径（如../test）|相对于当前目录切换路径|
|~ 或 cd|回到当前用户的家目录|
|-|回到上一次所在目录|
|..|回到当前目录的上一级目录|
|-P|跳转到实际物理路径（忽略快捷方式路径）|
#### 示例

```Bash

# 切换到根目录
cd /
# 切换到用户家目录
cd ~
# 回到上一级目录
cd ..
# 回到上一次所在目录
cd -
```

#### 8.2.4 mkdir：创建目录

- 全称：make directory

- 基本语法：`mkdir [选项] 目录名`

#### 示例

```Bash

# 创建单个目录
mkdir a
# 递归创建多级目录（父目录不存在时自动创建）
mkdir -p a/b/c
# 同时创建多个同级目录
mkdir d e f
```

#### 8.2.5 rmdir：删除空目录

- 全称：remove directory

- 基本语法：`rmdir [目录名]`

- 限制：仅能删除空目录，非空目录需先删除内部文件/子目录

#### 示例

```Bash

# 删除空目录a
rmdir a
# 递归删除多级空目录（需各级目录均为空）
rmdir a/b/c
```

#### 8.2.6 touch：创建空文件

- 基本语法：`touch 文件名`

- 功能：创建空文件，若文件已存在则更新其修改时间

#### 示例

```Bash

# 创建单个空文件
touch test.txt
# 同时创建多个空文件
touch file1.txt file2.txt
```

#### 8.2.7 cp：复制文件或目录

- 全称：copy

- 基本语法：`cp [选项] 源文件/目录 目标文件/目录`

#### 选项说明

|选项|功能|
|---|---|
|-r|递归复制目录（含目录内所有文件和子目录）|
|-f|强制覆盖目标文件（不提示）|
|-i|覆盖前提示用户确认（默认行为）|
#### 示例

```Bash

# 复制文件
cp nginx.conf nginx.conf.bak
# 递归复制目录（含所有内容）
cp -r logs logs_bak
# 不强制覆盖（使用反斜杠取消别名）
\cp nginx.conf nginx.conf.bak
# 查看cp命令别名（默认可能带-i选项）
alias cp
```

#### 8.2.8 rm：删除文件或目录

- 全称：remove

- 基本语法：`rm [选项] 文件/目录`

#### 选项说明

|选项|功能|
|---|---|
|-r|递归删除目录（含所有文件和子目录）|
|-f|强制删除（不提示用户确认）|
|-v|显示删除过程详细信息|
#### 示例

```Bash

# 删除文件（带提示）
rm test.txt
# 强制删除文件（无提示）
rm -f test.txt
# 递归删除目录（含所有内容）
rm -r dir
# 强制递归删除目录（常用，无提示）
rm -rf dir
```

#### 8.2.9 mv：移动文件/目录或重命名

- 全称：move

- 基本语法：

    1. 重命名：`mv 旧文件名 新文件名`

    2. 移动：`mv 源文件/目录 目标目录`

#### 示例

```Bash

# 重命名文件
mv test.txt new_test.txt
# 重命名目录
mv dir old_dir
# 移动文件到目标目录
mv file.txt /tmp/
# 移动目录到目标目录
mv dir /tmp/
```

#### 8.2.10 cat：查看文件内容

- 基本语法：`cat [选项] 文件名`

- 功能：读取文件内容并输出到控制台，适用于小文件

#### 选项说明

|选项|功能|
|---|---|
|-n|显示所有行的行号（含空行）|
|-b|显示非空行的行号|
|-s|压缩连续空行为单个空行|
#### 示例

```Bash

# 查看文件内容
cat nginx.conf
# 查看文件内容并显示行号
cat -n nginx.conf
```

#### 8.2.11 more：文件内容分屏查看器

- 功能：以全屏幕方式按页显示文本文件内容，适用于中大型文件

- 基本语法：`more 文件名`

#### 常用操作快捷键

|操作|功能|
|---|---|
|空白键（Space）|向下翻一页|
|Enter|向下翻一行|
|q|立即退出more|
|Ctrl + F|向下滚动一屏|
|Ctrl + B|返回上一屏|
|=|显示当前行号|
|:f|显示文件名和当前行号|
#### 8.2.12 less：分屏显示文件内容（推荐查看大文件）

- 功能：与more类似，但支持按需加载内容（效率更高），支持向前翻页、搜索等增强功能

- 基本语法：`less 文件名`

#### 常用操作快捷键

|操作|功能|
|---|---|
|空白键|向下翻一页|
|PageDown|向下翻一页|
|PageUp|向上翻一页|
|/字符串|向下搜索指定字符串（n继续向下，N向上）|
|?字符串|向上搜索指定字符串（n继续向上，N向下）|
|q|退出less|
#### 8.2.13 echo：输出内容到控制台

- 基本语法：`echo [选项] 输出内容`

- 功能：将指定内容输出到控制台，支持字符串、变量等

#### 选项说明

|选项|功能|
|---|---|
|-e|支持反斜线控制的字符转换（如换行、制表符）|
#### 控制字符说明

|控制字符|功能|
|---|---|
|\\|输出反斜线本身|
|\n|换行符|
|\t|制表符（Tab键）|
#### 示例

```Bash

# 输出普通字符串
echo "Hello Linux"
# 支持换行和制表符
echo -e "Name\tAge\nTom\t20"
# 查看系统环境变量（Tab键补全变量名）
echo $PATH
echo $HOME
```

#### 8.2.14 head：显示文件头部内容

- 功能：默认显示文件前10行内容，可指定行数

- 基本语法：

    ```Bash
    
    head 文件名  # 显示前10行
    head -n 行数 文件名  # 显示指定前N行
    ```

#### 示例

```Bash

# 显示文件前10行（默认）
head nginx.conf
# 显示文件前5行
head -n 5 nginx.conf
```

#### 8.2.15 tail：显示文件尾部内容

- 功能：默认显示文件后10行内容，支持实时监控文件变化（常用日志查看）

- 基本语法：

    ```Bash
    
    tail 文件名  # 显示后10行
    tail -n 行数 文件名  # 显示指定后N行
    tail -f 文件名  # 实时监控文件尾部变化（按Ctrl+C退出）
    ```

#### 示例

```Bash

# 显示文件后10行（默认）
tail nginx.conf
# 显示文件后5行
tail -n 5 nginx.conf
# 实时监控日志文件变化
tail -f /var/log/messages
# 暂停监控：Ctrl + S；继续监控：Ctrl + Q
```

#### 8.2.16 输出重定向和追加

- 输出重定向（`>`）：将命令执行结果写入文件，覆盖原有内容

- 追加（`>>`）：将命令执行结果追加到文件末尾，不覆盖原有内容

#### 示例

```Bash

# 列出当前目录内容，写入a.txt（覆盖）
ls -l > a.txt
# 列出所有文件（含隐藏），追加到aa.txt
ls -al >> aa.txt
# 将文件1内容覆盖到文件2
cat file1.txt > file2.txt
# 追加字符串到文件
echo "Hello" >> file.txt
```

#### 8.2.17 ln：创建链接文件（软链接/硬链接）

### 1）软链接（符号链接）

- 类似Windows快捷方式，有独立数据块，存放目标文件路径

- 基本语法：`ln -s 目标文件/目录 链接名`

#### 示例

```Bash

# 创建文件软链接
ln -s web.log web_link
# 查看链接（前缀为l）
ll
# 输出：lrwxrwxrwx 1 root root 7 5月 16 00:36 web_link -> web.log
# 进入软链接指向的实际目录（需链接指向目录）
cd -P web_dir_link
```

#### 注意事项

- 删除软链接：`rm -rf 链接名`（不可加/，否则会删除目标目录内容）

- 示例：`rm -rf web_link`（正确），`rm -rf web_link/`（错误，删除目标文件内容）

### 2）硬链接

- 与目标文件共享同一inode，相当于文件的副本，修改任一文件都会同步

- 基本语法：`ln 目标文件 链接名`

#### 示例

```Bash

# 创建文件硬链接
ln web.log web_hard_link
```

#### 8.2.18 history：查看历史命令

- 功能：查看已执行过的命令历史，支持清除历史记录

- 基本语法：

    ```Bash
    
    history  # 查看所有历史命令
    history -c  # 清空历史命令（当前会话，重启终端后恢复）
    ```

#### 示例

```Bash

# 查看历史命令（默认保存1000条，可通过/etc/profile修改HISTSIZE）
history
# 清空当前会话历史命令
history -c
```

### 8.3 时间日期类命令

#### 8.3.1 date：显示或设置系统时间

- 基本语法：

    ```Bash
    
    date  # 显示当前时间
    date +"格式"  # 按指定格式显示时间
    date -s "时间字符串"  # 设置系统时间
    ```

#### 常用格式说明

|格式符|含义|
|---|---|
|%Y|4位年份（如2024）|
|%m|2位月份（01-12）|
|%d|2位日期（01-31）|
|%H|24小时制小时（00-23）|
|%M|分钟（00-59）|
|%S|秒（00-59）|
|%s|时间戳（从1970-01-01 00:00:00到当前的秒数）|
#### 示例

```Bash

# 显示当前时间（默认格式）
date
# 按指定格式显示（年-月-日 时:分:秒）
date +"%Y-%m-%d %H:%M:%S"
# 显示时间戳
date +%s
# 显示1小时前的时间
date -d "-1 hours ago" +"%Y-%m-%d %H:%M:%S"
# 设置系统时间（需root权限）
date -s "2024-06-19 20:52:22"
# 同步网络时间（需安装ntpdate）
ntpdate -u ntp1.aliyun.com
```

#### 8.3.4 cal：查看日历

- 基本语法：`cal [选项] [年份/月份]`

- 功能：显示日历，默认显示当前月份

#### 选项说明

|选项|功能|
|---|---|
|-3|显示当前月、上月和下月三个月日历|
|-m|周一作为一周的第一天（默认周日）|
#### 示例

```Bash

# 显示当前月份日历
cal
# 显示2024年全年日历
cal 2024
# 显示2024年6月日历
cal 6 2024
# 显示三个月日历（当前月前后各一个）
cal -3
# 周一作为一周第一天
cal -m
```

### 8.4 用户管理命令

#### 核心功能：用户的创建、密码设置、切换、删除、权限配置等

#### 常用命令示例

```Bash

# 1. 创建新用户（默认在/home目录创建同名家目录）
useradd lys
# 创建用户并指定家目录（自定义路径）
useradd -d /home/dave david

# 2. 设置用户密码（需root权限，密码输入时不显示）
passwd lys
# 示例：
# passwd lys
# 更改用户 lys 的密码 。
# 新的 密码：
# 重新输入新的 密码：
# passwd：所有的身份验证令牌已经成功更新。

# 3. 查看用户信息（验证用户是否存在）
id lys
# 输出：uid=1005(lys) gid=1005(lys) groups=1005(lys)

# 4. 查看系统所有用户（查看/etc/passwd文件）
less /etc/passwd
# 或 grep 过滤特定用户
grep lys /etc/passwd

# 5. 切换用户（su：switch user）
su lys  # 从root切换到lys（无需密码）
su - lys  # 切换用户并加载其环境变量
# 退出当前用户（回到上一级用户）
exit

# 6. 查看当前登录用户
who am i
# 或
who

# 7. 删除用户（仅删除用户，保留家目录）
userdel lys
# 删除用户及家目录（彻底删除）
userdel -r lys

# 8. 配置普通用户sudo权限（拥有root权限）
vim /etc/sudoers
# 在文件中添加（lys为用户名）
lys     ALL=(ALL)       ALL
# 保存退出（需:wq!强制保存，因文件为只读）
# 使用sudo执行root命令
sudo systemctl restart network

# 9. 将用户添加到指定组（usermod：user modify）
usermod -g 组名 用户名
# 示例：将lys添加到wheel组
usermod -g wheel lys
```

### 8.5 用户组管理命令

- 每个用户默认属于与同名的用户组（创建用户时自动创建）

- 组管理本质是更新/etc/group文件

#### 常用命令示例

```Bash

# 1. 新增用户组
groupadd dev_group

# 2. 修改用户组名称（-n：new name）
groupmod -n new_dev_group dev_group

# 3. 删除用户组（需确保组内无用户，否则删除失败）
groupdel new_dev_group
```

### 8.6 文件权限类命令

Linux是多用户系统，通过权限控制不同用户对文件/目录的访问权限，保障系统安全。

#### 8.6.1 文件属性解读

使用`ll`或`ls -l`查看文件属性，输出格式如下：

`-rw-r--r-- 1 root root 1024 10-23 16:56 test.txt`

#### 1. 权限字段解析（左起第1-10位）

|位置|含义|
|---|---|
|第1位|文件类型（-：文件，d：目录，l：链接文件）|
|第2-4位|属主（所有者）权限（u：user）|
|第5-7位|属组（同组用户）权限（g：group）|
|第8-10位|其他用户权限（o：other）|
#### 2. 权限符号含义

|符号|权限类型|对文件的作用|对目录的作用|
|---|---|---|---|
|r（read）|读权限|可读取文件内容|可ls查看目录内容|
|w（write）|写权限|可修改文件内容|可在目录内创建/删除/重命名文件|
|x（execute）|执行权限|可执行文件（如脚本、程序）|可cd进入目录|
|-|无权限|无法执行对应操作|无法执行对应操作|
#### 3. 其他字段解读

- 第11位（数字1）：链接数（文件为硬链接数，目录为子文件夹数）

- 第12位（root）：文件属主（所有者）

- 第13位（root）：文件属组

- 第14位（1024）：文件大小（默认字节）

- 第15-17位（10-23 16:56）：修改时间

- 第18位（test.txt）：文件名

#### 8.6.2 chmod：改变文件/目录权限

- 基本语法：

    ```Bash
    
    # 符号模式（推荐，直观）
    chmod [u/g/o/a] [+/-/=] [r/w/x] 文件/目录
    # 数字模式（高效，常用）
    chmod 数字组合 文件/目录
    ```

#### 1. 符号模式说明

|参数|含义|
|---|---|
|u/g/o/a|权限对象（u：属主，g：属组，o：其他用户，a：所有用户）|
|+/-/=|权限操作（+：添加，-：移除，=：设置唯一权限）|
|r/w/x|权限类型|
#### 2. 数字模式说明

- 权限对应数字：r=4，w=2，x=1，-=0

- 数字组合规则：属主权限+属组权限+其他用户权限（如755=u=rwx, g=rx, o=rx）

- 常用数字组合：

    - 777：所有用户拥有读、写、执行权限（慎用）

    - 755：属主rwx，属组rx，其他用户rx（常用目录/程序文件）

    - 644：属主rw，属组r，其他用户r（常用普通文件）

#### 示例

```Bash

# 符号模式：给属主添加执行权限
chmod u+x nginx.conf
# 符号模式：给所有用户添加读权限
chmod a+r test.txt
# 符号模式：移除其他用户的写权限
chmod o-w file.txt
# 符号模式：设置属组权限为rwx
chmod g=rwx dir
# 数字模式：设置文件权限为644
chmod 644 test.txt
# 数字模式：设置目录及内部所有内容权限为755（-R递归）
chmod -R 755 /home/lys
# 数字模式：所有用户可读可写可执行（慎用）
chmod 777 tempdir
```

#### 8.6.3 chown：改变文件/目录所有者

- 基本语法：`chown [选项] 新属主[:新属组] 文件/目录`

- 选项：`-R` 递归修改目录及内部所有文件的所有者

#### 示例

```Bash

# 改变文件所有者为lys
chown lys test.txt
# 同时改变所有者和属组（lys为所有者，dev_group为属组）
chown lys:dev_group test.txt
# 递归改变目录及内部所有内容的所有者
chown -R lys /home/lys/project
```

#### 8.6.4 chgrp：改变文件/目录属组

- 基本语法：`chgrp [新属组] 文件/目录`

- 功能：单独修改文件/目录的属组（与chown :新属组功能一致）

#### 示例

```Bash

# 改变文件属组为dev_group
chgrp dev_group test.txt
# 递归改变目录属组
chgrp -R dev_group /home/lys/project
```

### 8.7 搜索查找类命令

#### 8.7.1 find：查找文件或目录（递归遍历，精准查找）

- 基本语法：`find [搜索范围] [选项] [查找条件]`

- 功能：从指定目录开始递归遍历所有子目录，按条件查找文件/目录

#### 常用选项

|选项|功能|
|---|---|
|-name 文件名|按文件名查找（支持通配符*和?）|
|-user 用户名|查找属于指定用户的所有文件/目录|
|-size 文件大小|按文件大小查找（+大于，-小于，无符号等于）|
|-type f/d/l|按类型查找（f：文件，d：目录，l：链接文件）|
|-mtime +n/-n|按修改时间查找（+n：n天前，-n：n天内）|
#### 大小单位说明

|单位|含义|
|---|---|
|b|块（512字节）|
|c|字节|
|w|字（2字节）|
|k|千字节（KB）|
|M|兆字节（MB）|
|G|吉字节（GB）|
#### 示例

```Bash

# 按文件名查找（当前目录及子目录）
find -name nginx.conf
# 按路径+文件名查找（/root目录下）
find /root -name nginx.conf
# 按后缀查找所有.txt文件（通配符*）
find /home -name "*.txt"
# 按用户名查找（属于lys的文件）
find /home -user lys
# 按大小查找（大于1MB的文件）
find / -size +1M
# 按大小查找（小于100KB的文件）
find /tmp -size -100k
# 按类型查找（所有目录）
find /usr -type d -name "bin"
```

#### 8.7.2 locate：快速定位文件路径（基于数据库，高效）

- 原理：基于系统预构建的文件路径数据库（/var/lib/mlocate/mlocate.db），查询速度极快

- 基本语法：`locate 文件名`

- 注意：首次使用前需更新数据库（`updatedb`），数据库默认每天自动更新

#### 示例

```Bash

# 首次使用：更新数据库（需root权限）
updatedb
# 快速查找文件
locate nginx.conf
# 查找命令所在路径（结合which/whereis）
which ls  # 显示命令绝对路径（仅外部命令）
whereis locate  # 显示命令及帮助文档路径
```

#### 8.7.3 grep：过滤查找（结合管道符，文本内容查找）

- 功能：在文件或命令输出中查找匹配的字符串，支持正则表达式

- 基本语法：`grep [选项] 查找内容 源文件/管道输入`

- 管道符`|`：将前一个命令的输出作为后一个命令的输入

#### 常用选项

|选项|功能|
|---|---|
|-n|显示匹配行及行号|
|-i|忽略大小写匹配|
|-v|反向匹配（显示不包含查找内容的行）|
|-r|递归查找目录下所有文件|
#### 示例

```Bash

# 查找文件中包含"location"的行，并显示行号
grep -n "location" nginx.conf
# 忽略大小写查找
grep -i "hello" test.txt
# 反向查找（不包含"error"的行）
grep -v "error" /var/log/messages
# 递归查找目录下所有文件中包含"lys"的内容
grep -r "lys" /home/
# 结合管道符：查找当前目录下包含"test"的文件名
ls | grep "test"
# 结合管道符：查找进程中包含"java"的进程
ps aux | grep "java"
```

#### 拓展：wc命令（统计文本信息）

- 功能：统计文件的行数、单词数、字节数

- 基本语法：`wc [选项] 文件名`

- 示例：

```Bash

# 统计文件行数、单词数、字节数（默认）
wc nginx.conf
# 输出：136  302  3022 nginx.conf（行数 单词数 字节数 文件名）
# 仅统计行数
wc -l nginx.conf
# 仅统计单词数
wc -w nginx.conf
# 仅统计字节数
wc -c nginx.conf
```

### 8.8 压缩和解压类命令

#### 8.8.1 gzip/gunzip：文件压缩/解压（仅文件，不保留原文件）

- 特点：仅支持压缩文件，不支持目录；压缩后原文件消失，生成.gz后缀压缩包

- 基本语法：

    ```Bash
    
    # 压缩文件（生成.gz文件，原文件删除）
    gzip 文件名
    # 解压.gz文件（生成原文件，压缩包删除）
    gunzip 压缩包名.gz
    # 或使用gzip -d解压
    gzip -d 压缩包名.gz
    ```

#### 示例

```Bash

# 压缩单个文件
gzip test.txt  # 生成test.txt.gz，原文件删除
# 压缩多个文件（生成多个.gz文件）
gzip file1.txt file2.txt
# 解压文件
gunzip test.txt.gz  # 生成test.txt，压缩包删除
# 或
gzip -d test.txt.gz
```

#### 8.8.2 zip/unzip：文件/目录压缩/解压（跨平台，保留原文件）

- 特点：支持压缩文件和目录，保留原文件；压缩包后缀为.zip，跨Windows/Linux平台

- 基本语法：

    ```Bash
    
    # 压缩文件/目录（-r递归压缩目录）
    zip [选项] 压缩包名.zip 源文件/目录
    # 解压文件（-d指定解压目录）
    unzip [选项] 压缩包名.zip
    ```

#### 常用选项

|命令|选项|功能|
|---|---|---|
|zip|-r|递归压缩目录（含子目录和文件）|
|unzip|-d|指定解压后的文件存放目录|
#### 示例

```Bash

# 压缩单个文件（保留原文件）
zip test.zip test.txt
# 递归压缩目录（含所有内容）
zip -r logs.zip logs/
# 解压到当前目录
unzip test.zip
# 解压到指定目录（目录不存在会自动创建）
unzip -d ./tmp logs.zip
# 查看压缩包内容（不解压）
unzip -l logs.zip
```

#### 8.8.3 tar：打包/压缩/解压（Linux常用，支持目录）

- 特点：默认仅打包（生成.tar文件），结合选项可同时压缩；支持.gz/.bz2/.xz等格式，常用.tar.gz格式

- 基本语法：

    ```Bash
    
    # 打包压缩（-z：gzip压缩，-c：创建打包文件，-v：显示过程，-f：指定文件名）
    tar [选项] 打包压缩文件名.tar.gz 源文件/目录
    # 解压（-x：解压，-z：gzip解压，-v：显示过程，-f：指定文件名，-C：指定解压目录）
    tar [选项] 打包压缩文件名.tar.gz
    ```

#### 核心选项（助记：czvf打包，xzvf解压）

|选项|功能|助记|
|---|---|---|
|-c|生成.tar打包文件|create（创建）|
|-v|显示打包/解压过程|verbose（详细）|
|-f|指定打包/压缩文件名|file（文件）|
|-z|结合gzip压缩/解压|gzip（压缩格式）|
|-x|解压.tar文件|extract（提取）|
|-C|指定解压目录（需在解压时使用）|change directory（切换目录）|
#### 示例

```Bash

# 打包并压缩单个文件（.tar.gz格式）
tar -zcvf nginx.tar.gz nginx.conf
# 打包并压缩多个文件
tar -zcvf files.tar.gz file1.txt file2.txt
# 打包并压缩目录（递归）
tar -zcvf project.tar.gz /home/
```
> （注：文档部分内容可能由 AI 生成）