ubuntu
-------------	
	apt		//advanced package tool,高级包工具。
	apt-get install

centos
-------------
	yum		//yellowdog updater modified.
	

	
软件源
-------------------
	Repository		//仓库.
	URL				//http:// 

	.d				//directory目录
	xxxd			//daemon

查看仓库文件
------------------
	/etc/yum.repos.d/xxx.repo

curl
------------------
	传输url上的数据的。
	[下载文件到指定目录]
	curl -o /etc/yum.repos.d/ali.repo http://mirrors.aliyun.com/repo/Centos-7.repo


更换centos的软件源
------------------
	1.下载源仓库文件,xxx.repo
		curl -o /etc/yum.repos.d/ali.repo http://mirrors.aliyun.com/repo/Centos-7.repo
	2.将repo文件保存到/etc/yum.repos.d/目录中。
	
屏蔽软件仓库
------------------
	1.将/etc/yum.repos.d/xxx.repo文件删除或者更换扩展名即可。

修改centos能够使用sudo命令
-------------------------------
	[/etc/sudoers]
	$>su root
	$>nano /etc/sudoers
		...
		centos ALL

使用yum进行软件包安装卸载
-------------------------------	
	$>yum list							//列出所有软件包
	$>yum list installed				//列出已经安装的软件包
	$>yum list installed | grep nano	//列出已经安装的软件包
	$>yum search nano					//在yum的软件源中搜索软件 
	$>yum remove nano					//卸载软件
	$>yum -y install nano				//直接安装，不需要yes确认.
	$>yum list installed | grep nano	//查看是否安装了Nano

	$>mkdir /home/centos/rpms
	
	$echo 以下命令只下载软件，不安装软件
	$>sudo yum install --downloadonly				//只下载
				  --downloaddir=/home/centos/rpms	//指定下载目录
				  wget
	
	//下载已经安装的软件
	$>sudo yum reinstall --downloadonly	
						 --downloaddir=/home/centos/rpms
						 wget

	$>sudo yum localinstall xxx.rpm	//从本地rpm文件直接安装软件


	
	$>su root
	$>yum search ifconfig
	$>yum -y install net-tools		//安装网络工具

	
	#==========修改网络地址======================	//需要重启network服务
	$>sudo nano /etc/sysconfig/network-scripts/ifcfg-eth1677736
		[/etc/sysconfig/network-scripts/ifcfg-eth1677736]
		...
		IPADDR=192.168.231.201
		GATEWAY=192.168.231.2
		DNS=192.168.231.2

	$>service network restart						//重启网络服务。

	$>sudo nano /etc/resolv.conf					//修改该文件不需要重启network服务
		[/etc/resolv.conf]
		nameserver 192.168.231.2

在没有nano时，使用自带的vi文本编辑器
-------------------------------------
	1.vi xx.txt
	2.模式切换
		esc				//切换到命令模式,退出编辑模式
						//:q!  不保存退出
						//:wq  保存退出
						//x		删除一个字符
						//dd	删除一行

		insert			//切换到编辑模式,退出命令模式
						//del backspace




制作iso镜像文件
-------------------------------------
	0.清除yum的缓存文件
		$.sudo yum clean cache

	1.重新制作yum的缓存(需要几分钟时间)
		$>sudo yum makecache

	2.搜索mkisofs软件包
		$>sudo yum search mkisofs
	
	3.安装mkisofs软件包
		$>sudo yum install mkisofs
	
	4.查看是否安装成功
		a)which
			$>which mkisofs
		
		b)通过yum list
			$>sudo yum list installed | grep geniso					//geniso是软件包名

	5.制作iso文件
		$>sudo mkisofs -r 
					   -o CentOS-7-Packages.iso /home/centos/rpms	//-r : 保留原文件,-o:输出的iso文件名

	6.挂载iso文件到client的光驱中。
		点击右下角的光驱图标。
	
	7.挂载cdrom中的文件到/mnt/cdrom下.
		$>mount /dev/cdrom /mnt/cdrom
	
	8.复制/mnt/cdrom/*到/home/centos/rpms目录下
		$>su centos
		$>mkdir ~/rpms
		$>cp /mnt/cdrom/* /home/centos/rpms
	
	9.挂载vmware安装目录下的linux.iso(虚拟机增强工具镜像文件)文件
		a)卸载/mnt/cdrom目录
			$>sudo umount /mnt/cdrom
		b)插入linux.iso镜像文件到光驱.
		c)连接设备
		d)挂载/dev/cdrom到/mnt/cdrom
			$>mount /dev/cdrom /mnt/cdrom
		
		e)复制/mnt/cdrom/*到/home/centos/linux/目录下
			$>su centos ; mkdir ~/linux
			$>cp /mnt/cdrom/* /home/centos/linux
	
安装虚拟机增强工具
----------------------
	1.挂载并复制linux.iso镜像文件文件到/home/centos/linux中
	2.tar开VM-xx-xxx.tar.gz
		$>su centos ; cd ~/linux
		$>tar -xzvf VMxxx.tar.gz
		$>cd vmware-tools-distrib
		$>su root ; 
		#====可能重复以下过程====
		$>./vmware-install.pl
		$>出现perl没有解释器的错误.
			解决办法:
			$>cd /home/centos/rpms
			$>sudo yum localinstall perl-5.16.3-286.e17.x86_64.rpm
		
		$>./vmware-install.pl
		$>出现gcc path找不到
			解决办法:
			$>cd /home/centos/rpms
			$>sudo yum localinstall gcc-xxx.rpm
		
		$>./vmware-install.pl
		$>出现kenel-headers path找不到
			解决办法:
			$>cd /home/centos/rpms
			$>sudo yum localinstall kernel-devel-xxx.rpm
		
