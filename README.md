# USTB openGauss 数据库实验

## List

必做
- [x] 任务1  安装配置VMware Workstation虚拟化软件
- [x] 任务2  安装CentOS 7.6 操作系统
- [x] 任务3  安装openGauss DBMS
- [x] 任务4  openGauss的简单维护
- [x] 任务5  准备测试数据集
- [x] 任务6  学习使用openGauss DBMS的客户端工具gsql
- [x] 任务8  测试openGauss DBMS的数据类型
- [x] 任务13 openGauss逻辑结构：表管理
- [x] 任务15 openGauss逻辑结构：视图管理
- [x] 任务17 openGauss逻辑结构：触发器管理
- [x] 任务20 openGauss DML语句测试
- [x] 任务21 openGauss SELECT语句
- [x] 任务22 使用JDBC访问openGauss数据库
- [ ] 任务28 基于Visio的openGauss数据库设计
- [ ] 任务29 基于PowerDesigner的openGauss数据库设计

选做（2.5*2）
- [ ] SQL引擎实现
- [ ] 存储引擎实现（要求支持事务并发）


---

## mission1

### 实验内容

安装虚拟化软件VMWare，配置虚拟网卡，并关闭宿主机防火墙，进入BIOS打开VT-d。首先从VMware官网下载VMware Workstation 15试用版安装文件，下载完成后双击安装文件开始安装，完成后配置虚拟网卡，将VMnet1的IP设为192.168.100.1，子网掩码设为255.255.255.0。随后为宿主机联网，并关闭防火墙，重启进入BIOS打开CPU的VT-d技术。


### 实验记录

我使用的电脑是macOS，没有提供对应的VMWare可执行文件，因此自行上网下载对应版本并成功完成实验。

### 心得体会

通过阅读教材理解了VMware的网络连接原理。VMware安装后会在宿主机中添加两块虚拟网卡与三个虚拟交换机。虚拟网卡VMnet1是Host-Only的网卡，VMnet8是NAT类型的网卡。三个虚拟交换机分别是NAT类型、Host-Only类型和Bridge类型。以后的实验中都会使用Host-Only联网方式，虚拟机通过和宿主机进程间通讯的方式，仿真出一个TCP/IP收发数据，实现上网。

## mission2

### 实验内容

访问CentOS介质下载网站下载CentOS 7.6系统镜像，在VMware中创建一台4个CPU、4G物理内存、900G硬盘的PC虚拟机，随后在这台PC上安装刚刚下载的镜像文件，使用CentOS引导程序安装并配置CentOS，选择Server with GUI安装选项，随后进行分区并等待安装完成即可。

### 实验记录



### 心得体会

通过本次实验。我了解了VMWare创建虚拟机的基本操作，了解了安装并初始化CentOS的方法和流程，学会了设置CentOS相关的操作，如网卡配置、用户组配置等，学会了CentOS中包管理器yum的基本使用方法，同时了解了docker工具的使用，并成功实例化openGauss的Docker镜像，完成了实验环境的搭建。

## mission3

### 实验内容

首先对CentOS进行相关配置，关闭防火墙和SELinux，配置库搜索路径和网络参数，允许SSH登录到root用户，完成重启登录到root，下载并安装openGauss DBMS介质，安装时需要配置XML文件并临时关闭CentOS交换区，随后进行openGauss DBMS安装的交互式检查，完成后使用chmod给予安装脚本权限，最后进行安装即可。

### 实验记录



### 心得体会

本次实验中，我了解到了以CentOS为例的Linux系统配置的一些基本操作，如关闭防火墙、允许ssh登录、使用vim文本编辑器编辑文本、关闭交换区、使用chmod命令修改文件权限等。了解到了CentOS中安装openGauss的具体步骤，收获颇多，最终成功在CentOS中安装并运行了openGauss DBMS。


## mission 4

### 实验内容

以omm用户的身份停止openGauss数据库，随后以omm的身份查看openGauss的状态信息，确认数据库已经停止后关闭CentOS操作系统。随后再开机，使用root登录CentOS，启动桌面环境后使用omm用户打开一个终端，随后启动openGauss的DBMS服务，查看状态并监视性能等相关信息，完成实验。

### 实验记录

### 心得体会

通过本次实验，我掌握乐openGauss DBMS的启动和关闭命令以及查看openGauss数据库的状态的相关命令。同时我还了解到了，在关闭CentOS操作系统之前一定要先关闭openGauss DBMS，然后再执行Linux的shutdown关机命令，在以root身份启动CentOS 7之后，还需要以omm启动openGauss DBMS才能正常实验。


## mission 5

### 实验内容

首先创建数据库用户student。使用Linux用户omm打开一个Linux终端窗口，使用openGauss DBMS的gsql客户端程序作为DBA,连接到openGauss DBMS，随后创建表空间student_t，创建数据库studentdb，设置数据库studentdb的会话超时时间，再使用给定的脚本文件创建大学应用模式表、为大学应用模式表填充测试数据，完成对openGauss DBMS数据集的测试及装载。

### 实验记录

### 心得体会

本次实验中我学习到了为openGauss DBMS准备用于测试的数据库studentdb及数据集的方法及具体步骤，同时学习到了脚本文件的编写与使用方法，发现使用脚本文件可以大大简化工作流程，提升实验效率。通过阅读测试集的模式，我对studentdb数据库的关系有了宏观上的初步认知与了解。

## mission 6

### 实验内容

学习使用openGauss DBMS的客户端工具gsql。首先学习相关语法，在终端窗口中执行gsql --help查看gsql命令行工具的语法与语义，随后了解gsql的常用选项，分别对-d、-h、-U、-p、-W、-r、-E、、-t、-A、-v、-c、-f、-q选项进行了解和使用测试，完成后学习gsql的元命令，最后对gsql的环境变量以及自定义变量设置进行学习，同时了解.gsqlrc配置文件的使用方法，编辑.gsqlrc完成实验。

### 实验记录

### 心得体会

本次实验学习到了openGauss DBMS的客户端工具gsql的使用，包括基本语法、常用选项、元命令、环境变量、用户自定义变量以及配置文件.gsqlrc的使用。通过本次实验，我了解并熟练掌握了工具gsql的使用，学会了如何配置gsql的变量与编写gsql配置文件等操作，能够熟练地搭配各种选项和元命令使用gsql命令行工具，收获很大。


## mission 8

### 实验内容

首先使用用户omm登录到studentdb数据库，然后依次对以下数值数据类型测试：smallint、integer、bigint、numberic、decimal、real、float，对序列类型snallserial、serial、bigserial进行测试，对货币类型money进行测试，对字符串类型character/char、varchar、text进行测试，对布尔类型boolean进行测试，对日期和时间类型时区、DATE、TIMESTAMPTZ和TIMESTAMP、TIME with/without time zone、interval进行测试，对枚举类型测试并进行最好的扫尾工作。

### 实验记录

### 心得体会

本次实验收获很大，我通过对studentdb中的数值数据类型（如smallint、integer、bigint、numberic、decimal、real、float）、序列类型（如snallserial、serial、bigserial）、字符串类型（如haracter/char、varchar、text）、货币类型（如money）、日期和时间类型（如时区、DATE、TIMESTAMPTZ和TIMESTAMP）、枚举测试类型进行测试，了解了openGauss中各种数据类型的特点及定义、使用方法和使用场景等，对openGauss数据库中数据类型有了更加全面的认识。


## mission 13

### 实验内容

首先用omm用户打开终端并创建表空间、数据库、用户并授予权限，随后使用另一个终端连接到刚刚创建的数据库，完成准备工作后创建表，创建测试表并查看public模式中有哪些表，随后在当前数据库中使用不同模式创建表，随后分别在创建表时添加定义列级约束、创建表时定义表级约束、为标的属性添加默认值，完成验证创建表时使用自增数据类型，最后使用现有的表创建新表，完成上述后在gsql中查看表的信息并修改表中各种数据，随后清楚表中数据，完成扫尾工作结束实验。

### 实验记录

### 心得体会

通过本次实验我熟练掌握了关系表的管理操作，主要包括创建表操作、在创建表时定义约束（如列级约束和表级约束）操作、修改表（如添加字段、删除字段、添加约束、删除约束、修改数据类型、修改字段的名字、修改字段的默认值）等操作。在实验中进行上述操作的过程中，我巩固了openGauss数据库gsql的使用方法等，加深了对实验用数据库结构等的认识，同时了解到了可以对openGauss数据库进行的操作，

## mission 15

### 实验内容

首先执行教材给出的命令和语句，创建一个名叫pupil的数据库用户，并授予用户pupil访问数据库，通过视图对用户隐藏信息，在omm用户打开的终端中使用student用户连接至studentdb数据库查询内容，并分别通过视图对用户隐藏信息、创建一个比逻辑模型更符合用户直觉的表，创建视图时对视图指定属性名，并基于视图建立新视图、物化视图，完成清理工作后结束实验。

### 实验记录

### 心得体会

本次实验主要了解了在三级模式二级映射体系中，可以将概念模式映射为外模式这一操作的可行性。通过本次实验，我认识到了视图是将概念模式映射为外模式的手段，同时掌握了openGauss数据库的视图的管理的相关操作，如：创建视图、删除视图、查询视图的信息、修改视图的信息等。


## mission 17

### 实验内容

首先测试openGauss的触发器，创建测试表与触发器对应的函数，随后创建并测试触发器；分别测试行级触发器和语句级触发器，完成对AFTER触发器的测试。随后测试BEFORE触发器，按照之前的步骤首先创建测试表与触发器对应的函数，执行命令创建行级BEFORE触发器，最后执行命令测试建行级BEFORE触发器。最后清理数据并完成实验。

### 实验记录

### 心得体会

本次实验我了解到了触发器的管理和使用，认识到了触发器可用来实现数据完整性约束（检查列值是否在某个范围内），也可以用来实现表间的数据完整性约束（补偿不保持依赖的表分解）、可以基于某个表达式为列提供默认值，甚至可以为那些只能使用常量默认值进行定义的列类型提供值、可以在行删除或更新之前先检查行的当前内容。这种能力能完成许多任务，如记录已有行的更改情况。


## mission 20

### 实验内容

本次实验主要对openGauss中DML语句的用法进行掌握与运用，包括INSERT语句、DELETE语句和UPDATE语句。首先测试INSERT语句，先一次插入一行，为插入行提供部分列的值，随后一次插入多行，为一行的所有列提供值，同时尝试执行一个违反主键约束的语句，发现无法插入。随后使用DELETE语句配合WHERE子句进行删除，最后使用UPADATE语句进行数据修改，完成清理实验环境结束实验。

### 实验记录

### 心得体会

通过本次实验我掌握了openGauss中DML语句的用法，包括INSERT语句、DELETE语句和UPDATE语句。通过本次实验，我了解到了INSERT语句可以一次插入一行，为插入行提供部分列的值，或者一次插入多行，为一行的所有列提供值，同时了解到了有些违反主键约束的语句无法正常进行插入。学会了如何使用DELETE配合WHERE子句进行数据删除。学会了使用UPDATE语句进行数据的修改更新。通过本次实验我学会了这三种语句的用法用途。




## mission 21

### 实验内容

本次实验主要掌握SQL中SELECT语句的用法。首先学习掌握SQL中一个完整的SELECT语句的组成部分以及执行顺序，其次学习SQL语句中注释的写法。完成上述预备知识学习后，进行单表查询和多表查询的练习。首先进行单表查询，分别使用SELECT子句、加入WHERE子句中谓词、ORDER BY子句、GRUOP BY子句和HAVING子句与SQL函数进行单表查询，随后使用不同关系代数算符进行多表查询，最后清理环境完成实验。

### 实验记录

### 心得体会

通过本次实验我掌握了SQL中SELECT语句的用法。了解到了一个完整的SQL语句包括SELECT columnlist、FROM tablelist、WHERE condition、GROUP BY columnlist、HAVING condition、ORDER BY columnlist六个部分，并通过实验对这六个部分的功能和执行顺序进行了认识。同时学习了SQL中注释的写法，最后学习并练习了单表查询与多表查询的操作与方法，在学习的过程中还巩固了理论课中关系代数的相关知识。

## mission 22

### 实验内容

本次实验主要掌握使用JDBC编程访问数据库。首先进行准备工作，使用omm用户打开shell并创建对应的数据库用户、表空间和数据库。随后下载安装Java SE 8开发环境并安装配置，随后下载IDE eclipse并安装，最后下载安装openGauss的JDBC驱动包，完成后使用eclipse新建并编写一个JDBC测试程序并对openGauss的JDBC进行测试使用，最后清理环境结束实验。

### 实验记录

### 心得体会

本次实验收获很多。我了解到了JDBC的概念与使用方法，第一次学会了在Java程序中通过JDBC驱动对数据库进行访问以及数据的增删改查，在配置开发环境的过程中我还了解并练习了Java SDK的安装与环境变量的配置，对在Linux系统下开发环境的配置流程有了掌握，收获颇丰。


## mission 28
<!-- todo -->
### 实验内容

### 实验记录

### 心得体会

### ER模型设计

![ER Diagram](/img/er1.png)


## mission 29

### 实验内容

### 实验记录

### 心得体会

### ER模型设计
