# linux常用命令

## 1.1 systemctl 命令

系统操作命令,对linux系统的服务进行关闭和开启

- 网络
  - 关闭网络：systemctl stop network
  - 启动网络：systemctl start network
  -  重启网络：systemctl restart network
  - 开机自启：systemctl enable network
  - 开机不自启:systemctl disable network
  - 查看网络: systemctl status network
  - ![image-20220119140918270](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119140918.png)
- 防火墙
  - 关闭防火墙：systemctl stop firewalld
  -  启动防火墙：systemctl start firewalld
  - 重启防火墙：systemctl restart firewalld
  - 开机不启动：systemctl disable firewalld
  - 查看防火墙 : systemctl status firewalld
  - ![image-20220119140950344](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119140950.png)
- 关机
  -  关机：poweroff /shutdown now
  -  重启：reboot

## 1.2 目录及路径

- 目录

- ![image-20220119124319913](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119124320.png)

- 绝对路径：从/目录计算

- 相对路径：从当前你所在的目录，到目标目录

- pwd:显示你当前所在的绝对路径

- ../   上一级目录

- ./ 当前目录

- ls 显示当前目录下的所有子目录和文件

- cd 目录    切换目录

- 练习:进入到root目录

- 使用绝对路径进入到home目录

- 使用相对路径进入到opt目录

- ~代表家目录

- ```linux
  cd /root -- 绝对路径进入到root目录
  cd /home -- 绝对路径进入到home目录
  cd ../opt -- 相对路径进入到opt目录
  
  ```

- 练习:

- 使用绝对路径进入到etc/rpm目录

- 使用cd /root回到root目录

- 使用相对路径进入到etc/rpm目录

- ```linux
  [root@localhost opt]# cd /etc/rpm --绝对路径进入到rpm目录
  [root@localhost rpm]# cd /root  --绝对路径进入到root目录
  [root@localhost rpm]# cd ../etc/rpm --相对路径进入到rpm目录
  ```

## 1.3 文件编辑

- vi 文件名称
  - vi 文件名 
  - 如果文件存在,那么就直接对这个文件进行查看
  - 如果文件不存在,就会新建一个文件,并且进入编辑该文件
- 模式
  - 模式一:编辑模式----vi 文件名 按i 进入到文件的编辑模式
  - 模式二:命令模式---vi 文件名 就进入到了文件的命令模式
  - 模式三:命令行模式 --- vi 文件名 按shift+: 就进入到了文件的命令行模式
- 保存命令
  - 按ESC--切换到命令模式
  - 按shift + :
  - 输入wq ---保存并且退出
  - 输入w ---保存但是不退出
  - 输入q!---不保存强制退出
  - ! 强制
  - 按tab键可以自动帮你补全文件名称
- 插入命令i

![image-20210423150243010](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/lilimin/20210423150243.png)

练习题
	          1.在home目录下创建test.txt文件,在文件里添加1111,2222,3333,4444 ,    4行数据并保存退出
  			2.编辑该文件,在2222行后面添加一行8888
  			3.在8888行末尾添加yyyy
  			4.删除8888行末尾的yyyy
  			5.保存文件
  			6.重新编辑该文件,在最后添加9999
  			7.不保存文件,直接退出
  			8.重新编辑,在最后添加2323232,保存不退出
  			

- 命令模式---定位光标
  - A光标移动到行尾并且进入到编辑模式
  - $移动到该行末尾
  - ^移动到该行开头
  - G移动到末行行首
  - gg移动到最开始行首
- 命令模式---删除命令
  - dd   删除光标所在的行

![image-20210423150855741](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/lilimin/20210423150855.png)

- 命令模式---复制和剪切
  - yy     复制当前行
  - nyy   复制多行
  - p        粘贴

![image-20210423151058247](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/lilimin/20210423151058.png)

- 命令模式---替换和取消
  - r      替换光标所在地方的值

![image-20210423151356271](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/lilimin/20210423151356.png)

- 命令行模式
  - :/字符串     从上到下查询文件中的字符串
  - :%s/准备要被替换的字符串/替换后的字符串/g
  - :起始行标号,结束行标号s/替换前字符串/替换后的字符串/g

![image-20210423151541147](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/lilimin/20210423151541.png)

- :n1,n2d    删除第n1行到第n2行数据
- :wq  保存退出
- :set nu 设置行号
- :set nonu 取消行号

练习 

使用命令模式 删除第2行

使用命令模式移动光标到最头

使用命令模式复制第一行

使用命令模式把第一行粘贴到最末行

练习:

使用编辑模式输入1111,2222,3333,4444,5555,6666  6行数据

切换到命令模式,复制第3行数据,粘贴到末尾

切换到命令行模式,设置行号,删除第1-3行数据

* 三种模式切换关系

* ![image-20220527155159588](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220527155206.png)



## 1.4 目录管理

- 创建

  - mkdir 目录名字   ---在当前目录下创建子目录

    ```
    [root@localhost ~]# mkdir aaa
    [root@localhost ~]# ls
    aaa  anaconda-ks.cfg  c.sh
    ```

    

  - mkdir 绝对路径目录名  ---在绝对路径下创建子目录

  - ```
    [root@localhost ~]# mkdir /root/bbb
    [root@localhost ~]# ls
    aaa  anaconda-ks.cfg  bbb  c.sh
    
    ```

  - mkdir 相对路径目录名  ---在相对路径下创建子目录

  - ```linux
    [root@localhost ~]# mkdir ../mnt/fff
    [root@localhost ~]# cd ../mnt
    [root@localhost mnt]# ls
    ccc  fff
    [root@localhost mnt]# 
    ```

  - mkdir -p 目录名   ---递归创建目录

  - ```
    [root@localhost ~]# mkdir -p bbb/ccc
    [root@localhost ~]# ls
    anaconda-ks.cfg  bbb  c.sh
    [root@localhost ~]# cd bbb/ccc
    您在 /var/spool/mail/root 中有新邮件
    [root@localhost ccc]# pwd
    /root/bbb/ccc
    [root@localhost ccc]# 
    ```
    
  - 练习:

  - 在home目录创建一个自己名字目录,进入到刚才创建的目录里,在创建一个目录ccc

  - 回到home目录,直接使用递归创建方法,在ccc目录下继续创建vvv/bbb

  - 回到home目录,使用绝对路径在bbb目录下创建一个ddd目录

- 删除目录

  - rm -rf 目录名  ---删除该目录及该目录下所有递归的目录
  - 练习
    - 在使用rm -rf 删除xxx目录
    - 删除home目录下所有的目录

- 复制目录

  - cp -r 源目录 新目录

  - ```
    [root@localhost ~]# cp -r aaa bbb
    [root@localhost ~]# ls
    aaa  anaconda-ks.cfg  bbb
    [root@localhost ~]# cd bbb
    [root@localhost bbb]# ls
    a.txt
    
    ```
    
  - 练习
  
    - 在home目录下创建一个aaa目录,使用复制命令,复制一个bbb目录
    - 在home目录下复制aaa目录到/opt/qqq目录
  
- 移动(剪切)或者重名名目录

  - mv 源目录 新目录

  - ```linux
    [root@localhost ~]# ls
    anaconda-ks.cfg  bbb  ccc
    [root@localhost ~]# mv bbb /mnt/
    [root@localhost ~]# cd /mnt
    [root@localhost mnt]# ls
    bbb
    [root@localhost mnt]# 
    ```

  - 练习
    - 在home目录下创建2个目录,test和demo,把home目录下的test目录移动到demo目录
    - 进入到demo目录下 对test目录重命名为test999

- 练习题

  ```
    	1.同时创建Lee lee1 lee2 lee3目录
    	# 2.复制lee1目录到lee目录下
    	# 3.移动lee2目录到lee目录下
    	# 4.修改lee3的名字为aaa
    	# 5.删除aaa目录
    	# 6.删除lee目录 lee1目录 lee2目录
  ```


## 1.5 文件操作

- 创建
  
  - touch 文件名   ---创建一个空文件
  - vi 文件名 ---创建一个新文件并且对这个文件进行编辑
  - cat > 文件名  ---对文件进行重写新内容,按ctrl+d结束重写内容 
  - cat >> 文件名  ---对文件进行末行追加新内容,按ctrl+d结束追加内容
  
- 删除
  
  - rm 文件名
  - rm -rf 文件名
  
- 复制
  
  - cp 源文件 目标文件
  
- 移动(重命名)
  
  - mv 源文件 目标文件
  
- 文件查看
  
  - cat  文件名
  - vi 文件名
  - more -数字 文件名            每个屏幕显示多少行
  - less 文件名                           显示文件内容,可以使用上下键回看内容
  - head -数字 文件名               显示前多少行数据
  - tail -数字 文件                       显示末尾多少行
  - tailf  -数字 文件                    显示末尾多少行，当这个文件更新时跟着更新
    - 一个软件，产生大量的日志文件
    - 查看日志，日志末尾，实时更新
  
- 退出文件的几种情况

   - cat > a.txt  要退出追加内容 按ctrl+d
   - tailf a.txt  按ctrl+c 退出
   -  esc退出编辑模式
   - less a.txt 按q退出

- 练习题
  		
  	```linux
  # 1.在/home下创建一个aaa.txt文件
  # 2.百度一首歌曲，把歌词放入到aaa.txt文件中
  # 3.通过cat查看文件内容
  # 4.通过vi查看文件内容
  # 5.通过more，每个屏幕显示10行数据，查看文件内容
  # 6.通过less，显示文件的行标，查看内容
  # 7.通过head，查看文件的前10行内容
  # 8.通过tail，查看文件的末尾10行内容
  ```
  
  
  
- 链接

> 软连接类似于计算机的快捷方式
>
> 硬连接类似于计算机的复制功能,比复制功能更强大

ln -s 源文件 软连接名   

ln -d 源文件 硬链接名

区别:

1.命令参数不一样,软连接是个-s,硬链接-d

2.删除源文件,软连接没有被删除,但是失效了;硬链接不受影响,可以继续使用

练习:

1.创建一个文件a.txt,编辑该文件写入123456内容

2.对a.txt创建一个软连接s

3.对a.txt创建一个硬链接d

4.修改a.txt文件内容添加7890

5.查看软连接s和硬链接d

6.删除a.txt,查看软连接s和硬链接d

## 1.6 虚拟机网络连接模式

- 虚拟机网络模式

  - net模式
    - 同桌之间无法访问
    - ![image-20220528162014863](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220528172448.png)
  - 桥接模式
    - 同桌之间可以访问
    - ![image-20220528162244847](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220528172444.png)
  - 仅主机模式
    - 仅自己访问虚拟机,且虚拟机没有网络
    - ![image-20220528172436362](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220528172436.png)
  
   

## 1.7 显示目录及文件

* ls 查看当前目录下的所有子目录和文件
  * ls -a 显示当前目录下的所有子目录和文件并且还显示隐藏的目录和文件
  * ls -l  ==ll 显示当前目录下的所有子目录和文件的详细信息

## 1.8 组操作

> 权限:定义资源(目录和文件)或服务的访问能力,称之为权限
>
> 用户权限:定义某一个特定的人访问资源或者服务的访问能力
>
> 用户组权限:定义一类用户具有访问某个资源或服务的能力.同时用户组还拥有具有访问某个资源的权限



* 组的分类
  * 管理员组
  * 程序组
  * 用户组

- 组和用户的概念
  - 组下面有用户,用户组设置一定的权限,那么组下面所有的人都有相应的权限

- 创建组
  - groupadd 组名

- 修改组
  - groupmod  -n 新组名  原组名

- 删除组
  - groupdel 组名
- 查看用户所在的组信息
  - groups 用户名

```linux
练习:
1.创建一个用户组text,查看用户组信息
2.把text用户组名修改为test
3.删除test用户组,查看用户组信息
```



## 1.9 用户操作

- 创建用户
  
  - useradd 用户名
  - useradd -g 主组名   用户名  (指定主组时,必须先有一个空组,才可以指定主组)
  - useradd -G 附加组名 用户名
  - useradd  -g 主组名  -G 附加组名 用户名
- 注意：
  
  - 一个用户必须有一个组,当创建一个新用户时,系统会默认给该用户生产一个同名的组,且会在home目录下创建一个同名的家目录
  
- 切换用户

  - su 用户名

- 对用户设置密码

  - 使用root账户  passwd 用户名  需要输入两次相同的密码即可

- 查看用户信息

  - cat /etc/passwd:查看用户
  - cat /etc/group:查看组

- 修改用户

  - usermod -g  用户组 用户：重新指定用户的主组
  - usermod -G 用户组名 用户：重新指定用户的附加组
  - usermod -d 新的家目录 用户：重新指定用户的家目录
  - usermod -u 新的uid 用户：重新指定用户的id

- 删除用户

  - userdel 用户名：删除用户,不删除家目录,默认会删除组
  - userdel -rf 用户名： 删除用户把主组删掉，以及家目录删除

- 练习题

  * 把所有的用户和组和家目录全部删除,使用-rf命令

  - 创建一个用户test1，主组为test1

  - 创建一个用户test2，主组为test2
  - 创建一个用户test3，主组为test3
  - 给test1添加附加组test3
  
  - 删除用户test3，使用-rf命令，组test3删掉了么？test3家目录不在了？
  - 删除用户test2，使用-rf命令，查看组test2的变化，以及/home/test2变化?
  - 创建一个用户test4，主组为test4
  - 修改test1的主组为test4
  - 删除用户test4，使用-rf命令，查看组test4，，
  - 删除组test1，查看/home/test1的变化，
  - 注意：
  
    - 查看删除用户的时候，主组以及家目录如何变化--当组下无其他人,一锅删除
  - 如果一个主组下只有一个用户，删除用户可以同时删除主组
    - 如果一个主组下有多个用户，删除用户不会删除主组


```mysql
创建一个空组test
创建一个用户demo,并且设置demo的主组为test
创建一个用户test99,并且设置附加组为test
创建一个空组test2,并且创建一个用户test88,指定主组为test2 指定附加组为test
```

## 1.10 权限修改

- 控制规则
  * 对象:文件和目录
- 权限
  - 对文件和目录拥有一定的权利(r读,w写,x执行)
- 命令授权
  - chmod o+wrx 文件名  对其他组的用户授权rwx(读写执行)的权限
  - chmod g+wrx 文件名  对附加组的用户授权rwx(读写执行)的权限
  - chmod u+wrx 文件名  对主组的用户授权rwx(读写执行)的权限
- 数字授权
  -  chmod  -R 777 文件名  (r--4 w--2 x--1,一个数字代表一个组,第一个主组,第二个附加组,第三个其他组)
  - ![image-20220120164029646](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220120164029.png)
- ![image-20220120164101551](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220120164101.png)
- 
- 改拥有者-change owner
  - chown 新的拥有者 文件或者目录：修改拥有者  
  - chown -R 新的拥有者 文件或者目录：递归授权
- 修改文件所在的组-change group
  - chgrp 新的组 文件或者目录:修改文件所在的组
  - chgrp -R 新的组 文件或者目录:递归修改文件所在的组
- 练习题
  - 创建test1用户
  - 创建test2用户
  - test1用户进入/home/test1目录下，创建aaa目录
  - test2用户进入/home/test2目录下，创建bbb目录
  - 使用test1账户访问/home/test2目录
  - 给test1添加附加组：test2
  - 使用test1账户访问/home/test2目录
  - 给tset2目录增加附加组读写执行权限
  - 使用test1账户访问/home/test2目录

练习.现在有一个东西,权限是-rwxr-x--x  ,它是什么类型的?   现在对该文件授权其他人读,执行权限,请问授权的命令用数字表示chmod 755 文件名



## 1.11 文件与内容查询

> find 查找文件或者目录
>
> grep 查找的文件的内容

- 根据名字查询
  - find  查找目录 -name 条件
  - 精确查询
    - find 查找目录 -name 文件or目录名字
  - 模糊查询
    - find ./ -name 't*':在当前目录查找以t开头的所有文件或者目录
    - find / -name '\*t\*' :在根目录查找名字包含t的所有文件或者目录
    - 正则表达式  |管道符
    - find ./ -name "[c|d]*"：[|]以c或者d开头的所有文件或者目录
    - find ./ -name "\[^c|d|t|a]\*"： 不以cdta开头的文件或者目录
  - ![image-20220528145141967](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220528145319.png)
- 根据权限
  - find / -perm 777:查询根目录下权限为777的文件或者目录
  - find / -perm 666:查询根目录下权限位666的文件或者目录
- 根据路径
  - find / -path 排除目录 -prune -o -name "文件"
- 根据时间
  - find / -mtime -3: 到当前时间3天内更新过的文件
  - find / -mtime +3: 3天前更新过的文件
- 根据类型
  - find / -type d
  - d:目录
  - l:软连接
  - f：文件
- 根据大小
  - find / -size 6c：大小为6字节的文件
  - G 代表GB
  - b 代表字节
- grep命令
  - grep 内容 文件
  - 精确匹配
    - grep 查找的内容 文件名
  - 模糊匹配
    - ^开头
      - grep '^内容' 文件名
    - $结尾
      - grep '内容$' 文件名
- | 管道符
  - find / -name 文件名 | xargs grep 内容

## 1.12 压缩归档

> 压缩是对文件或者目录进行缩小文件大小的这么个方法

* 压缩
  * 命令
  * gzip 文件名

```linux
-rw-r--r--. 1 root root 2 1月  21 09:44 a.txt
[root@localhost home]# vi a.txt 
[root@localhost home]# ls
a.txt
[root@localhost home]# ll
总用量 4
-rw-r--r--. 1 root root 1870 1月  21 09:45 a.txt
[root@localhost home]# gzip a.txt 
[root@localhost home]# ls
a.txt.gz
[root@localhost home]# ll
总用量 4
-rw-r--r--. 1 root root 897 1月  21 09:45 a.txt.gz

```

* 解压缩

  * 命令
  * gzip -d 压缩包名

  ```
  [root@localhost home]# ls
  a.txt.gz
  [root@localhost home]# gzip -d a.txt.gz 
  [root@localhost home]# ls
  a.txt
  ```

* 压缩命令

  * zip---第三件软件需要下载安装使用 yum -y install zip
  * unzip 自己起压缩包名 yum -y install unzip
  * 命令:zip 起名 源文件   (文件名.zip)
  * 命令:unzip 压缩包名

```
[root@localhost home]# ls
a.txt
[root@localhost home]# zip a.txt.zip a.txt ---使用zip对a.txt进行压缩
  adding: a.txt (deflated 53%)
[root@localhost home]# ls ---查看压缩包
a.txt  a.txt.zip


[root@localhost home]# ls
a.txt.zip
[root@localhost home]# unzip a.txt.zip  ---使用unzip对压缩包进行解压
Archive:  a.txt.zip
  inflating: a.txt                   
[root@localhost home]# ls
a.txt  a.txt.zip
```

* 归档

  * 就是把多个文件归档到一起

  * 命令

  * tar -cvf 起归档名 文件

  * ```
    [root@localhost home]# ls
    a.txt  b.txt.gz  liangyuesi
    [root@localhost home]# tar -cvf a.txt.tar a.txt
    a.txt
    [root@localhost home]# ls
    a.txt  a.txt.tar  b.txt.gz  liangyuesi
    ```

  * 

* 解归档

  * 就是一个文档里的文件解出来

  * 命令

  * tar -xvf 归档名

  * ```linux
    [root@localhost home]# ls
    a.txt.tar  b.txt.gz  liangyuesi
    [root@localhost home]# tar -xvf a.txt.tar
    a.txt
    [root@localhost home]# ls
    a.txt  a.txt.tar  b.txt.gz  liangyuesi
    ```

* 压缩归档

  * 命令

  * tar -zcvf 起名字.tar.gz  文件名

  * ```linux
    [root@localhost home]# ls
    a.txt  b.txt  liangyuesi
    [root@localhost home]# tar -zcvf ab.tar.gz a.txt b.txt
    a.txt
    b.txt
    [root@localhost home]# ls
    ab.tar.gz  a.txt  b.txt  liangyuesi
    ```

  * 

* 解压缩解归档

  * 命令
  * tar -zxvf 文件名

```linux
[root@localhost home]# ls
ab.tar.gz  liangyuesi
[root@localhost home]# tar -zxvf ab.tar.gz
a.txt
b.txt
[root@localhost home]# ls
ab.tar.gz  a.txt  b.txt  liangyuesi
```





## 1.13 网络命令

- 查看ip
  - ip addr--ip a
  - ping ip
- 网络配置文件
  - /etc/sysconfig/network-scripts/ifcfg-ens33

```linux
TYPE=Ethernet                               网卡类型:以太网
PROXY_METHOD=none                           代理方式:关闭状态
BROWSER_ONLY=no                             只是浏览器(yes|no)
BOOTPROTO=static/dhcp(变)                       设置网卡获得ip地址的方式(static|dhcp|none|bootp)
DEFROUTE=yes                                设置为默认路由(yes|no)
IPV4_FAILURE_FATAL=no                       是否开启IPV4致命错误检测(yes|no)
IPV6INIT=yes                                IPV6是否自动初始化
IPV6_AUTOCONF=yes                           IPV6是否自动配置
IPV6_DEFROUTE=yes                           IPV6是否可以为默认路由
IPV6_FAILURE_FATAL=no                       是不开启IPV6致命错误检测
IPV6_ADDR_GEN_MODE=stable-privacy           IPV6地址生成模型
NAME=eth0                                   网卡物理设备名称
UUID=6e89ea13-f919-4096-ad67-cfc24a79a7e7   UUID识别码
DEVICE=eth0                                 网卡设备名称
ONBOOT=yes                                  开机自启(yes|no)
IPADDR=192.168.40.203(变)                  IP地址(路由器的网段必须是192.168.11.xxx   3-255)
NETNASK=255.255.255.0                       子网掩码,也可使用掩码长度表示(PREFIX=24)
GATEWAY=192.168.40.1(变)                    网关
DNS1=114.114.114.114                        首选DNS
DNS2=8.8.8.8                                备用DNS
```

![image-20220530163632090](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220530163632.png)

## 1.14 进程操作

win系统

```linux
打开任务管理器--选择进程--选中某程序进程--鼠标右键,点击结果任务
```

linux系统

```linux
netstat---需要下载 yum -y install net-tools   查看网络进程
ps -ef 查看所有进程
ps -ef | grep mysql

kill pid 结束进程
kill -9 pid 强制结束进程

top 查看系统资源占用情况
top -d 10 更改top命令刷新的间隔时间,默认是3秒刷新一次
ctrl+c退出top命令
history 历史操作记录
history -c 清楚历史操作记录

clear 清屏
id  显示用户的详细信息
date 显示当前时间
date -s 设置时间
alias 显示系统的起别名命令
alias a='ls -a'
free-h 查看系统内存
df -h 查看磁盘空间
--help 查看帮助
yum -y install ntp
ntpdate time1.aliyun.com   同步系统时间命令
```

```
命令：top

每行代表意思：

任务进程

第一行：

10:01:23 — 当前系统时间

126 days, 14:29 — 系统已经运行了126天14小时29分钟（在这期间没有重启过）

2 users — 当前有2个用户登录系统

load average: 1.15, 1.42, 1.44 — load average后面的三个数分别是1分钟、5分钟、15分钟的负载情况。

第二行：

Tasks — 任务（进程），系统现在共有183个进程，其中处于运行中的有1个，182个在休眠（sleep），stoped状态的有0个，zombie状态（僵尸）的有0个。

第三行：cpu状态

6.7% us — 用户空间占用CPU的百分比。

0.4% sy — 内核空间占用CPU的百分比。

0.0% ni — 改变过优先级的进程占用CPU的百分比

92.9% id — 空闲CPU百分比

0.0% wa — IO等待占用CPU的百分比

0.0% hi — 硬中断（Hardware IRQ）占用CPU的百分比

0.0% si — 软中断（Software Interrupts）占用CPU的百分比

第四行：内存状态

8306544k total — 物理内存总量（8GB）

7775876k used — 使用中的内存总量（7.7GB）

530668k free — 空闲内存总量（530M）

79236k buffers — 缓存的内存量 （79M）

第五行：swap交换分区

2031608k total — 交换区总量（2GB）

2556k used — 使用的交换区总量（2.5M）

2029052k free — 空闲交换区总量（2GB）

4231276k cached — 缓冲的交换区总量（4GB）

第五行以下:

PID — 进程id

USER — 进程所有者

PR — 进程优先级

NI — nice值。负值表示高优先级，正值表示低优先级

VIRT — 进程使用的虚拟内存总量，单位kb。VIRT=SWAP+RES

RES — 进程使用的、未被换出的物理内存大小，单位kb。RES=CODE+DATA

SHR — 共享内存大小，单位kb

S — 进程状态。D=不可中断的睡眠状态 R=运行 S=睡眠 T=跟踪/停止 Z=僵尸进程

%CPU — 上次更新到现在的CPU时间占用百分比

%MEM — 进程使用的物理内存百分比

TIME+ — 进程使用的CPU时间总计，单位1/100秒

COMMAND — 进程名称（命令名/命令行
```



## 1.15 安装卸载

* 文件上传
  * 命令rz 需要下载yum install lrzsz
  * 或者使用xftp工具进行上传

* yum在线安装
  * 命令
  * yum -y install 软件名 
* yum卸载
  * 命令
  * yum -y remove 软件名
* rpm安装
  * 命令
  * rpm -ivh 安装包名   
* rpm卸载
  * 命令
  * rpm -e --nodeps 软件名  卸载这个软件,不需要验证依赖关系





## 1.16 基础软件部署

>安装基础软件：tomcat、jdk、mysql
>
>部署测试环境：woniusales.war放入到了tomcat-werbapps，导入数据库创建。。，修改配置文件



```linux
	1.rpm安装，软件包，rpm直接安装即可或者 安装，在线安装，yum软件包的仓库，有一系列可以支持你安装rpm包--msyql、jdk
	2.脚本安装，tar.gz--tomcat
	3.源码安装，软件源码组成，make&make install编译并安装一下才能使用
	
国内yum源：
	网易163 yum源，安装方法查看：http://mirrors.163.com/.help/ （我推荐）
	中科大的 yum源，安装方法查看：	https://lug.ustc.edu.cn/wiki/mirrors/help
	sohu的 yum源，安装方法查看: http://mirrors.sohu.com/help/
	阿里云的 yum源，安装方法查看: http://mirrors.aliyun.com/repo/ （推荐）
	清华大学的 yum源，安装方法查看: https://mirrors.tuna.tsinghua.edu.cn/
	浙江大学的 yum源，安装方法查看: http://mirrors.zju.edu.cn/
	中国科技大学yum源，安装方法查看: http://centos.ustc.edu.cn/

yum命令使用
	yum install -y 软件：在线安装软件，从远程仓库下载对应的rpm包，并且自动下载该软件的依赖自动安装
	yum -y remove 软件：卸载软件

rpm命令使用
	rpm -ivh 软件.rpm：安装软件
	rpm -qa |grep mysql：查询是否安装了mysql
	rmp -e --nodeps 软件  卸载软件

基础软件
	tomcat
	mysql 
	jdk-- linux windows
	
服务器
	30%--windows系统
	70%--linux系统
	woniusales可以部署在linux系统上，也可以部署在windows系统上
	
安装jdk
	在线安装：yum install -y java
	离线安装：rpm包
	1.传输文件到/opt目录： yum install -y lrzsz
	2.tar -zvxf jdk-8u251-Linux-x64.tar.gz -C /opt
	3.修改配置文件：vi /etc/profile   系统环境变量
		环境变量：我的电脑-右键-属性-高级-环境变量
		export JAVA_HOME=/opt/jdk1.8.0_251 
		export PATH=$JAVA_HOME/bin:$PATH 
		export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
	4.java -version


 windows:
        1、准备jdk包（可安装，免安装）
        2、配置环境变量
            WIN7:计算机右键-属性-高级系统设置-环境变量-系统变量-新建
                JAVA_HOME=>E:\Java\jdk1.8.0_181
            WIN7:计算机右键-属性-高级系统设置-环境变量-系统变量-编辑
                PATH=>;E:\Java\jdk1.8.0_181\bin; 
                PATH=>;%JAVA_HOME%\bin;
            WIN10:计算机右键-属性-高级系统设置-环境变量-系统变量-新建
                JAVA_HOME=>E:\Java\jdk1.8.0_181
            win10:搜索高级系统设置-环境变量-系统变量-编辑-新建
        3、验证是否配置生效：java javac java -version
	
mysql安装
	1.检查系统是否存在历史版本，如果存在则删除
	2.上传文件
	3.安装依赖包
	4.安装服务端
		1.配置文件：/usr/my.cnf
		2.随机密码地址：/root/.mysql_secret
		3.Innodb:搜索引擎
		4.服务地址：/usr/sbin/mysqld
		5.查看状态：systemctl status mysql
		6.启动服务：systemctl start mysql	
	5.安装客服端
		1.重置密码：mysqladmin -u root -p password 123456
		2.回车
		3.输入随机密码
		4.回车
		5.systemctl stop mysql
		6.systemcly start mysql
	6.关闭防火墙
		
	7.验证
tomcat安装
    1、Windows准备tomcat包tar.gz【免安装版】
    2、上传至Linux操作系统的opt目录
    3、解压tar -zxvf tomcat.tar.gz
    4、运行tomcat 服务：sh /opt/apache-tomcat-9.0.13/bin/startup.sh    
    5、验证tomcat服务是否启动成功
        1.查询后台进程 ps aux|grep tomcat   ps -aux|grep tomcat  ps ef|grep tomcat
        2、浏览器远程访问tomcat服务：http://192.168.16.70:8080/【防火墙需要关闭方可远程访问！！！】
        
        
MySQL部署
    1、安装mysql【默认8.0最新版，若需要自定义版本安装：https://dev.mysql.com/downloads/repo/yum/，下载mysql的安装的仓库文件，修改配置信息】
        下载仓库文件，上传至Linux系统中opt
    2、安装仓库文件
    3、修改仓库配置文件： vi /etc/yum.repos.d/mysql-community.repo，保存并退出
        # Enable to use MySQL 5.6
        [mysql56-community]
        name=MySQL 5.6 Community Server
        baseurl=http://repo.mysql.com/yum/mysql-5.6-community/el/7/$basearch/
        enabled=1
        gpgcheck=1
        gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
        [mysql80-community]
        name=MySQL 8.0 Community Server
        baseurl=http://repo.mysql.com/yum/mysql-8.0-community/el/7/$basearch/
        enabled=0
        gpgcheck=1
        gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
        检查当前的仓库文件的mysql默认安装版本：yum repolist enabled | grep "mysql.*-community.*"
    4、yum安装mysql-server：yum -y install mysql-server
    5、检查mysql-server是否安装完毕：systemctl list-unit-files | grep mysql
    6、启动mysql服务：systemctl start mysqld  //    service mysqld start
    7、验证mysql是否启动成功：ps aux|grep mysqld
    8、本地登录mysql -u root  -p /  mysql【mysql>】
    9、查看所有的数据库：show databases;
    10、修改mysql用户root的密码
        use mysql;
        update user set password=password('123456') where user='root';
        update mysql.user set user.password=password('123456') where user.user='root';
        flush privileges;
    11、为mysql授权远程访问权限
        GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '123456' WITH GRANT OPTION;
        flush privileges;

```

## 1.17 项目部署



```linux

目标：woniusales
语言：java
环境：tomcat+jdk+mysql

部署过程
	tomcat目录
		bin:tomcat的执行程序，shutdown.sh关闭程序,startup.sh启动程序
		conf：server.xml端口配置文件
		logs：日志文件，tomcat启动不起来，catalina.out 记录日志
		webapps:项目woniusales,woniuboss.war
   
    1、获取项目包war包，上传至Linux系统的/opt/apache-tomcat-9.0.13/webapps路径下
    2、创建数据库：woniusales
    3、还原数据库：Navicat远程访问Linux数据库进行操作，运行SQL文件
    4、修改数据库连接文件，【/opt/apache-tomcat-9.0.13/webapps/Woniusales1.4/WEB-INF/classes/db.properties】保持数据库配置信息与Linux服务器的数据库配置一致！！！
            db_url=jdbc:mysql://localhost:3306/woniusales?useUnicode=true&characterEncoding=utf8 
            db_username=root
            db_password=123456
            db_driver=com.mysql.jdbc.Driver
    5、重启tomcat服务
            sh /opt/apache-tomcat-9.0.13/bin/shutdown.sh  --->  sh /opt/apache-tomcat-9.0.13/bin/startup.sh
            ps aux|grep tomcat   --->kill 63139 --->sh /opt/apache-tomcat-9.0.13/bin/startup.sh
    6、访问项目：
            http://192.168.16.70:8080/Woniusales1.4/
            
            
JAVA项目-Windows
    1、JDK+Tomcat+MySQL+war包
    2、MySQL
            Windows本地数据库-xampp[localhost 3306 ]
            Linux远程数据库-mysql5.6[192.168.16.70 123456]
    3、war包放入tomcat/webapps目录下，启动tomcat服务，修改数据库连接文件db.properties 数据库名，用户名，密码
    4、浏览器访问localhost:8080/woniusales
    
    
常见问题解决方案
    1、访问页面404
        URL地址是否正确？
        数据库连接信息是否正确？
    2、检查代理服务器和防火墙，ERR_CONNECTION_TIMED_OUT
        防火墙；代理服务器
    3、所有问题均未出现，切换网络
    4、切换网络还未解决，删除自动化解压后的源码文件，重新部署
    5、同一台tomcat服务器上部署了多个项目，部署失败，将tomcat进程kill掉，再次启动
        
        
PHP项目-Linux
    1、获取xampp的包【tar.gz】，上传至Linux系统的opt目录下
        curl -O http://excellmedia.dl.sourceforge.net/project/xampp/XAMPP%20Linux/1.6.8a/xampp-Linux-1.6.8a.tar.gz
    2、解压xampp包
         tar -zvxf  xampp-Linux-1.6.8a.tar.gz -C /opt   【-C：指定路径解压】
    3、启动Apache服务【lampp-Apache-80，mysql-localhost 3306】
        /opt/lampp/lampp 启动xampp服务
        启动出现报错：XAMPP is currently only availably as 32 bit application. Please use a 32 bit compatibility library for your system.
        解决方案：安装依赖包-yum -y install glibc*i686
    4、远程浏览器访问：http://192.168.16.70:80,页面进入xampp的主页
    5、直接沿用MySQL56的服务器，在线创建数据库，配置数据库连接信息，数据库连接成功
    6、将项目源码包（agileone.zip --> unzip agileone.zip）解压后放置xampp的容器中，在/opt/lampp/htdocs 
    7、重启Apache服务，远程访问页面：http://192.168.16.70:80/agileone,页面跳转至安装页面http://192.168.16.70/agileone/Install/，进行数据库的连接配置
    8、配置数据库
            数据库主机：MySQL56 192.168.16.70  123456  agileone
            创建数据库及表，连接项目http://192.168.16.70:80/agileone，admin admin
            
配置文件
	apache端口：lampp/etc/httpd.conf
	数据库端口：lampp/etc/my.cnf
            
            
1.yum install -y http://li.nux.ro/download/nux/dextop/el7/x86_64/nux-dextop-release-0-5.el7.nux.noarch.rpm
2.yum install exfat-utils fuse-exfat
然后再执行挂载操作即可。
1.cd /media
2.mkdir udisk
3.mount -t exfat /dev/sdbX(X是你的盘号） udisk
```



## 1.17 挂载

- 定义

  - 正常来讲，centos只能识别/根目录下面
  - 识别除了/之外的一些文件

- 语法

  - 挂载：mount
    - -t 文件类型
    - -o  参数
  - 卸载 umount
    - -l

  案例：把windows系统的共享文件夹挂载到/mnt/aaa

  - 1.在windows系统创建文件夹aaa,并且进入到aaa文件夹里创建一个1.txt,在1.txt里随意输入内容,保存退出.

  - 2.设置文件夹aaa为共享文件夹

  - 3.使用xshell cd到/mnt目录下,创建aaa目录

  - 4.挂载

        mount -t cifs -o username=’administrator’,password=’123321’ //物理机ip/文件夹  /mnt/目录名

    mount -t cifs -o username=’Administrator’,password=’123321’ //192.168.1.99/aaa  /mnt/aaa

    即可挂载成功,进入到aaa目录可以看到aaa目录下有1.txt文件

    - 查看当前win系统的用户名win+L
  * 卸载挂载目录
    * umount -l /mnt/aaa

  * 删除目录
    * rm -rf /mnt/aaa