#使用Sublime Text 2单应用完成编程,带公式笔记
*******
##第一步,所需软件
1. Sublime Text[介绍](http://www.iplaysoft.com/sublimetext.html)
2. (可选)对于电脑没有编译器的人,可以下载MinGW(G++),或者Clang.Clang的错误提示做的比G++好得多,但我在用Windows系统时只接触过G++,所以对于Clang下面不会给出更多"教程".

##第二步,需要学的
+ 对于记带公式的笔记,要慢慢学Tex语言,因为我们要用的MathJax基本上就是把Tex挪过来用的. [Tex介绍](http://www.ctex.org/TeX/) 对于记笔记这点小事来说,Mathematica和Tex似乎都过于笨重了,还是Markdown和Mathjax配合比较合适.
+ [Markdown](http://zh.wikipedia.org/wiki/Markdown)对于需要效率的我们来说比Tex优秀的多,比Word轻便地多,不会出一些稀奇古怪的问题.
+ 学习起来或许会有点麻烦,但以后用处多多.理工科的论文标准都是Tex,而其他时候的小论文小笔记,Markdown+Mathjax绝对是首选.

##第三步,C++,搭建编译环境
1. 首先在网上下载Sublime Text 2(我没用过3,而且据说还不是很稳定).想破解请自行寻找方法,不破解也没啥事,极偶尔在保存的时候会提示你注册.
2. 对于要用G++的而且系统是Windows的童鞋,网上下载MinGW的Installation Manager,运行.下载所需的包并安装.大概会用到含有MinGW和G++字眼的包,不确定不放心全选也没啥大问题.最好选择默认位置,要不3.中的步骤你就得自行更改了.
对于OS X用户,最简便的方法就是在AppStore把Xcode下载下来安装,系统自行解决后续问题.
3. (OS X用户跳过)这台电脑 - 属性 - 高级系统设置 -高级 - 环境变量
添加系统变量.**要注意跟之前的值用";"分开**
名 C_INCLUDEDE_PATH 值: C:\MinGW\include
名 LIBRARY_PATH     值: C:\MinGW\lib
名 Path             值: C:\MinGW\bin
4. (OS X用户跳过)打开命令提示符,输入gcc -v.若出现版本号则设置正确.
5. (OS X用户跳过)运行Sublime Text,工具栏Preferences - Browse Packages - Default,找到exec.py,拖进Sublime Text里.第45行前加//使其成为注释,并另起一行加入如下代码
`# proc_env[k] =os.path.expandvars(v).encode(sys.getfilesystemencoding())
proc_env[k] =os.path.expandvars(v.decode(sys.getfilesystemencoding())).encode(sys.getfilesystemencoding()) `

##第四步,Markdown和MathJax
&emsp;&emsp;OS X上的Markdown实用已有人总结[链接](http://www.jianshu.com/p/378338f10263?comment=12766).Windows上的安装过程没啥区别,几个快捷键可能不一样,摸索一下很容易就完事.
由于我们使用的是校园网,而MathJax的服务器在国外,所以会产生一个问题:只有连收费网络MathJax才会帮我们把代码渲染成美丽的公式.
那我们就需要用10分钟的收费网络一劳永逸地解决问题.
1.连接收费网络,下载[MathJax最新版](https://github.com/mathjax/MathJax/archive/v2.4-latest.zip)
2.解压下载下来的Zip包,把文件夹拖到某个你喜欢的位置.
3.进入Sublime Text 2的Package安装目录,找到Markdown Preview文件夹,把文件名是MathJax的文件拖进Sublime Text,可以看到以下
![拖入Mathjax后](/Users/recitativa/Pictures/com.tencent.ScreenCapture/mathjax.png)
将第一行的http...到latest/改为你的mathjax文件夹所在路径,MathJax.js前不要忘记要有"/".

##完毕,效果展示
&emsp;&emsp;要输入数学公式,用$$包起你的代码,例如:
<center>`$e^(i\pi)+1=0$`<center>
<center>$e^{i\pi}+1=0$<center>
**另外,其实整个"教程"也是ST2+Markdown产物...**
![代码](/Users/recitativa/Pictures/com.tencent.ScreenCapture/markdown.png)
如果不用数学公式,Ulysses会是比Sublime Text2更好用的编辑器.