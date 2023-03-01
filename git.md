Git &Sourcetree安装、配置和使用SOP

Git是一个开源的分布式版本控制系统，可以有效、高速地处理从很小到非常大的项目版本管理
(一)、Git的下载、安装和配置
网站：https://git-scm.com/downloads
1.下载Git
 
  
2.安装Git   --将下载的dmg文件进行验证和安装
3.配置Git (在终端完成  ~~用户名和邮件 需自定义)   
-- >>>打开终端 输入git ， 如果终端回应正常，表示Git安装成功
-- >>>git config --global user.name "name"      #配置自己的用户名
-- >>>git config --global user.email "x@mail" 	#配置自己的邮箱名
Git配置完成！
可以输入open ~/.gitconfig 查看配置后的文件
Git思维导图：
 
 	
 
(二)、Mac电脑shh密钥生成 
作用：方便将服务器的git文件项目进行本地克隆，避免繁琐的密码输入
1.	打开终端
	ssh-keygen -t rsa -C "x@mail"    #输入指令和Git配置的Email --生成密钥
	ssh-add -K ~/.ssh/id_rsa         #将生成的密钥 添加到id_rsa.pub文件里
	cat ~/.ssh/id_rsa.pub            #打开id_rsa.pub文件，将密钥读取出来
将读取的密钥 复制出来 并发给 Git仓库管理员 (x@mail) 以获取免密授权

(三)、Sourcetree下载、安装和使用

SourceTree 是 Windows 和Mac OS X 下免费的 Git 和 Hg 客户端，支持可视化Git操作：创建、提交、clone、push、pull 和merge等

网站：https://www.sourcetreeapp.com/
1.	下载和安装Sourcetree
 

下载SourceTree并安装，由于网络限制，我们只能使用本地的局域网服务器的仓库
以下将简单介绍几个Sourcetree的git可视化操作
2.	Sourcetree的基本使用 （更多操作请查看 https://blog.csdn.net/syq8023/article/details/89844030）
（1）“新建” 操作 	：新建本地项目，方便项目管理和版本迭代（版本迭代 便于debug问题和提升效率）
在 新建选项中选择“创建本地仓库”或者“添加已存在的本地仓库”
（2）“克隆” 操作 	：将远程服务器仓的团体项目克隆到自己本地电脑
URL路径：ssh://x.git   （远程服务器仓库管理员X）
  
  
将克隆的项目修改后，Sourcetree会自动检测项目的变动文件和 位置（文本文件）
 
 
（3）“提交”操作 ：将修改好的项目进行 本地版本迭代 

 
   超前一个版本表示 本地版本比服务器版本要新一代

（4）“推送”操作 ：将修改好的项目进行 服务器端 版本迭代
如果想将版本的新版本 推送到服务器，可以点击 “推送” ，这时将会更新服务器中对应的项目版本
   
 
（5）“检出”操作 ：将服务器端 指定版本 推送 到本地  
 