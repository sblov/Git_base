## GIT

#### 版本控制

​	集中式：SVN……

​	分布式：Git……

### 一、Git简介

![](C:\Users\Administrator\Desktop\Web\Git\git简介.png)

​	优势：

- 大部分操作在本地完成，不需要联网

- 完整性保证

- 尽可能添加数据而不是删除或修改数据

- 分支操作非常快捷流畅

- 与linux命令全面兼容

  ![Git结构](C:\Users\Administrator\Desktop\Web\Git\git结构.png)

### 二、Git命令行操作

#### 	本地库操作

##### 	1.本地库初始化

​		命令：**`git init`**

![](C:\Users\Administrator\Desktop\Web\Git\git init.png)

##### 	2.设置签名

​		用以区别不同开发人员的身份，这里设置的签名与登录远程库（代码托管中心）的账号、密码没有任何关系

​		命令：

​		项目级别/仓库级别：仅在当前本地范围内有效

​			**`git config user.name xxx`**

​			**`git config user.email xxx@xxx.xx`**

​			![](C:\Users\Administrator\Desktop\Web\Git\config.png)

​		系统用户级别：登录当前操作系统的用户范围

​			**`git config --global user.name xxx`**

​			**`git config --global user.email xxx@xxx.xx`**	

​			![](C:\Users\Administrator\Desktop\Web\Git\config global.png)

​		(优先使用项目级别，且必须设置签名)	

##### 	3.基本操作

###### 		1）状态查看

​	**`git status`**	查看工作区，暂存区状态

###### 		2）添加到暂存区

​	**`git add [file name]`**	将工作区的“新建/修改”添加到暂存区

###### 		3）提交本地库

​	**`git commit -m "commit message" [file name]`**	将暂存区的内容提交到本地库

###### 		4）查看历史记录

​	**`git log`**	查看当前版本记录（1.哈希函数生成的版本索引 2.指向当前版本）

​	**`git log --pretty=oneline`**

​	**`git log --oneline`**		只显示当前版本之前的历史记录

​	**`git reflog`**

![](C:\Users\Administrator\Desktop\Web\Git\log.png)

###### 5）版本定位

​	**`git reset --hard [哈希索引值]`**	将HEAD指针重新定位

​	**`git reset --hard HEAD^`** 	后退版本，^的个数代表后退的个数

​	**`git reset --hard HEAD~2`**	 后退版本，~后跟数字，表示后退的版本数

​	**reset三个参数：**

​		--soft：只移动本地库的HEAD指针，相对来说，执行git add

​		--mixed：本地库移动HEAD指针，重置暂存区，相对，只是修改文件，没有add

​		--hard：本地库HEAD指针移动，暂存区工作区重置，相对，add，commit

​	**通过在版本间交互，实现文件删除的恢复**

###### 7）文件比较

​	**`git diff [文件名]`**	将工作区中文件与暂存区进行比较

​	**`git diff [本地库版本] \[文件名]`** 	将工作区中的文件与本地库版本比较	

##### 	4.分支管理

​	在版本控制过程中，使用多条线同时推进多个任务

![](C:\Users\Administrator\Desktop\Web\Git\分支.png)

​	**`git branch [分支名]`	**创建分支

​	**`git branch -v`	**查看分支

​	**`git checkout [分支名]`	**	切换分支

​	**合并分支：**	1.**`git checkout [被合并分支名]`	**

​				2.**`git merge [有新内容的分支]`**![branch](C:\Users\Administrator\Desktop\Web\Git\branch.png)

​	**合并冲突：**	1.修改冲突文件

​				2.**`git add [文件名]`**

​				3.**`git commit -m "日志信息"`**

![](C:\Users\Administrator\Desktop\Web\Git\branch-issue.png)

![](C:\Users\Administrator\Desktop\Web\Git\branch-resolve.png)

#### 	远程库操作

​	`git remote -v`	查看添加的远程地址

​	`git remote add [别名] [远程地址]`	 添加远程库地址

​	`git push [远程地址别名] [分支名]`	 推送到指定远程分支

![](C:\Users\Administrator\Desktop\Web\Git\remote.png)

​	`git clone [远程地址]`		克隆远程库到本地，同时创建origin远程库别名，初始化本地库

​	![](C:\Users\Administrator\Desktop\Web\Git\remote-clone.png)

​	**邀请成员**：只有通过该邀请，该成员才有权限提交更改

![](C:\Users\Administrator\Desktop\Web\Git\collaborators.png)![](C:\Users\Administrator\Desktop\Web\Git\other-push.png)

​	`git pull [远程库地址别名] [远程分支名] `		从远程库拉取更新到本地，同时本地库版本及内容会更新；pull = fetch + merge

​		`git fetch [远程库地址别名] [远程分支名]` 

​		`git merge [远程库地址别名] [远程分支名]`

###### 	**推送冲突**	

​		如果不是基于github远程库最新版本所做的修改，不能推送，必须先pull，pull后可能有merge冲突。

###### 	**跨团队协作**

​		GitHub中**fork+pull request**

###### 	SSH登录

* **cd ~**

* **rm -rvf .ssh** ：删除.ssh目录（如果有）

* **ssh-keygen -t rsa -C xxxx@sina.com**  ： 为该用户生成实时密钥

* **cat id_rsa.pub**  ： 获取密钥信息

* 在github中新建ssh key

  ![](C:\Users\Administrator\Desktop\Web\Git\sshkey.PNG)

  ![sshkey-1](C:\Users\Administrator\Desktop\Web\Git\sshkey-1.png)

  ![](C:\Users\Administrator\Desktop\Web\Git\sshlogin.png)

  

### 三、Gitlab服务器环境搭建

### 四、Git图形界面操作

---

### 哈希

​	哈希时一系列的加密算法，每个不同的哈希算法加密强度不同。

​	无论数据多大，用同一个哈希算法，得到加密长度固定，同一个数据得到加密数据一致；哈希算法不可逆

​	Git底层采用**SHA-1**算法

### github.com/github/gitignore

​	各ide及语言可忽略文件总览

### win10凭据

![](C:\Users\Administrator\Desktop\Web\Git\凭据.png)

​		

​	