centos基本命令
---------------------------
	CentOS						Windows
	$>ls						cmd>dir				//
	$>ls --help										//查看命令帮助
	$>man ls										//查看命令帮助
	
	$>clear						cmd>cls				//清屏
	$>cd /home					cmd>cd d:/			//切换目录
	$>cd .						cmd>cd .			//进入当前目录
	$>cd ..						cmd>cd ..			//进入上级目录
	$>cd /home/centos			cmd>cd d:/xx/x/x	//进入绝对路径

	$>pwd											//显式当前目录
	$>whoami										//显式当前用户名

	$>su root										//切换用户,输入密码,swith user
	$>passwd										//修改当前用户的密码

	$>ifconfig					cmd>ipconfig			//查看ip地址
	$>ping localhost			cmd>ping localhost		//查看网络连通情况
	$>ping www.baidu.com		cmd>ping www.baidu.com	//查看网络连通情况

	$>启动桌面版的网卡
		on.
	$>su centos											//
	$>cd /home/centos									//
	$>cd ~												//回到主目录
	$>cd -												//回到上次的目录
	$>ll												//别名,ls -l --autocolor...
	$>alias												//查看所有的别名
	$>ls -a -l -h										//查看当前目录-h:人性化 -l:列表 -a:显式.开头
	$>mkdir ~/Downloads/a								//创建目录
	$>touch ~/Downloads/a/1.txt							//创建文件
	$>echo helloworld > 1.txt							//重定向输出(覆盖)
	$>echo helloworld >> 1.txt							//重定向输出(追加模式)
	$>cat 1.txt					cmd>type a.txt			//查看文件
	$>cp 1.txt 2.txt									//复制文件
	$>rm 1.txt											//删除文件
	$>rm -rf /											//强行递归删除
	$>mv a.txt tmp/										//强行递归删除


	[centos client中切换模式]
	ctrl + alt + f6										//切换到文本模式
	ctrl + alt											//切换鼠标
	ctrl + alt + f1										//切换桌面模式.
	ctrl + alt + f5										//切换到新的文本模式

	

	[nano文本编辑器,命令行模式]
	$>nano a.txt										//打开nano编辑器，编辑a.txt文件
	$>....
	$>ctrl + o											//保存文件,提示后直接回车
	$>ctrl + x											//退出文件
	$>ctrl + k											//cut 文本
	$>ctrl + u											//cut 文本

	$>more a.txt										//分屏显式
	  q:退出
	  h:帮助
	$>more -5 a.txt										//显式前5行内容
	$>tail a.txt										//最后10行内容

	$>find . | more										// | 是管道符，前面的命令的输出作为后面命令输入。
	$>find ~											
	$>ls -aR ~											//递归显式主目录所有的文件.(a表示包含.开头的文件)
	$>head a.txt										//显式前10行
	$>head -n 10 a.txt									//显式前10行
	$>head -10 a.txt									//显式前10行

	$>tail a.txt
	$>tail -n 20 a.txt
	$>tail -20 a.txt
	$>tail --lines=20 a.txt

	$>wc -c -l -w a.txt									//统计文本信息,
														//显式统计信息-c:字节 -l:line -w:word

	$>hostname		//查看主机名称
	$>uname -r		//查看系统内核
	$>uname -a		//查看系统内核
	$>uname -p		//查看系统内核
	$>uname -m		//查看系统内核


	$>file xxx.xx		//查看文件类型
	$>gzip a.txt		//原地压缩
	$>gzip -d a.txt		//原地压缩
	$>gzip -dr tmp		//递归操纵文件夹下的文件
	$>gunzip a.txt.gz	//等价于gzip -d a.txt

	$>tar -cvf my.tar 1.txt tmp		//创建归档文件
	$>tar -vxf my.tar				//解档文件

	$>find . | grep txt | cp `xargs` temp	//xargs是多行变单行，使用空格替换回车换行符.
											//`` : 是强制命令解析。
	$>ping `cat a.txt`						//命令嵌套

	$>which echo							//查看命令的文件路径

目录和权限
----------------
	[windows]
	以磁盘分区物理结构作为文件系统结构
	
	[Linux文件类型]
	-		//文件
	d		//目录
	l		//链接,类似于windows快捷方式.
	b		//block,块文件。
	c		//字符文件

	[linux的权限]
	$>chmod				//修改文件(夹)权限
	$>chmod	g-w			//去除group中write权.

	chmod				//不受文件权限控制,只有owner和root才具有文件权限的修改权。
			

	[read权限]
		文件	:文件内容
		文件夹	:文件夹的内容	



	write权限
	------------

	execute权限
	-------------
		文件	:执行
		文件夹	:进入目录		


	[centos]
	逻辑结构.
	/					//文件系统的根.

	/bin				//最初的命令(祖先)，binary文件,可执行文件
	/sbin				//super binary(重要性高)

	/usr/bin			//厂商相关的命令,ubuntu
	/usr/sbin			//厂商相关的命令,ubuntu

	/usr/local/bin		//用户级别。
	/usr/local/sbin

	
	[客户端与宿主机之间的网络连通方式]
	1.桥接
		桥接(client完全等价于一台物理主机)

	2.NAT(最多,默认模式)
		a.Net Address transform,网络地址转换.
		b.客户机能访问外网，可以访问局域网内的其他物理主机。
		c.其他的局域网内物理主机不能访问客户机。

	3.only host.
		a.和NAT非常像。
		b.不能访问外网。
		

	4.查看client机的网络连接模式
		a.右键选择Centos客户机。
		b.点击"设置"
		c.网络适配器.
		
	5.查看DHCP的分配网段
		a.vmware-->编辑-->虚拟网络编辑器
		b.选中V8条目
		c.下方显示的V8的详细信息。
		d.点击DHCP的设置.
		e.查看分配网段.


	[修改静态IP]
	1.切换root用户
		$>su root
	2.编辑/etc/sysconfig/network-scripts/ifcfg-eno16777736
		a.备份文件
			$>cd /etc/sysconfig/network-scripts
			$>cp ifcfg-eno16777736 ifcfg-eno16777736.bak
		b.进入/etc/sysconfig/network-scripts
			$>cd /etc/sysconfig/network-scripts
		c.编辑ifcfg-eno16777736文件
			$>nano ifcfg-eno16777736
				TYPE=Ethernet					
				BOOTPROTO=none					
				DEFROUTE=yes					
				IPV4_FAILURE_FATAL=no			
				IPV6INIT=no
				IPV6_AUTOCONF=no
				IPV6_DEFROUTE=no
				IPV6_PEERDNS=no
				IPV6_PEERROUTES=no
				IPV6_FAILURE_FATAL=no
				NAME=eno16777736
				UUID=33f3ce5f-8b5c-41af-90ed-863736e09c29
				DEVICE=eno16777736
				ONBOOT=yes
				IPADDR=192.168.231.200
				PREFIX=24
				GATEWAY=192.168.231.2
				DNS=192.168.231.2

			注意:查看NAT网络的网关地址。
				0)Client机的网卡的DNS和GATEWAY设置为虚拟网卡NAT的网关值。
				1)vmware-->编辑-->虚拟网路编辑器
				2)v8条目
				3)点击"NAT设置"按钮
				4)查看网关地址:192.168.231.2(通常为xxx.xxx.xxx.2)
		e.重启网络服务
			$>su root
			$>service network restart
		
		f.****解决通过ip能够访问网络，通过域名无法访问的问题。*****
			1)编辑/etc/resolv.conf,添加名称服务器，内容是网关地址。
				nameserver 192.168.231.2
			2)保存退出
			
			3)重启服务
				$>su root
				$>service network restart
			4)测试www.baidu.com
				$>ping www.baidu.com

service管理命令
-------------------
	1.查看服务的状态
		$>service server_name status		//语法
		$>service network status
		$>service network start				//启动
		$>service network stop				//停止
		$>service network restart			//重启

mount挂载外设
-------------------
	1.右键client右下角的光盘图标 ->设置
	2.iso文件
		选择一个iso镜像文件。
	3.右键client右下角的光盘图标 ->连接.
	4.创建文件夹/mnt/cdrom
		$>su root
		$>mkdir cdrom
	5.挂载光驱/dev/cdrom到/mnt/cdrom
		$>mount /dev/cdrom /mnt/cdrom
		$>find . /mnt/cdrom				

卸载外设
--------------------
	1.从挂载的目录中出来,否则出现设备繁忙
		$>cd ..
	2.使用umount进行卸载
		$>umount /mnt/cdrom
	
启用client和host之间共享目录的功能
---------------------
	1.右键点击vmware中的client机，选择设置
	2.找到"选项" -> "共享文件夹" 
	3.选择"总是启用"
	4.在文件夹区域中添加要共享的目录
		d:/downloads
	5.确定.
	6.重启客户机.


vmware Vnet8虚拟网卡丢失的找回问题
--------------------------------------
	1.打开VMware Workstation 
	2.然后点击Edit --> Virtual Network Edit --> 打开Virtual Network Edit框 ，
	3.点击最下面的的Restore Default 按钮，
	3.恢复默认设置，这会在网络连接那块可以看到丢失的VMware Network Adapter VMnet8 又回来啦，
	  或者 在Virtual Network Edit框 找到一个Add Network... 的按钮 弹出来一个框 然后在select a network to add 中选择VMnet8 
	  单击OK 就可以啦


虚拟机增强工具
------------------------------------
