[TOC]

# 第1章 数据库系统概述（可不看）


## 1.1 数据管理技术的发展及特点

1. **人工管理阶段**（1950年）

   - 数据只参与计算，不保存
   - 数据和程序耦合性高，修改数据就要改程序
   - 数据的物理存储改变麻烦，一旦修改就要重新编程
   - 多应用不共享相同数据，导致数据高冗余

   <img src=".\assets\image-20241203134700043.png" style="zoom: 80%;" />

2. **文件系统阶段**（1960年）

   - 数据可长期保存至外存

   - 区分了数据的物理与逻辑结构，无需知道文件的物理存储位置，直接用文件名调用

   - 文件形式多样化

   - 数据与程序之间有一定独立性，多个程序通过文件系统调用多个数据文件

   <img src=".\assets\屏幕截图 2024-12-03 134719.png" alt="屏幕截图 2024-12-03 134719" style="zoom:80%;" />

3. **数据库系统阶段**（1960年后期）

   - 数据结构化，与文件系统相比，将不同数据文件之间关联起来

   - 数据共享，不同用户使用的数据进行重叠，且可同时被多个用户访问

   - 数据冗余减少

   - 较高的数据独立性，数据存储方式的改变不会影响应用

   - 用户接口，在DBS中通过DBMS提供给用户对数据库的多个控制操作

   <img src=".\assets\image-20241203152607491.png" alt="image-20241203152607491" style="zoom:80%;" />

## 1.2 数据库系统

**概述**：数据库系统（DBS），具有管理数据库功能的计算机系统，由以下5个东西组成。

1. **计算机系统**：由硬件和软件组成
   - 硬件：磁盘等外存、附属设备、控制器、I/O通道、内存、CPU等外设
   - 软件：操作系统、各种驱动程序等
2. **数据库**：是指DBS中集中存储的一批数据的集合，是DBS的工作对象。将数据分为<u>存储（输入）数据</u>、<u>工作（输出）数据</u>和<u>操作（中间）数据</u>
   - 存储数据特性——集成：将某个应用中各种数据的关系按一定的结构形式存储，使得整体数据结构化，并降低数据冗余
   - 存储数据特性——共享：指DB中多个用户可同时存取同一个数据块
3. **DBMS**： 数据库管理系统，使用户必须通过DBMS才能实现对数据库的存取、维护和管理
4. **应用程序**：介于用户和DBMS之间，为了回应用户对应用操作的回应，应用会和DB互动，完成增删改查操作
5. **用户**：是指存储、维护和检索数据库中数据的使用人员，分为<u>终端用户</u>、<u>应用程序员</u>、<u>数据库管理员</u>

<img src=".\assets\image-20241203222327235.png" alt="image-20241203222327235" style="zoom:90%;" />

## 1.3 数据库系统与文件系统的区别

**数据库系统**：各种用户的数据操作都通过DBMS实现，而不是直接对数据库文件进行存取。

**文件系统**：各种用户直接对自己的数据文件进行存取

<img src=".\assets\image-20241203152451851.png" alt="image-20241203152451851" style="zoom:70%;" />

# 第2章 数据模型（选看）

**概述**：数据模型是一种表示数据及其联系的模型，是数据库的框架，简化的描述了数据库的数据组织形式。数据模型分为两类，第一类是概念模型，第二类是逻辑模型和物理模型。

![image-20241203222254161](.\assets\image-20241203222254161.png)

## 2.1 概念模型

### 2.1.1 实体间的联系方式

两个实体集之间的联系分为3类：<u>1：1</u>、<u>1：n</u>、<u>m：n</u>。

<img src=".\assets\image-20241203224020661.png" alt="image-20241203224020661" style="zoom:90%;" />

### 2.1.2 （实体-联系 表示法）E-R图

**概述**：建立概念模型一般用E-R图方法，从现实世界中抽象出不同实体之间的关系。其中，实体用方框；联系用菱形；属性用椭圆。

1. 两个实体之间联系的画法

   <img src=".\assets\image-20241203224657644.png" alt="image-20241203224657644" style="zoom:90%;" />

2. 两个以上画法

   ![image-20241203224731327](.\assets\image-20241203224731327.png)

**【例 2.1】**画出部门、主任、职工之间的E-R图

![image-20241203224946317](.\assets\image-20241203224946317.png)

## 2.2 关系模型

**概述**：关系模型由一组关系组成，每个关系的数据结构是一张二维表。

**关系模型的基本术语** ：

- 关系：一个关系就是一张表

- 元组：一个元组就是表里一行数据

- 属性：表中的列就是属性

- 域：属性的取值范围

- 关系模式：对关系的描述称为关系模式

  关系：student	关系模式：student(学号,姓名,性别,出生日期,班号)

- 候选码（候选关键字）：是属性或属性组合，满足唯一性

- 主码（主关键字）：一个关系中可能有多个候选码，从中选择一个作为主码

- 主属性：在候选码中的各属性就是主属性

- 非主属性：不在候选码中的各属性就是非主属性

- 外码（外关键字）：如果关系B的属性x是关系A的主码，则属性x就是关系B的外码

- 全码：关系中的所有属性都是候选码，则称为全码

# 第3章 关系数据库

**概念**：关系数据库系统采用关系模型作为数据的组织方式。

## 3.1 关系的概念   

1. **域**：一组具有相同数据类型的值的集合，例如：整数、正整数、实数、{1，2，3}等

2. <a id="笛卡尔积">**笛卡尔积**</a>

   - <div style="padding:1px;background:rgba(0,0,0,0.1);width:50%;"><img src=".\assets\image-20241204130157246.png" alt="image-20241204130157246" /></div>

   - **D~i~（i=1，2，…，n）**：D~i~就是一个属性的元组集合，例如：姓名集合D~1~={张三，李四，王五}、课程集合D~2~={C语言，数据结构，计算机原理}
   - <div style="padding:1px;background:rgba(0,0,0,0.1);width:45%;"><img src=".\assets\image-20241204130755502.png" alt="image-20241204130755502" /></div>

   - **元素（d~1~，d~2~，…，d~n~）**：元素就是元组，例如上图中：（张三，C语言）、（李四数据结构）等

   - **分量d~i~（i=1，2，…，n）**：d~i~就是一个元素中的单个值，例如：元素（张三，C语言）中的“张三”和“C语言”就是两个分量

   - **D~i~的基数m~i~（i=1，2，…，n）**：m~i~就是对应元素集合D~i~中的元素（元组）个数，例如：元素集合D~1~={张三，李四，王五}的基数m~1~=3

   - **D~1~ x D~2~ x … x D~n~的基数M**：M就是笛卡尔积结果集的元素（元组）个数，例如：上图中D~1~ x D~2~的基数M=9


## 3.2 关系代数

### 3.2.1 传统的集合运算

1. **并**：关系R和关系S的所有元组合并，且删除重复元组组成的新关系，记为R U S
2. **差**：关系R和关系S的差是指只属于R的所有元组的集合，记为R — S
3. **交**：是指同时属于R和S的元组集合，记为R &cap; S
4. <a href="#笛卡尔积">**笛卡尔积**</a>

![image-20241204231805245](.\assets\image-20241204231805245.png)

![image-20241204231924879](.\assets\image-20241204231924879.png)

### 3.2.2 专门的关系运算

1. **选择**：是从关系中筛选出满足指定条件的记录的操作，相当于where，表示为：&sigma;~F~（R）

   - F：就是指定的条件，例如：sex = '男'、age > 10等
   - R：就是关系名，即表名

2. **投影**：是从关系中选择若干属性组成新关系进行展示的操作，表示为：&prod;~L~（R）

   - L：属性名，例如：<u>姓名</u>、<u>性别，年龄</u>、<u>邮箱，学号</u>等

3. **连接**：是将两个关系拼接成新关系，其中都是满足条件的元组

   - &theta;连接：将关系R和S中满足条件的元组筛选出来后拼接成新关系，记为<img src=".\assets\image-20241204234013208.png" alt="image-20241204234013208" style="zoom: 60%;" />，其中i和j分别是R和S中的属性序号，&theta;为“=”时就是等值连接

     ![image-20241204233923871](.\assets\image-20241204233923871.png)![image-20241204233937794](.\assets\image-20241204233937794.png)

   - F连接：将关系R和S中满足条件公式F的元组筛选出来后拼接成新关系，记为<img src=".\assets\image-20241204234350240.png" alt="image-20241204234350240" style="zoom:70%;" />

     - F：指F~1~ &Lambda; F~2~ &Lambda; … &Lambda; F~n~的形式，每个F~i~（1&le;i&le;n）都是形似&theta;连接中的条件<u>i&theta;j</u>

   - 自然连接：就是去除重复属性的等值连接，记为<img src=".\assets\image-20241204234936679.png" alt="image-20241204234936679" style="zoom:70%;" />

     ![image-20241204235027968](.\assets\image-20241204235027968.png)

4. **除**：![image-20241204235157600](.\assets\image-20241204235157600.png)![image-20241204235210935](.\assets\image-20241204235210935.png)

# 第4章 关系数据库规范化理论

## 4.1 函数依赖

**概述**：函数依赖是指一个关系内各属性之间的联系。

### 4.1.1 函数依赖的定义

**定义1**：设有关系R（X，Y），当属性X唯一而Y不唯一，则称X函数决定Y，或Y函数依赖于X，记作：X&rarr;Y。

- 举例：<a id="S_SC_C关系">S(学号，姓名，性别)，SC(学号，课程号，分数)，C(课程号，课程名)</a>

  函数依赖：学号&rarr;姓名、学号&rarr;性别、课程号&rarr;课程名、(学号，课程号)&rarr;分数

  函数依赖集F={学号&rarr;姓名，学号&rarr;性别，课程号&rarr;课程名，(学号，课程号)&rarr;分数}

  ![image-20241205114836839](.\assets\image-20241205114836839.png)

- 如果属性X和Y之间是1：1关系，例如：学校和校长之间就是1：1关系，则存在函数依赖X&rarr;Y和Y&rarr;X

- 如果X和Y是1：n，则存在函数依赖X&rarr;Y

- 如果X和Y是m：n，则不存在函数依赖



**定义2**：若X&rarr;Y，且Y&sube;X，则称X&rarr;Y是平凡函数依赖。

- 举例：在<a href="#S_SC_C关系">关系SC</a>中，平凡函数依赖有：(学号,课程)&rarr;学号、(学号,课程)&rarr;课程号、(学号,课程)&rarr;(学号,课程)



**定义3**：设X‘是X的子集（X’&sub;X），当X&rarr;Y且X‘&rarr;Y不成立，则称X&rarr;Y是完全函数依赖，记作<img src=".\assets\image-20241205121804763.png" alt="image-20241205121804763" style="zoom:100%;" />。

- 举例：在<a href="#S_SC_C关系">关系SC</a>中，(学号，课程号)&rarr;分数，但<u>学号&rarr;分数</u>和<u>课程号&rarr;分数</u>均不成立，所以<u>(学号，课程号)&rarr;分数</u>是一个完全函数依赖



**定义4**：设X‘是X的子集（X’&sub;X），当X&rarr;Y且X‘&rarr;Y成立，则称X&rarr;Y是部分函数依赖，记作![image-20241205122953394](.\assets\image-20241205122953394.png)。

- 举例：在<a href="#S_SC_C关系">关系SC</a>中，(学号，课程号)&rarr;姓名，但<u>学号&rarr;姓名</u>成立，所以<u>(学号，课程号)&rarr;姓名</u>是一个部分函数依赖



**定义5**：设关系R（X，Y，Z），如果X&rarr;Y（Y&#8840;X，Y&#8603; X），且Y&rarr;Z，则称Z传递函数依赖于X，记为![image-20241205124840651](.\assets\image-20241205124840651.png)。

- 举例：设有关系<u>班级(班号，专业名，系名，人数，入学年份)</u>

  函数依赖有：班号&rarr;专业名，专业名&rarr;系名，则传递函数依赖有：班号&rarr;系名

### 4.1.2 Armstrong公理（可不看）

**Armstrong公理的3条推理：**

1. 自反律：若B&sube;A，则A&rarr;B，这是平凡函数依赖
   - 例：{姓名，班号}&rarr;姓名
2. 增广律：若A&rarr;B，则AC&rarr;BC
   - 例：{学号，课程号}&rarr;{姓名，课程号}
3. 传递律：若A&rarr;B且B&rarr;C，则若A&rarr;C
   - 例：学号&rarr;班号，班号&rarr;专业，则学号&rarr;专业

**Armstrong公理的4条推论：**

1. 自合规则：A&rarr;A
   - 例：学号&rarr;学号
2. 分解规则：若A&rarr;BC，则A&rarr;B且A&rarr;C
   - 例：学号&rarr;{姓名，班号}，则<u>学号&rarr;姓名</u>，<u>学号&rarr;班号</u>
3. 合并规则：若A&rarr;B，A&rarr;C，则A&rarr;BC
   - 例：学号&rarr;姓名，学号&rarr;班号，则<u>学号&rarr;{姓名，班号}</u>
4. 复合规则：若A&rarr;B，C&rarr;D，则AC&rarr;BD
   - 例：学号&rarr;姓名，课程号&rarr;课程名，则<u>{学号，课程号}&rarr;{姓名，课程名}</u>

## 4.2 关系范式

### 4.2.1 第一范式（1NF）

**概述**：当一个关系的所有值都不存在重复组和嵌套结构，那这个关系就是第一范式。

- 非第一范式：![image-20241206095404879](.\assets\image-20241206095404879.png)
- 第一范式：![image-20241206095418088](.\assets\image-20241206095418088.png)

### 4.2.2 第二范式（2NF）

**概述**：在一个1NF关系中，若所有非主属性对候选码完全函数依赖，没有部分函数依赖，则这个关系就是第二范式。

- 设有关系R(X,Y,Z,O)，其中(X,Y)是候选码，X&rarr;Z，Y&rarr;O，所以(X,Y)![image-20241206100523976](.\assets\image-20241206100523976.png)Z，(X,Y)![image-20241206100523976](.\assets\image-20241206100523976.png)O，由于非主属性Z，O对候选码不是完全函数依赖，所以关系R不是第二范式。
- 错例：<img src=".\assets\image-20241206100837857.png" alt="image-20241206100837857" style="zoom:80%;" />
  - 候选码：（工程号，材料号）
  - 函数依赖：工程号&rarr;开工日期、工程号&rarr;完工日期、材料号&rarr;单价
  - 完全函数依赖：（工程号，材料号）&rarr;数量
  - 部分函数依赖：（工程号，材料号）&rarr;开工日期、（工程号，材料号）&rarr;完工日期、（工程号，材料号）&rarr;单价
- <a id="2NF正例3NF错例">正例</a>：<img src=".\assets\image-20241206101329786.png" alt="image-20241206101329786" style="zoom:80%;" />
  - 候选码：课程名
  - 函数依赖：课程名&rarr;教师名、教师名&rarr;教师职称
  - 传递函数依赖：课程名&rarr;教师职称
  - 完全函数依赖：课程名&rarr;教师名、课程名&rarr;教师职称

### 4.2.3 第三范式（3NF）

**概述**：在一个2NF关系中，若所有非主属性对候选码完全函数依赖，没有传递函数依赖，则这个关系就是第三范式。

- <a href="#2NF正例3NF错例">错例</a>
- 正例：<img src=".\assets\image-20241206102925994.png" alt="image-20241206102925994" style="zoom:80%;" />
  - 候选码：（学号，课程名）、（学号、教师名）
  - 完全函数依赖：（学号，课程名）&rarr;教师名、（学号、教师名）&rarr;课程名

# 第5章 T-SQL基础

## 5.1 数据库的操作语句

### 5.1.1 创建数据库

```mssql
create database 数据库名
[on [primary] filespec]
[log on filespec]

-- filespec的替换SQL代码
(
    [name = 数据文件名或日志文件名（无后缀名）,]
    [filename = 数据文件名或日志文件名存储位置,]
    [size = n,]
    [maxsize = n,]
    [filegrowth = n]
)
```

- **on**：定义数据库的数据文件
- **log on**：定义数据库的日志文件
- **primary**：指定文件为主文件，一个数据库只能有一个主文件，不设置默认第一个文件为主文件
- **name**：数据文件或日志文件的文件名
- **filename**：数据文件或日志文件的路径
- **size**：数据文件或日志文件的文件大小，单位（MB，KB…）
- **maxsize**：数据文件或日志文件的最大文件大小，单位（MB，KB…）
- **filegrowth**：当更新数据文件或日志文件内容，而文件大小不够时，为文件增长的大小，单位（MB，KB…）

**【例 5.1】**创建一个名称为test1的数据库，设定数据文件为“G:\DB\测试数据1.MDF”，大小为10MB，最大为50MB，每次增长5MB。日志文件为“G:\DB\测试数据1日志.MDF”，大小为10MB，最大为20MB，每次增长5MB。

```mssql
create database test1
on (
    name = 测试数据1,
    filename = 'G:\DB\测试数据1.MDF',
    size = 10MB,
    maxsize = 50MB,
    filegrowth = 5MB
)
log on (
    name = 测试数据1日志,
    filename = 'G:\DB\测试数据1日志.MDF',
    size = 10MB,
    maxsize = 20MB,
    filegrowth = 5MB
)
```

### 5.1.2 使用、查询、删除数据库

```sql
-- 使用数据库
use 数据库名;

-- 查询数据库
select name from sys.tables;

-- 删除数据库
drop database 数据库名;
```

### 5.1.3 修改数据库（可不看）

```mssql
alter database 数据库名 {
	add file filespec |
	add log file filespec |
	remove file 数据文件名或日志文件名（无后缀名） |
	modify file filespec |
	modify name = 新数据库名
}

-- filespec的替换SQL代码
(
    [name = 数据文件名或日志文件名（无后缀名）,]
    [filename = 数据文件名或日志文件名存储位置,]
    [size = n,]
    [maxsize = n,]
    [filegrowth = n]
)
```

- **add file**：添加数据文件
- **add log file**：添加日志文件
- **remove file**：删除数据文件或日志文件
- **modify file**：修改数据文件或日志文件，但一次只能改一个属性
- **modify name = 新数据库名**：重命名数据库

**【例 5.2】**为数据库test1添加数据文件，文件名为“G:\DB\测试数据.MDF”，大小为10MB，最大为50MB，每次增长5MB。

```mssql
alter database test1
	add file (
        name = 测试数据,
        filename = 'G:\DB\测试数据.MDF',
        size = 10MB,
        maxsize = 50MB,
        filegrowth = 5MB
    )
```

## 5.2 数据表的操作语句

### 5.2.1 创建数据表

```mssql
create table 表名 (
    列名1 数据类型 table_constraint,
    [,……n]
    [主键约束]
    [外键约束]
)

-- table_constraint的替换SQL代码
{
	[null | not null]
	[primary key[(列名1[,…,列名n])] | unique]
	[check (列名 运算符 值)]
	[default 值]
	[foreign key references 关联的表名(关联的列名)]
}

-- 主键约束的替换SQL代码
[constraint 主键名] primary key (列名[,……n])

-- 外键约束的替换SQL代码
[constraint 外键名] foreign key (列名) references 关联的表名(关联的列名)
```

### 5.2.2 由旧表创建新表（可不看）

```mssql
-- 当where查询条件为：where 1 = 0时，仅复制旧表的结构，不复制内容
select 旧表列名…
into 新表名
from 旧表名
[where 查询条件]
```

### 5.2.3 删除数据表

```mssql
drop table 表名
```

### 5.2.4 修改数据表（可不看）

```mssql
alter table 表名 {
	add 新列名 数据类型 table_constraint |
	drop {constraint 约束名 | column 列名} |
	alter column 列名 数据类型 table_constraint
}

-- table_constraint的替换SQL代码
[null | not null] [primary key | unique] [check (列名 运算符 值)] [default 值] [foreign key (列名) references 关联的表名(关联的列名)]
```

- **add 新列名 数据类型 table_constraint**：增加新列
- **drop {constraint 约束名 | column 列名}**：删除约束或列
- **alter column 列名 数据类型 table_constraint**：修改列属性

### 5.2.5 查询数据表（基础版）

```mssql
select [distinct] [列名或聚合函数 [[as] 别名],…]
from {表名 [[as] 别名],… | 视图名,…}
[where 查询条件]
[group by 分组表达式]
[having 分组条件]
[order by 次序表达式 [asc | desc]]
```

- **distinct**：返回唯一不同的值，作用于后面所有列名和聚合函数
- **as**：给表起别名
- **where**：添加查询条件
- **group by**：添加分组
- **having**：添加分组条件
- **order by**：添加排序，次序默认为：升序&rarr;asc

## 5.3 数据的操作语句

### 5.3.1 insert语句

```mssql
insert [into] 表名或视图名 [(列名,…)] values
	(value,…,value);
```

- **into**：加不加都行

### 5.3.2 delete语句

```mssql
delete 表名或视图名 [where 条件表达式]
```

### 5.3.3 update语句

```mssql
update 表名或视图名
set 列名1 = 数据值1 [, …, 列名n = 数据值n]
[where 条件表达式]
```

## 5.4 连接查询

### 5.4.1 简单连接查询

1. **等值连接**：指多表之间用“=”关系连接起来，产生一个临时表

   ```mssql
   -- 语法格式
   select 列名,…
   from 表名,…
   where 连接条件
   
   -- 示例：查询所有学生的姓名、考试课程和课程成绩
   select st.姓名, sc.课程号, sc.分数
   from student st, score sc
   where st.学号 = sc.学号
   ```

2. **非等值连接**：指多表之间用非“=”关系连接起来，产生一个临时表

   ```mssql
   create table grade(
   	low int,
       upp int,
       rank char(1)
   );
   
   insert into grade values
   	(90, 100, 'A'),
   	(80, 90, 'B'),
   	(70, 80, 'C'),
   	(60, 70, 'D'),
   	(00, 60, 'E');
   
   -- 示例：查询所有学生的学号、课程号和rank等级列
   select sc.学号, sc.课程号, gr.rank as '等级'
   from score sc, grade gr
   where sc.分数 between gr.low and gr.upp
   order by gr.rank;
   ```

3. **自连接**：一张表与自身连接起来

   ```mssql
   /* 题目：查询选修“3-105”课程的成绩高于“109”学号学生成绩的所有学生记录，并按成绩从高到低排列 */
   select sc1.学号, sc1.课程号, sc1.分数
   from score sc1, score sc2
   where sc2.课程号 = '3-105' and sc2.学号 = '109'
   	and sc1.课程号 = '3-105' and sc1.分数 > sc2.分数
   order by sc1.分数 desc;
   ```

### 5.4.2 内连接查询

```mssql
select 列名,…
from A [[as] 别名]
inner join B [[as] 别名] on A.列名 比较运算符 B.列名
[inner join C [[as] 别名] on 连接条件]
[……]
-- 注意：当某表起别名后，引用此表的列时只能用别名引用，不可用表原名引用
```

### 5.4.3 外连接

！！！略！！！

## 5.5 子查询

### 5.5.1 简单子查询——非相关子查询

**概述**：子查询不依靠外部查询的值，且子查询的结果代入外部查询的where中进行计算，这类子查询就是非相关子查询。

```mssql
-- 语句格式
select 列名,…
from {{表名 | 视图名} [[as] 别名] | 子查询 [as] 别名}
where 列名 比较运算符 {值 | 子查询} 

-- 示例：从成绩表中筛选出学号为'2024000001'的学生记录
select *
from (select 学号,课程号
      from 成绩) as test
where 学号 = (select 学号
            from 学生
            where 学号 = '2024000001');
```

### 5.5.2 相关子查询（可不看）

**概述**：子查询内部使用外部查询的值，这类子查询就是相关子查询。

```mssql
-- 示例：查询成绩比该课程平均成绩低的学生成绩表
select *
from (select 学号,课程号,成绩
      from 成绩) as score1
where 成绩 < (select avg(成绩)
            from 成绩 as score2
            where score1.课程号 = score2.课程号)
```

### 5.5.3 复杂子查询（可不看）

1. **使用in或not in的子查询**：使用时无需比较运算符

   ```mssql
   -- 示例：查询选修了“6-166”课程号的学生的学号和姓名
   select st.学号, st.姓名
   from student st
   where st.学号 in (select sc.学号
                   from score sc
                   where sc.课程号 = '6-166')
   ```

2. **使用any或all的子查询**：使用时需要比较运算符，any或all写在比较运算符后面

   ```mssql
   -- 示例：查询课程号为“3-105”的学生的学号、课程号和分数，且只展示分数至少比课程号为“3-245”的学生分数其中之一高的记录，最后按分数降序排列
   select sc1.学号, sc1.课程号, sc1.成绩
   from score as sc1
   where sc1.课程号 = '3-105'
   	and sc1.成绩 > any (select sc2.成绩
                         from score as sc2
                         where sc2.课程号 = '3-245')
   order by sc1.成绩 desc
   ```

3. **使用exists或not exists的子查询**：使用时无需列名和比较运算符

   - exists：从外部查询表中筛选出存在与exists子查询结果中的记录
   - not exists：从外部查询表中筛选出不存在与not exists子查询结果中的记录

   ```mssql
   -- 示例：查询所有任课教师的姓名和所在系名
   select te.姓名, te.系名
   from teacher as te
   where exists (select *
                 from course as co
                 where te.教师号 = co.教师号);
   
   -- 示例：查询所有未讲课的教师的姓名和所在系名
   select te.姓名, te.系名
   from teacher as te
   where not exists (select *
                     from course as co
                     where te.教师号 = co.教师号);
   ```

# 第6章 T-SQL程序设计

## 6.1 注释

1. 单行注释

   ```mssql
   -- 使用双连字符，也就是两个减号
   ```

2. 多行注释

   ```mssql
   /* 使用正斜杠＋星号对格式 */
   /*阿斯蒂芬
   可跨行
   阿斯顿发生记得发链接
   阿斯蒂芬*/
   ```

## 6.2 数据类型

！！！略！！！

## 6.3 局部变量

### 6.3.1 定义局部变量

**概述**：局部变量的定义由“@”符号开头，变量不能定义为“text、ntext、image”数据类型。

```mssql
-- 定义局部变量格式
declare @局部变量名1 数据类型 [,…,@局部变量名n 数据类型];
```

### 6.3.2 直接赋值

**概述**：将一个常量或常量表达式赋给变量。

```mssql
-- 方法一
set @局部变量名 = 表达式;
-- 方法二
select @局部变量名1 = 表达式 [,…,@局部变量名n = 表达式];

-- 示例
declare @f float, @cn char(8);		-- 定义变量@f和@cn
set @f = 85;						-- 使用方法一为@f赋值
select @cn = '3-105';				-- 使用方法二为@cn赋值

select *
from score
where 课程号 = @cn and 分数 > @f;
```

### 6.3.3 在查询语句中为变量赋值

**概述**：若select语句返回多列多指，则将返回集中对应该变量的列中最后一个值赋给变量；若无返回值，变量则保留原值。

```mssql
-- 示例
-- 定义变量@no和@name
declare @no char(5), @name char(10);
-- 利用查询语句为变量赋值
select @no = 学号, @name = 姓名
from student
where 班号 = '1003';
-- 打印变量值
print @no + ' ' + @name;
```

### 6.3.4 利用排序规则在查询语句中为变量赋值（可不看）

**概述**：由于变量只取返回集中对应列中的最后一个值，所以可用“order by”语句控制最后一个值。

```mssql
-- 示例
-- 定义变量@no和@name
declare @no char(5), @name char(10);
-- 利用排序规则在查询语句中为变量赋值
select @no = 学号, @name = 姓名
from student
where 班号 = '1003'
order by 学号 desc;
-- 打印变量
print @no + ' ' + @name;
```

### 6.3.5 利用聚合函数为变量赋值（可不看）

**概述**：直接将聚合函数的结果赋给变量。

```mssql
-- 示例
-- 定义变量@f
declare @f float;
-- 在查询语句中用聚合函数为变量赋值
select @f = max(分数)
from score
where 分数 is not null;
-- 打印变量
print '最高分：' + @f;
```

### 6.3.6 利用子查询为变量赋值（可不看）

**概述**：直接将子查询的结果赋给变量。

```mssql
-- 示例
-- 定义变量@f
declare @f float;
-- 在查询语句中用聚合函数为变量赋值
select @f = (select max(分数)
             from score
             where 分数 is not null);
-- 打印变量
print '最高分：' + @f;
```

## 6.4 运算符

！！！略！！！

## 6.5 控制流语句

！！！略！！！

## 6.6 游标

！！！略！！！

# 第7章 索引和视图

## 7.1 索引（基础版）

**概述**：用于增加查询速度。

**按存储结构分为**：聚集索引、非聚集索引

- 聚集索引：建表时设定一个或多个列为主键时，则默认为主键列建立聚集索引，所以一张表只有一个聚集索引。

- 非聚集索引：数据的物理存储不连续，一张表可以有多个非聚集索引。

**按唯一性分为**：唯一索引、非唯一索引

- 唯一索引：在表中为某列创建了唯一约束，系统将自动创建该列的唯一索引

### 7.1.1 创建索引

```mssql
-- 语法格式
create [unique] [clustered | nonclustered] index 索引名
	on {表名 | 视图名}(列名1 [asc | desc],…,列名n [asc | desc]);
go

-- 示例
create unique index index_cd
on student(身份证号);
go
-- 注意：不指定[unique]时为非唯一索引，不指定[clustered | nonclustered]时为nonclustered非聚集索引
```

### 7.1.2 删除索引

```mssql
-- 语法格式
drop index 表名.索引名;

-- 示例
drop index student.index_cd;
go
```

### 7.1.3 修改索引（可不看）

```mssql
-- 语法格式：all表示修改表中所有索引
alter index {索引名 | all} on {表名 | 视图名}
	rebuild [with (rebuild_index_option)];
	
-- rebuild_index_option部分的替换代码
{
	pad_index = {on | off}
	| fillfactor = fillfactor
	| ignore_dup_key = {on | off}
	| drop_existing = {on  | off}
	| statistics_norecompute = {on | off}
	| sort_in_tempdb = {on | off}
	| allow_row_locks = {on | off}
	| allow_page_locks = {on | off}
}
```

```mssql
-- 示例：将索引index_cd的fillfactor设为90
alter index index_cd on student
	rebuild with (pad_index = on, fillfactor = 90);
```

### 7.1.4 禁用和启用索引（可不看）

```mssql
-- 语法格式：all表示修改表中所有索引
-- 禁用
alter index {索引名 | all} on {表名 | 视图名} disable;

-- 启用
alter indes {索引名 | all} on {表名 | 视图名} rebuild;
```

### 7.1.5 查看索引（可不看）

```mssql
-- 语法格式
-- 方法一：利用存储过程sp_helpindex查看某张表中的所有索引，其中对象名就是表名
exec sp_helpindex 对象名;

-- 方法二：查询系统索引表sys.indexes，利用where子句查询指定索引
select * from sys.indexes where name = 索引名;
```

```mssql
-- 示例
-- 方法一：查看student表中的所有索引
exec sp_helpindex student;
go

-- 方法二：查询student表中的index_cd索引
select * from sys.indexes where name = 'index_cd';
go
```

### 7.1.6 使用索引（可不看）

**概述**：创建并启用索引后，默认情况下系统自动使用索引执行表数据查询操作，但也可以在查询数据时显示设置使用某索引。

```mssql
-- 显示引用索引语法格式
select 列名,…
from {表名 | 视图名}
with (index = 索引名)
where 查询条件
```

```mssql
-- 示例：利用索引查询身份证号为“******20030103****”的学生的信息
select *
from student
with (index = index_cd)
where cd = '******20030103****';
```

## 7.2 视图（基础版）

### 7.2.1 创建视图

```mssql
-- 语法格式
create view 视图名
as
	select语句;
```

```mssql
-- 示例：创建视图view_student_score_course，其中包括所有学生的姓名、课程、分数
create view view_student_score_course
as
	select st.姓名, co.课程名, sc.分数
	from student st, score sc, course co
	where st.学号 = sc.学号 and sc.课程号 = co.课程号;
go
```

### 7.2.2 删除视图

```mssql
-- 语法格式
drop view 视图名1 [,…,视图名n];

-- 示例
drop view view_student_score_course;
go
```

### 7.2.3 修改视图（可不看）

```mssql
-- 语法格式
alter view 视图名
as
	select语句;
```

```mssql
-- 示例：将视图view_student_score_course恢复原样
alter view view_student_score_course
as
	select st.姓名, co.课程名, sc.分数
	from student st, score sc, course co
	where st.学号 = sc.学号 and sc.课程号 = co.课程号;
```

### 7.2.4 查看和使用视图（选看）

```mssql
-- 语法格式
-- 利用存储过程sp_helptext查看视图
exec sp_helptext 视图名;
-- 使用视图
select 列名,…
from 视图名;
```

```mssql
-- 示例
-- 查看视图
exec sp_helptext view_student_score_course;
-- 使用视图
select * from view_student_score_course;
```

# 第8章 默认值——使用默认对象

**概述**：类似于常量，但定义后不可直接使用，需要通过绑定到某表某列的方式使用。绑定表后，将表删除不影响默认对象。

## 8.1 创建默认对象

```mssql
-- 语法格式
create default 默认对象名 as 常量表达式;

-- 示例
create default sex as '男';
```

## 8.2 绑定默认对象

```mssql
-- 语法格式：利用存储过程sp_bindefault绑定默认对象
exec sp_bindefault '默认对象名','需绑定默认对象的表名.列名';

-- 示例
exec sp_bindefault 'sex','student.性别';
```

## 8.3 重命名默认对象（可不看）

```mssql
-- 语法格式：利用存储过程sp_rename重命名默认对象
exec sp_rename '旧默认对象名','新默认对象名';

-- 示例
exec sp_rename 'sex','gender';
```

## 8.4 解除默认对象的绑定（选看）

```mssql
-- 语法格式：利用存储过程sp_unbindefault解除默认对象的绑定
exec sp_unbindefault '绑定默认对象的表名.列名';

-- 示例
exec sp_unbindefault 'student.性别';
```

## 8.5 删除默认对象

```mssql
-- 语法格式
drop default 默认对象名;

-- 示例
drop default gender;
```

# 第9章 函数和存储过程

## 9.1 函数——用户自定义函数

### 9.1.1 创建函数

1. **标量值函数**：仅返回单个值

   ```mssql
   -- 创建标量值函数语法格式
   create function 函数名([
       @参数名1 数据类型 [= 默认值]
       [,…n]
   ])
   returns 返回值数据类型 [as]
   begin
   	函数体
   	return 标量表达式
   end
   go
   ```

   ```mssql
   -- 示例：创建一个加法函数，并返回相加结果
   create function addition(@value1 int, @value2 int)
   returns int as
   begin
   	declare @result int;
   	set @result = (@value1 + @value2);
   	return @result;
   end
   go
   
   -- 测试函数
   declare @value1 int, @value2 int;
   select @value1 = 10, @value2 = 20;
   print cast(@value1 as char(2)) + ' + ' + cast(@value2 as char(2)) + ' = ' + cast(dbo.addition(@value1, @value2) as char(2));
   go
   ```

2. **内联表值函数**：返回函数中select语句查询的表

   ```mssql
   -- 创建内联表值函数语法格式
   create function 函数名([
       @参数名1 数据类型 [= 默认值]
       [,…n]
   ])
   returns table [as]
   return [(]
   	select语句
   [)]
   go
   ```

   ```mssql
   -- 示例：创建一个内联表值函数，返回一个student表和score表的简单连接表，且只展示“1003”班的学生的姓名、课程号和分数
   create function fun_student_score(@c_id char(10))
   returns table as
   return (
   	select st.姓名, sc.课程号, sc.分数
       from student st, score sc
       where st.学号 = sc.学号 and st.班号 = @c_id;
   )
   go
   
   -- 测试函数
   select * from fun_student_score('1003');
   go
   ```

3. **多语句表值函数**：将函数中select语句查询的表按照自定义的表结构重构成新表返回

   ```mssql
   -- 创建多语句表值函数语法格式
   create function 函数名([
       @参数名1 数据类型 [= 默认值]
       [,…n]
   ])
   returns @返回值表名 table(
   	表结构
   ) [as]
   begin
   	insert @返回值表名
   	select语句
   	return
   end
   go
   ```

   ```mssql
   -- 示例：创建一个多语句表值函数，返回一个表，表中展示所有学生的姓名和各自所有课程的平均分，且仅展示平均分高于80分的，并按照学号升序排列
   create function fun_student_avg_score(@low float)
   returns @st table(
       学号 char(10),
       姓名 char(10),
       平均分 float
   ) as
   begin
   	insert @st
   	
   	select st.学号, st.姓名, avg(sc.分数)
   	from student st, score sc
   	where st.学号 = sc.学号 and sc.分数 is not null and sc.分数 > @low
   	group by st.学号
   	order by st.学号 asc
   	
   	return
   end
   go
   
   -- 测试函数
   select * from fun_student_avg_score(80);
   go
   ```

### 9.1.2 删除函数

```mssql
-- 语法格式
drop function 用户自定义函数名;

-- 示例
drop function fun_student_avg_score;
go
```

### 9.1.3 修改函数（可不看）

```mssql
-- 语法格式
alter function 函数名([@参数名1 数据类型 [,…n] ])
{语句剩余部分，3种函数各自参考各自的创建函数语句的剩余部分}
go
```

## 9.2 存储过程

**概述**：由于函数只能由数据库自己调用，外部服务（例如：Java端、python端等）无法调用，这时就可以使用存储过程。

### 9.2.1 创建存储过程

```mssql
-- 语法格式
create proc[edure] 存储过程名([
    @参数名1 数据类型 [= 默认值] [out | output]
    [,…n] 
])
as
	SQL语句
go
```

```mssql
-- 示例：创建一个存储过程，实现查询指定学生学号、姓名、平均分，平均分作为存储过程返回值，若不指定，则默认查询学号“10003”的学生
create proc proc_student_score(@s_id char(10) = '10003', @name char(10) output, @st_avg float output)
as
	select st.学号, @name = st.姓名, @st_avg = avg(sc.分数)
	from student st, score sc
	where st.学号 = @s_id and st.学号 = sc.学号
	group by st.学号, st.姓名
go
```

### 9.2.2 执行存储过程

```mssql
-- 语法格式
exec 存储过程名 {值 | @变量名 [out | output]} [,…n];
go
```

```mssql
-- 示例
declare @name char(10), @st_avg float;
exec proc_student_score @name output, @st_avg output;
select '姓名' = @name, '平均分' = @st_avg;
go
```

### 9.2.3 删除存储过程

```mssql
-- 语法格式
drop procedure 存储过程名;
go

-- 示例
drop procedure proc_student_score;
go
```

### 9.2.4 修改存储过程

！！！略！！！

### 9.2.5 重命名存储过程

！！！略！！！

### 9.2.6 查看存储过程

！！！略！！！

# 第10章 触发器

**概述**：触发器就是在某些操作前后执行的操作。

## 10.1 DML触发器（基础版）

**概述**：DML触发器作用于表数据的插入、修改和删除。

### 10.1.1 创建DML触发器

```mssql
-- 创建DML触发器语法格式
create trigger 触发器名
on {表名 | 视图名} {after | for | instead of} {[insert][,][update][,][delete]}
as
	SQL语句
go
```

```mssql
-- 示例：在每次为student表删除或添加数据后，执行查询student表数据操作
create trigger tri_student_insert
on student after insert,delete
as
	select * from student
go
```

### 10.1.2 删除DML触发器

```mssql
-- 语法格式
drop trigger 触发器名;
go

-- 示例
drop trigger tri_student_insert;
go
```

## 10.2 DDL触发器（基础版）

**概述**：DDL触发器作用于数据库对表的创建、修改和删除。

### 10.2.1 创建DDL触发器

```mssql
-- 创建DDL触发器语法格式
create trigger 触发器名
on {all server | database} {after | for} {[create_table][,][alter_table][,][drop_table]}
as
	SQL语句
go
```

```mssql
-- 示例：在每次删除表后，提示删除成功
create trigger tri_drop_table
on database after drop_table
as
	print '删除成功'
go
```

### 10.2.2 删除DDL触发器

```mssql
-- 语法格式
drop trigger 触发器名;
go

-- 示例
drop trigger tri_drop_table;
go
```

# 第11章 权限与角色

！！！略，这几分不要也罢！！！
