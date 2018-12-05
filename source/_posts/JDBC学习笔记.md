---
title: JDBC学习笔记
date: 2018-12-05 15:54:46
tags: 学习笔记
---

# JDBC
## 1. 简介
JDBC(Java Data Base Connectivity,java数据库连接),由一些接口和类构成的API。
J2SE的一部分,由java.sql,javax.sql包组成。

## 2. 连接数据库的步骤
### 2.1 注册驱动 (只做一次)
```java
Class.forName(“com.mysql.jdbc.Driver”);
	推荐这种方式,不会对具体的驱动类产生依赖。
	
DriverManager.registerDriver(com.mysql.jdbc.Driver);
	会造成DriverManager中产生两个一样的驱动,并会对具体的驱动类产生依赖。
	
System.setProperty(“jdbc.drivers”, “driver1:driver2”);
	虽然不会对具体的驱动类产生依赖；但注册不太方便,所以很少使用。 
	
驱动类型(四种类型)
```
### 2.2 建立连接(Connection) 

```java
Connection conn = DriverManager.getConnection(url, user, password);
url格式：
	JDBC:子协议:子名称//主机名:端口/数据库名？属性名=属性值&…
User,password可以用“属性名=属性值”方式告诉数据库；
其他参数如：useUnicode=true&characterEncoding=UTF-8&useSSL=false。
```
### 2.3 创建执行SQL的语句(Statement)
```java
Statement
	Statement st = conn.createStatement();
	st.executeQuery(sql);
PreparedStatement
	String sql = “select * from table_name where col_name=?”;
	PreparedStatement ps = conn.preparedStatement(sql);
	ps.setString(1, “col_value”);
	ps.executeQuery();
```
### 2.4 执行语句
```java
ps.executeQuery();	//执行查询
ps.executeUpdate();	//执行更新和插入和删除	
```
### 2.5 处理执行结果(ResultSet)
```java
ResultSet rs = statement.executeQuery(sql);
While(rs.next()){
	rs.getString(“col_name”);
	rs.getInt(“col_name”);
	//…
}
```
### 2.6 释放资源
```java
释放ResultSet, Statement,Connection.
数据库连接(Connection)是非常稀有的资源,用完后必须马上释放,如果Connection不能及时正确的关闭将导致系统宕机。Connection的使用原则是尽量晚创建,尽量早的释放。
```
## 3. 基本的CRUD(创建、读取、更新、删除) 
### 3.1 模板代码 
```java
Connection conn = null;
Statement st=null;
ResultSet rs = null;
try {
	//获得Connection
	//创建Statement
	//处理查询结果ResultSet
} finally {
	//释放资源ResultSet, Statement,Connection
}
```
### 3.2 创建
增加对应SQL的INSERT,返回增加成功的行(记录)数
```java
conn = getConnection();
Statement st = conn.createStatement();
String sql=“insert into user(name, age,regist_date )” +  		“values(‘name’, 10, now())”;
int i = st.executeUpdate(sql);
//i为插入的记录数
```
### 3.3 读取
读取(查询)对应SQL的SELECT,返回查询结果
```java
conn = getConnection();
st = conn.createStatement();
String sql = "select id, name, age, regist_date from user";
rs = st.executeQuery(sql);
while (rs.next()) {
		System.out.print(rs.getInt("id") + " \t\t ");
		System.out.print(rs.getString("name") + " \t\t ");
		System.out.print(rs.getInt("age") + " \t\t ");
		System.out.print(rs.getTimestamp("regist_date") + " \t\t ");
		System.out.println();
}
```
### 3.4 更新
更新(修改)对应SQL的UPDATE,返回被修改的行(记录)数 
```java
conn = getConnection();
Statement st = conn.createStatement();
String sql=“update person set name = 'new name‘”;
int i = st.executeUpdate(sql);
//i为符合条件的记录数
```
### 3.5 删除
删除对应SQL的DELETE,返回被删除的行(记录)数 
```java
conn = getConnection();
Statement st = conn.createStatement();
String sql=“delete from user where id=1”;
int i = st.executeUpdate(sql);
//i为删掉的记录数
```
### 3.6 总结
```java
增、删、改用Statement.executeUpdate来完成,返回整数(匹配的记录数),这类操作相对简单。
查询用Statement.executeQuery来完成,返回的是ResultSet对象,ResultSet中包含了查询的结果；查询相对于增、删、改要复杂一些,因为有查询结果要处理。
```
## 4. SQL注入,PreparedStatement和Statement
```java
在SQL中包含特殊字符或SQL的关键字(如：' or 1 or ')时Statement将出现不可预料的结果(出现异常或查询的结果不正确),可用PreparedStatement来解决。
PreperedStatement(从Statement扩展而来)相对Statement的优点：
	1.没有SQL注入的问题。
	2.Statement会使数据库频繁编译SQL,可能造成数据库缓冲区溢出。
	3.数据库和驱动可以对PreperedStatement进行优化(只有在相关联的数据库连接没有关闭的情况下有效)。 
```
## 5. 数据类型
```java
详细信息见java.sql.Types
几种特殊且比较常用的类型
	1.DATA,TIME,TIMESTAMP date,time,datetime
存：ps.setDate(i,d); ps.setTime(i,t); ps.setTimestamp(i, ts);
  	  取：rs.getDate(i); rs.getTime(i); rs.getTimestamp(i);
	2.CLOB -> text(文本文件)
	  存：ps.setCharacterStream(index, reader, length);
	         ps.setString(i, s);
	  取：reader = rs. getCharacterStream(i);
	         reader = rs.getClob(i).getCharacterStream();
	         string = rs.getString(i);
	3.BLOB -> blob(字节文件,如图片)
	 存：ps.setBinaryStream(i, inputStream, length);
       取：rs.getBinaryStream(i);
	        rs.getBlob(i).getBinaryStream(); 
```
## 6. 一个简单用户相关的数据访问层 
J2EE三层架构简介
​		表示层 、业务逻辑层、数据访问层,三层之间用接口隔离。
定义domain对象User,定义存取用户的接口
用JDBC实现接口
用配置文件(properties)和反射实现与具体类的耦合 
## 7. 事务
### 7.1 事务(ACID)
原子性(atomicity)：组成事务处理的语句形成了一个逻辑单元,不能只执行其中的一部分。 
一致性(consistency)：在事务处理执行前后,数据库是一致的(两个账户要么都变,或者都不变)。 
隔离性(isolcation)：一个事务处理对另一个事务处理没有影响。 
持续性(durability)：事务处理的效果能够被永久保存下来 。
```java
connection.setAutoCommit(false);//打开事务。
connection.commit();//提交事务。
connection.rollback();//回滚事务。
```
### 7.2 事务(SavePoint)
当只想撤销事务中的部分操作时可使用SavePoint
```java
//建立保存点
SavePoint sp = connection.setSavepoint();
//回滚到保存点
connection.rollerbak(sp);
//提交事务
connection.commit();
```
### 7.4 事务(JTA)
跨越多个数据源的事务,使用JTA容器实现事务。
分成两阶段提交。
```java
javax.transaction.UserTransaction tx = (UserTransaction)ctx.lookup(“jndiName");
	tx.begin();
	//connection1 connection2 (可能来自不同的数据库)… 
    tx.commit();//tx.rollback();
```
### 7.4 隔离级别多线程并发读取数据时的正确性 
connection.setTransactionIsolation(Connection.TRANSACTION_READ_COMMITTED); 
V:可能出现,X:不会出现
| 隔离级别                   | 脏读 | 不可重复读 | 幻读 |
| -------------------------- | ---- | ---------- | ---- |
| 读未提交(Read Uncommitted) | V    | V          | V    |
| 读已提交(Read Committed)   | X    | V          | V    |
| 可重复读(Repeatable Read)  | X    | X          | V    |
| 可串行化                   | X    | X          | X    |
## 8. 存储过程
CallableStatement(从PreperedStatement扩展来)
```java
cs = connection.prepareCall(“{call psname(?,?,?)}”);
cs.registerOutParameter(index, Types.INTEGER);
cs.setXXX(i, xxxx);
cs.executeUpdate();
int id=cs.getInt(index);
```
## 9. 其他的几个API
返回插入语句的主键：Statement.getGeneratedKeys()
```java
PreparedStatement ps = connection.prepareStatement(sql,	Statement.RETURN_GENERATED_KEYS);
ps.executeUpdate();
ResultSet rs = st.getGeneratedKeys();rs.getInt(1);
```
批处理,可以大幅度提升大量增、删、改的速度。
```java
PreparedStatement.addBatch();
PreparedStatement.executeBatch();
```
可滚动的结果集
```java
Statement st = 
connection.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE,	ResultSet.CONCUR_UPDATABLE);
ResultSet rs = st.executeQuery(sql);
rs.beforeFirst(); rs.afterLast();rs.first();rs.isFirst();rs.last();rs.isLast();
rs.absolute(9);rs.moveToInsertRow();
```
可更新的结果集
```java
conn.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE,
				ResultSet.CONCUR_UPDATABLE);
rs.updateString("col name", "new value");
rs.updateRow();
```
## 10. 元数据
### 10.1 DatabaseMetaData
```java
DatabaseMetaData meta = connection.getMetaData();
```
通过DatabaseMetaData可以获得数据库相关的信息如：数据库版本、数据库名、数据库厂商信息、是否支持事务、是否支持某种事务隔离级别,是否支持滚动结果集等。
### 10.2 ResultSetMetaData
```java
ResultSetMetaData meta = rs.getMetaData();
通过ResultSetMetaData可以获得结果有几列、各列名、各列别名、各列类型等。 
可以将ResultSet放入Map(key:列名 value:列值)。
用反射ResultSetMetaData将查询结果读入对象中(简单的O/RMapping) 
	1)让SQL语句中列别名和要读入的对象属性名一样；
	2)通过ResultSetMetaData获得结果列数和列别名；
	3)通过反射将对象的所有setXxx方法找到;
	4)将3)找到的方法setXxx和2)找到的列别名进行匹配(即方法中的xxx于列别名相等)；
	5)由上一步找到的方法和列别名对应关系进行赋值
	Method.invoke(obj, rs.getObject(columnAliasName));
```
## 11. 数据源与连接池
### 11.1 简介
DataSource用来取代DriverManager来获取Connection；
通过DataSource获得Connection速度很快；
通过DataSource获得的Connection都是已经被包裹过的(不是驱动原来的连接),他的close方法已经被修改。
一般DataSource内部会用一个连接池来缓存Connection,这样可以大幅度提高数据库的访问速度；
连接池可以理解成一个能够存放Connection的Collection；
我们的程序只和DataSource打交道,不会直接访问连接池；
### 11.2 简单数据源和连接池的实现
使用装饰模式的Connection(核心代码)
```java
class MyConnection implements Connection{
	private Connection realConn;
	private LinkedList connPool;
	MyConnection(Connection rConn, LinkedList cPool){
		this.realConn=rConn;
		this.connPool=cPool;
	}
	public void close(){
		this.connPool.addLast(this);
	}
	//….
}
```
DataSource(核心代码)
```java
class MyDataSource implements DataSource{
	private LinkedList connPool = new Vector();
	public Connection getConneciton (){
		if(this.connPool.size()>0)
			return this.connPool.removeFirst(0);
		return createConnection();
	}
	private Connection createConnection(){
	  Connection realConn = DriverManager.getConnection();
	  Connection myConn = 
		new MyConnection(realConn,this.connPool);
	  return myConn;
	}
	//….
}
```
### 11.3 常用的开源实现DBCP
使用DBCP必须用的三个包：
​	commons-dbcp-1.2.1.jar, commons-pool-1.2.jar, commons-collections-3.1.jar；
配置参数：
jdbc.properties
```java
#连接设置
driverClassName=com.mysql.jdbc.Driver
url=jdbc:mysql://localhost:3306/jdbc
username=root
password=root

#<!-- 初始化连接 -->
initialSize=10

#最大连接数量
maxActive=50

#<!-- 最大空闲连接 -->
maxIdle=20

#<!-- 最小空闲连接 -->
minIdle=5

#<!-- 超时等待时间以毫秒为单位 6000毫秒/1000等于60秒 -->
maxWait=60000


#JDBC驱动建立连接时附带的连接属性属性的格式必须为这样：[属性名=property;] 
#注意："user" 与 "password" 两个属性会被明确地传递,因此这里不需要包含他们。
connectionProperties=useUnicode=true;characterEncoding=gbk

#指定由连接池所创建的连接的自动提交(auto-commit)状态。
defaultAutoCommit=true

#driver default 指定由连接池所创建的连接的只读(read-only)状态。
#如果没有设置该值,则“setReadOnly”方法将不被调用。(某些驱动并不支持只读模式,如：Informix)
defaultReadOnly=

#driver default 指定由连接池所创建的连接的事务级别(TransactionIsolation)。
#可用值为下列之一：(详情可见javadoc。)NONE,READ_UNCOMMITTED, READ_COMMITTED, REPEATABLE_READ, SERIALIZABLE
defaultTransactionIsolation=READ_UNCOMMITTED
```
代码中读取配置信息
```java
Properties properties= new Properties();
ppt.load(ClassLoader.getSystemResourceAsStream("jdbc.properties"));
DataSource dataSource = BasicDataSourceFactory.createDataSource(properties)； 
Connection conn = dataSource.getConnection();
```
## 13. Spring的JDBC工具
### 13.1 JdbcTemplate
查询带有参数,和行映射方法：
```java
public Object queryForObject(String sql, Object[] args, RowMapper rowMapper),使用自定义的UserRowMapper完成映射。
一个RowMapper的常用实现BeanPropertyRowMapper,该实现可将结果集转换成一个Java Bean(字段名与Java Bean属性名不符合规范,可用别名处理)。
public List query(String sql, Object[] args, RowMapper rowMapper)返回多个结果。
public int queryForInt(String sql)(如:select count(*) from user),其他结果比如String可用queryForObject方法向下转型。
public Map queryForMap(String sql, Object[] args)返回若类型的Map(key：字段名或别名,value：列值)。
public List queryForList(String sql, Object[] args)返回多Map。
```
更新：
```java
public int update(String sql, Object[] args)。
```
插入数据并获得结果：
```java
public Object execute(ConnectionCallback action)
```
### 13.2 NamedParamterJdbcTemplate
```java
NamedParameterJdbcTemplate内部包含了一个JdbcTemplate,所以JdbcTemplate能做的事情NamedParameterJdbcTemplate都能干； 
NamedParameterJdbcTemplate相对于JdbcTemplate主要增加了参数可以命名的功能。
public Object queryForObject(String sql, Map paramMap, RowMapper rowMapper)
public Object queryForObject(String sql, SqlParameterSource paramSource, RowMapper rowMapper)
	SqlParameterSource的两个主要实现MapSqlParameterSource
	和BeanPropertySqlParameterSource
public int update(String sql, SqlParameterSource paramSource, KeyHolder generatedKeyHolder)保存数据获得主键。
```
### 13.3 SimpleJdbcTemplate
```java
SimpleJdbcTemplate内部包含了一个NamedParameterJdbcTemplate;
所以NamedParameterJdbcTemplate能做的事情SimpleJdbcTemplate都能干,SimpleJdbcTemplate相对于NamedParameterJdbcTemplate主要增加了JDK5.0的泛型和可变长度参数支持。
public <T> List<T> query(String sql, ParameterizedRowMapper<T> rm, Object... args)
public <T> T queryForObject(String sql, ParameterizedRowMapper<T> rm, SqlParameterSource args)
public <T> List<T> query(String sql, ParameterizedRowMapper<T> rm, SqlParameterSource args)
getJdbcOperations返回的是JdbcOperations(实现JdbcTemplate)
getNamedParameterJdbcOperations返回的是NamedParameterJdbcOperations(实现是NamedParameterJdbcTemplate)
```