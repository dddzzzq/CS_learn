# DBMS

## 1. 实体关系图（ER图）相关概念

- **概念**：ER图显示实体集之间的关系。实体集是一组相似的实体，这些实体可以具有自己的属性。就DBMS而言，实体就是表的表或属性，因此通过显示表之间的关系以及属性，ER图就展示了数据库的完整逻辑结构。以下是一个简单的ER图来理解这个概念，

  ![image-20241024162528288](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241024162528288.png)

- **符号**：以下是ER图中的几何形状及其含义。

  - 矩形：表示实体
  - 椭圆：属性
  - 菱形：关系集
  - 线：他们将属性连接到实体集，将实体集连接到关系集
  - 双椭圆：多值属性
  - 。。。

- 组成部分：**实体**、**属性**、**关系**

  ![image-20241024162935774](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241024162935774.png)

## 2.ER图的组成

### 2.1 实体

​	实体是数据的对象或者组件，实体在ER图中表示为**矩形**。

​	**弱实体**：指不能通过自身属性唯一标识，并依赖于其他实体的关系的实体称为弱实体，弱实体由**双矩形**表示。*例如，如果不知道银行账户所属的银行，就无法唯一的识别该账户，因此银行账户是一个弱实体。*

### 2.2 属性

​	属性描述实体的属性。属性在ER图中表示为椭圆，有四种类型的属性：

​		1.关键属性

​		2.复合属性

​		3.多值属性

​		4.派生属性

#### 2.2.1 关键属性

​	关键属性（key属性）可以唯一标识实体集中的实体。例如：学生学号可以从一组学生中唯一标识一个学生。key属性由椭圆表示，但**key属性的文本带有下划线**。

​	![image-20241024164229841](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241024164229841.png)

#### 2.2.2 复合属性

​	作为**其他属性组和**的属性称为复合属性，例如：在学生实体中，学生地址是一个复合属性，因为地址由其他属性组成，例如PIN码、州、国家。

![image-20241024164404085](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241024164404085.png)

#### 2.2.3 多值属性

​	可以**包含多个值**的属性成为多值属性。它在ER图中的表示为双椭圆，例如：一个人可以有多个电话号码，因此phonenumber属性是多值的。

#### 2.2.4 派生属性

​	派生属性是指其值是**dynamic**的并从**另一个属性派生**的属性，因为它会随时间变化而变化，并且可以从另一属性（出生日期）派生。

![image-20241024164803137](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241024164803137.png)

上图是一个具有**多值属性**和**派生属性**的E-R图。

### 2.3 关系

​	关系在ER图中用**菱形**表示，它显示了实体之间的关系。有四种类型的关系：

- - 一对一
  - 一对多
  - 多对一
  - 多对多

#### 2.3.1 ISA联系（分类）

- 某些实体型是某个实体型的子类型，这种父类-子类联系称为ISA联系，表示"is a"语义。
- ISA联系的重要性质：子类继承了父类的所有属性，子类也可以有自己的属性。

![image-20241024180629011](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241024180629011.png)

- **不相交约束**：描述父类中的一个实体**不能同时属于**多个子类中的实体集。**符号表示**为ISA联系符号三角形中的一个叉号来表示。没有叉号则表示可以重叠。

- **完备性约束**：描述一个父类中的一个实体是否必须是某一个子类中的实体。

  - 若必须是，则叫做完全特化，用**双线连接**表示。
  - 否则叫做部分特化，用**单线链接**表示。

  ![image-20241024181241415](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241024181241415.png)

- **基数约束**：指实体之间一对一、一对多、多对多联系的细化。

  ​	表示方法：约束用一个数对min..max表示。例如：0..1,1..3,1..*,其中，\*表示无穷大。

  ​	min=1表示强制参与约束

  ​	min=0表示非强制参与约束

  ![image-20241024181619752](D:\DZQ\课程学习\图片\image-20241024181619752.png)

- 独占联系：如果一个实体型的存在**依赖**于其他实体的存在，那么这个实体型叫做弱实体型，否则叫做强实体型。

  ​	一般地如果不能从一个实体型的属性中可以作为关键属性的属性，那么这是实体就是弱实体型。

  ​	在ER图中，用**双矩形**表示弱实体型，用**双菱形**表示识别联系。

  ![image-20241024182231710](D:\DZQ\课程学习\图片\image-20241024182231710.png)

## 3. 一些特殊概念

### 3.1 实体集的总参与量

​	实体集的总数表示实体集中的每一个实体在关系集中至少要有一个关系，因此它也被称为强制参与。**例如**：在下图中，每个学院必须至少有一个关联的Student。总参与率在实体集和关系集之间用在**双线**表示。

![image-20241024170206399](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241024170206399.png)

### 3.2 实体集的部分参与

​	实体集的部分参与表示实体集中的每个实体都可能参与也可能不参与该关系集的关系实例。它也被称为**可选参与**。使用**单线**表示。

## 4. ER图到表格的转换

### 4.1 具有Simple属性的强实体集

​	强实体集成为表，实体集的属性成为表属性，实体集的key属性成为表的主键。**例如**：一个实体集Employee，其属性为Name、Age、Emp_Id和Salary。转换为表后，实体集转换为表，因此我们有一个名为"Employee"的表，实体集的属性将成为表的属性。如下图所示。

![image-20241024172842183](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241024172842183.png)

### 4.2 具有复合属性的强实体集

​	大体步骤和simple属性强实体集转换相同，但是复合属性的简单属性成为表的属性，而复合属性**本身**在转换过程中将**被忽略**。如下图所示。

![image-20241024173114909](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241024173114909.png)

### 4.3 具有多值属性的强实体集

​	具有多值属性的实体集需要关系模型中的**两个表**。每当我们有一个多值属性时，就需要有多个表来表示ER图。如下图所示：

![image-20241024173404444](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241024173404444.png)

### 4.4 关系集到表转换

​	在将关系集转换为表时，实体集的**关键属性（key属性）**成为表的属性，如果关系集有属性也成为表的属性。如下图中，实体集Employee的关键属性Emp_Id和关系集的属性Experience以及实体集Department的关键属性Dept_Id成为表的属性。

![image-20241024173848673](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241024173848673.png)

## 5.  泛化

​	**泛化**是多个实体的公共属性形成新实体的过程，这个新形成的实体被称为广义实体。

### 5.1 泛化示例

假设我们有两个实体集合：

​		Student：Name、Address、Grade

​		Teacher：Name、Address、Salary

则泛化前的ER图如下所示：

![image-20241024174513380](C:\Users\党子清\AppData\Roaming\Typora\typora-user-images\image-20241024174513380.png)

​	泛化后形成新的实体Person，该实体具有两个实体所共有的属性，在繁华过程后，实体Student和Teacher分别具有专门的属性Grade和Salary，而两个实体与新形成的实体Person具有关系。泛化后的ER图如下所示：
![image-20241024174744232](D:\DZQ\课程学习\图片\image-20241024174744232.png)			

### 5.2 注意

1. 泛化使用自下而上的方法，其中两个或多个较低级别的实体组合在一起，形成一个更高级别的新实体。
2. 新的通用尸体可以进一步与较低级别的实体组合在一起，以创建更高级别的通用实体。

## 6.特化（专业化）

​	**特化**是将实体划分为多个实体的过程，可将其理解为泛化的**反向过程**，泛化是一个自下而上的过程，而特化是一个自上而下的过程。

​	**目的**：查找几乎没有分类属性的实体子集。*例如*：一个实体员工，可以进一步分类为子实体技术员、工程师和会计师。示例如下：

![image-20241025095841286](D:\DZQ\课程学习\图片\image-20241025095841286.png)



## 7. DBMS中的分层模型

​	在**分层模型**中，数据被组织成一个树状结构，媒体哦啊记录都有一个父记录和许多子记录。此模型的主要缺点是，他在节点之间只能具有**一对多**的关系。因此现在也很少使用分层模型。

## 8. DBMS中的约束

​	约束可对从表中插入/更新/删除的数据或数据类型进行限制，而约束的全部目的是在对表进行操作的过程中保持数据完整性。

### 8.1 约束类型

- NOT NULL
- UNIQUE
- DEFAULT
- CHECK
- Key Constraints - PRIMARY KEY, FOREIGN KEY
- Domain constraints
- Mapping constraints

### 8.2 NOT NULL

​	NOT NULL 约束确保表的列**不包含NULL值**，当我们在将记录插入表中没有为特定列提供值时，默认情况下他会采用NULL值，而通过NOT NULL限制可以保证特定列不能有NULL值。

​	示例：

```sql
CREATE TABLE STUDENT
(
ROLL_NO INT NOT NULL,
STU_NAME VARCHAR(35) NOT NULL,
STU_ADDRESS VARCHAR(235) NOT NULL
);
```

### 8.3 UNIQUE

​	UNIQUE Constraints强制一列或一组列具有**唯一值**。如果列具有唯一约束，则意味着该特定列在表中不能有重复的值。

​	示例：

```sql
CREATE TABLE STUDENT (
ROLL_NO INT NOT NULL UNIQUE,
STU_NAME VARCHAR(15) NOT NULL,
...
);
```

### 8.4 DEFAULT

​	DEFAULT为列提供**默认值**。

​	示例：

```sql
CREATE TABLE STUDENT 
(
ROLL_NO INT NOT NULL UNIQUE,
STUDENT_NAME VARCHAR(15) NOT NULL,
EXAM_FEE INT DEFAULT 10000,
...
);
```

### 8.5 CHECK

​	此约束用于指定表的特定列的值范围。在列上设置此约束时，它确保指定列的值必须在指定范围内。

​	示例：

```sql
CREATE TABLE STUDENT
(
ROLL_NO INT NOT NULL UNIQUE CHECK(ROLL_NO > 1000),
STUDENT_NAME VARCHAR(15) NOT NULL,
...
);
```

### 8.6 PRIMARY KEY

​	PRIMARY KEY唯一标识表中的每条记录。它必须具有唯一值，并且不能包含null值，在下面的示例中，ROLL_NO字段被标记为主键，这意味着ROLL_NO不能有重复值和NULL值。

```sql
CREATE TABLE STUDENT 
(
ROLL_NO INT,
STUDENT_NAME VARCHAR(15) NOT NULL,
STUDENT_ADDRESS VARCHAR(235) NOT NULL
...,
PRIMARY KEY (ROLL_NO)
);
```

### 8.7 FOREIGN KEY

​	外键是指向另一个表的主键的列，它充当表之间的交叉引用。

### 8.8 Domain Contraints

​	每个表都有一组特定的列，并且每个列都允许根据其数据类型使用相同类型的数据。该列不接受任何其他数据类型的值。

​	**域约束**是**用户定义的数据类型**，我们可以像这样定义它们：

域约束 = 数据类型 + 约束（NOT NULL / UNIQUE / PRIMARY KEY / FOREIGN KEY / CHECK / DEFAULT）

### 8.9 映射约束（Mapping Contrainnts）

示例：

```sql
CREATE TABLE Customer (
customer_id int PRIMARY KEY NOT NULL,
first_name varchar(20),
last_name varchar(20)
);

CREATE TABLE Orders (
order_id int PRIMARY KEY NOT NULL,
customer_id int,
order_details varchar(50),
constraint fk_Customers foreign key (customer_id) 
       references dbo.Customer
);
```

- `constraint fk_Customers foreign key (customer_id)`：这定义了一个名为 `fk_Customers` 的外键约束。外键约束用于维护数据库的引用完整性。在这里，它指定了 `Order` 表中的 `customer_id` 列是外键。
- `references dbo.Customer`：这指定了外键 `customer_id` 列引用的是 `dbo`（数据库所有者）模式下的 `Customer` 表。这意味着 `Order` 表中的每个 `customer_id` 必须在 `Customer` 表中有一个对应的 `customer_id`。



## 9. 逻辑结构设计

​	**将ER图转换为关系表**。

### 9.1 实体的转换

#### 9.1.1 转换原则

转换原则：一个实体型转换为一个关系模式。

- 实体名做关系名
- 实体的普通属性（非派生属性、组合属性、多值属性）转换为关系的属性。
- 实体标识符转换为关系的码
- 派生属性不转换（丢弃）
- 组合属性丢弃，只取其分量
- 每个多值属性分别与实体标识符另构成新的关系模式。

如下所示：

![image-20241031212146294](D:\DZQ\课程学习\图片\image-20241031212146294.png)

如上所示的ER图转换为如下的关系模式：

![image-20241031212243817](D:\DZQ\课程学习\图片\image-20241031212243817.png)

#### 9.1.2 弱实体的转换

- 弱实体的主码由标识性实体的主码和弱实体的分辨属性构成。
- 弱实体名作为关系名。
- 弱实体的属性转换为关系的属性。

如下所示：
![image-20241031212512729](D:\DZQ\课程学习\图片\image-20241031212512729.png)

### 9.2 两个实体之间的转换

#### 9.2.1（ 1：1）

​	一个1：1联系可以转换为一个独立的关系模式，也可以与另一个实体合并。

​	但一般情况下推荐选择与某一端对应的关系模式合并：

- 合并后关系的属性：加入另一关系的码和联系本身的属性
- 合并后关系的码：**不变**

示例如下：

![image-20241031212849230](D:\DZQ\课程学习\图片\image-20241031212849230.png)

#### 9.2.2 （1：n）

​	一个1：n联系可以转换为一个独立的关系模式，也可以与n端的关系模式合并。

​	一般情况下，推荐与n端的关系合并处理。

- 合并后关系的属性：在n端关系中加入1端关系的码和联系本身的属性
- 合并后关系的码：**不变**

示例如下：

![image-20241031213250691](D:\DZQ\课程学习\图片\image-20241031213250691.png)

#### 9.2.3 （n：m）

​	一个n：m的联系转换成一个独立的关系模式

- 关系的属性：与该联系相连的各实体的码以及联系本身的属性。
- 关系的码：各实体码的组合

示例如下：

![image-20241031213635630](D:\DZQ\课程学习\图片\image-20241031213635630.png)

### 9.3 三个或三个以上实体间联系的转换

​	这样的**多元联系**可以转换为一个独立的关系模式，也可以分解成多个二元联系。

1. 转换为一个独立的关系模式

   - 关系的属性：与该多元联系相连的各实体的码以及联系本身的属性
   - 关系的码：各实体码的组合

   示例如下：

   ![image-20241031214044515](D:\DZQ\课程学习\图片\image-20241031214044515.png)

2. 分解为多个二元联系

   三元关系转成二元关系具体步骤：

   1. 用新的实体集替代联系R，如图中的供应单代替供应这一关系
   2. 建立三个新的联系：RA,RB,RC，如下图中的橙色菱形框图
   3. 针对联系R中的每个联系ai,bi,ci，在E中创建一个新实体ei，ei则代表ai，bi，ci。

示例如下：

![image-20241031214138894](D:\DZQ\课程学习\图片\image-20241031214138894.png)



## 10. 模式&角色&用户

### 10.1 模式（Schema）

​	模式是数据库中组织数据的一种逻辑结构，它是一个命名空间，用于包含表、视图、索引、序列、数据类型、函数和操作符等数据库对象。模式可以看作是数据库对象的集合。

**定义模式**：

```sql
CREATE SCHEMA schema_name AUTHORIZATION user_name;
```

这里，`CREATE SCHEMA` 是用来创建一个新的模式，`schema_name` 是新模式的名称，`AUTHORIZATION` 子句指定了拥有该模式权限的用户。

**修改模式**：

```sql
ALTER SCHEMA schema_name RENAME TO new_schema_name;
```

**删除模式**：

```sql
DROP SCHEMA schema_name CASCADE;
```

`DROP SCHEMA` 语句用于删除一个模式，`CASCADE` 选项表示同时删除该模式中的所有对象。



### 10.2 用户（User）

用户是数据库中的一个实体，可以访问和操作数据库中的数据。每个用户都有自己的权限和角色，这些权限决定了用户可以执行的操作。

**创建用户**：

```sql
CREATE USER user_name WITH PASSWORD 'password';
```

`CREATE USER` 语句用于创建一个新的数据库用户，`WITH PASSWORD` 子句为用户设置密码。

- **修改用户：**

```sql
ALTER USER user_name WITH PASSWORD 'new_password';
```

`ALTER USER` 语句用于修改用户属性，例如更改密码。

- **删除用户：**

```sql
DROP USER user_name;
```

`DROP USER` 语句用于删除一个用户。

### 3. 角色（Role）

角色是一组权限的集合，可以分配给一个或多个用户。角色简化了权限管理，因为你可以将一组权限赋予一个角色，然后将该角色赋予多个用户，而不是单独为每个用户设置权限。

- **创建角色：**

```sql
CREATE ROLE role_name;
```

`CREATE ROLE` 语句用于创建一个新的角色。

- **给角色授权：**

```sql
GRANT SELECT, INSERT ON schema_name.table_name TO role_name;
```

`GRANT` 语句用于给角色授予权限，例如对特定表的选择和插入权限。

- **将角色赋予用户：**

```sql
GRANT role_name TO user_name;
```

这个语句将角色赋予用户，用户将继承角色的所有权限。

- **删除角色：**

```sql
DROP ROLE role_name;
```

`DROP ROLE` 语句用于删除一个角色。

在管理数据库时，模式、用户和角色都是实现数据安全和权限控制的重要组成部分。合理地使用这些概念可以有效地管理数据库资源，保证数据的安全性和完整性。
