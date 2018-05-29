# ORM

## 定义
ORM全称是：Object Relational Mapping(对象关系映射)，其主要作用是在编程中，把面向对象的概念跟数据库中表的概念对应起来。举例来说就是，我定义一个对象，那就对应着一张表，这个对象的实例，就对应着表中的一条记录。

## 背景
1. 当我们工作在一个面向对象的系统中时，存在一个对象模型和关系数据库不匹配的问题

|不匹配| 描述|
| --- | --- |
|粒度|  有时你将会有一个对象模型，该模型类的数量比数据库中关联的表的数量更多
|继承|  RDBMSs 不会定义任何在面向对象编程语言中本来就有的继承
|身份|  RDBMS 明确定义一个 'sameness' 的概念：主键。然而，Java 同时定义了对象判等（a==b）和 对象值判等（a.equals(b)）
|关联|  面向对象的编程语言使用对象引用来表示关联，而一个 RDBMS 使用外键来表示对象关联
|导航|  在 Java 中和在 RDBMS 中访问对象的方式完全不相同

## 理解
1. 简单：ORM以最基本的形式建模数据。比如ORM会将MySQL的一张表映射成一个PHP类（模型），表的字段就是这个类的成员变量
2. 精确：ORM使所有的MySQL数据表都按照统一的标准精确地映射成PHP类，使系统在代码层面保持准确统一
3. 易懂：ORM使数据库结构文档化。比如MySQL数据库就被ORM转换为了PHP程序员可以读懂的PHP类，PHP程序员可以只把注意力放在他擅长的PHP层面（当然能够熟练掌握MySQL更好）
4. 易用：ORM的避免了不规范、冗余、风格不统一的SQL语句，可以避免很多人为Bug，方便编码风格的统一和后期维护

## 例子
OOP
```
// 声明class User
class User{
    $id;
    $name;
    function create(){/*...*/}
    function load($id){/*...*/}
}

// 使用class User
$user = new User();
$user->name = 'fancy';
$user->create();
```

通过ORM，我们可以不用去声明class User，可以直接继承ORM提供的工厂类
```
// 直接使用！对于熟悉MVC的亲知道这个意义之所在！
$user = new ORM('user');  // ORM都有自己的规则，这里直接使用了MySQL的表名
$user->name = 'fancy';    // MySQL的表的字段就是$user对象的成员变量
$user->save();            // 掉用ORM提供的接口函数
```

## 参考资料
* [ORM到底是用还是不用？](https://www.pureweber.com/article/orm/)