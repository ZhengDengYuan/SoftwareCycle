# 一、创建dll

### 新建项目，选择 动态链接库（DLL）
![](https://i.imgur.com/ds9rdF3.png)

默认目录如下
![](https://i.imgur.com/98uOpAd.png)


1.新建头文件--标头.h（名字随意）
![](https://i.imgur.com/AruOzJt.png)

新头文件  先不写东西

2.新建源文件--源.cpp（名字随意）
源.cpp代码如下

    #include "stdafx.h"
    #include "aaaa.h"
    int funAdd(int a, int b)
    {
       return (a + b);
    }

3.打开头文件，即aaaa.h，修改代码如下
#pragma once
__declspec(dllexport) int funAdd(int a, int b);





4.先看一眼项目的目录
![](https://i.imgur.com/TdBXjoV.png)

5.菜单栏--生成--生成解决方案（F7）
![](https://i.imgur.com/YuEO2RW.png)


再看看项目的内容，多了个debug文件夹，找到了.dll与.lib文件
![](https://i.imgur.com/a8GxrwM.png)

至此，dll生成成功






#二、使用dll
1.接下来重新打开一个VS2017界面，新建空项目或者控制台应用程序，这里新建一个控制台应用程序
![](https://i.imgur.com/x8IhnlI.png)

默认目录如下

![](https://i.imgur.com/15Htjlz.png)


2.把头文件（标头.h）和生成的.dll及.lib文件拷贝到【6】新建项目的文件夹中

操作如下：
头文件--添加现有项（标头.h），源文件--添加新建项（源.cpp）（名字随意），资源文件--添加现有项（Dll1.dll和Dll1.lib）
![](https://i.imgur.com/2KWvbhX.png)

3.在 源.cpp中添加内容如下：
    #include "aaaa.h"
    #include <stdio.h>


    int main()
    {
	int a = 5, b = 6;

	int c = funAdd(a, b);

	printf("c=%d", c);

	getchar();
    }

4.Ctrl+F5

成功！！！

注：生成的.exe文件可直接运行
