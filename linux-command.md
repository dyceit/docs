# Linux 常用命令

## 简介

本文只记录目前用到过的，常用的 Linux 命令，作为日常查询使用。每个命令都附上了英文全称，方便记忆。

## 网址

[Linux 命令大全](https://www.runoob.com/linux/linux-command-manual.html)

[Linux 常用命令全拼](https://www.runoob.com/w3cnote/linux-command-full-fight.html)

## 常用

### cd：Change Directory

切换当前工作目录至 dirName(目录参数)：

```shell
# cd [dirName]
cd /usr/bin 
cd / # 开头是 "/" 则列表系统根目录
cd ~ # 用户根目录
cd ./../usr # 上层目录下的usr目录，"." 则是表示目前所在的目录
cd ../../ # 上上两层，".." 则表示目前目录位置的上一层目录
```

### pwd：Print Work Directory

打印当前目录，显示出当前工作目录的绝对路径：

```shell
# pwd [--help][--version]
pwd # 显示当前路径
```

### ls：List files

```shell
# ls [-alrtAFR] [name...]
ls
```

### ps：Process Status

显示进程状态，类似于windows的任务管理器

```shell
# ps [options] [--help]
ps -aux # 显示所有进程
ps -ef # 显示所有命令，连带命令行
# ps -A # 显示进程信息
# ps -auxf # 显示进程状态

# 配合 grep
ps -aux | grep node # 显示带 “node” 的进程
ps -ef | grep node # 显示带 “node” 的进程
```

### df：Disk Free 

显示磁盘可用空间数目信息及空间结点信息。换句话说，就是报告在任何安装的设备或目录中，还剩多少自由的空间。

```shell
# df [选项]... [FILE]...
df -h # --human-readable 使用人类可读的格式
# df -i # --inodes 列出 inode 资讯，不列出已使用 block
# df -T # --print-type 显示文件系统的形式
# df --help
```

### du：Disk Usage

显示目录或文件的大小

```shell
# du [-abcDhHklmsSx][-L <符号连接>][-X <文件>][--block-size][--exclude=<目录或文件>][--max-depth=<目录层数>][--help][--version][目录或文件]
du -h --max-depth=1 # 显示一层目录结构的文件大小信息
# -h, --human-readable 以K，M，G为单位，提高信息的可读性
# --max-depth=<目录层数> 超过指定层数的目录后，予以忽略
# du --help
```

### rmdir：Remove Directory

删除目录

```shell
# rmdir [-p] dirName
# -p 是当子目录被删除后使它也成为空目录的话，则顺便一并删除
```

### rm：Remove file

删除目录或文件

```shell
# rm [options] name...
rm  -r  * # 删除当前目录下的所有文件及目录
rm -f *2019* # 强制删除包含“2019”的目录
# rm -i 删除前逐一询问确认。
# rm -f 即使原档案属性设为唯读，亦直接删除，无需逐一确认。
# rm -r 将目录及以下之档案亦逐一删除。文件一旦通过rm命令删除，则无法恢复，所以必须格外小心地使用该命令。
```

### cp：Copy file

```shell
# cp [options] source dest
# -f：覆盖已经存在的目标文件而不给出提示。
# -i：与-f选项相反
# -r：若给出的源文件是一个目录文件，此时将复制该目录下所有的子目录和文件。
cp -r file ../newfile # 复制 file 到上级目录下 全名为 newfile
cp –r test/ newtest # 将当前目录"test/"下的所有文件复制到新目录"newtest"下
```

### cat：Concatenate 

连接文件并打印到标准输出设备上

```shell
# cat [-AbeEnstTuv] [--help] [--version] fileName
cat svnSwitch.sh # 显示文件内容
# cat -n textfile1 > textfile2 # 把 textfile1 的文档内容加上行号后输入 textfile2 这个文档里
# cat -b textfile1 textfile2 >> textfile3
```

### ln：Link files

创建一个软链接，相当于创建一个快捷方式

```shell
# ln [参数][源文件或目录][目标文件或目录]
ln -s log2013.log link2013
```

### mkdir：Make Directory

创建目录

```shell
# mkdir [-p] dirName
mkdir parent/child # parent不存在，则报错
mkdir -p parent/child # -p 确保父级目录名称存在，不存在的就建一个
```

### mv：Move file

为文件或目录改名、或将文件或目录移入其它位置

```shell
# mv [options] source dest
# mv [options] source... directory
# -i: 若指定目录已有同名文件，则先询问是否覆盖旧文件;
# -f: 在mv操作要覆盖某已有的目标文件时不给任何指示;
mv aaa bbb # 将文件 aaa 更名为 bbb
mv info/ logs # 将info目录放入logs目录中。注意，如果logs目录不存在，则该命令将info改名为logs
mv /usr/student/*  . # 再如将/usr/student下的所有文件和目录移到当前目录下
```

### chmod：Change mode

控制文件权限

```shell
# chmod [-cfvR] [--help] [--version] mode file...
# mode : 权限设定字串，[ugoa...][[+-=][rwxX]...][,...]
# u 表示该文件的拥有者，g 表示与该文件的拥有者属于同一个群组(group)，o 表示其他以外的人，a 表示这三者皆是
# + 表示增加权限、- 表示取消权限、= 表示唯一设定权限
# r=4，w=2，x=1
# 若要rwx属性则4+2+1=7
# 若要rw-属性则4+2=6
# 若要r-x属性则4+1=5
chmod 777 file # chmod a=rwx file
# chmod 771 file # chmod ug=rwx,o=x file
# chmod 4755 filename # 可使此程序具有root的权限
```

# 其它

touch: touch

su：Swith user(切换用户)

mkfs: Make file system

fsck：File system check

uname: Unix name

lsmod: List modules

fg: Foreground

bg: Background

chown: Change owner

chgrp: Change group

umount: Unmount

dd: 本来应根据其功能描述"Convert an copy"命名为"cc"，但"cc"已经被用以代表"CComplier"，所以命名为"dd"

tar：Tape archive （磁带档案）

ldd：List dynamic dependencies

insmod：Install module

rmmod：Remove module

lsmod：List module

