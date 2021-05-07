#2021/4/28 
#docker
	ubuntu 启动命令：
    sudo docker images
    密码：1

##官网查命令：
	命令：https://docs.docker.com/reference/

##Ubuntu进入root权限
	命令：sudo su    //key=1

#B站拷贝常用命令
	attach    # 当前shell下attach连接指定运行镜像
	build     # 通过Dockerfile定制镜像
	commit    # 提交当前容器为新的镜像
	cp        # 从容器中拷贝指定文件或目录到宿主机中
	create    # 创建一个新的容器，同 run 但不启动容器
	diff      # 查看 docker 容器变化
	events    # 从docker服务器获取容器实时事件
	exec      # 在已存在的容器上运行命令
	export    # 导出容器的内容流作为一个 tar 归档文件【对应 import】
	history   # 展示一个镜像形成历史
	images    # 列出系统当前镜像
	import    # 从tar包中的内容创建一个新的文件系统映像【对应 export】
	info      # 显示系统相关信息
	inspect   # 查看容器详细信息
	kill      # kill 指定的容器
	load      # 从一个 tar 包中加载一个镜像【对应 save】
	login     # 注册或者登录一个 docker 源服务器
	logout    # 从当前 Docekr registry 退出
	logs      # 输出当前容器日志信息
	port  	  # 查看映射端口对应的容器内部源端口
	pause	  # 暂停容器
	ps        # 猎户容器列表
	pull      # 从docker镜像源服务器拉取指定镜像或者库镜像
	push      # 推送指定镜像或者库镜像至docker源服务器
	restart   # 重启运行的容器
	rm        # 移除一个或多个容器
	rmi       # 移除一个或多个镜像 （无容器使用该镜像才可删除，否则需要删除相关容器才可继续或 -f 强制删除）
	run       # 创建一个新的容器并运行一个命令
	save      # 保存一个镜像为一个 tar 包【对应 load】
	search    # 在 docker hub 中搜索镜像
	start     # 启动容器
	stop      # 停止容器
	tag       # 给源中镜像打标签
	top       # 查看容器中运行的进程信息
	unpause   # 取消暂停容器
	version   # 查看 docker版本号
	wait      # 截取容器停止时的退出状态值

#Linux命令
	1. mkdir #建立目录
	2. 删除目录：
		rmdir 删除空目录
		rm -r 删除非空目录,有提示
		rm -r -f 删除非空目录,无提示
	3.ls    查看当前目录下所有文件
	  pwd　 查看当前目录路径
	4.进入文件后，按"i"开始写入内容；按"esc"后再":wq"保存并退出
	q   表示退出，
	wq  表示保存退出，
	q！ 表示强制退出，不对文件进行保存。
	wq  强制性写入文件并退出。即使文件没有被修改也强制写入，并更新文件的修改时间。
	5.ls
	ls -a 列出文件下所有的文件，包括以“.“开头的隐藏文件（linux下文件隐藏文件是以.开头的，如果存在..代表存在着父目录）。
	ls -l 列出文件的详细信息，如创建者，创建时间，文件的读写权限列表等等。
	ls -F 在每一个文件的末尾加上一个字符说明该文件的类型。"@"表示符号链接、"|"表示FIFOS、"/"表示目录、"="表示套接字。
	ls -s 在每个文件的后面打印出文件的大小。  size(大小)
	ls -t 按时间进行文件的排序  Time(时间)
	ls -A 列出除了"."和".."以外的文件。
	ls -R 将目录下所有的子目录的文件都列出来，相当于我们编程中的“递归”实现
	ls -L 列出文件的链接名。Link（链接）
	ls -S 以文件的大小进行排序

#docker名词意义
	镜像（image）：docker镜像就好比是一个模板，通过这个模板来创建容器服务，例如：tomcat镜像===>run===>tomcat01容器（提供服务器），通过这个镜像可以创建多个容器（最终服务运行或者项目运行就是在容器中的）
	容器（container）：docker利用容器技术，独立运行一个或者一组应用，通过镜像来创建的。启动，停止，删除等基本命令。目前可以把容器理解为就是一个简易的Linux系统。
	仓库（repository）：仓库就是存放镜像的地方，可分为公有仓库和私有仓库。如docker hub、阿里云等

#docker常用命令
	命令： docker ps  #列出当前正在运行的容器
		-a     #列出当前正在运行的容器+带出历史运行过的容器
		-n=?   #显示最近创建的容器
		-q     #只显示容器编号

#镜像命令
	查看所有本地的主机上的镜像
	docker images
		解释：
			REPOSITOPY	镜像的仓库源
			TAG			镜像的标签
			IMAGE ID	镜像id
			CREATED		镜像的创建时间
			SIZE		镜像的大小
		可选项
		  -a	列出所有镜像
		  -q	只显示镜像的id
	搜索镜像
	docker search 

	强制删除镜像
	docker rmi -f 镜像id
	
#容器命令
##退出容器
	命令：
	 exit 直接停止且退出容器
	 ctrl+p+q 容器不停止但退出

		
###删除容器
	命令：
	  docker rm 容器id		删除指定容器，不能删运行中的
	  docker rm -f $(docker ps -aq) 删除所有容器，能删运行中的
	
###启动与停止容器
	命令：
	  docker start 容器id		启动
	  docker restart 容器id	重启
	  docker stop 容器id		停止当前运行容器
	  docker kill 容器id		强制停止
###后台启动容器
	 命令： docker run -d 镜像名
		#问题：docker ps,发现该容器进程停止了
		 常见的坑：docker 容器使用后台运行，就必须要有一个前台进程，docker发现没有应用，就会自动停止。
		 例如安装nginx，容器启动后，发现自己没有提供服务，就会立刻停止
###查看日志
	 命令： docker logs
###显示日志
	 命令： docker logs -tf --tail 10 容器id
		注：-tf //显示日志
			--tail number //要显示的日志条数
###查看容器中的进程信息 
	 命令： docker top 容器id
###查看镜像元数据
	 命令： docker inspect 容器id
###进入当前正在运行的容器
	//容器通常都是使用后台方式运行的，需要进入容器，修改一些配置
	命令： 
		docker exec -it 容器id bashShell  //进入容器后开启新的终端，可以在里面操作（常用）
		docker attach 容器id //进入容器正在执行的终端，不会启动新进程
###从容器内拷贝文件到主机上
	docker cp 容器id：/容器内路径/目的的主机路径
#作业1 部署NGINX
	docker search nginx //查询NGINX镜像
	docker pull nginx  //下载安装
	docker images  //查看镜像
	docker run -d --name nginx01 -p 3344:80 nginx  
		//docker run 启动
		  -d 后台运行
		  --name 给容器命名
		  -p 暴露一些端口号
		      3344 服务器外部地址
		      80 容器内部地址
	docker ps //查看
	curl localhost:3344 //本机自测
	docker exec -it nginx01 /bin/bash //进入容器
	whereis nginx //找配置文件
	cd /etc/nginx //进入nginx
	ls
	docker stop //停止
	
	#思考问题：每次改动nginx配置文件，都需要进入容器内部，十分的麻烦。是否能够实现在容器外部提供一个映射路径，达到在容器外修改文件名，容器内部自动修改？
	答：可以，用“-v 数据卷”技术。

#作业2 装Tomcat	
	#官方的使用：docker run -it --rm tomcat:9.0
	  一般用来测试，用完即删
	#作业1中，先下载再启动，用完后容器还在
	
	
	//docker pull tomcat:9.0
	docker pull tomcat
	docker images
	docker run -d -p 3355:8080 --name tomcat01 tomcat //外网已经可以访问，但404
	docker exec -it tomcat01 /bin/bash  //进入容器
		#发现问题：1.Linux命令少了；2.没有webapps。这是阿里云镜像的原因，默认是最小的镜像，所有不必要的都剔除掉。
	ls
	ll
	ls -al
	
	cd webapps.dist/  #进入文件夹webapps.dist
	ls
	cd .. #后退一步
	cp -r webapps.dist/* webapps #将webapps.dist下所有文件都拷贝到webapps下.可以访问了

	#思考问题：每次部署项目，都要进入容器，十分麻烦？若是可以在容器外部提供一个映射路径，webapps,我们在外部放置项目，就自动在内部同步了。

#作业3 部署es+kibana
	3.1elasticsearch
	#es暴露的端口很多；十分耗内存；es的数据一般需要放置到安全目录，挂载。
	官方启动es：
	docker run -d --name elasticsearch --net somenetwork -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:tag
	//--net somenetwork 网络配置
	//启动后发现整个服务器都卡了
	docker stats //查看CPU状态
	-e 限制状态
	docker run -d --name elasticsearch02 --net somenetwork -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -e ES_JAVA_OPTS="-Xms64m -Xmx512m elasticsearch:tag
	curl localhost:9200


#docker镜像
##镜像是什么
	镜像是一种轻量级、可执行的独立软件包，用来打包软件运行环境和基于运行环境开发的软件，它包含运行某个软件所需的所有内容，包括代码、运行时的库和环境变量和配置文件。
	所有的应用直接打包成镜像，就能直接跑起来。
	如何得到镜像：
	1.从远程仓库下载
	2.拷贝
	3.自己制作一个镜像dockerfile

##docker镜像加载的原理
	docker的镜像实际上是由一层一层的文件系统组成，名为联合文件系统UnionFS
	bootfs（boot file system）主要包含BootLoader和kernel，BootLoader主要是引导加载kernel，Linux刚启动时会加载bootfs文件系统，在docker镜像的最底层是bootfs。这一层与我们典型的Linux/Unix系统是一样的，包含boot加载器和内核，当boot加载完成之后，整个内核就都在内存中了，此时内存的使用权已由bootfs转交给内核，且系统也会卸载bootfs。

	rootfs，在bootfs之上，包含的就是典型Linux系统中的/dev /proc /bin /etc等标准目录和文件，rootfs就是各种不同的操作系统发行版，比如Ubuntu，centos等。

	平时安装进虚拟机的centos都是好几个G，为什么docker这里才200M？
	对于一个精简的os，rootfs可以很小，只需要包含最基本的指令、工具和程序库就行，因为底层直接用host的kernel，自己只需要提供rootfs就可以了。由此可见对于不同的Linux发行版，bootfs基本是一致的，rootfs会有差别，因此不同的发行版可以共用bootfs。

	虚拟机启动是分钟级别，容器时秒级

#commit镜像
	docker commit 提交容器成为一个新的副本
	#命令与git原理相似
	docker commit -m="提交的描述信息" -a="作者" 容器id 目标镜像名:[TAG]
	例：
	docker pull tomcat
	docker images
	docker run -d -p 8080:8080 tomcat
	docker ps
	docker exec -it 容器id /bin/bash #进入容器
	cd .. #后退一步
	cp -r webapps.dist/* webapps #将webapps.dist下所有文件都拷贝到webapps下.可以访问了
	exit
	docker ps
	docker commit -a="sys" -m="add webapps app" 容器id tomcat02:1.0 #生成了一个全新版本
	docker images #查看，发现新版本了，size也比原来的略大

#容器数据卷
	docker理念：将应用和环境打包成一个镜像。
	如果数据都在容器中，删除容器的同时，数据也丢失了。需求：数据持久化。
	容器之间可以有一个数据共享的技术。
	docker容器中产生的数据，同步到本地。这就是卷技术。本质：目录的挂载，将我们容器内的目录，挂载到Linux上。
	总结：容器的持久化和同步操作，容器间也是可以数据共享的。
##使用数据卷
	方法一：直接使用命令挂载 -v
		docker run -it -v 主机目录:容器内目录
	cd /home
	ls
	docker run -it -v /home/ceshi:/home centos /bin/bash
	#启动后，通过  docker inspect 容器id  查看

###实战：MySQL数据同步
	docker search mysql
	docker pull mysql:5.7  #下载获取镜像

	docker images
	##官方测试：docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:tag
	docker run -d -p 3310:3306 -v /home/mysql/conf:/etc/mysql/conf.d -v /home/mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 --name mysql01 mysql:5.7
	##
	  -d 后台运行
	  -p 端口映射
	  -v 卷挂载
	  -e 环境配置
	  --name 容器名字
	###启动成功后，在本地使用SQLyog，发现成功连接。
	###在本地创建一个数据库，查看一下映射的路径，发现同步出一个文件
	###假设将容器删除：docker rm -f mysql01
	   （新开的命令行）挂载到本地的数据卷，依旧没有丢失
			cd mysql
			cd data/
			ls

#具名和匿名挂载
##匿名挂载
	-v 容器内路径
	docker run -d -p --name nginx01 -v /ect/nginx nginx

	#查看所有卷(volume)的情况
	docker volume ls
	
##具名挂载
	docker run -d -P --name nginx02 -v juming-nginx:/etc/nginx nginx
	docker volume inspect juming-nginx(卷名)  #查看这个卷
	
	##所有的docker容器内的卷，没有指定目录的情况下，都是在"/var/lib/docker/volumes/xxxx/_data"
	通过具名挂载可以方便地找到我们的一个卷，大多数情况再使用具名挂载

	#如何确定是具名/匿名/指定路径挂载？
	-v 容器内路径  		#匿名挂载
	-v 卷名:容器内路径 	#具名挂载
	-v /宿主机路径:容器内路径	#指定路径挂载
	#拓展
	docker run -d -p --name nginx01 -v /ect/nginx:ro nginx   //只读，只有宿主机能操作，容器内部不能
	docker run -d -p --name nginx01 -v /ect/nginx:rw nginx   //可读可写

#初识Dockerfile 挂卷法二
	Dockerfile就是用来构建docker镜像的构建文件。命令脚本
	#测试
	mkdir docker-test-voume  //新建文件夹
	ls
	pwd  //列出当前绝对路径
	cd docker-test-voume/    //进入该文件夹
	vim dockerfile		//创建脚本文件，通过这个脚本可以生成镜像，镜像是一层一层的，脚本就是一个个命令，每个命令都是一层
		FROM centos
		VOLUME ["volume01","volume02"]
		CMD echo "----end----"
		CMD /bin/bash
			//:w --保存但不退出
			//:wq --保存并退出	
	cat dockerfile	//查看
	docker build -f /home/docker-test-volumem/dockerfile -t sys/ubuntu:1.0 .  //生成镜像
	docker images
	docker run -it 容器id /bin/bash   //启动自己写的镜像容器
	ls -l	
	ls
	cd volume01  //进入该卷
	touch container.txt //创建文件
	#新开一个命令行，root，开docker
	docker ps
	docker inspect 正在运行的容器id  ##能找到mounts，可查看卷挂载的路径
	cd volume01对应的路径拷贝
	ls  //可以看到文件container.txt
	###测试一下刚才的文件是否同步出去了
	###这种方式未来使用得多，因为我们通常会构建自己的镜像
	###假设构建镜像的时候没有挂载卷，则需要手动挂载 -v 卷名:容器内的路径

#数据卷容器
###多个MySQL同步数据
	#启动docker01
	docker run -it --name docker01 自建容器的id
	 #按ctrl+p+q
	docker ps
	#启动docker02
	docker run -it --name docker02 --volumes-from docker01 容器id（或sys/ubuntu:1.0）//docker02挂载到docker01上，后者是父卷
		#新建命令行
		docker attach 容器id
		ls -l
		cd volume01
		touch docker01  //在docker01中创建一个文件
	cd volume01
	ls  //可以发现：docker02的volume01中创建的文件，在docker01的volume01中同步出现

    ##退出卷后，删掉docker01
	docker ps -a  //显示所有容器
	docker rm -f 容器docker01的id  //删除docker01容器
	docker01 ps -a
	##在docker02 的volume01中去
	ls  //发现docker01的volume01创建的文件仍然存在

####多个MySQL实现数据共享
	docker run -d -p 3310:3306 -v /etc/mysql/conf.d -v /var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 --name mysql01 mysql:5.7

	docker run -d -p 3310:3306 -v /etc/mysql/conf.d -v /var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 --name mysql02 --volumes-from mysql01 mysql:5.7
	##这个时候，可以实现两个容器数据同步

	#结论：容器之间配置信息的传递，数据卷容器的生命周期持续到没有容器使用为止。

##dockerfile介绍
	dockerfile是用来构建docker镜像的文件，命令参数脚本
	构建步骤
		1.编写一个dockerfile文件
		2.docker build构建成为一个镜像
		3.docker run运行镜像
		4.docker push 发布镜像（DockerHub、阿里云镜像仓库）
##dockerfile构建过程
###基础知识
	1.每个保留关键字（指令）都必须是大写字母
	2.执行按照从上至下顺序执行
	3.#表示注释
	4.每一个指令都会创建提交一个新的镜像层，并提交
	
	dockerfile是面向开发的，我们以后要发布项目，做镜像，就需要编写dockerfile文件，这个文件十分简单。
	docker镜像逐渐成为企业交付的标准，必须要掌握。

	DockerFile：构建文件，定义了一切步骤，源代码。
	DockerImages：通过DockerFile构建生成的镜像，最终发布和运行的产品。
	Docker容器：容器就是镜像运行起来提供服务的。
#2021/4/29 
###dockerfile基本指令

	FROM	#指定基础镜像，一切从这里开始构建

	MAINTAINER	#指定镜像是谁写的，姓名+邮箱。格式为MAINTAINER user_name user_email

	RUN		#镜像构建的时候需要运行的命令。格式为RUN command或 RUN ["EXECUTABLE","PARAM1","PARAM2".....]，前者在shell终端中运行命令，/bin/sh -c command，例如：/bin/sh -c "echo hello"；后者使用exec执行，指定其他运行终端使用RUN["/bin/bash","-c","echo hello"]

	ADD		#步骤，添加Tomcat镜像，这个Tomcat压缩包就是添加内容

	WORKDIR	#设置镜像的工作目录。格式： WORKDIR /path 
	为后续的RUN CMD ENTRYPOINT指定配置工作目录，可以使用多个WORKDIR指令，若后续指令用得是相对路径，则会基于之前的命令指定路径

	VOLUME	#作用是创建在本地主机或其他容器可以挂载的数据卷，用来存放数据。格式为 VOLUME ["/data"]

	EXPOSE	#指定暴露端口。格式为 EXPOSE port [port2,port3,...]

	CMD		#用于指定容器启动时执行的命令，每个Dockerfile只能有一个CMD命令，多个CMD命令只执行最后一个。若容器启动时指定了运行的命令，则会覆盖掉CMD中指定的命令
	支持三种格式：
	CMD ["executable","param1","param2"]，使用exec执行，这是推荐的方式。
	CMD command param1 param2 在/bin/sh中执行。
	CMD ["param1","param2"] 提供给ENTERYPOINT的默认参数。

	ENTRYPOINT	#用于配置容器启动后执行的命令，这些命令不能被docker run提供的参数覆盖。和CMD一样，每个Dockerfile中只能有一个ENTRYPOINT，当有多个时最后一个生效。可以追加命令。
	格式有两种：
	ENTRYPOINT ["executable","param1","param2"]
	ENTRYPOINT command param1,param2 会在shell中执行

	ONBUILD	#指定当所创建的镜像作为其他新建镜像的基础镜像时所执行的指令。格式ONBUILD [INSTRUCTION]

	COPY	#类似ADD，将文件拷贝到镜像中。格式为：COPY src desc 复制本地主机src目录或文件到容器的desc目录，desc不存在时会自动创建

	ENV		#用于指定环境变量，这些环境变量，后续可以被RUN指令使用，容器运行起来之后，也可以在容器中获取这些环境变量。格式为：EVN key value 

	USER	#指定容器运行时的用户名或UID，后续的RUN也会使用指定的用户。要临时使用管理员权限可以使用sudo。在USER命令之前可以使用RUN命令创建需要的用户。格式为：USER username

##dockerfile实战
	Docker Hub中99%的镜像都是从"FROM scratch"这个基础镜像过来的，然后添加需要的软件和配置来构建的。

	创建一个自己的centos/Ubuntu：
	1.编写dockerfile配置文件
	mkdir dockerfile  #创建目录文件
	cd dockerfile/	  #进入该目录
	vim mydockerfile-ubuntu #创建文件，内容见日记截图
	cat mydockerfile-ubuntu #查看该文件

	2.通过上面这个文件构建镜像
	#命令 docker build -f dockerfile文件路径 -t 镜像名:[tag]
	docker build -f mydockerfile-ubuntu -t myubuntu:1.0 .
	
	3.测试
	docker images
	docker run -it myubuntu:1.0
	pwd  #显示：/usr/local
	ifconfig #能运行
	vim test #能运行

###CMD和ENTRYPOINT的区别
	1.测试CMD
	cd dockerfile/ 	#进入该文件夹
	vim dockerfile-cmd-test	#创建、编写文件
		FROM ubuntu
		CMD ["ls","-a"]
	docker build -f dockerfile-cmd-test -t cmdtest .	#构建镜像
	docker run cmdtest的id	#跑起来，发现命令"ls-a"生效
	#继续测试
	docker run cmdtest的id -l	#报错，见日记
	##原因：
		用cmd的情况下，"-l"替换了" CMD ["ls","-a"] "命令，而"-l"是无效命令，所以报错。

	2.测试ENTRYPOINT 追加命令直接拼接在其后
	vim dockerfile-entrypoint-test	#创建、编写文件
		FROM ubuntu
		ENTRYPOINT ["ls","-a"]
	docker build -f dockerfile-entrypoint-test -t entrypoint-test .	#构建镜像
	docker run 刚建的entrypoint的id	#跑起来，发现命令"ls-a"生效
	#继续测试
	docker run entrypoint的id -l		#顺利执行
	
	
	
	
#Tomcat镜像
	


	
2021/5/2 9:14:57 	
#部署net-snmp
	mkdir snmp-test  #创建目录文件
	cd snmp-test/	  #进入该目录
	docker pull weldpua2008/net-snmp:ubuntu-14.04 #下载安装snmpd
	docker images #查看镜像
	#运行镜像
	docker run -d --name snmp01 -p 161:161 容器id
	//curl localhost:161 #本机自测
	#利用commit将容器布置成为镜像
	doacker images
	docker commit -a="sys" -m="make snmpd to images" 容器id net-snmp:1.0
	docker images	



##开始测试
	snmpwalk -v 1或2(代表SNMP版本) -c SNMP读密码 IP地址 OID(对象标示符)

	(1) -v： 指定snmp的版本, 1或者2；
	(2) -c:    指定连接设备SNMP读密码；
	(3) IP:    指定要walk的设备的IP地址；
	(4) Oid：代表要获取设备的指标oid；

	用法举例：

	例如获取cisco设备192.168.17.191的接口类型
	Snmpwalk –v 2 –c public 192.168.17.191 1.3.6.1.2.1.2.2.1.3

	snmpwalk命令则是测试系统各种信息最有效的方法,常用的方法如下:

	1、snmpwalk -c public -v 1 -m ALL 10.0.1.52 .1.3.6.1.2.1.25.1    得到取得windows端的系统进程用户数等

	2、snmpwalk -c public -v 1 -m ALL 10.0.1.52 .1.3.6.1.2.1.25.2.2  取得系统总内存

	3、snmpwalk -c public -v 1 -m ALL 10.0.1.52 hrSystemNumUsers       取得系统用户数

	4、snmpwalk -c public -v 1 -m ALL 10.0.1.52 .1.3.6.1.2.1.4.20   取得IP信息

	5、snmpwalk -v 2c -c public 10.0.1.52 system  查看系统信息

	6、snmpwalk -v 1 10.0.1.52 -c public ifDescr  获取网卡信息

	1、snmpwalk -v 2c -c public 10.0.1.52 .1.3.6.1.2.1.25.1   得到取得windows端的系统进程用户数等

	其中-v是指版本,-c 是指密钥。

	snmpwalk功能很多,可以获取系统各种信息,只要更改后面的信息类型即可。如果不知道什么类型,也可以不指定,这样所有系统信息都获取到:

	snmpwalk -v 2c -c public 10.0.1.52

	####查询ip地址
	1.宿主机ip查询：hostname -I 第一个ip就是物理机的
	2.运行容器的ip：docker inspect 容器名  //找IPAddress
	测试机985 231 890
	宿主机ip:192.168.1.109
	被测试机927 924 283
	宿主机ip:192.168.1.103
	容器snmp06 ip：172.17.0.2

	docker exec -it 容器名 ip addr


#记录成功查询的流程
	注：开启文件夹在12402-文档-sunlogin files中看“927启动文档”
	1.部署镜像
	docker pull really/snmpd:latest #下载镜像
	docker images
	docker run -d --name snmp01 -p 161:161 镜像id #后台启动
	docker ps
	docker inspect 容器id #查容器的ip地址 172.17.0.2

	2.查询：参考博客园-三度的“docker网络详细理解-容器网络互通”
	##启动snmp服务
	sudo service snmpd start
	sudo netstat -antup | grep 161
	##查询物理机的ip地址
	hostname -I  192.168.1.103
	##用Linux ping通容器
	ping -c 10 172.17.0.2 #丢包率为0%
	#用snmpwalk指令查询容器ip信息
	snmpwalk -v 2c -c public 192.168.1.103 #查物理机ip出信息
	snmpwalk -v 2c -c public 172.17.0.2 1.3.6.1.2.1.4.20.1.1 #查容器ip地址 出信息，成功
