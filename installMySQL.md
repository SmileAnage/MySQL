Centos、Ubuntu、Windows下安装MySQL
===
## Centos下安装MySQL
* sudo yum install mysql
* sudo yum install mysql-server
* service mysqld start | stop (启动服务器| 关闭服务器)
* mysql -u root -p (输入密码，进入mysql)
## Ubuntu下安装MySQL
* sudo apt-get install mysql-server
* sudo apt-get install mysql-client
* sudo /etc/inti.d/mysql start | stop (启动服务器|关闭服务器)
* mysql -u root -p (输入密码，进入mysql)
## Windows下安装MySQL
### 一、前往官网下载ZIP包
* 下载后解压放到需要指定的文件夹下(D:\MySQL\mysql-5.6.45-winx64)
### 二、配置环境变量
* 计算机-->属性-->高级系统设置-->环境变量
* 新建==MYSQL_HOME==变量名，变量值= ==D:\MySQL\mysql-5.6.45-winx64==也就是解压之后文件的路径
* 找到==path==变量，新建一条数据写入==%MYSQL_HOME%\bin==，回车三次确定over
* 后续进入mysql可以直接在CMD中输入mysql即可进入
### 三、生成data文件
* 进入mysql文件下的bin路径里，按shift + 鼠标右键 打开CMD(D:\MySQL\mysql-5.6.45-winx64\bin)
* 执行命令：```mysqld --initialize-insecure --user=mysql```，默认在mysql路径下生成data目录，也就是bin目录的同级路径下。
### 四、启动服务
#### 1. 执行命令：```net start mysql```，若启动不了，有两种可能出现的问题（分别为问题1和问题2）
#### 2. 问题 1 (前提是启动不了服务)
* 执行命令：```mysqld -install```
* 启动服务：```net start mysql```
#### 3. 问题 2 (前提是启动不了服务)
* 之前肯定安装过mysql数据库。去任务管理器-->服务，找到mysql，右键执行开始，如果出现==错误2：系统找不到指定的文件==
* 修改注册表，窗口键 + R 输入 regedit，进入注册表找到```HKEY_LOCAL_MACHINE ->SYSTEM -> CurrentControlSet -> services -> MySQL```，修改==ImagePath==的路径为mysql的路径，格式为 mysql\bin路径 + msyqld MySQL。例如(D:\MySQL\mysql-5.6.45-winx64\bin\mysqld MySQL)
* 启动服务：```net start mysql```
### 五、登录mysql
* 进入mysql文件下的bin路径里，按shift + 鼠标右键 打开CMD(D:\MySQL\mysql-5.6.45-winx64\bin)
* 登录命令：```mysql -u root -p```，(默认密码为空)
* quit：退出mysql
* 注：如需修改mysql登录密码
	* 进入mysql，登录命令：```mysql -u root -p```，(默认密码为空)
	* ```set password for 'root'@'localhost' = password('123456');```，将密码设置为：123456，自行修改密码即可
