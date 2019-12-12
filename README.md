# third
这是一个test
# vim中删除大段代码
1.按esc进入命令行模式下，": set nu"显示行号
2.输入想要删除的行号，如":10,20d",回车即可
3.如果发现删错了，切换到命令行模式，按下"u"键撤销

#单行删除：
": 1d"
#多行删除：
": 10,20d"
#删除光标所在行
dd
#删除光标所在行以下的N行
Ndd

#复制多行
1.进入命令行模式下：
10,20 co 30 -->复制第10行到第20行的内容到第30行后面

vim 中多行注释
1 Ctrl+v进入v模式
2 上下方向键选中要注释的行
3 shift+i（即大写的I）行首插入
4 输入注释符//
5 按esc返回

反注释
1 Ctrl+v进入v模式
2 上下方向键选中要注释的行，左右键选择要删除的字符//
3 按d删除

#压缩命令
tar命令
　　解包：tar zxvf FileName.tar

　　打包：tar czvf FileName.tar DirName

gz命令

　　解压1：gunzip FileName.gz

　　解压2：gzip -d FileName.gz

　　压缩：gzip FileName

　　.tar.gz 和 .tgz

　　解压：tar zxvf FileName.tar.gz

　　压缩：tar zcvf FileName.tar.gz DirName

   压缩多个文件：tar zcvf FileName.tar.gz DirName1 DirName2 DirName3 ...

bz2命令

　　解压1：bzip2 -d FileName.bz2

　　解压2：bunzip2 FileName.bz2

　　压缩： bzip2 -z FileName

　　.tar.bz2

　　解压：tar jxvf FileName.tar.bz2

　　压缩：tar jcvf FileName.tar.bz2 DirName

bz命令

　　解压1：bzip2 -d FileName.bz

　　解压2：bunzip2 FileName.bz

　　压缩：未知

　　.tar.bz

　　解压：tar jxvf FileName.tar.bz

Z命令

　　解压：uncompress FileName.Z

　　压缩：compress FileName

　　.tar.Z

　　解压：tar Zxvf FileName.tar.Z

　　压缩：tar Zcvf FileName.tar.Z DirName

zip命令

　　解压：unzip FileName.zip

　　压缩：zip -r FileName.zip DirName

# linux系统在xshell终端输入命令不显示回车才显示的解决办法
可以输入：stty sane
尝试解决
etc/profile.d/conda.sh
/home/amy/lvmingxing/miniconda3

# 针对ctrl +c 终止进程无效的情况：
1.ctrl + z   挂起这个进程
2.jobs       查看正在后台运行的任务
3.bg(background) num     让进程在后台运行,查看后台进程情况，num为后台进程作业号
4.fg(foreground) num(fg % jobnumber) 调回前台，jobnumber是通过jobs命令查到的后台正在执行的命令的序号(不是pid)


ps -ef | grep 运行程序名(不带后缀)
ps aux | grep programe_name
kill -9 进程号
$ --这个符号主要是用在命令后，可以把命令执行放到后台执行

wget [parm] [url] 下载资源命令

取消vim中查找到的关键字后的背景颜色命令
:noh

监控日志文件：
tail -f logfilename
查看文件最后几行内容：
tail -n number filename
查看文件最后几行内容：
tail -n +number filename

#定时任务
cron crontab 命令

#调到后台运行
nohup python2 searche_image_rebuild.py >log/search_print.log 2>&1 &
nohup python2 get_feature_for_search_uu.py >log/get_feature_print.log 2>&1 &
nohup python2 addFeature_uu.py >log/addFeature_print.log 2>&1 &
最后的&表示后台运行
2 输出错误信息到提示符窗口
1 表示输出信息到提示符窗口, 1前面的&注意添加, 否则还会创建一个名为1的文件

# nohup 可以把进程调到后台运行，bg/fg也可以在前台后台切换，但不同的是，nohup在终端
# shell断开之后会忽略终端发出的hangup信号，但是bg 不会，所以当终端shell断开后，bg切换
# 的程序就会自动挂掉，但是nohup执行的程序不会这样

nohup python write_log.py > ./write_print.log 2>&1 &
nohup python read_log.py > ./read_print.log 2>&1 &

nohup python consume_msg.py > ./print_msg.log 2>&1 &

#linux中clear命令失效出现terminals database is inaccessible
解决办法：~$ export TERMINFO=/usr/share/terminfo
ctrl+l 也是和clear效果一样的

？为什么在linux中按下ctrl+c后，程序没有被杀死或者终止？
而只能通过ctrl+z挂起，之后通过ps查看pid,再通过kill杀掉进程

？如果想要把程序设置在后台运行，首先ctrl+z 挂起该进程，然后使用bg + %n设置在后台运行

#针对没有权限使用rm -rf 的文件，但是还是需要你使用删除操作
yes | rm -r frames_115w_1

通用架构
线上数据 -> flume -> kafka -> hdfs -> MR离线计算 或者：
线上数据 -> flume -> kafka -> storm

# linux中查看文件目录下的文件个数
ls -l|grep "^-"| wc -l
nohup python produce_msg_p.py >./print_msg.log 2>&1 &
