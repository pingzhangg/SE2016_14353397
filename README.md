# SE2016_14353397

安装DOL的步骤(ubuntu为例)：
1.
$	sudo apt-get update
$	sudo apt-get install ant
$ 	sudo apt-get install openjdk-7-jdk
$	sudo apt-get install unzip

2.解压文件
新建dol的文件夹 
$	mkdir dol
将dolethz.zip解压到 dol文件夹中
$	unzip dol_ethz.zip -d dol
解压systemc
$	tar -zxvf systemc-2.3.1.tgz
编译systemc
解压后进入systemc-2.3.1的目录下
$	cd systemc-2.3.1
新建一个临时文件夹objdir
$	mkdir objdir
进入该文件夹objdir
$	cd objdir
运行configure(能根据系统的环境设置一下参数，用于编译)
$	../configure CXX=g++ --disable-async-updates

3.编译dol
进入刚刚dol的文件夹
$	cd ../dol
修改build_zip.xml文件
找到下面这段话，就是说上面编译的systemc位置在哪里，
<property name="systemc.inc" value="YYY/include"/>
<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>
把YYY改成上页pwd的结果（注意，对于  64位 系统的机器，lib-linux要改成lib-linux64）

<property name="systemc.inc" value="/home/shapes/base/resources/lib/systemC/include"/><property name="systemc.lib" value="/home/shapes/base/resources/lib/systemC/lib-linux/libsystemc.a"/>
然后是编译
$	ant -f build_zip.xml all
若成功会显示build successful

接着可以试试运行第一个例子
进入build/bin/mian路径下
$	cd build/bin/main
然后运行第一个例子
$	ant -f runexample.xml -Dnumber=1

成功结果如图
到目前为止，实验过程中在安装ＤＯＬ环境的时候，总是在需要过程截图的地方出现不一样，个人虽然前面有学过操作系统，但是还是觉得挺困难，最后在ＴＡ的帮助下完成了ＤＯＬ的环境配置。GIT的安装这次实验
一直以为会很困难（因为上课TA讲了好多东西，而我坐在后面并没有听懂什么），但是后来接触百度呀问TA或者同学。其实还可以，做出来了很有成就感。

（注：有截图保留，但是好像这个不能复制图片上去，所以就没有上传，如果需要的话可以发电子版给TA）
