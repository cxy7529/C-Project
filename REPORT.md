# C++ Report
 学号 18062012  
 姓名 陈贤勇
 ## 具体步骤
我是电脑装好了双系统 在Ubuntu18.04 上来做这个大作业的  
这个项目让我们先配置好nebula的启动环境，然后需要我们进行test的运行。
首先，我按照教程上对nebula 进行了git clone 操作并且安装好了依赖  
按照其步骤一步一步来，在最开始的时候，cmake一直报错，导致我将nebula删除之后，重新git clone
在历经无数次(大约10来次）的艰苦努力之后 我选择网页直接download zip  
终于获得了nebula 并且成功cmake .. 最终 耗时70min make成功  
nebula 项目启动成功
紧接着开始启动nbebula的服务  
然后进入nebula/src/common/time/test 测试目录下 发现vim 失败
重新配置了一遍vim然后开始接下来的操作  
它又出bug了，只能git init试试看  
最终在google的帮助下 我配置好了SSH Key  虽然对这一步没啥影响  
由于开始的bug没有解决 我选择重新启动 然后又是艰难的等待70min
然后他就好了 可以成功将test目录下的 .cpp 文件都测试了一下  
然后我更新了本地分支，从主分支创建了一个新的分支myfeature并且成功切换  
然后在git 的时候他又一直eof   
然后用SSH Key 他也报错 最后不得已重新配置SSH Key  
最终他终于git 下来了
在分支myfeature上运行并且启动nebula成功  并且保持分支同步
在src/console目录下 vim CmdProcessor.cpp 文件并且build成功  
其中有一部分代码还不是很懂  
git push它报错了
大体就完成了以上功能  
修改文件应该没有 commit成功 
