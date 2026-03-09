# Linux学习笔记 

## 1 Linux入门

### 1.1 概述

Linux内核最初由芬兰人Linux Torvalds在赫尔辛基大学上学时出于个人爱好编写。

Linux是一套免费使用和自由传播的类Unix操作系统，基于POSIX和UNIX，支持多用户、多任务、多线程和多CPU。它能运行主要的UNIX工具软件、应用程序和网络协议，支持32位和64位硬件，继承了Unix以网络为核心的设计思想，是性能稳定的多用户网络操作系统。

目前主流发行版：Ubuntu、RedHat、CentOS、Debian、Fedora、SuSE、OpenSUSE。

### 1.2 Linux和Windows区别

|比较维度|Windows|Linux|
|---|---|---|
|免费与收费|收费且价格较高|免费或仅需少许费用|
|软件与支持|软件数量和质量有优势，多为收费软件；由微软官方提供支持服务|开源自由软件，用户可修改定制和再发布；部分软件质量和体验欠缺；由全球Linux开发者和自由软件社区提供支持|
|安全性|需频繁打补丁更新，仍易中病毒木马|相对更安全，安全问题较少|
|使用习惯|纯图形界面操作，依赖鼠标键盘，上手容易|兼具图形界面和命令行操作，可仅用键盘完成所有操作，新手入门较难，熟练后效率极高|
|可定制性|封闭系统，可定制性差|开源系统，可定制化极强|
|应用场景|主要用于桌面操作系统|广泛用于服务器，支撑百度、谷歌、淘宝等软件和服务|
### 1.3 CentOS下载地址

- 网易镜像：[https://mirrors.163.com/centos/7/isos/](https://mirrors.163.com/centos/7/isos/)

- 搜狐镜像：[https://mirrors.sohu.com/centos/7/isos/](https://mirrors.sohu.com/centos/7/isos/)

## 2 VM与Linux的安装

具体安装步骤参考其他文章

## 3 Linux文件与目录

### 3.1 Linux文件

Linux系统中一切皆文件

### 3.2 Linux目录结构

核心目录：/root、/bin、/boot、/dev、/etc、/home、/var、/lib、/usr、/media等

|目录|含义|
|---|---|
|/bin|Binary的缩写，存放所有一般用户可使用的二进制可执行文件，如cat、chmod、mv、mkdir、cd等常用指令|
|/sbin|Super User专用，存放仅root用户有权限执行的可执行文件，如init、ip、mount等命令|
|/boot|存放开机引导文件，包括Linux内核文件、开机菜单及所有开机所需配置文件|
|/dev|device（设备）目录，所有设备以文件形式存放，如硬盘、键盘、鼠标、光驱等，访问该目录下的文件即访问对应设备|
|/etc|存放所有程序和系统的配置文件，如用户账号密码文件、各服务的起始文件、启动/停止单个程序的shell脚本；普通用户可查阅，仅root可修改|
|/home|系统默认用户家目录，新建用户时会自动在此创建以用户名命名的目录|
|/lib|library（库）目录，存放系统开机所需函数库及/bin、/sbin目录下命令调用的函数库|
|/lib64|存放支持64位格式的函数库（对应/lib）|
|/media|存放可移除媒体设备，如光盘、DVD等|
|/mnt|mount（挂载）目录，系统管理员临时挂载文件系统的安装点|
|/opt|optional（可选）目录，用于安装第三方软件（非系统自带软件）|
|/proc|特殊动态目录，维护系统信息和状态（包括当前运行进程信息），虚拟文件系统，不占用硬件容量|
|/root|系统管理员root的主目录|
|/run|存放最近一次开机后产生的信息，如当前用户、正在运行的守护进程等|
|/srv|service（服务）目录，存放服务启动后所需的数据|
|/sys|与/proc类似的虚拟文件系统，存放系统核心与硬件相关信息，管理设备文件，不占用硬件容量|
|/tmp|temporary（临时）目录，存放系统运行中的临时文件，所有用户可访问，系统重启时清空|
|/usr|存放绝大部分用户可访问的应用程序和文件，包括二进制文件、库文件、文档和二级程序源代码|
|/var|variable（可变）目录，存放日志、数据库等内容可能增长的文件|
## 4 VI/VIM编辑器

### 4.1 VIM是什么

- VI是Unix和类Unix操作系统中最通用的文本编辑器

- VIM是VI的增强版，性能更强大，支持语法颜色辨别，方便程序设计，与VI完全兼容

### 4.2 模式转换

VIM分为三种核心模式：

- 一般模式：快速编辑、光标跳转

- 插入模式：编辑文本内容

- 指令模式：搜索、替换、保存、退出等操作

### 4.3 一般模式（常用操作）

|语法|功能描述|
|---|---|
|yy|复制光标当前一行|
|y数字y|复制指定范围的行（从第几行到第几行）|
|y(shift+4)|复制当前光标到行尾的字符串|
|p|箭头移动到目标行后粘贴|
|u|撤销上一步操作|
|dd|删除光标当前行|
|d数字d|删除光标（含）后指定行数|
|x|剪切一个字母（等同于Del键）|
|X|剪切一个字母（等同于Backspace键）|
|w|切换到下一个词|
|e|快速跳转到下一个词尾|
|b|跳转到上一个词|
|yw|复制一个词|
|dw|删除一个词|
|shift+6|移动到行首|
|shift+4|移动到行尾|
|gg|移动到文档开头（页头）|
|G/L|移动到文档末尾（页尾）|
|数字+shift+g|移动到指定目标行|
|数字b|跳转到上n个词|
**行号显示控制**：

- 显示行号：`:set nu`

- 隐藏行号：`:set nonu`

### 4.4 插入模式

一般模式下无法编辑文本，需按下以下按键进入插入模式（左下角显示`INSERT`或`REPLACE`），按`Esc`键返回一般模式。

|按钮|功能|
|---|---|
|i|在当前光标前插入|
|a|在当前光标后插入|
|o|在当前光标行的下一行插入新行|
|I|在光标所在行的最前面插入|
|A|在光标所在行的最后面插入|
|O|在当前光标行的上一行插入新行|
### 4.5 指令模式

一般模式下输入`:/?`中的任意一个符号，光标移动到屏幕底部进入指令模式，支持搜索、保存、退出等操作。

|命令|功能|
|---|---|
|:w|保存文件|
|:q|退出VIM|
|:wq|保存并退出|
|:q!|不保存强制退出|
|/要查找的词|向下搜索指定词，n键查找下一个，N键向上查找|
|:noh|取消搜索高亮显示|
|:set nu|显示行号|
|:set nonu|关闭行号显示|
|:s /old/new|替换当前行匹配到的第一个old为new|
|:s /old/new/g|替换当前行匹配到的所有old为new|
|:%s/old/new|替换文档中每一行匹配到的第一个old为new|
|:%s/old/new/g|替换文档中所有的old为new（常用）|
#### 其他重要命令

1. 寄存器使用：拷贝/粘贴/删除命令前加`"x`（x=a..z,*），如`"ay$`将剩余行内容拷贝到寄存器a

2. 重复操作：命令前加数字，如`2p`（粘贴2次）、`d2w`（删除2个词）、`5i`（插入5次）

3. 快捷操作：ZZ（保存退出）、ZQ（不保存退出）

4. 屏幕定位：zt（光标行移到屏幕顶端）、zb（移到底端）、zz（移到中间）

5. 其他：gg（文首，VIM专属）、gf（打开光标处文件名，VIM专属）

### 4.6 模式之间转换

```Plain Text

命令行启动VI/VIM（vi 文件名）→ 一般模式（核心操作：删除、复制、粘贴）
→ 按i/a/o等键 → 插入模式（编辑文本）→ 按Esc键 → 一般模式
→ 按:/?等键 → 指令模式（保存、退出、搜索、替换）→ 执行命令后返回一般模式
```

## 5 网络配置和系统管理操作

### 5.1 查看网络IP和网关

#### 1）查看虚拟网络编辑

Windows系统查看IP：

```Bash

ipconfig
```

#### 2）虚拟机网卡配置

- **桥接模式**：虚拟机直接连接外部物理网络，主机充当网桥；可直接访问外部网络，且在同一路由器内可见（占用局域网IP）

- **NAT模式（Network Address Translation）**：虚拟机与主机构建专用网络，通过NAT设备转换IP；虚拟机可访问外部网络，但外部网络无法访问虚拟机

- **仅主机模式**：虚拟机仅与主机共享专用网络，无法与外部网络通信

#### 3）查看网关

```Bash

ifconfig
```

### 5.2 配置网络IP（静态IP）

```Bash

# 进入网络配置文件目录
cd /etc/sysconfig/network-scripts
# 编辑网卡配置文件（按Tab键补全文件名，如ifcfg-eth0、ifcfg-ens33等）
vim ifcfg-xxx
```

修改配置内容：

```Bash

# 将DHCP自动获取改为静态IP
BOOTPROTO="static"
# 设置IP地址
IPADDR=192.162.202.100
# 设置网关
GATEWAY=192.168.202.2
# 设置域名解析器
DNS1=192.168.202.2
```

重启网络服务：

```Bash

service network restart
```

#### 常见问题解决

1. 物理机能ping通虚拟机，虚拟机ping不通物理机：关闭物理机防火墙

2. 虚拟机能ping通物理机，无法ping通外网：检查DNS设置

3. 虚拟机ping [www.baidu.com](http://www.baidu.com)显示域名未知：验证GATEWAY和DNS配置是否正确

4. 上述设置无效：关闭并禁用NetworkManager服务

    ```Bash
    
    systemctl stop NetworkManager  # 关闭
    systemctl disable NetworkManager  # 禁用
    ```

5. systemctl status network报错：检查网卡配置文件（如ifcfg-ens33）

### 5.3 配置主机名

#### 5.3.1 修改主机名称

```Bash

# 查看当前主机名
hostname

# 方法1：编辑配置文件（需重启服务器）
vim /etc/hostname  # 修改文件内的值
reboot

# 方法2：使用hostnamectl（无需重启）
# 查看主机相关信息
hostnamectl
# 修改主机名为lys（立即生效）
hostnamectl set-hostname lys
```

#### 5.3.2 修改hosts映射文件

##### Linux系统

```Bash

vim /etc/hosts
```

##### Windows系统

编辑文件路径：`C:\Windows\System32\drivers\etc\hosts`

## 6 远程登录

### Windows命令行连接

```Bash

# 格式1：默认端口22
ssh root@11.212.33.44
# 格式2：指定端口
ssh zhangsan@11.212.33.44 -p Port
```

### 其他工具

可使用Xshell等可视化工具进行远程登录

## 7 系统管理

### 7.1 Linux中的进程和服务

- **进程（process）**：正在执行的程序或命令

- **服务（service）**：启动后常驻内存的进程

### 7.2 service服务管理（CentOS 6版本，了解）

#### 基本语法

```Bash

service 服务名 start | stop | restart | status
```

#### 经验技巧

查看系统服务：`ls /etc/init.d/`

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

chkconfig  # 查看所有服务器自启配置
chkconfig 服务名 off  # 关闭指定服务自动启动
chkconfig 服务名 on  # 开启指定服务自动启动
chkconfig 服务名 --list  # 查看服务开机启动状态
```

#### 案例实操

```Bash

# 开启/关闭network服务自动启动
chkconfig network on
chkconfig network off

# 开启/关闭network服务指定级别的自动启动
chkconfig --level 指定级别 network on
chkconfig --level 指定级别 network off
```

### 7.4 systemctl（CentOS 7版本，重点掌握）

#### 基本语法

```Bash

systemctl start | stop | restart | status 服务名
```

#### 经验技巧

查看系统服务：`ls -al /usr/lib/systemd/system`

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

### 7.5 systemctl设置后台服务自启

#### 基本语法

```Bash

systemctl list-unit-files  # 查看所有服务开机启动状态
systemctl disable service_name  # 关闭指定服务自动启动
systemctl enable service_name  # 开启指定服务自动启动
```

#### 案例实操

```Bash

# 开启/关闭防火墙服务自动启动
systemctl enable firewalld.service
systemctl disable firewalld.service
```

### 7.6 系统运行级别

#### 1. Linux传统运行级别（7种）

- 0：系统停机状态（不可设为默认，否则无法正常启动）

- 1：单用户工作状态（root权限，系统维护，禁止远程登录）

- 2：多用户状态（无NFS，不支持网络）

- 3：安全多用户状态（有NFS，登录后进入控制台命令行模式）

- 4：系统未使用，保留

- 5：X11控制台（登录后进入图形GUI模式）

- 6：系统正常关闭并重启（不可设为默认，否则无法正常启动）

#### 2. CentOS7简化运行级别

- multi-user.target：等价于传统级别3（多用户、有网、无图形界面）

- graphical.target：等价于传统级别5（多用户、有网、有图形界面）

#### 3. 查看当前运行级别

```Bash

systemctl get-default
# 或编辑配置文件（不推荐直接修改）
vim /etc/inittab
```

#### 4. 修改当前运行级别

```Bash

systemctl set-default TARGET.target  # TARGET为multi-user或graphical
```

### 7.7 关闭防火墙

#### 1. 临时关闭防火墙（重启后失效）

```Bash

# 查看防火墙状态
systemctl status firewalld
# 停止防火墙
systemctl stop firewalld
```

#### 2. 开机禁用防火墙（永久生效）

```Bash

# 查看防火墙开机启动状态
systemctl is-enabled firewalld.service
# 禁用开机启动
systemctl disable firewalld.service
```

#### 查看所有服务开机自启状态

```Bash

systemctl list-unit-files
```

### 7.8 关机重启命令

#### 基本语法

|命令|功能|
|---|---|
|sync|将内存数据同步到硬盘|
|halt|停机，关闭系统（不断电）|
|poweroff|关机并断电|
|reboot|重启（等同于shutdown -r now）|
|shutdown [选项] 时间|定时关机/重启|
#### 常用操作

```Bash

# 1分钟后关机
shutdown

# 3分钟后关机
shutdown 3

# 指定时间关机（如15:00）
shutdown 15:00

# 取消关机
shutdown -c

# 立刻关机
shutdown now
shutdown -h now

# 立刻重启
shutdown -r now
reboot

# 将内存数据同步到硬盘（关机/重启前推荐执行）
sync
```

#### 经验技巧

Linux采用“预读迟写”机制提升磁盘读写效率，文件保存时数据可能先存于缓冲区，未立即写入磁盘。关机/重启前执行`sync`可避免数据丢失。

## 8 常用基本命令

Shell是命令解释器，提供交互式文本控制台界面，用户输入命令后由Shell解释并交给内核执行。

### 8.1 帮助命令

#### 8.1.1 man获取帮助信息

#### 基本语法

```Bash

man [命令或配置文件]  # 获取详细帮助信息
```

#### 示例

```Bash

man -f cd  # 查看cd命令的帮助文档分类
cd (1)               - bash built-in commands, see bash(1)
cd (n)               - Change working directory

# 查看第1类帮助文档（数字对应上面的括号内容）
man 1 cd
```

#### 帮助文档结构说明

|sections|功能|
|---|---|
|NAME|命令名称和单行描述|
|SYNOPSIS|命令使用格式|
|DESCRIPTION|命令功能详细说明|
|EXAMPLES|命令使用示例|
|SEE ALSO|相关主题（其他帮助文档）|
#### 8.1.2 help获取shell内置命令帮助

- **内置命令**：系统启动时随Shell加载，常驻内存（如cd、echo）

- **外部命令**：独立于Shell的可执行文件（如ls、man）

#### 判断内置命令

```Bash

type 命令名
# 示例：cd是内置命令
type cd
cd is a shell builtin
```

#### 基本语法

```Bash

help 命令名  # 仅适用于内置命令
```

#### 示例

```Bash

help cd  # 查看cd命令的帮助信息
```

#### 8.1.3 常用快捷键

|快捷键|功能|
|---|---|
|Ctrl + C|停止当前进程|
|Ctrl + L|清屏（等同于clear；彻底清屏用reset）|
|Tab|命令/文件名自动补全（防止敲错）|
|上下箭头|查找历史执行命令|
### 8.2 文件目录类命令

#### 8.2.1 pwd：显示当前工作目录绝对路径

```Bash

pwd  # print working directory的缩写
```

#### 8.2.2 ls：列出目录内容

#### 基本语法

```Bash

ls [选项] [文件或目录]
```

#### 选项说明

|选项|功能|
|---|---|
|-a|显示所有文件（包括隐藏文件，以.开头的文件）|
|-l|长格式显示（包含文件属性、权限、大小等信息），等价于ll|
|-lh|人性化显示文件大小（以G/M/K为单位）|
#### 显示说明

每行输出信息依次为：文件类型与权限 → 链接数 → 文件属主 → 文件属组 → 文件大小（字节） → 最后修改时间 → 文件名

#### 8.2.3 cd：切换目录

|参数|功能|
|---|---|
|cd 绝对路径|切换到指定绝对路径（如cd /home/lys）|
|cd 相对路径|切换到指定相对路径（如cd ../test）|
|cd ~ 或 cd|回到当前用户家目录|
|cd -|回到上一次所在目录|
|cd ..|回到当前目录的上一级目录|
|cd -P|跳转到实际物理路径（忽略快捷方式路径）|
#### 8.2.4 mkdir：创建目录

```Bash

# 创建单个目录
mkdir a

# 递归创建多级目录（推荐）
mkdir -p a/b/c

# 手动创建多级目录（繁琐，不推荐）
mkdir a a/b a/b/c
```

#### 8.2.5 rmdir：删除空目录

```Bash

# 删除单个空目录
rmdir a

# 删除多级空目录（需从子目录开始）
rmdir a/b/c
```

#### 8.2.6 touch：创建空文件

```Bash

touch 文件名  # 如touch test.txt
```

#### 8.2.7 cp：复制文件或目录

```Bash

# 基本语法
cp [选项] 源文件/目录 目标文件/目录

# 复制文件
cp nginx.conf nginx.conf2

# 递归复制整个文件夹（-r：递归）
cp -r logs logs2

# 不强制覆盖（避免误删，推荐）
\cp 源文件 目标文件

# 查看系统别名（如cp默认是否带-i选项）
alias
```

#### 8.2.8 rm：删除文件或目录

#### 选项说明

|选项|功能|
|---|---|
|-r|递归删除目录及所有内容|
|-f|强制删除，不提示确认|
|-v|显示删除详细过程|
#### 常用操作

```Bash

# 删除文件
rm test.txt

# 递归删除目录（谨慎使用）
rm -r dir

# 强制递归删除目录（无提示，极其谨慎）
rm -rf dir
```

#### 8.2.9 mv：移动文件/目录或重命名

```Bash

# 重命名文件/目录
mv oldNameFile newNameFile  # 如mv test.txt demo.txt

# 移动文件/目录到目标路径
mv /tmp/moveFile /targetFolder
```

#### 8.2.10 cat：查看文件内容

```Bash

# 基本语法
cat [选项] 文件名

# 显示所有行号（包括空行）
cat -n 文件名
```

#### 8.2.11 more：文件内容分屏查看器

基于VI编辑器的文本过滤器，全屏幕按页显示文本内容，支持快捷键操作。

|操作|功能说明|
|---|---|
|空白键（Space）|向下翻一页|
|Enter|向下翻一行|
|q|立即退出more|
|Ctrl + F|向下滚动一屏|
|Ctrl + B|返回上一屏|
|=|显示当前行号|
|:f|显示文件名和当前行号|
#### 8.2.12 less：分屏显示文件内容（适合大文件）

功能与more类似，但更强大，支持按需加载内容（大文件打开效率更高）。

```Bash

less 文件名
```

|操作|功能说明|
|---|---|
|空白键|向下翻一页|
|PageDown|向下翻一页|
|PageUp|向上翻一页|
|/字符串|向下搜索指定字符串（n：下一个，N：上一个）|
|?字符串|向上搜索指定字符串（n：上一个，N：下一个）|
|q|退出less|
#### 8.2.13 echo：输出内容到控制台

```Bash

# 基本语法
echo [选项] 输出内容
```

#### 选项说明

- `-e`：支持反斜线控制的字符转换

|控制字符|功能|
|---|---|
|\\|输出\本身|
|\n|换行符|
|\t|制表符（Tab键）|
#### 示例

```Bash

# 输出普通文本
echo "Hello Linux"

# 支持换行和制表符
echo -e "Name\tAge\nTom\t20"

# 查看系统环境变量（按Tab键补全变量名）
echo $PATH
echo $HOME
```

#### 8.2.14 head：显示文件头部内容

默认显示前10行，可通过`-n`指定行数。

```Bash

# 显示文件前10行（默认）
head 文件名

# 显示文件前5行
head -n 5 文件名
```

#### 8.2.15 tail：显示文件尾部内容

```Bash

# 显示文件最后5行
tail -n 5 文件名

# 实时监听文件内容变化（如日志文件）
tail -f 文件名
```

#### 监听控制

- Ctrl + S：暂停监听

- Ctrl + Q：恢复监听

#### 查看文件索引

```Bash

ls -i 文件名  # 如ls -i web.log
```

#### 8.2.16 输出重定向和追加

|命令|功能描述|
|---|---|
|ls -l > a.txt|将列表内容覆盖写入a.txt（原有内容清空）|
|ls -al >> aa.txt|将列表内容追加到aa.txt末尾（原有内容保留）|
|cat 文件1 > 文件2|将文件1的内容覆盖到文件2|
|echo "内容" >> 文件|将指定内容追加到文件末尾|
#### 8.2.17 ln：创建链接（软链接/硬链接）

#### 软链接（符号链接）

类似Windows快捷方式，有独立数据块，存放目标文件路径。

```Bash

# 创建软链接（-s：软链接）
ln -s 目标文件/目录 链接名
# 示例：给web.log创建软链接web
ln -s web.log web

# 查看软链接（前缀为l）
ll
lrwxrwxrwx 1 root root       7 May 16 00:36 web -> web.log

# 进入软链接对应的实际路径
cd -P 软链接名

# 删除软链接（注意：不要加/，否则会删除目标目录内容）
rm -rf 软链接名  # 正确：rm -rf web
# 错误：rm -rf web/（会删除web.log对应的内容）
```

#### 硬链接

相当于文件的副本，与目标文件共享inode，修改任一文件都会影响对方。

```Bash

ln 目标文件 链接名
```

#### 8.2.18 history：查看历史命令

```Bash

# 查看所有执行过的历史命令
history

# 清空历史命令（仅当前会话，永久清空需删除配置文件）
history -c
```

### 8.3 时间日期类命令

#### 基本语法

```Bash

date [选项] +[格式]  # 显示时间
date -s "日期时间"    # 设置系统时间
```

#### 8.3.1 date：显示/设置当前时间

#### 显示时间

```Bash

# 显示当前完整时间
date

# 显示年/月/日/时/分/秒（单独显示）
date +%Y  # 年（如2025）
date +%m  # 月（01-12）
date +%d  # 日（01-31）
date +%H  # 时（24小时制）
date +%M  # 分（00-59）
date +%S  # 秒（00-59）

# 自定义格式显示（常用）
date "+%Y-%m-%d %H:%M:%S"

# 查看时间戳（从1970-01-01 00:00:00到当前的秒数）
date +%s

# 显示相对时间（如1小时前）
date -d "-1 hours ago"
```

#### 设置系统时间

```Bash

date -s "2022-06-19 20:52:22"
```

#### 同步网络时间

```Bash

ntpdate -u ntp1.aliyun.com  # 阿里云时间服务器
```

#### 8.3.4 cal：查看日历

```Bash

# 显示本月日历（默认）
cal

# 显示最近3个月日历
cal -3

# 周一作为每周第一天
cal -m

# 显示2022年全年日历
cal 2022

# 显示本年度日历
cal -y
```

### 8.4 用户管理命令

```Bash

# 1. 创建新用户
useradd 用户名  # 如useradd lys
# 查看创建的用户家目录（默认在/home下）
cd /home

# 2. 创建用户并指定家目录
useradd -d /home/dave david  # 用户名david，家目录/home/dave

# 3. 设置用户密码
passwd 用户名  # 如passwd lys（输入密码时不显示）

# 4. 查看用户信息（验证用户是否存在）
id 用户名  # 如id lys
# 输出示例：uid=1005(lys) gid=1005(lys) groups=1005(lys)

# 5. 查看系统所有用户
less /etc/passwd

# 6. 切换用户（su：switch user）
su 用户名  # 如su lys（从root切换到lys）
# 退出当前用户，返回上一级用户
exit

# 7. 查看当前登录用户
who am i

# 8. 删除用户（仅删除用户，保留家目录）
userdel 用户名  # 如userdel lys

# 9. 彻底删除用户（包括家目录）
userdel -r 用户名  # 如userdel -r lys

# 10. 设置普通用户具有root权限（sudo）
vim /etc/sudoers
# 在文件中添加（lys为用户名）
lys     ALL=(ALL)       ALL
# 普通用户使用root权限执行命令
sudo 命令  # 如sudo systemctl restart network

# 11. 将用户添加到指定组
usermod -g 组名 用户名
```

### 8.5 用户组管理命令

每个用户默认属于与用户名同名的用户组，用户组管理本质是更新`/etc/group`文件。

```Bash

# 1. 新增用户组
groupadd 组名  # 如groupadd dev

# 2. 修改用户组名称
groupmod -n 新组名 旧组名  # 如groupmod -n develop dev

# 3. 删除用户组（需确保组内无用户）
groupdel 组名  # 如groupdel develop
```

### 8.6 文件权限类命令

Linux是多用户系统，通过文件权限控制不同用户的访问权限，使用`ll`或`ls -l`查看文件属性。

#### 8.6.1 文件属性说明

文件属性的10个字符含义（从左到右）：

```Plain Text

- rw-rw-r-- 1 z3 z3 8 10-23 16:56 a.txt
```

1. 第0位：文件类型

    - `-`：普通文件

    - `d`：目录

    - `l`：链接文件（软链接）

2. 第1-3位：文件属主（所有者）权限（User）

3. 第4-6位：文件属组（同组用户）权限（Group）

4. 第7-9位：其他用户权限（Other）

#### 权限符号含义

|符号|权限类型|作用于文件|作用于目录|
|---|---|---|---|
|r|可读（read）|可读取、查看文件内容|可使用ls查看目录内容|
|w|可写（write）|可修改文件内容（不代表可删除文件）|可在目录内创建、删除、重命名文件/目录|
|x|可执行（execute）|可被系统执行（如脚本、程序）|可进入该目录（cd命令）|
|-|无对应权限|-|-|
#### 补充说明

- 删除文件的前提：对文件所在目录有写权限，而非对文件本身有写权限

- 链接数含义：文件的硬链接个数；目录的子目录个数（含.和..）

#### 8.6.2 chmod：改变文件权限

权限设置支持两种方式：符号法和数字法

#### 符号法语法

```Bash

chmod [u|g|o|a] [+-=] [rwx] 文件/目录
```

- u：属主（User）

- g：属组（Group）

- o：其他用户（Other）

- a：所有用户（All，默认）

- +：添加权限

- -：移除权限

- =：设置权限（覆盖原有权限）

#### 示例

```Bash

# 给文件属主添加执行权限
chmod u+x nginx.conf

# 给所有用户添加执行权限
chmod a+x nginx.conf

# 移除属组的写权限
chmod g-w nginx.conf

# 给所有用户设置读写执行权限（覆盖原有）
chmod a=rwx nginx.conf
```

#### 数字法语法

权限对应数字：r=4，w=2，x=1，无权限=0

- 属主权限：u_num = r(4)+w(2)+x(1)

- 属组权限：g_num = r(4)+w(2)+x(1)

- 其他用户权限：o_num = r(4)+w(2)+x(1)

- 完整权限数字：u_num+g_num+o_num（如777、644）

#### 示例

```Bash

# 给所有用户设置读写执行权限（7=4+2+1）
chmod 777 nginx.conf

# 递归设置目录及所有子文件权限（-R：递归）
chmod -R 777 /home/lys

# 常用权限：属主读写执行，属组读执行，其他读执行（755）
chmod 755 shell.sh
```

#### 8.6.3 chown：改变文件所有者

```Bash

# 基本语法
chown [选项] 新属主 文件/目录

# 改变文件所有者为lys
chown lys a.txt

# 递归改变目录及所有子文件的所有者（-R：递归）
chown -R lys /home/lys/dir
```

#### 8.6.4 chgrp：改变文件属组

```Bash

# 基本语法
chgrp 新属组 文件/目录

# 改变文件属组为root
chgrp root a.txt

# 递归改变目录属组
chgrp -R dev /home/lys/project
```

### 8.7 搜索查找类命令

#### 8.7.1 find：查找文件或目录

从指定目录向下递归遍历所有子目录，按条件查找文件/目录。

#### 基本语法

```Bash

find [搜索范围] [选项] [查找条件]
```

#### 选项说明

|选项|功能|
|---|---|
|-name 文件名|按文件名查找（支持通配符*和?）|
|-user 用户名|查找属于指定用户的所有文件|
|-size 文件大小|按文件大小查找（单位：b=块(512字节)、c=字节、w=字(2字节)、k=千字节、M=兆字节、G=吉字节）|
#### 示例

```Bash

# 1. 按文件名查找（当前目录及子目录）
find -name nginx.conf

# 2. 按路径+文件名查找（/root目录及子目录）
find /root -name nginx.conf

# 3. 按文件后缀查找（所有.txt文件）
find -name "*.txt"

# 4. 按用户名查找（查找属于lys的文件）
find /home -user lys

# 5. 按文件大小查找（+大于，-小于）
find -size +1M  # 查找大于1兆的文件
find -size -100k  # 查找小于100千字节的文件
find -size 512c  # 查找等于512字节的文件
```

#### 8.7.2 locate：快速定位文件路径

基于预构建的文件路径数据库（/var/lib/mlocate/mlocate.db），查询速度极快，无需遍历文件系统。

#### 基本语法

```Bash

locate 文件名
```

#### 注意事项

- 首次使用前需创建数据库：`updatedb`

- 数据库默认每天更新，新增文件后需手动执行`updatedb`更新

#### 示例

```Bash

# 创建数据库（首次使用）
updatedb

# 快速查找nginx.conf文件
locate nginx.conf

# 查看命令所在路径（结合which/whereis）
which ls  # 查看ls命令路径
whereis locate  # 查看locate命令及帮助文档路径
```

#### 8.7.3 grep：过滤查找及管道符

- **管道符** **`|`**：将前一个命令的输出作为后一个命令的输入

- **grep**：过滤查找符合条件的文本内容

#### 基本语法

```Bash

grep [选项] 查找内容 源文件
# 结合管道符
命令 | grep [选项] 查找内容
```

#### 选项说明

- `-n`：显示匹配行及行号

- `-i`：忽略大小写

- `-v`：反向匹配（显示不包含查找内容的行）

#### 示例

```Bash

# 1. 查找文件中包含location的行，并显示行号
grep -n location nginx.conf

# 2. 过滤目录中包含test的文件（结合ls命令）
ls /home | grep -n test

# 3. 查看进程中包含java的进程（结合ps命令）
ps aux | grep java

# 4. 统计文件中匹配内容的行数
grep -c "error" app.log
```

#### wc：统计文本信息

```Bash

wc 文件名  # 输出：行数 单词数 字节数 文件名
# 示例
wc nginx.conf
136  302 3022 nginx.conf  # 136行，302个单词，3022字节
```

### 8.8 压缩和解压类命令

#### 8.8.1 gzip/gunzip：压缩/解压文件

- 仅支持压缩文件，不支持目录

- 压缩后删除原文件

- 多个文件压缩后生成多个压缩包（.gz后缀）

#### 示例

```Bash

# 压缩文件（生成nginx.conf.gz，删除原文件）
gzip nginx.conf

# 解压文件（生成nginx.conf，删除压缩包）
gunzip nginx.conf.gz

# 压缩多个文件（生成nginx.conf.gz和nginx.conf2.gz）
gzip nginx.conf nginx.conf2
```

#### 8.8.2 zip/unzip：压缩/解压文件（跨平台）

支持Windows/Linux跨平台使用，可压缩目录，保留原文件。

#### 基本语法

```Bash

# 压缩
zip [选项] 压缩包名 文件/目录
# 解压
unzip [选项] 压缩包名
```

#### 选项说明

- `zip -r`：递归压缩目录

- `unzip -d`：指定解压后文件的存放目录

#### 示例

```Bash

# 1. 压缩目录（递归压缩logs目录，生成logs.zip）
zip -r logs.zip logs/

# 2. 压缩多个文件（生成files.zip）
zip files.zip nginx.conf test.txt

# 3. 解压压缩包到指定目录（解压到./tmp目录）
unzip -d ./tmp logs.zip

# 4. 查看压缩包内容（不解压）
unzip -l logs.zip
```

#### 8.8.3 tar：打包压缩/解压（Linux常用）

支持打包并压缩目录，压缩后文件格式为`.tar.gz`（或`.tgz`）。

#### 基本语法

```Bash

# 打包压缩
tar [选项] 压缩包名 待压缩文件/目录
# 解压
tar [选项] 压缩包名 -C 目标目录
```

#### 核心选项（常用组合：zcvf打包压缩，zxvf解压）

|选项|功能|助记|
|---|---|---|
|-c|生成.tar打包文件|create（创建）|
|-v|显示打包/解压详细过程|verbose（详细）|
|-f|指定压缩包文件名|file（文件）|
|-z|结合gzip进行压缩/解压|gzip（压缩格式）|
|-x|解压.tar文件|extract（提取）|
|-C|指定解压目标目录|change directory（切换目录）|
#### 示例

```Bash

# 1. 打包压缩单个文件（生成nginx.tar.gz）
tar -zcvf nginx.tar.gz nginx.conf

# 2. 打包压缩多个文件（生成nginx-all.tar.gz）
tar -zcvf nginx-all.tar.gz nginx.conf nginx.conf2

# 3. 打包压缩目录（生成logs.tar.gz）
tar -zcvf logs.tar.gz logs/

# 4. 解压到指定目录（解压到./tmp目录）
mkdir tmp
tar -zxvf nginx.tar.gz -C tmp/

# 5. 解压不显示过程（静默解压）
tar -zxf logs.tar.gz

# 6. 查看压缩包内容（不解压）
tar -ztf nginx.tar.gz
```

### 8.9 磁盘查看和分区类命令

#### 8.9.1 du：查看文件和目录占用磁盘空间

du（disk usage）：显示目录下每个文件/子目录的磁盘占用情况。

#### 基本语法

```Bash

du [选项] 目录/文件
```

#### 选项说明

|选项|功能|
|---|---|
|-h|人性化显示（G/M/K单位）|
|-a|显示所有文件和子目录的占用大小（默认仅显示目录）|
|-c|显示所有文件/目录总大小|
|-s|仅显示总大小（不显示子目录详情）|
|--max-depth=n|指定统计子目录深度（n为数字，如1仅统计一级子目录）|
#### 示例

```Bash

# 1. 查看当前目录总大小（人性化显示）
du -sh

# 2. 查看当前目录一级子目录大小
du --max-depth=1 -ah

# 3. 查看/home/lys目录总大小
du -sh /home/lys

# 4. 查看文件占用大小
du -h test.txt
```

#### 8.9.2 df：查看磁盘空间使用情况

df（disk free）：显示文件系统的整体磁盘占用情况，包括总空间、已用空间、剩余空间等。

#### 基本语法

```Bash

df [选项]
```

#### 选项说明

- `-h`：人性化显示（G/M/K单位）

#### 示例

```Bash

# 查看所有文件系统磁盘使用情况
df -h
```

#### 8.9.3 lsblk：查看设备挂载情况

```Bash

# 查看设备挂载概览
lsblk

# 查看详细设备信息（包括文件系统类型）
lsblk -f
```

#### 8.9.4 mount/umount：挂载/卸载设备

Linux中所有分区需挂载到目录后才能使用，挂载本质是将设备与目录关联。

#### 基本语法

```Bash

# 挂载设备
mount [-t 文件系统类型] [-o 选项] 设备名 挂载点
# 卸载设备
umount 设备名 或 umount 挂载点
```

#### 参数说明

|参数|功能|
|---|---|
|-t vfstype|指定文件系统类型（如ext4、ntfs、vfat、iso9660等，默认自动识别）|
|-o options|挂载选项（ro：只读，rw：读写，loop：挂载文件为设备，iocharset：指定字符集）|
|设备名|要挂载的设备（如/dev/sdb1、/dev/cdrom）|
|挂载点|关联的目录（如/mnt/cdrom）|
#### 示例

```Bash

# 1. 挂载光盘（设备/dev/cdrom，挂载点/mnt/cdrom）
mkdir /mnt/cdrom
mount /dev/cdrom /mnt/cdrom

# 2. 挂载U盘（假设设备为/dev/sdb1，文件系统vfat）
mount -t vfat /dev/sdb1 /mnt/usb

# 3. 挂载ISO文件（loop选项）
mount -o loop CentOS-7-x86_64-DVD-1810.iso /mnt/iso

# 4. 卸载设备（两种方式）
umount /dev/cdrom
umount /mnt/cdrom
```

#### 设置开机自动挂载

编辑`/etc/fstab`文件，添加挂载配置（重启后生效）：

```Bash

vim /etc/fstab
# 添加格式：设备名/UUID 挂载点 文件系统类型 选项 0 0
# 示例：挂载光盘
/dev/cdrom /mnt/cdrom iso9660 defaults 0 0
```

#### 8.9.5 fdisk：磁盘分区

用于查看和管理磁盘分区（需root权限）。

#### 基本语法

```Bash

# 查看所有磁盘分区详情
fdisk -l

# 管理指定磁盘分区（如/dev/sda）
fdisk /dev/sda
```

#### 分区操作按键说明（进入fdisk交互模式后）

|按键|功能|
|---|---|
|m|显示命令列表|
|p|显示当前磁盘分区情况|
|n|新增分区|
|d|删除分区|
|w|保存分区信息并退出|
|q|不保存分区信息直接退出|
#### 分区信息说明

|字段|含义|
|---|---|
|Device|分区设备名（如/dev/sda1）|
|Boot|是否为引导分区（*表示是）|
|Start|分区起始磁柱|
|End|分区结束磁柱|
|Blocks|分区容量（单位：块）|
|Id|分区类型ID|
|System|分区类型（如Linux、NTFS、FAT32等）|
### 8.10 进程管理类命令

进程是正在执行的程序或命令，每个进程有独立地址空间并占用系统资源；服务是启动后常驻内存的进程。

#### 8.10.1 ps：查看当前系统进程状态

ps（process status）：查看系统进程的静态快照。

#### 基本语法

```Bash

# 常用组合1：查看所有进程（含详细信息）
ps aux

# 常用组合2：查看进程及父子关系
ps -ef

# 过滤指定进程（如java进程）
ps aux | grep java
ps -ef | grep java
```

#### 选项说明

|选项|功能|
|---|---|
|a|列出所有带有终端的用户进程|
|x|列出当前用户所有进程（含无终端进程）|
|u|人性化显示（含用户、CPU、内存占用等）|
|-e|列出所有进程|
|-f|显示完整格式（含PID、PPID等）|
#### 1. ps aux显示信息说明

|字段|含义|
|---|---|
|USER|进程所属用户|
|PID|进程ID（唯一标识）|
|%CPU|进程占用CPU百分比|
|%MEM|进程占用物理内存百分比|
|VSZ|进程占用虚拟内存大小（KB）|
|RSS|进程占用实际物理内存大小（KB）|
|TTY|进程运行的终端（tty1-5：本地字符终端，pts/0-255：虚拟终端）|
|STAT|进程状态（R：运行，S：睡眠，T：暂停，Z：僵尸，s：含子进程，l：多线程，+：前台，<：高优先级，N：低优先级）|
|START|进程启动时间|
|TIME|进程占用CPU的运算时间|
|COMMAND|启动进程的命令及参数|
#### 2. ps -ef显示信息说明

|字段|含义|
|---|---|
|UID|用户ID|
|PID|进程ID|
|PPID|父进程ID（Parent PID）|
|C|CPU优先级因子（数字越大，CPU密集型，优先级越低；反之越高）|
|STIME|进程启动时间|
|TTY|运行终端|
|TIME|CPU占用时间|
|CMD|启动命令及参数|
#### 查看守护进程

```Bash

# 查看系统所有服务（守护进程通常以d.service结尾）
ls /usr/lib/systemd/system
ls /usr/lib/systemd/system | grep d.service
```

#### 8.10.2 kill：终止进程

#### 基本语法

```Bash

# 通过PID终止进程
kill [选项] 进程PID

# 通过进程名终止进程（支持通配符）
killall 进程名
```

#### 选项说明

- `-9`：强制终止进程（立即停止，慎用）

- `-15`：默认选项，正常终止进程（允许进程清理资源）

#### 示例

```Bash

# 1. 查看java进程PID
ps aux | grep java

# 2. 正常终止进程（PID为12345）
kill 12345

# 3. 强制终止进程（PID为12345）
kill -9 12345

# 4. 终止所有java进程（支持通配符）
killall java

# 查看kill命令信号含义
kill -l
```

#### 8.10.3 pstree：查看进程树

以树形结构显示进程间的父子关系。

#### 基本语法

```Bash

pstree [选项]
```

#### 选项说明

|选项|功能|
|---|---|
|-p|显示进程PID|
|-u|显示进程所属用户|
#### 示例

```Bash

# 查看所有进程树
pstree

# 查看进程树及PID
pstree -p

# 查看进程树及所属用户
pstree -u
```

#### 8.10.4 top：实时监控系统进程状态

动态监控进程状态，默认每3秒更新一次。

#### 基本语法

```Bash

top [选项]
```

#### 选项说明

|选项|功能|
|---|---|
|-d 秒数|指定更新间隔（如-d 5：每5秒更新）|
|-i|不显示闲置或僵尸进程|
|-p PID|仅监控指定PID的进程|
#### 交互操作（top运行中）

|操作|功能|
|---|---|
|P|按CPU使用率排序（默认）|
|M|按内存使用率排序|
|N|按PID排序|
|q|退出top|
|u|输入用户名，过滤该用户的进程|
|k|输入PID，终止指定进程|
|1|显示所有CPU核心的使用率|
#### 8.10.5 netstat：显示网络状态和端口占用
> （注：文档部分内容可能由 AI 生成）