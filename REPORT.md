# C++ Report
 学号 18062012  
 姓名 陈贤勇
 ## 具体步骤
 ### 第一步 配置环境
 我是电脑装好了双系统 在Ubuntu18.04 上来做这个大作业的  
 #### 按照[快速使用手册](https://github.com/vesoft-inc/nebula/blob/master/docs/manual-CN/1.overview/2.quick-start/1.get-started.md)的提示，
#### 通过[编译源码](https://github.com/vesoft-inc/nebula/blob/master/docs/manual-EN/3.build-develop-and-administration/1.build/1.build-source-code.md)的方式安装[Nebula Graph](https://github.com/vesoft-inc/nebula)
按照其步骤一步一步来，在最开始的时候，cmake一直报错，导致我将nebula删除之后，重新git clone
在历经无数次(大约10来次）的艰苦努力之后 我选择网页直接download zip  
终于获得了nebula 并且成功cmake .. 最终 耗时70min make成功  
nebula 项目启动成功
紧接着开始启动nbebula的服务  
然后进入nebula/src/common/time/test 测试目录下 发现vim 失败
重新配置了一遍vim然后开始接下来的操作 
在build目录下test都测试成功 
#### 如下图所示
![](https://github.com/cxy7529/C-Project/blob/master/QQ%E5%9B%BE%E7%89%8720191227012922.png)
### 第二步 配置远程仓库
在git remote的时候它又出bug了，只能git init试试看  
最终在google的帮助下 我配置好了SSH Key  虽然对这一步没啥影响  
由于开始的bug没有解决 我选择重新启动 然后又是艰难的等待70min
然后他就好了 可以成功将test目录下的 .cpp 文件都测试了一下  
然后我更新了本地分支，从主分支创建了一个新的分支myfeature并且成功切换  
然后在git 的时候他又一直eof   
然后用SSH Key 他也报错 最后不得已重新配置SSH Key  
最终他终于git 下来了
在分支myfeature上运行并且启动nebula成功  并且保持分支同步
在src/console目录下 vim CmdProcessor.cpp 文件并且build成功  
#### 在问题2增加当时的时间的情况下我作出了修改，修改路径就是nebula/src/comsole/CmdProcessor.cpp
##### 增加代码
```cpp
void CmdProcessor::getTime() {
    time_t timep;
    time(&timep);
    char tmp[64];
    strftime(tmp, sizeof(tmp), "%Y-%m-%d %H-%M-%S", localtime(&timep));
    std::string Time(tmp);
    std::cout << Time << std::endl;
}
```
#### 最后提交成功
![](https://github.com/cxy7529/C-Project/blob/master/BC13A83563BB33EBD27A50113AAA9326.png)

### 总结
总而言之，在这门课一开始，老师就已经告诉我们C++是一门很难的课程。我也很想去学好这门课程。而在开源平台上的学习和使用更对我来说是一个挑战，
老师上课讲的内容确实非常有用，虽然我对其中很多都不是很懂。不过如果有机会的话，我会在假期把这门课捡起来再好好学习一遍。将老师上课讲授的内
容融会贯通，好好钻研。也算完成对自己刚刚上课时候的一个小小的期待吧。
