# linux基础概念

## 1 vmware的安装

### 1.0 前置条件

* 开启cpu虚拟化
  * win10---打开任务管理器--性能---看虚拟化--已启用
  * ![image-20220526092516767](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220526092516.png)
  * win7---软件(LeoMoon CPU-V下载的Linux压缩包里)显示两个√代表虚拟化已开启
  * ![image-20220119093846672](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119093846.png)
* 卸载
  * 通过控制面板卸载
  * 使用第三方软件(群文件Uninstall Tool工具)卸载
  * 卸载完毕一定使用群文件CCleaner软件清理一下注册表,目的是为了清理虚拟网卡残留注册表,否则无法安装虚拟网卡
* 虚拟化未开启解决办法
  * 查看自己电脑的品牌及型号,自己百度虚拟化开启方法



### 1.1 安装步骤(win7使用vm15版本,win10使用vm16版本)

1.检查电脑的环境

![image-20220119095255003](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119095255.png)



2.安装向导,点击下一步

![image-20220119095348982](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119095349.png)

3.同意协议并下一步

![image-20220119095835611](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119095835.png)





4.选择安装路径,根据需要自己选择安装路径

![image-20220119095909384](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119095909.png)

![image-20220530083842178](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220530083842.png)

5.用户体验不勾选,下一步

![image-20220119100000113](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119100000.png)

6.创建快捷方式,下一步

![image-20220119100029620](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119100029.png)



7.安装

![image-20220119100046699](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119100046.png)

8.安装中

![image-20220119100130555](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119100130.png)

9.点击许可证

![image-20220119100244938](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119100245.png)

10.输入许可证,AU15A-6XZEH-0891Q-LGYXV-YG0ZF(如果不能用百度搜一个)

![image-20220119100336911](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119100336.png)

11.安装完成

![image-20220119100351822](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119100351.png)

## 2 centos安装

1.点击创建虚拟机,点击下一步

![image-20220119102420828](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119102420.png)

2.选择centos7系统镜像文件--点击下一步

![image-20220119102529592](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119102529.png)

3.选择存放路径--下一步

![image-20220119102635564](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119102635.png)

4.设置硬盘大小--60G,点击下一步

![image-20220119102739430](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119102739.png)

5.点击完成

![image-20220119102759374](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119102759.png)

6.![image-20220119102832924](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119102833.png)

7.选中虚拟机,点击开启次虚拟机

![image-20220119102909140](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119102909.png)

* 开机蓝屏解决办法(没有就跳过)
  * ![image-20220526092925304](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220526092925.png)
  * ![image-20220526093230785](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220526093230.png)
  * 重启电脑

8.选择第一个安装centos7,按回车键

![image-20220119103044042](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119103044.png)

9.选择语言--中文,点击继续

![image-20220119103310234](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119103310.png)

10.点击安装位置,然后跳转界面,直接点击完成

![image-20220526085727880](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220526085735.png)

![image-20220119103438017](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119103438.png)

11.点击网络和主机名(一定需要点)

![image-20220119103535315](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119103535.png)

![image-20220119103603606](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119103603.png)

12.点击开始安装

![image-20220119103633539](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119103633.png)

13.点击设置root用户密码,设置密码123456,点击完成

![image-20220119103717797](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119103717.png)

14.等待安装完成

![image-20220119103806704](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119103806.png)



15.等待安装完后,点击重启即可

![image-20220119105708268](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119105708.png)

### 2.1 vmware的开关机及拍快照

* vmware上方可以进行关闭,重启等操作
* 快照功能:使用快照功能可以对当前linux操作系统备份

## 3.linux系统介绍

### 3.1 linux的发展史 

![image-20220117202634227](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220117202634.png)

- 创始人
  
  - 林纳斯-托瓦兹 
  
- 发展
  - ![image-20220420104450583](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220420104457.png)
  - ![image-20220420104525383](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220420104525.png)
- 优点
  - 安全
  - 开源
  - 稳定
  - 图形界面不是它的优点
- 版本

```mysql
# CentOS7.6 下载地址
  
  
# CentOS-7-x86_64-DVD-1810.iso  CentOS 7.6 DVD 版  4G
http://mirrors.163.com/centos/7.6.1810/isos/x86_64/CentOS-7-x86_64-DVD-1810.iso
  
# CentOS-7-x86_64-Everything-1810.iso CentOS 7.6 Everything版  10G
http://mirrors.163.com/centos/7.6.1810/isos/x86_64/CentOS-7-x86_64-Everything-1810.iso
  
# CentOS-7-x86_64-LiveGNOME-1810.iso CentOS 7.6 LiveGNOME版  1G 桌面版
http://mirrors.163.com/centos/7.6.1810/isos/x86_64/CentOS-7-x86_64-LiveGNOME-1810.iso
  
# CentOS-7-x86_64-LiveKDE-1810.iso CentOS 7.6 LiveKDE版 2G  桌面版
http://mirrors.163.com/centos/7.6.1810/isos/x86_64/CentOS-7-x86_64-LiveKDE-1810.iso
  
# CentOS-7-x86_64-Minimal-1810.iso CentOS 7.6 最小化版 918M
http://mirrors.163.com/centos/7.6.1810/isos/x86_64/CentOS-7-x86_64-Minimal-1810.iso
  
# CentOS-7-x86_64-NetInstall-1810.iso CentOS 7.6 网络安装版
http://mirrors.163.com/centos/7.6.1810/isos/x86_64/CentOS-7-x86_64-NetInstall-1810.iso
```

### 3.2 xshell的安装

* 解压安装包,点击绿化处理,在桌面可以找到xshell图标
* 1.点击新建
* ![image-20220119114535019](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119114535.png)
* ![image-20220119114606039](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119114606.png)
* ![image-20220119114640885](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119114640.png)
* ![image-20220119114717743](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119114717.png)
* ![image-20220119114805620](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119114805.png)
* ![image-20220119114908442](https://woniumd.oss-cn-hangzhou.aliyuncs.com/test/xiayongxiong/20220119114908.png)
* 

### 3.3 目录

- cd:切换目录
- ls:显示当前目录下的子目录和文件
- cd ../  返回上一级
- 练习
  - 进入etc目录 
  - 进入sysconfig目录
  - 返回上级目录     
  - 进入/目录

















