### Git

本地结构：  工作区进入暂存区 (git add) 再进入本地库 (git commit)

托管中心种类：

局域网环境下：可以搭建GitLab服务器作为代码托管中，GitLab可以自己去搭建

外网环境下：可以由GitHub或者Gitee作为代码托管中心，GitHub或者Gitee是现成的托管中心，不用自己去搭建

**1**，在电脑随意处创建一个文件夹  例如：GitRepository  本地git仓库

**2，**打开Git终端    Git Bash Here:

​	 **在Git中命令跟Linux是一样的:**

​     1.查看git安装版本： git --version    查库的表：git config --list  查看全部: ll 显示total为0    ll -la     进入盘符：cd   .git/

​     2. 清屏：  clear

​     3.设置签名：git config  --global user.name "zhangsan"       git 配置 全局 用户名

​        设置用户名和邮箱： git config  --global user.email "798208052@qq.com"

​     4.本地仓库的初始化操作： git init    .git目录是隐藏的，可以调出来查看： 

​          弹出些许： Initialized empty Git repository in D:/gitApp/.git/   在D:/gitApp/.git/中初始化一个空Git仓库

​          查看.get下内容：    

​    	  注意事项：.git目录下的本地库相关的子目录和子文件不要删除，不要修改

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

设置签名和邮箱出错：解决办法

在git 中，我们使用git config命令用来配置git的配置文件，git配置级别主要有以下3类：

1、local 仓库级别

2、global用户级别 ，当前用户在所有仓库都用这个配置（  C:\Users\Dhb\\.gitconfig.lock )

3、system系统级别，整台计算机都用这个配置（”D:\Program Files\Git\etc\gitconfig)

优先级别： git config （git config --local) > git config --global >git config --system

方法一、

  git 修改当前的project的用户名的命令为：**git config user.name 你的目标用户名;**

  git 修改当前的project提交邮箱的命令为：**git config user.email 你的目标邮箱名;**

方法二、

​            直接修改git的配置文件的方式来进行修改

​			打开**全局**的.gitconfig文件的命令为：**$ vi ~/.gitconfig;**  然后在文件中直接修改即可.

​            打开**当前project** 中的config文件，该文件在每个project中的.git目录下，直接进入该目录进行编辑即可。当然，**如果没有进行过修改的话，默认打开时没有对应的用户名和密码的。**只有进行过修改之后，才会在config中产生对应字段。

git 的配置文件在哪 

1，全局配置  例如用户名，邮箱等 位于文件  ~/.gitconfig

​      例如Windows下，则是  C:\Users\Dhb\.gitconfig

2，各个仓库的位置   

​      在仓库目录下： .git/config

​      orange仓库目录下  /home/Dhb/orange/.gitconfig

### 特别注意事项：如果你以前设置ssh密码你永远也不能创建 用户名和邮箱 

### $git config --global user.name "daihaibing"  

-------------------------------------------------------------------------------------------------------------------------------------

**git bash here里面设置如何配置**

Config file location
    --global              use global config file
    --system              use system config file
    --local               use repository config file
    --worktree            use per-worktree config file
    -f, --file <file>     use given config file
    --blob <blob-id>      read config from given blob object

Action
    --get                 get value: name [value-pattern]
    --get-all             get all values: key [value-pattern]
    --get-regexp          get values for regexp: name-regex [value-pattern]
    --get-urlmatch        get value specific for the URL: section[.var] URL
    --replace-all         replace all matching variables: name value [value-pattern]
    --add                 add a new variable: name value
    --unset               remove a variable: name [value-pattern]
    --unset-all           remove all matches: name [value-pattern]
    --rename-section      rename section: old-name new-name
    --remove-section      remove a section: name
    -l, --list            list all
    --fixed-value         use string equality when comparing values to 'value-pattern'
    -e, --edit            open an editor
    --get-color           find the color configured: slot [default]
    --get-colorbool       find the color setting: slot [stdout-is-tty]

Type
    -t, --type <type>     value is given this type
    --bool                value is "true" or "false"
    --int                 value is decimal number
    --bool-or-int         value is --bool or --int
    --bool-or-str         value is --bool or string
    --path                value is a path (file or directory name)
    --expiry-date         value is an expiry date

Other
    -z, --null            terminate values with NUL byte
    --name-only           show variable names only
    --includes            respect include directives on lookup
    --show-origin         show origin of config (file, standard input, blob, command line)
    --show-scope          show scope of config (worktree, local, global, system, command)
    --default <value>     with --get, use default value when missing entry

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**添加文件： add   提交文件：commit**

​		例如：1，先创建一个文件： Demo.txt     放在gitApp文件夹里面

​                   2，执行 **git add Demo.txt**

​                   3,  将暂存区的内容提交到本地库： **git commit -m "这是我提交的第一个文件 Demo.txt" Demo.txt**

​         注意事项：

​                    1，不放在本地仓库中的文件，git是不进行管理

​                    2，即使放在本地仓库的文件，git也不管理，必须通过add,commit命令操作才可以将内容提交到本地库。

​         查看工作区和暂存区的状态： **git status**      绿色字体就说明添加成功 

​         如果文件内容更改查看git status 本地库字体是红色的 就重新提交一次就OK   可以更新或者回退

查看日志：**git log**    fatal: your current branch 'master' does not have any commits yet 致命：你当前的分支还没有任 何提交 ![](E:\JSP使用\gitlog.png)

**日志展示多种方式：**方式1:   git log    

​                                   方式2： git log --pretty=oneline   

​                                   方式3：  git log --oneline  

​                                   方式4：  git reflog    多了信息：HEAD@{数字}  这个数字的含义：指针回到当前这个历史版本需要走多少步    

**常用命令：** 复制：在终端中选中索引就可以复制      粘贴：右键：paste

​                    reset   前进或者后退历史版本 ：**git reset --hard  bc07b79** [索引]          

​     参数        hard    本地库的指针移动的同时，重置暂存区，重置工作区

​     参数        mixed  本地库的指针移动的同时，重置暂存区，但是工作区不动

 	参数        soft      本地库的指针移动的时候，暂存区 工作区都不动

​		<img src="E:\JSP使用\hard参数等.png"  />



**常用命令：**rm   删除工作区中的 file.txt    **rm  file.txt**  找回本地库中删除的文件    

​                  实际上就是将历史版本切换到刚才添加文件的那个版本即可   查看hard参数

 				 找回暂存区删除的文件

**常用命令：**diff    前提是要更改   **git diff  file.txt**    将工作区的文件和暂存区中文件进行比较   、

​                     查看的时候出现红色字体 绿色字体 各是什么意思 ：Git是按照行为单位管理数据 所以：删除一行，添加一行 

​                      多个文件的比对：**git diff**   比较**工作区**中和**暂存区**中所有的文件的差异

​                      多个文件的比对：**git diff [历史版本] [文件名]**     比较**暂存区**和工**作区中**的内容

##### 什么是分支： 在版本控制过程中，使用多条线同时推进多个任务。这里面说的多条线，就是多个分支。

![](E:\JSP使用\什么是分支.png)

​							



【3】分支的好处： 同时多个分支可以并行开发，互相不耽误，互相不影响，提高开发效率

​                                  **如果有一个分支功能开发失败，直接删除了这个分支就可以了，不会对其他分支产生任何影响。**



【1】在工作区创建一个Test.txt文件，然后提交到暂存 区，提交到本地库：

​        $  git add Test4.txt	$git status   

【2】创建分支  $ git branch branch01

​         是指你在哪 个分支上，是通过*来显示的

【3】切换分支 $ git checkout branch01

【4】查看分支 $ git branch -v 



1，进入branch01分支：增加内容：

 	$ **git status**      查看暂存区

​    $ **git add Test4.txt**   添加到暂存区

​    $ **git commit -m** "在分支01中增加内容"  Ttest4.txt   提交本地仓库

2,将分支切换到maste 主分支

​    $ **git checkout master**   切换主分支

​    $ **git branch -v**     查看分支

​    $ **cat Test4.txt**    查看增加内容

3，合并分支    将branch01中的内容和主分支内容进行合并：

​      $ **git checkout maste**r  切换主分支   

​      $ **git merge branch01**   合并分支       显示这个（master|MERGING) 代表处在合并     Mergn conflict in Test4.txt (出现冲突）

​      $ **cat Test4.txt**             

​       什么时候出现冲突问题？在同一个文件的同一个位置修改

​      解决方法： 进行commit操作：

​      $ **git commit -m "解决了冲突问题”**        这里不可以带文件名否则出错   commit以后，就不是合并状态

### Linux操作命令

创建文件 touch Demo.txt   在当前目录创建Demo.txt (相对路径)  相对于当前目录

​     			touch /root/Demo.txt  在/root目录创建Deom.txt文件 （绝对路径）从/目录开始的路径

写入内容：第一种方式：echo "content" > Demo.txt    这个只能在双引号写入内容太单调

   				第二种方式：vi Deom.txt   按Esc退出编辑  输入 ： : wq     冒号+wq 来保存内容    全局写入内容  

​                    注意：vi  进入之后  输入 i 随后看见----Insert插入(写入)就可以写入内容  按Esc  :q :wq   

​                                ：wq退出保存  w保存  q退出    按Esc之后输入冒号(:) 再输入wq 或 w/q

删除文件：rm 删除目录      rm Demo.txt -fr   强制性删除

查看  cat Demo.txt 查看文件内容  

查看当前目录内容：ll  查看当前目录的详情  ls 查看当前目录内容（缺点：隐藏文件内容看不到） 

查看路径：pwd 查看当前路径所在的路径   

进入目录：cd 直接进入/root 目录    cd ..  回到升一级目录   cd ../..加到上一级目录  cd -  最后两次之间切换  

移动：mv    移动文件：mv 文件名 目录名    mv. Demo.txt dir    移动目录：mv GitResp dir

复制：cp    cp Deom.txt dir 将文件复制到dir目录  

​                    cp  Demo.txt dir/b.txt 将文件的内容复制dir目录下的b.txt

​                    cp  Demo.txt  Demo2.txt  将文件的内容复制到Demo2.txt

解压和压缩命令：

​               解压： .tar.gz     将比方snappy-1.1.1.targ.gz 上传到/root/dir目录

​               tar -zxyf snappy-1.1.1.tar.gz    默认解压当前目录

​               tar -xvf snappy-1.1.1.tar.gz     默认解压到当前目录

​               tar -xvf snappy-1.1.1.tar.gz   -C /opt  将压缩包解压到/opt目录

.zip格式解压：

​               unzip mysql-connector-java-8.0.29.zip  默认解压到当前目录

​               unzip -d /opt  mysql-connector-java-8.0.29.zip 解压到指定目录

.tar.gz 压缩：

​                tar -czvf  snappy-1.1.1.tar.gz   snappy-1.1.1   将 snappy-1.1.1文件夹进行打包压缩

​                tar -czvf /root/dir/snappy-1.1.1.tar.gz    /opt/server/snappy-1.1.1

.zip格式压缩:

​			zip -r mysql-connector-java-8.0.29.zip   mysql-connector-java-8.0.29/

 

-----------------------------------------------------------------------------------------------------------------------------------------------------------

### P526集**开始GitHub远程仓库 命令*

**配置签名查看初始化**

设置签名：git config  --global user.name "zhangsan"       git 配置 全局 用户名 

设置邮箱： git config  --global user.email "798208052@qq.com"

查看当前User和Email配置 ：$ git config --local --list  / git config --list    里没有签名和邮箱没有设置成功

本地仓库的初始化操作： git init    .git目录是隐藏的

#### **初始化本地库**

1,$ mkdir GitResp      //本地电脑新建一个文件夹 GitResp   创建文件 touch Demo.txt   打开vi Demo.txt  按 i 写入保存 Esc :wq

2,$ cd GitResp           //进入目录GitResp

3,$ git init                   //初始化 D:/GitResp/.git/    就在目录GitResp产生一个.git   切记里面东西不能删除或更改

4,在目录GitResp创建文件 比方叫做Demo.txt

5,$ git add Demo.txt   // 添加到暂存区

6,$ git commit  -m "增加了Demo.txt文件" Demo.txt    // 提交到本地库   git

- $ git status查看工作区和暂存区的状态  绿色字体就说明添加成功 
- $ git branch -v     查看分支

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

7,GitHub 创建用户名：登录好   头像左边有个 ”+” 加号左键点一下出现下拉框  选择New Repository 创建新的仓库

8，OWner 用户比如我的：Wh-dseatroops   / Repository name 比方仓库名是：GitResp          Description (描述）干什么用的    一般试着玩的话选择Public 

9，左上角有个logo小图像点击就回到你登录的主页  下面有你的仓库名称（用户名/仓库名）多个就选择你需要进入的仓库

10，远程仓库地址比较长，每次复制比较麻烦 https://github.com/Wh-dseatroops/GitResp.git  可以在Git本地将地址保存，通过别名  

11，查看别名： $ git remote -v    正常没有创建就没有

12，起别名： $ git remote add origin https://github.com/Wh-dseatroops/GitResp.git   把网址更改为origin (源码）   别名，可以随意按照你的需求真名

13，继续查看 $ git remote - v    https://github.com/Wh-dseatroops/GitResp.git     如下出现两行就说明成功替换

```Git beas here
  origin  https://github.com/Wh-dseatroops/GitResp.git (fetch)   //取来 拿   在这里指的是提取 远程仓库提取到本地仓库中
  origin  https://github.com/Wh-dseatroops/GitResp.git (push)    //推 按 挤  在这里指的是推送 本地仓库推送到远程仓库中
```

14，把本地仓库文件推送到远程仓库  $ git push origin master // master 主人 在这里指的是分支 你要推送的分支，选择一个分支即可  origin是别名远程仓库地址 

15，git clone https://github.com/Wh-dseatroops/GitResp.git  克隆

​         克隆可以帮我们完成：1,初始化本地仓库  2,将远程库内容完整的克隆到本地3,替我们创建远程的别名

16,  在电脑搜索框中输入：管理你的凭据就可以看到github凭据    删除掉你就要重新登录github账号 团队化操作

17，经理管理都邀请合作者： 进入github点击 code依次点击Collaborators 看到Add people 输入(其它账号)邀请

18，项目经理拉取:

​               (1) 先是抓取操作：fetch    $ git fetch origin master 

​                    抓取后只是将远程库的内容下载到本地但是工作区中的文件并没有更新工作区中还是原先的内容

​                    可以查看切换远程库的分支：$ git checkout origin/master 	  $ ll    $ cat Demo.txt  切换回来$ 

​                   发现内容都正确 随后进行合并  最后切换本地master分支 ： $ git checkout master 

​            （2) 进行合并：merge    $git merge origin/master

​              (3) 远程库的摘取可以直接利用pull命令来完成  $ git pull origin master 

​              总结： fetch（抓取）+merge（合并）操作   为了保险不出错 慎重（推荐使用这个）       pull (拉取) 做些简单代码可以直接pull 省事      

19，解决上传冲突问题：首先拉取下来 $ git pull origin master   该修就修 该删就删   依次提交上传  $ 暂存区 $ 本地库 **<u>提交不能带文件名</u>** $ 推送远程库

20，跨团队合作操作：  远程库A    远程库B    A manager    A programmer   B programmer  

​     首先拿A manager远程地址Bprogrammer复制Amanager远程地址 进行fork操作随后克隆你需要项目的新地址 

​     随后重新编译之后在  add commit  push 在进行 Pull requests 之后 Amanager 确认之合并 就OK 如下 

​               	![](E:\JSP使用\跨团队操作github.png)								

21，免密码操作 ：

​    			（1）进入用户的主目录中： $ cd ~

​				（2）ssh-keygen -t rsa -C  798208052@qq.com    

​                   注意：C要大写   后面的邮箱，是你的github注册的账号的时候对应的邮箱   三次回车确认默认值即可

​                               .ssh目录下有两个id_rsa和id_rsa.pub     keygen ---->key generation 

​                   （3）密钥生成之后  windows打开  clip <~/.ssh/id_rsa.pub    Mac: cd~/.ssh vi id_rsa.pub  

​                              Linux(requires Xclip):   Xclip -sel clip <~/.ssh/id_rsa.pub     这里我们就省略了直接在C:\Users\Dhb\.ssh

22,打开github账号：

​                   点击头像倒三角选择Settings---SSH and GPG keys---设置Title随意取名字   点击add SSH key添加Key(把id_rsa.pub复制) 

​                    生成密钥以后，就可以正常进行push操作

​                   对ssh远程地址起别名： $ git remote add origin_ssh git@github.com:…    查看别名$ git remote -V

23, 随后就可以使用  $ git add Test.txt  $ git commit -m "测试SSH密钥设置成功没有"  test.txt  $ git push origin_ssh master

24，密钥分为多种 

   1，Authentication key  验证密钥  （推荐）这个才有用       2，Signing Key  签名密钥    

 ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDpxY1r5aHazcr6V0ADLRmeWVL/sZGcpwPsGUBo/nY7dGPz1ieZ/I3U6AsG5I3//QFY9btqzQq+YzPYTFf9n3g7dCsDXhYWTW42xpex+IxwvBX5WXTzcvTD9cbkMmVdJBQCf/MpcQh+8yg66rTvOFjGDo4NfO7sucX1iv0nLlVqYsyRqqEPzJKnOvSPI/4RU79zKJ3cRXq2I/9b9KW8e/ijjBSqX49T/WF9RilePAVVGtFn9Dj0TBPVUImjl0h91hLFtfY/Fd5v66OrxNsNjGYeY4S7W7DGTRVXws2nstYwsI2xFih6iX6AUmXQCUMnlMqB6ohlP19M131M6iHZhfsGHja8LBxmLFqTpAqU/nMaQg/G0hUCC7djLx17zQH7TPe6RzDshqiPjQ3oehMHiYAKSqP44PK3Q8EjB9iFtmcz392zm9m9aOVGrV8Zbc1I+40M4VT6lImzBgQutx9Kmbg0XFJszpow3J/zM18Da48uVMwPOaseRoVs9mSI+z3Wtx8= 798208052@qq.com

 25，如何管理多个密钥：

​               1，当需要生成多个key的时候，如ssh-keygen -t rsa -C email创建github对应的sshkey,

​                      第一次需要敲回车的时候需要输入命名如：id_rsa_github的名字再回车 后面的两个回车可以直接敲

​               2,   在.ssh目录创建config文本文件并完成相关配置（最核心的地方）

​                     $ vi config    

​                        配置github.com

​                        Host github.com

****                                   HostName github.com

​                                   IdentityFile C:\Users\Dhb\.ssh\ id_rsa.pub

​                                    PreferredAuthentications publickey

​                                     User username1

​                            配置git.oschina.net

​                            Host git.oschina.net

​                                      HostName git.oschina.net

​                                      IdentityFile  C:\Users\Dhb\.ssh\ id_rsa_oschina

​                                      PreferredAuthentications publickey

​                                      User username1

### 26，IDEA集成Git使用

​            1，new文件比方TestGit进去之后File--Settings--查找Git----Path to Git executable: 执行路径D:\Program Files\git\PortableGit\bin\git.exe只需设置一次            

​       	 2，初始化本地仓库点击 VCSCreate Git Repository就可以了然后TestGit就变成仓库了.git文件夹和TestGit文件夹IDEA上面显示为Git 把VCS替换成Git完成

​                   注意：选择文件夹别选错了    一定要选择当前这个项目名称比方TestGit

​            3,创建一个简单java文件之后会提示 你创建了一个文件以后就会提示你是否进行add操作完之后  字体显示绿色(暂存区) git add Student绝色代表提交成功

​               而你这个项目没有添加到暂存区  需要右击TestModul01这个是module模块添加到Gti(暂存区)  点击**Git---Add**(ctrl+alt+A) 就显示 TestModul01.iml是绿色

​		    4，点击项目目录TestModul01----右击选择**Git----commit Directory----**弹出窗口自动勾选 (commit message 提交信息：第一次使用IDEA提交到本地仓库)  

​                  点击 **commit(提交)** 完成之后  左下角出现一个Git点击进去可以看到控制台**Console**相当于git base here 控制台  看到**log**里面有详细信息比方有索引 

​                 警告： warning: in the working copy of 'TestModul01/src/Main.java', LF will be replaced by CRLF the next time Git touches it

​                 解决警告: 提交: $ git config --global core.autolf true  (提交时转换为LF,检出时转换为CRLF ) 转出: $ git config --global core.autocrlf true

​                CR（carriageReturn回车'\r') 回到一行的开头，ASCII代码是13  LF（LineFeed换行'\n')另起一竺，ASCII代码是10

​               Dos和Window平台；使用回车(CR)和换行(LF)两个字符来结束一行，回车+换行(CR+LF),即"\t\n";所以平时编写文件的回车符应该确切来説叫做回车符

​               Mac和Linux平台：只使用换行（LF）一个字符来结束一行，即 "\n"  

​           5，比方在public class Strudent{ private int age; private String name; 增加属性之后前面有个浅蓝色长条就说明你没有提交}  

​                  使用  add (暂存区)  commit(提交到本地库) 

####            6, **两个不同的库合并**:      IDEA 可以拉取 也可以推送

####                    （1）拉取  $ **git pull git@github.com:Wh-dseatroops/GitResp.git master --allow-unrelated-histories**

####                    （2）推送  $ **git push -u  git@github.com:Wh-dseatroops/GitResp.git master -f** 

​                在TestGit文件夹Open:git base here ： (拉取)输入：$ git pull git@github.com:Wh-dseatroops/GitResp.git --allow-unrelated-histories   

​               提示：fatal(失败)  第一种更改用户名和文件夹 我采用了第二种方法，忽略安全检测 需要添加：$ git config --global --add safe.directory "*"; 

  			 如： Dhb@PC-20200122 MINGW64 /d/VShtml/GitProjectTest/TestGit (master)   $    目录后面显示有一个分支(master)  就可以输入：

​               $ **git pull git@github.com:Wh-dseatroops/GitResp.git master --allow-unrelated-histories**   提示确认要加入吗？ 输入：Yes 

    错误提示：
    hint: You have divergent branches and need to specify how to reconcile them.  //有不同的分支，需要指定如何协调它们
    hint: You can do so by running one of the following commands sometime before  //你可以在之前的某个时间运行以一下命令之一来完成操作
    hint: your next pull:  //你的下次拉动
    hint:
    hint:   git config pull.rebase false  # merge     // 重定向 合并
    hint:   git config pull.rebase true   # rebase    // 重定向  
    hint:   git config pull.ff only       # fast-forward only //只快进
    hint:
    hint: You can replace "git config" with "git config --global" to set a default 你可以将gitconfig替换为git config——globa来设置默认值
    hint: preference for all repositories. You can also pass --rebase, --no-rebase,所有存储库的首选项。你也可以传递——rebase，——no-rebase，
    hint: or --ff-only on the command line to override the configured default per或者在命令行中使用——ff-only来覆盖配置的默认per
    hint: invocation.调用
    fatal: Need to specify how to reconcile divergent branches.需要说明如何调和分歧的分支
​                解决问题：输入这一行：**$ git config pull.rebase false** 没有问题了 继续往下操作

​                提示vi 就直接输入： 进行拉取操作成功就OK    按 i   input content  Esc  ：wq 退出并保存   **查看目录有没有拉取文件下来**  继续往下操作

****                 push推送远程仓库：  $ **git push -u  git@github.com:Wh-dseatroops/GitResp.git master -f**   提示如下：推送成功

                 Enumerating objects: 25, done.   // 枚举对象                
                 Counting objects: 100% (25/25), done. // 计数对象 完成
                 Delta compression using up to 6 threads//增量压缩使用最多6个线程
                 Compressing objects: 100% (16/16), done.//压缩对象 完成
                 Writing objects: 100% (24/24), 2.99 KiB | 509.00 KiB/s, done. //写入对象完成
                 Total 24 (delta 2), reused 0 (delta 0), pack-reused 0   //Total 全部  reused 重用    包重用
                 remote: Resolving deltas: 100% (2/2), done.//远程 解决 全部   deltas变量增量
                 To github.com:Wh-dseatroops/GitResp.git
                 91bc376..8964554  master -> master  //主分支
                 branch 'master' set up to track 'git@github.com:Wh-dseatroops/GitResp.git/master'.//分支 设置跟踪
**注意：**

​           	最亲的版本需要添加--all-unrelated-histories 告诉git允许不相关历史合并。因为他们两个不同的项目，把两个不同的项目合并，在git pull之后，

​                假如我们是的源是origin 分支是master，那么我们需要这样写 **git pull origin master --allow-unrelated-histories** 

​               这个方法只解决因为两个仓库有不两只的开始点，也就是两个仓库没有共同的commit出现的无法提交。

​               如果使用本文的方法还无法提交，需要看一下是不是发生了冲突，解决冲突再提交 

​              push推送：**git push -u origin master -f**     

 **IDEA克隆clone** :   克隆下的名字跟远程名字是一样的比方这个 D:\VShtml\GitProjectTest\GitResp    远程库的名字也是GitResp

​                 File---new--- Project From Version Control ----弹出框主要是URL：克隆地址：git@github.com:Wh-dseatroops/GitResp.git          

**IDEA怎么push:**

​    		     比方创建一个类Person 提示是否添加到暂存区   随后自己commit到本地库  进行推送push  点击Git----push(ctrl+shift+K)  点击 Define remote 

​                  弹出输入框：Name origin(别名)  URL：地址：填写的是远程库的地址你比方是ssh就复制ssh密钥 git@github.com:Wh-dseatroops/GitResp.git

​                 又来一个提示框 让再确认：  Push    就OK

​                  一般在开发中**先pull操作**，**再push**操作，以防冲突 ，不会直接进行push操作！！！

在GitHub删除库操作：  相同的操作都是在进入仓库滚动最后看见**Danger Zone** 设置可见性 删除仓库 禁用分支保护规则 所有权转移 存档或只读   

​             1，  删除库：进去点击最左边logo图标 进入仓库 标题栏看到Settings 设置  滚动条接到最后面看到 Delete this repository 删除这个仓库 按提示操作即可

​		 	2， 设置私有:  Danger Zone ----Change respository visibility----点击Change visibility

​             3,   删除文件：进入文件  右边三个点的小拉框  选择 Delete file  

在GitHub改分支为主分支删除旧主分支操作 ：  General  ---- Default branch------双箭头点击输入哪个为主分支   改好之后就可以把不用的主分支删掉不要了

gitAppclone 用来克隆使用的 gitResp本地仓库  如果使用IDEA的话你的本地仓库就是你的项目或者把项目复制到gitResp再进行push推送

#### **IDEApush推送失败冲突：Push **rejected  /*rɪˈdʒektɪd*/ 拒绝

​                    推送弹出框Push Rejected  它说：不同分支机构的推送被拒绝，在推送之前需要合并远程更改。   

​                                                                               记住更新方法的选择并在将来静默更新（您可以在设置中更改这一点）  取消   合并  重写向

​                    随后点击合并(merge)  弹出Conflicts */*kənˈflɪkts*/*  (冲突)窗口   不用其它的直接点击合并（merge) 之后 又弹出内容让你查看 OK

​                   在来重新push推送成功 就OK了  

团队开发的时候避免在一个文件中改代码

在修改一个文件前，在push推送之前，先pull拉取操作



​                    

 																			





