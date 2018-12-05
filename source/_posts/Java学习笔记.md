---
title: Java学习笔记
date: 2018-12-05 16:18:01
tags: 学习笔记
---

# 计算机的基础知识

## 1. 计算机概述(了解)
```java
(1)计算机
(2)计算机硬件
(3)计算机软件
	系统软件：window,linux,mac
	应用软件：qq,yy,飞秋
(4)软件开发(理解)
	软件：是由数据和指令组成的。(计算器)
	开发：就是把软件做出来。
	如何实现软件开发呢?
		就是使用开发工具和计算机语言做出东西来
(5)语言
	自然语言：人与人交流沟通的
	计算机语言：人与计算机交流沟通的
		C,C++,C#,Java
(6)人机交换
	图形界面：操作方便只管
	DOS命令：需要记忆一些常见的命令
```
## 2. 键盘功能键的认识和快捷键(掌握)
```java
(1)功能键的认识
	tab
	shift
	ctrl
	alt
	windos
	空格
	上下左右
	回车
	截图
(2)快捷键
	全选	Ctrl+A
	复制	Ctrl+C
	粘贴	Ctrl+V
	剪切	Ctrl+X
	撤销	Ctrl+Z
	保存	Ctrl+S
```

## 3. 常见的DOS命令(掌握)
```java
(1)常见的如下
	盘符的切换
		d:回车
	目录的进入
		cd javase
		cd javase\day01\code
	目录的回退
		cd..
		cd\
	清屏
		cls
	退出
		exit
(2)其他的几个(了解)
	创建目录
		mkdir
	删除目录
		rmdir
	创建文件
		edit
	删除文件
		del
	显示目录下的内容
		dir
	删除带内容的目录
		rd /s/q
```
## 4. Java语言概述(了解)
```java
(1)Java语言的发展史
	Java之父
	JDK1.4.2
	JDK5
	JDK7
(2)Java语言的特点
	有很多小特点，重点有两个开源，跨平台
(3)Java语言是跨平台的，请问是如何保证的呢?(理解)
	我们是通过翻译的案例讲解的。
	
	针对不同的操作系统，提供不同的jvm来实现的。
(4)Java语言的平台
	JavaSE
	JavaME--Android
	JavaEE
```
## 5. JDK,JRE,JVM的作用及关系(掌握)
```java
(1)作用
	JVM：保证Java语言跨平台
	JRE：Java程序的运行环境
	JDK：Java程序的开发环境
(2)关系
	JDK：JRE+工具
	JRE：JVM+类库
```
## 6. JDK的下载,安装,卸载(掌握)
```java
(1)下载到官网。
	A:也可以到百度搜索即可。
	B:我给你。
(2)安装
	A:绿色版	解压就可以使用
	B:安装版	必须一步一步的安装，一般只要会点击下一步即可
	
	注意：
		建议所有跟开发相关的软件都不要安装在有中文或者空格的目录下。
(3)卸载
	A:绿色版	直接删除文件夹
	B:安装版	
		a:控制面板 -- 添加删除程序
		b:通过专业的软件卸载工具。(比如360的软件管家卸载)
```
## 7. 第一个程序：HelloWorld案例(掌握)
```java
class HelloWorld {
	public static void main(String[] args) {
		System.out.println("HelloWorld");
	}
}

(1)程序解释：
	A:Java程序的最基本单位是类，所以我们要定义一个类。
		格式：class 类名
		举例：class HelloWorld
	B:在类中写内容的时候，用大括号括起来。
	C:Java程序要想执行，必须有main方法。
		格式：public static void main(String[] args)
	D:要指向哪些东西呢，也用大括号括起来。
	E:你要做什么呢?今天我们仅仅做了一个简单的输出
		格式：System.out.println("HelloWorld");
		注意：""里面的内容是可以改动的。

(2)Java程序的开发执行流程：
	A:编写java源程序(.java)
	B:通过javac命令编译生成.class文件
	C:通过java命令运行.class文件
```
## 8. 常见的问题(掌握)
```java
(1)扩展名被隐藏
	如何找到：工具--文件夹选项--查看--去除隐藏扩展名的那个勾勾
(2)我要求文件名称和类名一致。
	实际上不这样做也是可以的。
	但是，注意：
		javac后面跟的是文件名+扩展名
		java后面跟的类名不带扩展名
(3)Java语言严格区分大小写，请注意。
	 还有就是单词不要写错了。
(4)见到非法字符: \65307肯定是中文问题。
	我们写程序要求标点符号必须全部是英文状态。
(5)括号的配对问题。
	一般来说，括号都是成对出现的。
(6)遇到
	在类 HelloWorld 中找不到主方法, 请将主方法定义为
	public static void main(String[] args)
	肯定是主方法的格式问题。
```
## 9. path环境变量(掌握)
```java
(1)path环境变量的作用
	保证javac命令可以在任意目录下运行。
	同理可以配置qq等
(2)path配置的两种方案：
	A:方案1(了解)
	B:方案2
		找到环境变量的位置，在系统变量里面
		新建：
			变量名：JAVA_HOME
			变量值：D:\develop\Java\jdk1.7.0_60
		修改：
			变量名：Path
			变量值：%JAVA_HOME%\bin;以前的内容
```
## 10. classpath环境变量(理解)
```java
(1)classpath环境变量的作用
	保证class文件可以在任意目录下运行
(2)classpath环境变量的配置
	找到环境变量的位置，在系统变量里面
	新建：
		变量名：classpath
		变量值：E:\JavaSE\day01\code\HelloWorld案例
```
# Java语言基础

## 1. 关键字(掌握)
```java
(1)被Java语言赋予特定含义的单词
(2)特点：
	全部小写。
(3)注意事项：
	A:goto和const作为保留字存在。
	B:类似于Notepad++这样的高级记事本会对关键字有特殊颜色标记
```
## 2. 标识符(掌握)
```java
(1)就是给类，接口，方法，变量等起名字的字符序列
(2)组成规则：
	A:英文大小写字母
	B:数字
	C:$和_
(3)注意事项：
	A:不能以数字开头
	B:不能是java中的关键字
	C:区分大小写
(4)常见的命名规则(见名知意)
	A:包	全部小写
		单级包：小写
			举例：liuyi,com
		多级包：小写，并用.隔开
			举例：cn.itcast,com.baidu				
	B:类或者接口
		一个单词：首字母大写
			举例：Student,Demo
		多个单词：每个单词首字母大写
			举例：HelloWorld,StudentName
	C:方法或者变量
		一个单词：首字母小写
			举例：name,main
		多个单词：从第二个单词开始，每个单词首字母大写
			举例：studentAge,showAllNames()
	D:常量
		全部大写
		一个单词：大写
			举例：PI
		多个单词：大写，并用_隔开
			举例：STUDENT_MAX_AGE
```
## 3. 注释(掌握)
```java
(1)就是对程序进行解释说明的文字
(2)分类：
	A:单行注释	//
	B:多行注释	/**/
	C:文档注释(后面讲) /** */
(3)把HelloWorld案例写了一个带注释的版本。
	后面我们要写一个程序的过程。
	需求：
	分析：
	实现：
	代码体现：
(4)注释的作用
	A:解释说明程序，提高了代码的阅读性。
	B:可以帮助我们调试程序。
		后面我们会讲解一个更高端的一个调试工具
```

## 4. 常量(掌握)
```java
(1)在程序执行的过程中，其值不发生改变的量
(2)分类：
	A:字面值常量
	B:自定义常量(后面讲)
(3)字面值常量
	A:字符串常量 "hello"
	B:整数常量	12,23
	C:小数常量	12.345
	D:字符常量	'a','A','0'
	E:布尔常量	true,false
	F:空常量	null(后面讲)
(4)在Java中针对整数常量提供了四种表现形式
	A:二进制	由0，1组成。以0b开头。
	B:八进制	由0，1，...7组成。以0开头。
	C:十进制	由0，1，...9组成。整数默认是十进制。
	D:十六进制	由0，1，...9,a,b,c,d,e,f(大小写均可)组成。以0x开头。
```
## 5. 进制转换(了解)
```java
(1)其他进制到十进制
	系数：就是每一个位上的数值
	基数：x进制的基数就是x
	权：对每一个位上的数据，从右，并且从0开始编号，对应的编号就是该数据的权。
	
	结果：系数*基数^权次幂之和。
(2)十进制到其他进制
	除基取余，直到商为0，余数反转。
(3)进制转换的快速转换法
	A:十进制和二进制间的转换
		8421码。
	B:二进制到八进制，十六进制的转换
```
## 6. 变量(掌握)
```java
(1)在程序的执行过程中，其值在某个范围内可以发生改变的量
(2)变量的定义格式：
	A:数据类型 变量名 = 初始化值;
	B:数据类型 变量名;
	  变量名 = 初始化值;
```
## 7. 数据类型(掌握)

	(1)Java是一种强类型语言，针对每种数据都提供了对应的数据类型。
	(2)分类：
		A:基本数据类型：4类8种
		B:引用数据类型：类，接口，数组。
	(3)基本数据类型
		A:整数			占用字节数
			byte			1
			short			2
			int 			4
			long			8
		B:浮点数
			float			4
			double			8
		C:字符
			char			2
		D:布尔
			boolean			1
			
		注意：
			整数默认是int类型，浮点数默认是double。
			
			长整数要加L或者l。
			单精度的浮点数要加F或者f。


## 8. 数据类型转换(掌握)

	(1)boolean类型不参与转换
	(2)默认转换
		A:从小到大
		B:byte,short,char -- int -- long -- float -- double
		C:byte,short,char之间不相互转换，直接转成int类型参与运算。
	(3)强制转换
		A:从大到小
		B:可能会有精度的损失，一般不建议这样使用。
		C:格式：
			目标数据类型 变量名 = (目标数据类型) (被转换的数据);
	(4)思考题和面试题：
		A:下面两种方式有区别吗?
			
			float f1 = 12.345f;//本来就是float
			float f2 = (float)12.345;//double转float
	
		B:下面的程序有问题吗，如果有，在哪里呢?
			
			byte b1 = 3;
			byte b2 = 4;
			byte b3 = b1 + b2;//b1+b2是int,需要强转(byte)(b1 + b2)
			byte b4 = 3 + 4;//会先判断3+4的值是否在byte区间内,区间内就没问题
	
		C:下面的操作结果是什么呢?
			byte b = (byte)130;//-126
			
		D:字符参与运算
			是查找ASCII里面的值
			'a'		97
			'A'		65
			'0'		48
	
			System.out.println('a');//a
			System.out.println('a' + 1);//98
	
		E:字符串参与运算
			这里其实是字符串的连接		
	
			System.out.println("hello"+'a'+1);//helloa1
			System.out.println('a'+1+"hello");//98hello
			System.out.println("5+5="+5+5);//5+5=55
			System.out.println(5+5+"=5+5");//10=5+5

## 1. 运算符(掌握)

	(1)算术运算符
		A:+,-,*,/,%,++,--
		B:+的用法
			a:加法
			b:正号
			c:字符串连接符
		C:/和%的区别
			数据做除法操作的时候，/取得是商，%取得是余数
		D:++和--的用法
			a:他们的作用是自增或者自减
			b:使用
				**单独使用
					放在操作数据的前面和后面效果一样。
					a++或者++a效果一样。
				**参与操作使用
					放在操作数的前面：先自增或者自减，再参与操作
						int a = 10;
						int b = ++a;
					放在操作数的后面：先参与操作，再自增或者自减
						int a = 10;
						int b = a++;
	(2)赋值运算符
		A:=,+=,-=,*=,/=,%=等
		B:=叫做赋值运算符，也是最基本的赋值运算符
			int x = 10; 把10赋值给int类型的变量x。
		C:扩展的赋值运算符的特点
			隐含了自动强制转换。
			
	面试题：
	
	short s = 1;
	s = s + 1;//有问题,需要强转(short)(s + 1)
	
	short s = 1;
	s += 1;//没问题,隐含了自动强制转换
	
	请问上面的代码哪个有问题?
	
	(3)比较运算符
		A:==,!=,>,>=,<,<=
		B:无论运算符两端简单还是复杂最终结果是boolean类型。
		C:千万不要把==写成了=
	(4)逻辑运算符
		A:&,|,^,!,&&,||
		B:逻辑运算符用于连接boolean类型的式子
		C:结论
			&:有false则false
			|:有true则true
			^:相同则false，不同则true。
				情侣关系。
			!:非true则false，非false则true
			
			&&:结果和&是一样的，只不过有短路效果。左边是false，右边不执行。
			||:结果和|是一样的，只不过有短路效果。左边是true，右边不执行。
	(5)位运算符(了解)
		A:^的特殊用法
			一个数据针对另一个数据位异或两次，该数不变
		B:面试题
			a:请实现两个变量的交换
				**采用第三方变量
				**用位异或运算符
					左边a,b,a
					右边a^b
			b:请用最有效率的方式计算出2乘以8的结果
				2<<3
	(6)三元运算符
		A:格式
			比较表达式?表达式1:表达式2;
		B:执行流程：
			首先计算比较表达式的值，看是true还是false。
			如果是true，表达式1就是结果。
			如果是false，表达式2就是结果。
		C:案例：
			a:比较两个数据是否相等
				System.out.println(a == b ? true : false);
			b:获取两个数据中的最大值
				System.out.println(a > b ? a : b);
			c:获取三个数据中的最大值
				System.out.println((a>b?a:b)>c?(a>b?a:b):c);
## 2. 键盘录入(掌握)

	(1)实际开发中，数据是变化的，为了提高程序的灵活性，我们加入键盘录入数据。
	(2)如何实现呢?目前就记住
		A:导包
			import java.util.Scanner;
			位置：在class的上边
		B:创建对象
			Scanner sc = new Scanner(System.in);
		C:获取数据
			int x = sc.nextInt();
	(3)把三元运算符的案例加入键盘录入改进。
		Scanner sc = new Scanner(System.in);
	    int a = sc.nextInt();
	    int b = sc.nextInt();
	    System.out.println(a > b ? a : b);

## 3. 流程控制语句

	(1)顺序结构 从上往下，依次执行
	(2)选择结构	按照不同的选择，执行不同的代码
	(3)循环结构 做一些重复的代码


## 4. if语句(掌握)

	(1)三种格式
		A:格式1
			if(比较表达式) {
				语句体;
			}
			
			执行流程：
				判断比较表达式的值，看是true还是false
				如果是true，就执行语句体
				如果是false，就不执行语句体
		
		B:格式2
			if(比较表达式) {
				语句体1;
			}else {
				语句体2;
			}
			
			执行流程：
				判断比较表达式的值，看是true还是false
				如果是true，就执行语句体1
				如果是false，就执行语句体2
				
		C:格式3
			if(比较表达式1) {
				语句体1;
			}else if(比较表达式2){
				语句体2;
			}
			...
			else {
				语句体n+1;
			}
			
			执行流程：
				判断比较表达式1的值，看是true还是false
				如果是true，就执行语句体1
				如果是false，就继续判断比较表达式2的值，看是true还是false
				如果是true，就执行语句体2
				如果是false，就继续判断比较表达式3的值，看是true还是false
				...
				如果都不满足，就执行语句体n+1
	(2)注意事项
		A:比较表达式无论简单还是复杂，结果是boolean类型
		B:if语句控制的语句体如果是一条语句，是可以省略大括号的；如果是多条，不能省略。
			建议：永远不要省略。
		C:一般来说，有左大括号，就没有分号，有分号，就没有左大括号。
		D:else后面如果没有if，是不会出现比较表达式的。
		E:三种if语句其实都是一个语句，只要有一个执行，其他的就不再执行。
	(3)案例：
		A:比较两个数是否相等
			
			if (a == b) {
			    System.out.println("a == b");
		    }
	
		B:获取两个数中的最大值
			
			if (a > b) {
	            System.out.println(a);
		    } else if (a < b) {
		        System.out.println(b);
		    }
	
		C:获取三个数中的最大值(if语句的嵌套)
			if (a > b) {
	            if (a > c) {
	                System.out.println(a);
	            } else if (c > a) {
	                System.out.println(c);
	            } else if (b > a) {
		            if (b > c) {
		                System.out.println(b);
		            } else if (c > b) {
		                System.out.println(c);
		            }
		        }
	
		D:根据成绩输出对应的等级
			if (score > 0 && score < 60) {
	            System.out.println("不及格");
	        } else if (score >= 60 && score < 90) {
	            System.out.println("合格");
	        } else if (score >= 90 && score <= 100) {
	            System.out.println("优秀");
	        }
		E:根据月份，输出对应的季节
		F:根据x计算对应y的值并输出
	(4)三元运算符和if语句第二种格式的关系
		所有的三元运算符能够实现的，if语句的第二种格式都能实现。
		反之不成立。
		
		如果if语句第二种格式控制的语句体是输出语句，就不可以。
		因为三元运算符是一个运算符，必须要有一个结果返回，不能是一个输出语句。

## 1. switch语句(掌握)

	(1)格式：
		switch(表达式) {
			case 值1:
				语句体1;
				break;
			case 值2:
				语句体2;
				break;
			...
			default:
				语句体n+1;
				break;
		}
		
		格式解释说明：
			switch:说明这是switch语句。
			表达式:可以是byte,short,int,char
				JDK5以后可以是枚举
				JDK7以后可以是字符串
			case:后面的值就是要和表达式进行比较的值
			break:表示程序到这里中断，跳出switch语句
			default:如果所有的情况都不匹配,就执行这里,相当于if语句中的else
	(2)面试题
		switch语句的表达式可以是byte吗?可以是long吗?可以是String吗?
			可以,不可以,JDK7以后可以
	(3)执行流程:
		A:首先计算表达式的值
		B:和每一个case进行匹配，如果有就执行对应的语句体，看到break就结束。
		C:如果没有匹配，就执行default的语句体n+1。
	(4)注意事项:
		A:case后面只能是常量，不能是变量，而且，多个case后面的值不能出现相同的
		B:default可以省略吗?
			可以省略，但是不建议，因为它的作用是对不正确的情况给出提示。
			特殊情况：
				case就可以把值固定。
				A,B,C,D
		C:break可以省略吗?
			可以省略，但是结果可能不是我们想要的。
			会出现一个现象：case穿透。
			最终我们建议不要省略
		D:default一定要在最后吗?
			不是，可以在任意位置。但是建议在最后。
		E:switch语句的结束条件
			a:遇到break就结束了
			b:执行到末尾就结束了
	(5)案例：
		A:键盘录入一个数字(1-7),输出对应的星期几。
			Scanner sc = new Scanner(System.in);
	
		        switch (sc.nextInt()) {
	            case ## 1. 
	                System.out.println("Monday");
	                break;
	            case ## 2. 
	                System.out.println("Tuesday");
	                break;
	            case ## 3. 
	                System.out.println("Wednesday");
	                break;
	            case ## 4. 
	                System.out.println("Thursday");
	                break;
	            case ## 5. 
	                System.out.println("Friday");
	                break;
	            case ## 6. 
	                System.out.println("Saturday");
	                break;
	            case ## 7. 
	                System.out.println("Sunday");
	                break;
	            default:
	                System.out.println("wrong");
	        }
		B:单项选择题
		C:键盘录入一个字符串的问题
			String s = sc.nextLine();
		D:根据给定的月份,输出对应的季节
	(6)if语句和switch语句各自的场景
		A:if
			针对boolean类型的判断
			针对一个范围的判断
			针对几个常量的判断
		B:switch
			针对几个常量的判断


## 2. 循环语句(掌握)

	(1)有三种:for,while,do...while
	(2)for循环语句
		A:格式
			for(初始化语句;判断条件语句;控制条件语句){
				循环体语句;
			}
			
			执行流程：
				a:执行初始化语句
				b:执行判断条件语句
					如果这里是true，就继续
					如果这里是false，循环就结束
				c:执行循环体语句
				d:执行控制条件语句
				e:回到b
		B:注意事项
			a:判断条件语句无论简单还是复杂，结果是boolean类型
			b:循环体语句如果是一条，可以省略大括号，但是不建议
			c:有分号就没有左大括号，有左大括号就没有分号
		C:案例
			a:输出10次HelloWorld
				for (int i = 0; i < 10; i++) {
		            System.out.println("HelloWorld");
		        }
			b:输出1-10的数据
				for (int i = 1; i < 11; i++) {
		            System.out.println(i);
		        }
			c:输出10-1的数据
				for (int i = 10; i > 0; i--) {
		            System.out.println(i);
		        }
			d:求1-10的和
				int sum = 0;
		        for (int i = 1; i < 11; i++) {
		            sum += i;
		        }
		        System.out.println(sum);
			e:求1-100的和,求1-100的偶数和,求1-100的奇数和
				int sum = 0;
		        int oddSum = 0;
		        int evenSum = 0;
		
		        for (int i = 1; i < 101; i++) {
		            sum += i;
		        }
		        System.out.println("sum:" + sum);
		
		        for (int i = 1; i < 101; i+=2) {
		            oddSum += i;
		        }
		        System.out.println("oddSum:" + oddSum);
		
		        for (int i = 2; i < 101; i+=2) {
		            evenSum += i;
		        }
		        System.out.println("evenSum:" + evenSum);
			f:求5的阶乘
				int sum = 1;
		        for (int i = 5; i > 0; i--) {
		            sum *= i;
		        }
		        System.out.println(sum);
			g:在控制台打印水仙花数(个位,十位,百位的立方和等于该数)
				for (int i = 100; i < 1000; i++) {
		            int ge = i % 10;
		            int shi = i / 10 % 10;
		            int bai = i / 100 % 10;		
		            if (Math.pow(ge, 3) + Math.pow(shi, 3) + Math.pow(bai, 3) == i) {
		                System.out.println(i);
		            }
		        }
			h:统计水仙花个数
				int flag = 0;
		        for (int i = 100; i < 1000; i++) {
		            int ge = i % 10;
		            int shi = i / 10 % 10;
		            int bai = i / 100 % 10;
		            if (Math.pow(ge, 3) + Math.pow(shi, 3) + Math.pow(bai, 3) == i) {
		                flag++;
		            }
		        }
		        System.out.println(flag);
			i:改进版的回文数
				一个五位数
				个位 = 万位
				十位 = 千位
				个位 + 十位 + 千位 + 万位 = 百位
				for (int i = 10000; i < 100000; i++) {
		            int ge = i % 10;
		            int shi = i / 10 %10;
		            int bai = i / 100 % 10;
		            int qian = i /1000 % 10;
		            int wan = i / 10000 % 10;
		            if (ge == wan && shi == qian && (ge + shi + qian + wan) == bai) {
		                System.out.println(i);
		            }
		        }
			j:统计1-1000之间同时满足如下条件的数据有多少个
				x%3==2
				x%5==3
				x%7==2
				int flag = 0;
		        for (int i = 1; i < 1001; i++) {
		            if (i % 3 == 2 && i % 5 == 3 && i % 7 == 2) {
		                flag++;
		            }
		        }
		        System.out.println(flag);
	(3)while循环
		A:基本格式
			while(判断条件语句) {
				循环体语句;
			}
			
			扩展格式：
			初始化语句;
			while(判断条件语句){
				循环体语句;
				控制条件语句;
			}
			
			通过查看这个格式，我们就知道while循环可以和for循环等价转换。
		B:while的练习
			把for语句的练习用while改进
		C:for和while的区别
			a:使用上的区别
				for语句的那个控制条件变量,在循环结束后不能在使用了。
				而while的可以继续使用。
			b:理解上的区别
				for适合于一个范围的判断
				while适合次数不明确的
					举例:吃葡萄
		D:案例：
			a:珠穆朗玛峰问题
			b:小芳存钱问题(break以后才能做)
	(4)do...while循环
		A:基本格式
			do {
				循环体语句;
			}while(判断条件语句);
			
			扩展格式：
			初始化语句;
			do {
				循环体语句;
				控制条件语句;
			}while(判断条件语句);
			
			通过查看格式，我们就可以看出其实三种循环的格式可以是统一的。
		B:三种循环的区别
			a:do...while循环至少执行一次循环体
			b:for和while必须先判断条件是否是true，然后后才能决定是否执行循环体
	(5)循环使用的注意事项(死循环)
		A:一定要注意修改控制条件,否则容易出现死循环。
		B:最简单的死循环格式
			a:while(true){...}
			
			b:for(;;){}

## 3. 控制跳转语句(掌握)

	(1)break:中断的意思
		A:用在循环和switch语句中，离开此应用场景无意义。
		B:作用
			a:跳出单层循环
			b:跳出多层循环，需要标签语句的配合
	(2)continue:继续
		A:用在循环中，离开此应用场景无意义。
		B:作用
			a:跳出单层循环的一次，可以继续下一次
		C:填空题
			for(int x=1; x<=10; x++) {
				if(x%3 == 0) {
					//补齐代码
				}
				System.out.println("Java基础班");
			}
			如何让控制台输出2次：Java基础班
				break;
			如何让控制台输出7次：Java基础班
				continue;
			如何让控制台输出13次：Java基础班
				System.out.println("Java基础班");
	(3)return:返回
		A:用于结束方法的，后面还会在继续讲解和使用。
		B:一旦遇到return,程序就不会在继续往后执行。



## 1. 方法(掌握)

	(1)方法：就是完成特定功能的代码块。
		注意：在很多语言里面有函数的定义，而在Java中，函数被称为方法。
	(2)格式：
		修饰符 返回值类型 方法名(参数类型 参数名1,参数类型 参数名2...) {
			方法体语句;
			return 返回值;
		}


		修饰符：目前就用 public static。后面再详细讲解其他修饰符
		返回值类型：就是功能结果的数据类型
		方法名：就是起了一个名字，方便我们调用该方法。
		参数类型：就是参数的数据类型
		参数名：就是变量
		参数分类：
			实参：实际参与运算的数据
			形参：方法上定义的，用于接收实际参数的变量
		方法体语句：就是完成功能的代码块
		return：结束方法
		返回值：就是功能的结果，由return带给调用者。
	(3)两个明确：
		返回值类型：结果的数据类型
		参数列表：参数的个数及对应的数据类型
	(4)方法调用
		A:有明确返回值的方法
			a:单独调用，没有意义
			b:输出调用，不是很好，因为我可能需要不结果进行进一步的操作。但是讲课一般我就用了。
			c:赋值调用，推荐方案
		B:void类型修饰的方法
			a:单独调用
	(5)案例：
		A:求和方案
			public static void sum(int a, int b) {
		        System.out.println("a + b = " + (a + b));
		    }
		B:获取两个数中的较大值
			public static void max(int a, int b) {
		        if (a > b) {
		            System.out.println(a);
		        } else if (b > a) {
		            System.out.println(b);
		        }
		    }
		C:比较两个数据是否相同
			public static void isEquals(int a, int b) {
		        if (a == b) {
		            System.out.println("a == b");
		        }
		    }
		D:获取三个数中的最大值
			public static void max(int a, int b, int c) {
		        if (a > b) {
		            if (a > c) {
		                System.out.println(a);
		            } else if (c > a) {
		                System.out.println(c);
		            }
		        } else if (b > a) {
		            if (b > c) {
		                System.out.println(b);
		            } else if (c > b) {
		                System.out.println(c);
		            }
		        }
		    }
		E:输出m行n列的星形
			public static void printStar(int row, int column) {
		        for (int m = 0; m < row; m++) {
		            String star = "";
		            for (int n = 0; n < column; n++) {
		                star += "*";
		            }
		            System.out.println(star);
		        }
		        System.out.println("--------------");
		        for (int m = 0; m < row; m++) {
		            String star = "";
		            for (int n = 0; n <= m; n++) {
		                star += "*";
		            }
		            System.out.println(star);
		        }
		        System.out.println("---------------");
		        for (int m = row; m > 0; m--) {
		            String star = "";
		            for (int n = 0; n < m; n++) {
		                star += "*";
		            }
		            System.out.println(star);
		        }
		    }
		F:输出nn乘法表
			public static void chengfabiao(int n) {
		        for (int i = 1; i <= n; i++) {
		            for (int j = 1; j <= i; j++) {
		                System.out.print(j + " * " + i + " = " + (j * i) + "\t");
		            }
		            System.out.println();
		        }
		    }
	(6)方法的注意事项
		A:方法不调用不执行
		B:方法之间是平级关系，不能嵌套定义
		C:方法定义的时候，参数是用，隔开的
		D:方法在调用的时候，不用在传递数据类型
		E:如果方法有明确的返回值类型，就必须有return语句返回。
	(7)方法重载
		在同一个类中，方法名相同，参数列表不同。与返回值无关。
		
		参数列表不同：
			参数的个数不同。
			参数的对应的数据类型不同。
	(8)方法重载案例
		不同的类型的多个同名方法的比较。

## 2. 数组(掌握)

	(1)数组：存储同一种数据类型的多个元素的容器。
	(2)特点：每一个元素都有编号，从0开始，最大编号是长度-1。
	         编号的专业叫法：索引
	(3)定义格式
		A:数据类型[] 数组名;
		B:数据类型 数组名[];
		
		推荐是用A方式，B方法就忘了吧。
		但是要能看懂
	(4)数组的初始化
		A:动态初始化
			只给长度，系统给出默认值
			
			举例：int[] arr = new int[3];
		B:静态初始化
			给出值，系统决定长度
			
			举例：int[] arr = new int[]{1,2,3};
			简化版：int[] arr = {1,2,3};
	(5)Java的内存分配
		A:栈 存储局部变量
		B:堆 存储所有new出来的
		C:方法区(面向对象部分详细讲解)
		D:本地方法区(系统相关)
		E:寄存器(CPU使用)
		
		注意：
			a:局部变量 在方法定义中或者方法声明上定义的变量。
			b:栈内存和堆内存的区别
				栈：数据使用完毕，就消失。
				堆：每一个new出来的东西都有地址
				    每一个变量都有默认值
						byte,short,int,long 0
						float,double 0.0
						char '\u0000'
						boolean false
						引用类型 null
				    数据使用完毕后，在垃圾回收器空闲的时候回收。
	(6)数组内存图
		A:一个数组
		B:二个数组
		C:三个数组(两个栈变量指向同一个堆内存)
	(7)数组的常见操作
		A:遍历
			方式1：
				public static void printArray(int[] arr) {
					for(int x=0; x<arr.length; x++) {
						System.out.println(arr[x]);
					}
				}
				
			方式2：
				public static void printArray(int[] arr) {
					System.out.print("[");
					for(int x=0; x<arr.length; x++) {
						if(x == arr.length-1) {
							System.out.println(arr[x]+"]");
						}else {
							System.out.println(arr[x]+", ");
						}
					}
				}
		B:最值
			最大值：
				public static int getMax(int[] arr) {
					int max = arr[0];
					
					for(int x=1; x<arr.length; x++) {
						if(arr[x] > max) {
							max = arr[x];
						}
					}
					
					return max;
				}
				
			最小值：
				public static int getMin(int[] arr) {
					int min = arr[0];
					
					for(int x=1; x<arr.length; x++) {
						if(arr[x] < min) {
							min = arr[x];
						}
					}
					
					return min;
				}
		C:逆序
			方式1：
				public static void reverse(int[] arr) {
					for(int x=0; x<arr.length/2; x++) {
						int temp = arr[x];
						arr[x] = arr[arr.length-1-x];
						arr[arr.length-1-x] = temp;
					}
				}
				
			方式2：
				public static void reverse(int[] arr) {
					for(int start=0,end=arr.length-1; start<=end; start++,end--) {
						int temp = arr[start];
						arr[start] = arr[end];
						arr[end] = temp;
					}
				}
		D:查表
				public static String getString(String[] strArray,int index) {
					return strArray[index];
				}
		E:基本查找
			方式1：
				public static int getIndex(int[] arr,int value) {
					for(int x=0; x<arr.length; x++) {
						if(arr[x] == value) {
							return x;
						}
					}
					
					return -1;
				}
				
			方式2：
				public static int getIndex(int[] arr,int value) {
					int index = -1;
				
					for(int x=0; x<arr.length; x++) {
						if(arr[x] == value) {
							index = x;
							break;
						}
					}
					
					return index;
				}



# Java面向对象

## 1. 成员变量和局部变量的区别(理解)

	(1)在类中的位置不同
		成员变量：类中方法外
		局部变量：方法定义中或者方法声明上
	(2)在内存中的位置不同
		成员变量：在堆中
		局部变量：在栈中
	(3)生命周期不同
		成员变量：随着对象的创建而存在，随着对象的消失而消失
		局部变量：随着方法的调用而存在，随着方法的调用完毕而消失
	(4)初始化值不同
		成员变量：有默认值
		局部变量：没有默认值，必须定义，赋值，然后才能使用

## 2. 类作为形式参数的问题?(理解)

	(1)如果你看到一个方法需要的参数是一个类名，就应该知道这里实际需要的是一个具体的对象。


## 3. 匿名对象(理解)

	(1)没有名字的对象
	(2)应用场景
		A:调用方法，仅仅只调用一次的时候。
		b:可以作为实际参数传递。

## 4. 封装(理解)

	(1)隐藏实现细节，提供公共的访问方式
	(2)好处：
		A:隐藏实现细节，提供公共的访问方式
		B:提高代码的复用性
		C:提高代码的安全性
	(3)设计原则
		把不想让外界知道的实现细节给隐藏起来，提供公共的访问方式
	(4)private是封装的一种体现。
		封装：类，方法，private修饰成员变量


## 5. private关键字(掌握)

	(1)私有的意义，可以修饰成员变量和成员方法
	(2)特点：
		被private修饰的后的成员只能在本类中被访问
	(3)private的应用：
		以后再写一个类的时候：
			把所有的成员变量给private了
			提供对应的getXxx()/setXxx()方法


## 6. this关键字(掌握)

	(1)代表当前类的引用对象
		记住：哪个对象调用方法，该方法内部的this就代表那个对象
	(2)this的应用场景：
		A:解决了局部变量隐藏成员变量的问题
		B:其实this还有其他的应用，明天讲解。


## 7. 构造方法(掌握)

	(1)作用：用于对对象的数据进行初始化
	(2)格式：
		A:方法名和类名相同
		B:没有返回值类型，连void都不能有
		C:没有返回值
		
		思考题：构造方法中可不可以有return语句呢?
		可以。只要我们写成这个样子就OK了：return;
		其实，在任何的void类型的方法的最后你都可以写上：return;
	(3)构造方法的注意事项
		A:如果我们没写构造方法，系统将提供一个默认的无参构造方法
		B:如果我们给出了构造方法，系统将不再提供默认构造方法
			如果这个时候，我们要使用无参构造方法，就必须自己给出。
			推荐：永远手动自己给出无参构造方法。
	(4)给成员变量赋值的方式
		A:setXxx()
		B:带参构造方法
	(5)标准案例
		class Student {
			private String name;
			private int age;
			
			public Student(){}
			
			public Student(String name,int age) {
				this.name = name;
				this.age = age;
			}
			
			public String getName() {
				return name;
			}
			
			public void setName(String name) {
				this.name = name;
			}
			
			public int getAge() {
				return age;
			}
			
			public void setAge(int age) {
				this.age = age;
			}
		}
		
		测试：
		class StudentDemo {
			public static void main(String[] args) {
				//方式1
				Student s1 = new Student();
				s1.setName("林青霞");
				s1.setAge(27);
				System.out.println(s1.getName()+"---"+s1.getAge());
				
				//方式2
				Student s2 = new Student("刘意",30);
				System.out.println(s2.getName()+"---"+s2.getAge());
			}
		}



## 8. 代码：Student s = new Student();做了哪些事情?(理解)

	(1)把Student.class文件加载到内存
	(2)在栈内存为s开辟空间
	(3)在堆内存为学生对象申请空间
	(4)给学生的成员变量进行默认初始化。null,0
	(5)给学生的成员变量进行显示初始化。林青霞,27
	(6)通过构造方法给成员变量进行初始化。刘意,30
	(7)对象构造完毕，把地址赋值给s变量

## 9. 面向对象的练习题(掌握)

	(1)标准的手机类的定义和测试
	(2)Demo类有求和方法，Test类进行测试。
		什么时候定义成员变量?
		当该变量是用来描述一个类的时候。
	(3)长方形案例
	(4)员工案例
	(5)MyMath案例(自己提供加减乘除并测试)
		public class MyMath {
		    public MyMath() {
		    }
		
		    public static void add(int a, int b) {
		        System.out.println("add" + (a + b));
		    }
		
		    public static void subtract(int a, int b) {
		        System.out.println("subtract" + (a - b));
		    }
		
		    public static void multiply(int a, int b) {
		        System.out.println("multiply" + (a * b));
		    }
		
		    public static void divide(int a, int b) {
		        System.out.println("divide" + (a / b));
		    }
		}

## 10. static关键字(理解)

	(1)静态的意思。可以修饰成员变量和成员方法。
	(2)静态的特点：
		A:随着类的加载而加载
		B:优先于对象存在
		C:被类的所有对象共享
			这其实也是我们判断该不该使用静态的依据。
			举例：饮水机和水杯的问题思考
		D:可以通过类名调用
			既可以通过对象名调用，也可以通过类名调用，建议通过类名调用。
	(3)静态的内存图
		静态的内容在方法区的静态区
	(4)静态的注意事项；
		A:在静态方法中没有this对象
		B:静态只能访问静态(代码测试过)
	(5)静态变量和成员变量的区别
		A:所属不同
			静态变量：属于类，类变量
			成员变量：属于对象，对象变量，实例变量
		B:内存位置不同
			静态变量：方法区的静态区
			成员变量：堆内存
		C:生命周期不同
			静态变量：静态变量是随着类的加载而加载，随着类的消失而消失
			成员变量：成员变量是随着对象的创建而存在，随着对象的消失而消失
		D:调用不同
			静态变量：可以通过对象名调用，也可以通过类名调用
			成员变量：只能通过对象名调用
	(6)main方法是静态的
		public:权限最大
		static:不用创建对象调用
		void:返回值给jvm没有意义
		main:就是一个常见的名称。
		String[] args:可以接收数据，提供程序的灵活性
			格式：java MainDemo hello world java
				  java MainDemo 10 20 30

## 1. 如何制作帮助文档(了解)

	(1)写一个类
	(2)加入文档注释
	(3)通过javadoc工具生成即可
		javadoc -d 目录 -author -version ArrayTool.java


## 2. 通过JDK提供的API学习了Math类(掌握)

	(1)API(Application Programming Interface)
		应用程序编程接口(帮助文档)
	(2)如何使用呢?
		请参照
			day08\code\02_如何使用JDK提供的帮助文档\如何使用帮助文档.txt
	(3)Math类
		A:是针对数学进行操作的类
		B:没有构造方法，因为它的成员都是静态的
		C:产生随机数
			public static double random(): [0.0,1.0)
		D:如何产生一个1-100之间的随机数
			int number = (int)(Math.random()*100)+1;
		E:猜数字小游戏


## 3. 代码块(理解)

	(1)用{}括起来的代码。
	(2)分类：
		A:局部代码块
			用于限定变量的生命周期，及早释放，提高内存利用率。
		B:构造代码块
			把多个构造方法中相同的代码可以放到这里，每个构造方法执行前，首先执行构造代码块。
		C:静态代码块
			对类的数据进行初始化，仅仅只执行一次。
	(3)静态代码块,构造代码块,构造方法的顺序问题?
		静态代码块 > 构造代码块 > 构造方法

## 4. 继承(掌握)

	(1)把多个类中相同的成员给提取出来定义到一个独立的类中。然后让这多个类和该独立的类产生一个关系，
	   这多个类就具备了这些内容。这个关系叫继承。
	(2)Java中如何表示继承呢?格式是什么呢?
		A:用关键字extends表示
		B:格式：
			class 子类名 extends 父类名 {}
	(3)继承的好处：
		A:提高了代码的复用性
		B:提高了代码的维护性
		C:让类与类产生了一个关系，是多态的前提
	(4)继承的弊端：
		A:让类的耦合性增强。这样某个类的改变，就会影响其他和该类相关的类。
			原则：低耦合，高内聚。
			耦合：类与类的关系
			内聚：自己完成某件事情的能力
		B:打破了封装性
	(5)Java中继承的特点
		A:Java中类只支持单继承
		B:Java中可以多层(重)继承(继承体系)
	(6)继承的注意事项：
		A:子类不能继承父类的私有成员
		B:子类不能继承父类的构造方法，但是可以通过super去访问
		C:不要为了部分功能而去继承
	(7)什么时候使用继承呢?
		A:继承体现的是：is a的关系。
		B:采用假设法
	(8)Java继承中的成员关系
		A:成员变量
			a:子类的成员变量名称和父类中的成员变量名称不一样，这个太简单
			b:子类的成员变量名称和父类中的成员变量名称一样，这个怎么访问呢?
				子类的方法访问变量的查找顺序：
					在子类方法的局部范围找，有就使用。
					在子类的成员范围找，有就使用。
					在父类的成员范围找，有就使用。
					找不到，就报错。
		B:构造方法
			a:子类的构造方法默认会去访问父类的无参构造方法
				是为了子类访问父类数据的初始化
			b:父类中如果没有无参构造方法，怎么办?
				子类通过super去明确调用带参构造
				子类通过this调用本身的其他构造，但是一定会有一个去访问了父类的构造
				让父类提供无参构造
		C:成员方法
			a:子类的成员方法和父类中的成员方法名称不一样，这个太简单
			b:子类的成员方法和父类中的成员方法名称一样，这个怎么访问呢?
				通过子类对象访问一个方法的查找顺序：
					在子类中找，有就使用
					在父类中找，有就使用
					找不到，就报错
	(9)两个面试题：
		A:Override和Overload的区别?Overload是否可以改变返回值类型?
		B:this和super的区别和各自的作用?
	(10)数据初始化的面试题
		A:一个类的初始化过程
		B:子父类的构造执行过程
		C:分层初始化
	(11)案例：
		A:学生和老师案例
			继承前
			继承后
		B:猫狗案例的分析和实现

## 1. final关键字(掌握)

	(1)是最终的意思，可以修饰类，方法，变量。
	(2)特点：
		A:它修饰的类，不能被继承。
		B:它修饰的方法，不能被重写。
		C:它修饰的变量，是一个常量。
	(3)面试相关：
		A:局部变量
			a:基本类型 值不能发生改变
			b:引用类型 地址值不能发生改变，但是对象的内容是可以改变的
		B:初始化时机
			a:只能初始化一次。
			b:常见的给值
				定义的时候。(推荐)
				构造方法中。

## 2. 多态(掌握)

	(1)同一个对象在不同时刻体现出来的不同状态。
	(2)多态的前提：
		A:有继承或者实现关系。
		B:有方法重写。
		C:有父类或者父接口引用指向子类对象。
		
		多态的分类：
			a:具体类多态
				class Fu {}
				class Zi extends Fu {}
				
				Fu f = new Zi();
			b:抽象类多态
				abstract class Fu {}
				class Zi extends Fu {}
				
				Fu f = new Zi();
			c:接口多态
				interface Fu {}
				class Zi implements Fu {}
				
				Fu f = new Zi();
	(3)多态中的成员访问特点
		A:成员变量
			编译看左边，运行看左边
		B:构造方法
			子类的构造都会默认访问父类构造
		C:成员方法
			编译看左边，运行看右边
		D:静态方法
			编译看左边，运行看左边
			
		为什么?
			因为成员方法有重写。
	(4)多态的好处：
		A:提高代码的维护性(继承体现)
		B:提高代码的扩展性(多态体现)
	(5)多态的弊端：
		父不能使用子的特有功能。
		
		现象：
			子可以当作父使用，父不能当作子使用。
	(6)多态中的转型
		A:向上转型
			从子到父
		B:向下转型
			从父到子
	(7)孔子装爹的案例帮助大家理解多态
	(8)多态的练习
		A:猫狗案例
		B:老师和学生案例


## 3. 抽象类(掌握)

	(1)把多个共性的东西提取到一个类中，这是继承的做法。
	   但是呢，这多个共性的东西，在有些时候，方法声明一样，但是方法体。
	   也就是说，方法声明一样，但是每个具体的对象在具体实现的时候内容不一样。
	   所以，我们在定义这些共性的方法的时候，就不能给出具体的方法体。
	   而一个没有具体的方法体的方法是抽象的方法。
	   在一个类中如果有抽象方法，该类必须定义为抽象类。
	(2)抽象类的特点
		A:抽象类和抽象方法必须用关键字abstract修饰
		B:抽象类中不一定有抽象方法,但是有抽象方法的类一定是抽象类
		C:抽象类不能实例化
		D:抽象类的子类
			a:是一个抽象类。
			b:是一个具体类。这个类必须重写抽象类中的所有抽象方法。
	(3)抽象类的成员特点：
		A:成员变量
			有变量，有常量
		B:构造方法
			有构造方法
		C:成员方法
			有抽象，有非抽象
	(4)抽象类的练习
		A:猫狗案例练习
		B:老师案例练习
		C:学生案例练习
		D:员工案例练习
	(5)抽象类的几个小问题
		A:抽象类有构造方法，不能实例化，那么构造方法有什么用?
			用于子类访问父类数据的初始化
		B:一个类如果没有抽象方法,却定义为了抽象类，有什么用?
			为了不让创建对象
		C:abstract不能和哪些关键字共存
			a:final	冲突
			b:private 冲突
			c:static 无意义


## 4. 接口(掌握)

	(1)回顾猫狗案例，它们仅仅提供一些基本功能。
	   比如：猫钻火圈，狗跳高等功能，不是动物本身就具备的，
	   是在后面的培养中训练出来的，这种额外的功能，java提供了接口表示。
	(2)接口的特点：
		A:接口用关键字interface修饰
			interface 接口名 {}
		B:类实现接口用implements修饰
			class 类名 implements 接口名 {}
		C:接口不能实例化
		D:接口的实现类
			a:是一个抽象类。
			b:是一个具体类，这个类必须重写接口中的所有抽象方法。
	(3)接口的成员特点：
		A:成员变量
			只能是常量
			默认修饰符：public static final
		B:构造方法
			没有构造方法
		C:成员方法
			只能是抽象的
			默认修饰符：public abstract
	(4)类与类,类与接口,接口与接口
		A:类与类
			继承关系，只能单继承，可以多层继承
		B:类与接口
			实现关系，可以单实现，也可以多实现。
			还可以在继承一个类的同时，实现多个接口
		C:接口与接口
			继承关系，可以单继承，也可以多继承
	(5)抽象类和接口的区别(自己补齐)?
		A:成员区别
			抽象类：可以是变量可以是常量
			接口：只能是常量
		B:关系区别:
			类与类：继承
			类与接口：实现
			接口与接口：继承
		C:设计理念不同
			抽象类：is a，抽象类中定义的是共性功能。
			接口：like a，接口中定义的是扩展功能。
	(6)练习：
		A:猫狗案例，加入跳高功能
		B:老师和学生案例，加入抽烟功能0



## 1. 形式参数和返回值的问题(理解)

	(1)形式参数：
		类名：需要该类的对象
		抽象类名：需要该类的子类对象
		接口名：需要该接口的实现类对象
	(2)返回值类型：
		类名：返回的是该类的对象
		抽象类名：返回的是该类的子类对象
		接口名：返回的是该接口的实现类的对象
	(3)链式编程
		对象.方法1().方法2().......方法n();
		
		这种用法：其实在方法1()调用完毕后，应该一个对象；
			      方法2()调用完毕后，应该返回一个对象。
				  方法n()调用完毕后，可能是对象，也可以不是对象。


## 2. 包(理解)

	(1)其实就是文件夹
	(2)作用：
		A:区分同名的类
		B:对类进行分类管理
			a:按照功能分
			b:按照模块分
	(3)包的定义(掌握)
		package 包名;
		多级包用.分开。
	(4)注意事项：(掌握)
		A:package语句必须在文件中的第一条有效语句
		B:在一个java文件中，只能有一个package
		C:如果没有package，默认就是无包名
	(5)带包的编译和运行
		A:手动式
		B:自动式(掌握)
			javac -d . HelloWorld.java

## 3. 导包(掌握)

	(1)我们多次使用一个带包的类，非常的麻烦，这个时候，Java就提供了一个关键字import。
	(2)格式：
		import 包名...类名;
		另一种：
			import 包名...*;(不建议)
	(3)package,import,class的顺序
		package > import > class

## 4. 权限修饰符(掌握)

	(1)权限修饰符
					本类	同一个包下	不同包下的子类	不同包下的无关类
		private		Y
			默认		Y		Y
		protected	Y		Y			 Y
		public		Y		Y			 Y				  Y
	(2)这四种权限修饰符在任意时刻只能出现一种。
		public class Demo {}		


## 5. 常见的修饰符(理解)

	(1)分类：
		权限修饰符：private,默认,protected,public
		状态修饰符：static,final
		抽象修饰符：abstract
	(2)常见的类及其组成的修饰
		类：
			默认,public,final,abstract
			常用的：public
		成员变量：
			private,默认,protected,public,static,final
			常用的：private
		构造方法：
			private,默认,protected,public
			常用的：public
		成员方法：
			private,默认,protected,public,static,final,abstract
			常用的：public
	(3)另外比较常见的：
		public static final int X = 10;
		public static void show() {}
		public final void show() {}
		public abstract void show();


## 6. 内部类(理解)

	(1)把类定义在另一个类的内部，该类就被称为内部类。
		举例：把类B定义在类A中，类B就被称为内部类。
	(2)内部类的访问规则
		A:可以直接访问外部类的成员，包括私有
		B:外部类要想访问内部类成员，必须创建对象
	(3)内部类的分类
		A:成员内部类
		B:局部内部类
	(4)成员内部类
		A:private 为了数据的安全性
		B:static 为了访问的方便性		
	成员内部类不是静态的：
		外部类名.内部类名 对象名 = new 外部类名.new 内部类名();
	成员内部类是静态的：
		外部类名.内部类名 对象名 = new 外部类名.内部类名();
(5)成员内部类的面试题(填空)

	30,20,10
	class Outer {
		public int num = 10;
			class Inner {
				public int num = 20;
				public viod show() {
				int num  = 30;
				System.out.println(num);
				System.out.println(this.num);
				System.out.println(Outer.this.num);
				}
			}
		}
(6)局部内部类

	A:局部内部类访问局部变量必须加final修饰。
	B:为什么呢?
		因为局部变量使用完毕就消失，而堆内存的数据并不会立即消失。
		所以，堆内存还是用该变量，而改变量已经没有了。
		为了让该值还存在，就加final修饰。
		通过反编译工具我们看到了，加入final后，堆内存直接存储的是值，而不是变量名。
(7)匿名内部类(掌握)

	A:是局部内部类的简化形式
	B:前提
		存在一个类或者接口
	C:格式:
		new 类名或者接口名() {
			重写方法;
		}
	D:本质：
		其实是继承该类或者实现接口的子类匿名对象
(8)匿名内部类在开发中的使用

	我们在开发的时候，会看到抽象类，或者接口作为参数。
	而这个时候，我们知道实际需要的是一个子类对象。
	如果该方法仅仅调用一次，我们就可以使用匿名内部类的格式简化。
	
	interface Person {
		public abstract void study();
	}
	
	class PersonDemo {
		public void method(Person p) {
			p.study();
		}
	}
	
	class PersonTest {
		public static void main(String[] args) {
			PersonDemo pd = new PersonDemo();
			pd.method(new Person() {
				public void study() {
					System.out.println("好好学习，天天向上");
				}
			});
		}
	}

(9)匿名内部类的面试题(补齐代码)

	interface Inter {
		void show();
	}
	
	class Outer {
		public static Inter method() {
			return new Inter() {
				public void show() {
					System.out.println("HelloWorld");
				}	
			};
		}
	}
	
	class OuterDemo {
		public static void main(String[] args) {
			Outer.method().show(); //"HelloWorld"
		}
	
	}

Java开发工具

	## 1. Eclipse的概述使用(掌握)
		请参照ppt和课堂练习.txt
		
	## 2. API的概述(了解)
		(1)应用程序编程接口。
		(2)就是JDK提供给我们的一些提高编程效率的java类。


​	
	## 3. Object类(掌握)
		(1)Object是类层次结构的根类，所有的类都直接或者间接的继承自Object类。
		(2)Object类的构造方法有一个，并且是无参构造
			这其实就是理解当时我们说过，子类构造方法默认访问父类的构造是无参构造
		(3)要掌握的方法：
			A:toString()
				返回对象的字符串表示，默认是由类的全路径+'@'+哈希值的十六进制表示。
				这个表示其实是没有意义的，一般子类都会重写该方法。
				如何重写呢?过程我也讲解过了，基本上就是要求信息简单明了。
				但是最终还是自动生成。
			B:equals()
				比较两个对象是否相同。默认情况下，比较的是地址值是否相同。
				而比较地址值是没有意义的，所以，一般子类也会重写该方法。
				重写过程，我也详细的讲解和分析了。
				但是最终还是自动生成。
		(4)要了解的方法：
			A:hashCode() 返回对象的哈希值。不是实际地址值，可以理解为地址值。
			B:getClass() 返回对象的字节码文件对象，反射中我们会详细讲解	
			C:finalize() 用于垃圾回收，在不确定的时间
			D:clone() 可以实现对象的克隆，包括成员变量的数据复制，但是它和两个引用指向同一个对象是有区别的。
		(5)两个注意问题；
			A:直接输出一个对象名称，其实默认调用了该对象的toString()方法。
			B:面试题 
				==和equals()的区别?
				A:==
					基本类型：比较的是值是否相同
					引用类型：比较的是地址值是否相同
				B:equals()
					只能比较引用类型。默认情况下，比较的是地址值是否相同。
	
				但是，我们可以根据自己的需要重写该方法。

# Java常见对象

## 1. Scanner的使用(了解)
		(1)在JDK5以后出现的用于键盘录入数据的类。
		(2)构造方法：
			A:讲解了System.in这个东西。
				它其实是标准的输入流,对应于键盘录入
			B:构造方法
				InputStream is = System.in;
				Scanner(InputStream is)
			C:常用的格式
				Scanner sc = new Scanner(System.in);
	(3)基本方法格式：
		A:hasNextXxx() 判断是否是某种类型的
		B:nextXxx()	返回某种类型的元素
	(4)要掌握的两个方法
		A:public int nextInt()
		B:public String nextLine()
	(5)需要注意的小问题
		A:同一个Scanner对象，先获取数值，再获取字符串会出现一个小问题。
		B:解决方案：
			a:重新定义一个Scanner对象
			b:把所有的数据都用字符串获取，然后再进行相应的转换

## 2. String类的概述和使用(掌握)

	(1)多个字符组成的一串数据。
		其实它可以和字符数组进行相互转换。
	(2)构造方法：
		A:public String()
		B:public String(byte[] bytes)
		C:public String(byte[] bytes,int offset,int length)
		D:public String(char[] value)
		E:public String(char[] value,int offset,int count)
		F:public String(String original)
		下面的这一个虽然不是构造方法，但是结果也是一个字符串对象
		G:String s = "hello";
	(3)字符串的特点
		A:字符串一旦被赋值，就不能改变。
			注意：这里指的是字符串的内容不能改变，而不是引用不能改变。
		B:字面值作为字符串对象和通过构造方法创建对象的不同
			String s = new String("hello");和String s = "hello"的区别?
			new String("hello")会在堆内存开辟空间,另一种不会,但是最终的值都在字符串缓存区.
	(4)字符串的面试题(看程序写结果)
		A:==和equals()
			String s1 = new String("hello");
			String s2 = new String("hello");
			System.out.println(s1 == s2);// false
			System.out.println(s1.equals(s2));// true


			String s3 = new String("hello");
			String s4 = "hello";
			System.out.println(s3 == s4);// false
			System.out.println(s3.equals(s4));// true


			String s5 = "hello";
			String s6 = "hello";
			System.out.println(s5 == s6);// true(常量会先去缓存区找,存在就不创建新的对象)
			System.out.println(s5.equals(s6));// true
		B:字符串的拼接
			String s1 = "hello";
			String s2 = "world";
			String s3 = "helloworld";
			System.out.println(s3 == s1 + s2);// false
			System.out.println(s3.equals((s1 + s2)));// true


			System.out.println(s3 == "hello" + "world");// false 这个我们错了，应该是true
			System.out.println(s3.equals("hello" + "world"));// true
	(5)字符串的功能(自己补齐方法中文意思)
		A:判断功能
			boolean equals(Object obj)
			boolean equalsIgnoreCase(String str)
			boolean contains(String str)
			boolean startsWith(String str)
			boolean endsWith(String str)
			boolean isEmpty()
		B:获取功能
			int length()
			char charAt(int index)
			int indexOf(int ch)
			int indexOf(String str)
			int indexOf(int ch,int fromIndex)
			int indexOf(String str,int fromIndex)
			String substring(int start)
			String substring(int start,int end)
		C:转换功能
			byte[] getBytes()
			char[] toCharArray()
			static String valueOf(char[] chs)
			static String valueOf(int i)
			String toLowerCase()
			String toUpperCase()
			String concat(String str)
		D:其他功能
			a:替换功能 
				String replace(char old,char new)
				String replace(String old,String new)
			b:去空格功能
				String trim()
			c:按字典比较功能
				int compareTo(String str)
				int compareToIgnoreCase(String str) 
	(6)字符串的案例
		A:模拟用户登录
			public static void login(String userName, String passwd) {
		        if (userName == "Xmos" && passwd == "123") {
		            System.out.println("login success");
		        }
		    }
		B:字符串遍历
			public static void printString(String s) {
		        char[] c = s.toCharArray();
		        for (int i = 0; i < c.length; i++) {
		            System.out.print(c[i]);
		        }
		    }
		C:统计字符串中大写，小写及数字字符的个数
			public static void method(String s) {
		        char[] c = s.toCharArray();
		        int lowerCaseNum = 0;
		        int upperCaseNum = 0;
		        int num = 0;
		        for (char c1 : c) {
		            if (c1 >= 'a' && c1 <= 'z') {
		                lowerCaseNum++;
		            } else if (c1 >= 'A' && c1 <= 'Z') {
		                upperCaseNum++;
		            } else if (c1 >= '0' && c1 <= '9') {
		                num++;
		            }
		        }
		        
		D:把字符串的首字母转成大写，其他小写
			public static void method1(String s) {
		        String s1 = s.substring(0, 1);
		        String s2 = s.substring(1, s.length());
		        String s3 = s1.toUpperCase() + s2.toLowerCase();
		
		        System.out.println(s3);
		    }		
		E:把int数组拼接成一个指定格式的字符串
			//方法一
			public static void method3(int[] i) {
		        String s = Arrays.toString(i);
		        System.out.println(s);
		    }
		    //方法二
			public static void method3(int[] i) {
			        String s = "";
			        for (int i1 : i) {
			            s += String.valueOf(i1);
			        }
			        System.out.println(s);
			    }
		F:字符串反转
			public static void revers(String s) {
		        char[] c = s.toCharArray();
		        for (int i = 0; i < c.length / 2; i++) {
		            char tmp = c[i];
		            c[i] = c[c.length - 1 - i];
		            c[c.length - 1 - i] = tmp;
		        }
		        System.out.println(String.valueOf(c));
		    }		
		G:统计大串中小串出现的次数


## 1. StringBuffer(掌握)

	(1)用字符串做拼接，比较耗时并且也耗内存，而这种拼接操作又是比较常见的，为了解决这个问题，Java就提供了
	   一个字符串缓冲区类。StringBuffer供我们使用。
	(2)StringBuffer的构造方法
		A:StringBuffer()
		B:StringBuffer(int size)
		C:StringBuffer(String str)
	(3)StringBuffer的常见功能(自己补齐方法的声明和方法的解释)
		A:添加功能
			appen();
		B:删除功能
			delete();
		C:替换功能
			replace()
		D:反转功能
			reverse()
		E:截取功能(注意这个返回值)
			String substring()
	(4)StringBuffer的练习(做一遍)
		A:String和StringBuffer相互转换
			String -- StringBuffer
				构造方法
			StringBuffer -- String
				toString()方法
		B:字符串的拼接
			StringBuffer sb = new StringBuffer("hello");
	        StringBuffer sb2 = new StringBuffer("world");
	        
	        StringBuffer sb3 = sb.append(sb2);
		C:把字符串反转
			StringBuffer sb = new StringBuffer("abc");
	        StringBuffer sb1 = sb.reverse();
		D:判断一个字符串是否对称
			public static void method(StringBuffer sb) {
		        if (sb.toString().equals(sb.reverse().toString())) {
		            System.out.println(true);
		        } else {
		            System.out.println(false);
		        }
		    }
			
	(5)面试题
		小细节：
			StringBuffer：同步的，数据安全，效率低。
			StringBuilder：不同步的，数据不安全，效率高。
		A:String,StringBuffer,StringBuilder的区别
			String 字符串常量
			StringBuffer 字符串变量（线程安全）
			StringBuilder 字符串变量（非线程安全）
		B:StringBuffer和数组的区别?
			StringBuffer : 可以存放任意类型的数据
			数组 : 只能存放同类型的数据
	(6)注意的问题：
		String作为形式参数，StringBuffer作为形式参数。
			String : 不会受影响
			StringBuffer : 除了=操作，其他操作会受影响
## 2. 数组高级以及Arrays(掌握)
	(1)排序
		A:冒泡排序
			相邻元素两两比较，大的往后放，第一次完毕，最大值出现在了最大索引处。同理，其他的元素就可以排好。
			
			public static void bubbleSort(int[] arr) {
				for(int x=0; x<arr.length-1; x++) {
					for(int y=0; y<arr.length-1-x; y++) {
						if(arr[y] > arr[y+1]) {
							int temp = arr[y];
							arr[y] = arr[y+1];
							arr[y+1] = temp;
						}
					}
				}
			}
			
		B:选择排序
			把0索引的元素，和索引1以后的元素都进行比较，第一次完毕，最小值出现在了0索引。同理，其他的元素就可以排好。
			
			public static void selectSort(int[] arr) {
				for(int x=0; x<arr.length-1; x++) {
					for(int y=x+1; y<arr.length; y++) {
						if(arr[y] < arr[x]) {
							int temp = arr[x];
							arr[x] = arr[y];
							arr[y] = temp;
						}
					}
				}
			}
	(2)查找
		A:基本查找
			针对数组无序的情况
			
			public static int getIndex(int[] arr,int value) {
				int index = -1;
				
				for(int x=0; x<arr.length; x++) {
					if(arr[x] == value) {
						index = x;
						break;
					}
				}
				
				return index;
			}
		B:二分查找(折半查找)
			针对数组有序的情况(千万不要先排序，在查找)
			
			public static int binarySearch(int[] arr,int value) {
				int min = 0;
				int max = arr.length-1;
				int mid = (min+max)/2;
				
				while(arr[mid] != value) {
					if(arr[mid] > value) {
						max = mid - 1;
					}else if(arr[mid] < value) {
						min = mid + 1;
					}
					
					if(min > max) {
						return -1;
					}
					
					mid = (min+max)/2;
				}
				
				return mid;
			}
	(3)Arrays工具类
		A:是针对数组进行操作的工具类。包括排序和查找等功能。
		B:要掌握的方法(自己补齐方法)
			把数组转成字符串：
				Arrays.toString();
			排序：
				Arrays.sort();
			二分查找：
				Arrays.binarySearch();
	(4)Arrays工具类的源码解析
	(5)把字符串中的字符进行排序
		举例：
			"edacbgf"
			得到结果
			"abcdefg"
			String s = "edacbgf";
	        char[] c = s.toCharArray();
	        Arrays.sort(c);
	        System.out.println(Arrays.toString(c));


## 3. Integer(掌握)

	(1)为了让基本类型的数据进行更多的操作，Java就为每种基本类型提供了对应的包装类类型
		byte 		Byte
		short		Short
		int			Integer
		long		Long
		float		Float
		double		Double
		char		Character
		boolean		Boolean
	(2)Integer的构造方法
		A:Integer i = new Integer(100);
		B:Integer i = new Integer("100");
			注意：这里的字符串必须是由数字字符组成
	(3)String和int的相互转换
		A:String -- int
			Integer.parseInt("100");
		B:int -- String
			String.valueOf(100);
	(4)其他的功能(了解)
		进制转换
			Integer.toBinaryString();
	        Integer.toHexString();
	        Integer.toOctalString();
	(5)JDK5的新特性
		自动装箱	基本类型--引用类型
		自动拆箱	引用类型--基本类型
		
		把下面的这个代码理解即可：
			Integer i = 100;
			i += 200;
	(6)面试题
		-128到127之间的数据缓冲池问题

## 4. Character(了解)

	(1)Character构造方法	
		Character ch = new Character('a');
	(2)要掌握的方法：(自己补齐)
		A:判断给定的字符是否是大写
			isUpperCase();
		B:判断给定的字符是否是小写
			isLowerCase();
		C:判断给定的字符是否是数字字符
			isDigit();
		D:把给定的字符转成大写
			toUpperCase();
		E:把给定的字符转成小写
			toLowerCase();
	(3)案例：
	
		统计字符串中大写，小写及数字字符出现的次数
			String s = "abcDEF123";
	        char[] c = s.toCharArray();
	        int lowerCaseNum = 0;
	        int upperCaseNum = 0;
	        int digitNum = 0;
	
	        for (char c1 : c) {
	            if (Character.isLowerCase(c1)) {
	                lowerCaseNum++;
	            } else if (Character.isUpperCase(c1)) {
	                upperCaseNum++;
	            } else if (Character.isDigit(c1)) {
	                digitNum++;
	            }
	        }
	
	        System.out.println("lowerCase:" + lowerCaseNum + "\t" + "upperCase:" + upperCaseNum + "\t" + "digit:" + digitNum);


## 1. 正则表达式(理解)

	(1)就是符合一定规则的字符串
	(2)常见规则
		A:字符
			x 字符 x。举例：'a'表示字符a
			\\ 反斜线字符。
			\n 新行（换行）符 ('\u000A') 
			\r 回车符 ('\u000D')
			
		B:字符类
			[abc] a、b 或 c（简单类） 
			[^abc] 任何字符，除了 a、b 或 c（否定） 
			[a-zA-Z] a到 z 或 A到 Z，两头的字母包括在内（范围） 
			[0-9] 0到9的字符都包括
			
		C:预定义字符类
			. 任何字符。我的就是.字符本身，怎么表示呢? \.
			\d 数字：[0-9]
			\w 单词字符：[a-zA-Z_0-9]
				在正则表达式里面组成单词的东西必须有这些东西组成
				
		D:边界匹配器
			^ 行的开头 
			$ 行的结尾 
			\b 单词边界
				就是不是单词字符的地方。
				举例：hello world?haha;xixi
			
		E:Greedy 数量词 
			X? X，一次或一次也没有
			X* X，零次或多次
			X+ X，一次或多次
			X{n} X，恰好 n 次 
			X{n,} X，至少 n 次 
			X{n,m} X，至少 n 次，但是不超过 m 次 
	(3)常见功能：(分别用的是谁呢?)
		A:判断功能
			String类的public boolean matches(String regex)
		B:分割功能
			String类的public String[] split(String regex)
		C:替换功能
			String类的public String replaceAll(String regex,String replacement)
		D:获取功能
			Pattern和Matcher
				Pattern p = Pattern.compile("a*b");
				Matcher m = p.matcher("aaaaab");
				
				find():查找存不存在
				group():获取刚才查找过的数据
	(4)案例
		A:判断电话号码和邮箱
			//普安段邮箱
			public static boolean checkMail(String s){
		        String regex = "\\d*\\w*@sina\\.com";
		        return s.matches(regex);
		    }
		    //判断电话号码
		    public static boolean checkPhoneNum(String s) {
		        String regex = "\\d{11}";
		        return s.matches(regex);
		    }
		B:按照不同的规则分割数据
			public static String[] split(String s) {
		        String regex = ",";
		        String[] result = s.split(regex);
		        return result;
		    }
		C:把论坛中的数字替换为*
			//替换为和数字等量的*
			public static String replaceStar(String s) {
		        String regex = "\\d";
		        return s.replaceAll(regex, "*");
		    }
		    //所有相连数字替换为一个*
		    public static String replaceStar(String s) {
		        String regex = "\\d+";
		        return s.replaceAll(regex, "*");
		    }
		D:获取字符串中由3个字符组成的单词
			public static List<String> method(String s) {
		        Pattern p = Pattern.compile("a\\d{3}b");
		        Matcher m = p.matcher(s);
		        List<String> result = new ArrayList<String>();
		        
		        while (m.find()) {
		            result.add(m.group());
		        }
		        return  result;
		    }

## 2. Math(掌握)

	(1)针对数学运算进行操作的类
	(2)常见方法(自己补齐)
		A:绝对值
			Math.abs();
		B:向上取整
			Math.ceil();
		C:向下取整
			Math.floor();
		D:两个数据中的大值
			Math.max();
		E:a的b次幂
			Math.pow(a, b);
		F:随机数
			Math.random();
		G:四舍五入
			Math.round();
		H:正平方根
			Math.sqrt();
	(3)案例：
		A:猜数字小游戏
			Scanner sc = new Scanner(System.in);
	        int i = (int)(Math.random() * 100) + 1;
	        int answer;
	        while ((answer = sc.nextInt()) != i) {
	            if (answer > i) {
	                System.out.println("bigger than result,go on");
	            } else if (answer < i) {
	                System.out.println("smaller than result,go on");
	            }
	        }
	        System.out.println("you are right");
		B:获取任意范围的随机数
			Scanner sc = new Scanner(System.in);
	        System.out.println("请输入起始:");
	        int start = sc.nextInt();
	        System.out.println("请输入结束:");
	        int end = sc.nextInt();
	
	        int i = (int)(Math.random() * (end - start)) + start;
	        System.out.println(i);
## 3. Random(理解)

	(1)用于产生随机数的类
	(2)构造方法:
		A:Random() 默认种子，每次产生的随机数不同
		B:Random(long seed) 指定种子，每次种子相同，随机数就相同
	(3)成员方法:
		A:int nextInt() 返回int范围内的随机数
		B:int nextInt(int n) 返回[0,n)范围内的随机数


## 4. System(掌握)

	(1)系统类,提供了一些有用的字段和方法
	(2)成员方法(自己补齐)
		A:运行垃圾回收器
			System.gc();
		B:退出jvm
			System.exit(0);
		C:获取当前时间的毫秒值
			System.currentTimemillis();
		D:数组复制
			System.arraycopy();

## 5. BigInteger(理解)

	(1)针对大整数的运算
	(2)构造方法	
		A:BigInteger(String s)
	(3)成员方法(自己补齐)
		A:加
			add();
		B:减
			subtract();
		C:乘
			multiply();
		D:除
			divide();
		E:商和余数
			divideAndRemainder();

## 6. BigDecimal(理解)

	(1)浮点数据做运算，会丢失精度。所以，针对浮点数据的操作建议采用BigDecimal。(金融相关的项目)
	(2)构造方法
		A:BigDecimal(String s)
	(3)成员方法：
		A:加
			add();
		B:减
			subtract();
		C:乘
			multiply();
		D:除
			divide();
		E:自己保留小数几位
			setScale();

## 7. Date/DateFormat(掌握)

	(1)Date是日期类，可以精确到毫秒。
		A:构造方法
			Date()
			Date(long time)
		B:成员方法
			getTime()
			setTime(long time)
		C:日期和毫秒值的相互转换
		案例：你来到这个世界多少天了?
	(2)DateFormat针对日期进行格式化和针对字符串进行解析的类，但是是抽象类，所以使用其子类SimpleDateFormat
		A:SimpleDateFormat(String pattern) 给定模式
			yyyy-MM-dd HH:mm:ss
		B:日期和字符串的转换
			a:Date -- String
				format()
				
			b:String -- Date
				parse()
		C:案例：
			制作了一个针对日期操作的工具类。
				Date d = new Date();
		        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
		        System.out.println(sdf.format(d));

## 8. Calendar(掌握)

	(1)日历类，封装了所有的日历字段值，通过统一的方法根据传入不同的日历字段可以获取值。
	(2)如何得到一个日历对象呢?
		Calendar rightNow = Calendar.getInstance();
		本质返回的是子类对象
	(3)成员方法
		A:根据日历字段得到对应的值
			Calendar c =Calendar.getInstance();
	        System.out.println(c.get(Calendar.YEAR));
	        System.out.println(c.get(Calendar.MONTH));
	        System.out.println(c.get(Calendar.DAY_OF_MONTH));
		B:根据日历字段和一个正负数确定是添加还是减去对应日历字段的值
			add(Calendar.DAY_OF_MONTH, +3);
		C:设置日历对象的年月日
			set(2018,5,30);
			set(Calendar.YEAR, 2018);
			set(Calendar.MONTH, 2018);
			set(Calendar.DAY_OF_MONTH, 2018);
	(4)案例：
		计算任意一年的2月份有多少天?
			Scanner sc = new Scanner(System.in);
	        Calendar c =Calendar.getInstance();
	
	        c.set(Calendar.YEAR, sc.nextInt());
	        System.out.println(c.get(Calendar.DAY_OF_MONTH));

# Java集合框架

# JavaIO流

## 1. 异常(理解)

	(1)程序出现的不正常的情况。
	(2)异常的体系
		Throwable
			|--Error	严重问题，我们不处理。
			|--Exception
				|--RuntimeException	运行期异常，我们需要修正代码
				|--非RuntimeException 编译期异常，必须处理的，否则程序编译不通过
	(3)异常的处理：
		A:JVM的默认处理
			把异常的名称,原因,位置等信息输出在控制台，但是程序不能继续执行了。
		B:自己处理
			a:try...catch...finally
				自己编写处理代码,后面的程序可以继续执行
			b:throws
				把自己处理不了的，在方法上声明，告诉调用者，这里有问题
	(4)面试题
		A:编译期异常和运行期异常的区别?
			编译期异常 必须要处理的，否则编译不通过
			运行期异常 可以不处理，也可以处理
		B:throw和throws是的区别
			throw:
				在方法体中,后面跟的是异常对象名,并且只能是一个
				throw抛出的是一个异常对象，说明这里肯定有一个异常产生了
			throws:
				在方法声明上,后面跟的是异常的类名,可以是多个
				throws是声明方法有异常，是一种可能性，这个异常并不一定会产生
	(5)finally关键字及其面试题
		A:finally用于释放资源，它的代码永远会执行。特殊情况：在执行到finally之前jvm退出了
		B:面试题
			a:final,finally,finalize的区别?
				final : 关键字,修饰类、方法、变量,被修饰的类无法被继承,方法无法重写,变量值不能改变.
				finally : try...catch...finally,一定会执行.
				finalize : 对象被垃圾回收器回收时执行的方法.
			b:如果在catch里面有return,请问finally还执行吗?如果执行,在return前还是后
				会，前。
				
				实际上在中间。这个上课我们讲过
		C:异常处理的变形
			try...catch...finally
			try...catch...
			try...catch...catch...
			try...catch...catch...fianlly
			try...finally
	(6)自定义异常
		继承自Exception或者RuntimeException,只需要提供无参构造和一个带参构造即可
			public class MyException extends RuntimeException {
			    public MyException(String message) {
			        super(message);
			    }
			
			    public MyException() {
			        super();
			    }
			}
	(7)异常的注意实现
		A:父的方法有异常抛出,子的重写方法在抛出异常的时候必须要小于等于父的异常 
		B:父的方法没有异常抛出,子的重写方法不能有异常抛出
		C:父的方法抛出多个异常,子的重写方法必须比父少或者小

## 2. File(掌握)

	(1)IO流操作中大部分都是对文件的操作，所以Java就提供了File类供我们来操作文件
	(2)构造方法
		A:File file = new File("e:\\demo\\a.txt");
		B:File file = new File("e:\\demo","a.txt");
		C:File file = new File("e:\\demo");
		  File file2 = new File(file,"a.txt");
	(3)File类的功能(自己补齐)
		A:创建功能
			createNewFile();
			mkdir();
			mkdirs();
		B:删除功能
			delete();
		C:重命名功能
			renameTo();
		D:判断功能
			isFile();
	        isDirectory();
	        exists();
	        canRea();
	        canWrite();
	        isAbsolute();
	        isHidden();
		E:获取功能
			getAbsoluteFile();
	        getAbsolutePath();
	        getPath();
	        getParent();
	        getParentFile();
	        getName();
	        length();
	        lastModified();
		F:高级获取功能
			list();
			listFiles();
		G:过滤器功能
			list(FilenameFilter filter);
				String[] s = file1.list(new FilenameFilter() {
	            @Override
	            public boolean accept(File dir, String name) {
	                return new File(dir, name).isFile() && name.endsWith(".jpg");
	            }
	        });
			listFiles(FilenameFilter filter);
	(4)案例：
		A:输出指定目录下指定后缀名的文件名称
			a:先获取所有的，在遍历的时候判断，再输出
				File file = new File("D:\\Movie\\M");
		        String[] s = file.list();
		
		        for (String result : s) {
		            if (result.endsWith(".mp4")) {
		                System.out.println(result);
		            }
		        }
			b:先判断，再获取，最后直接遍历输出即可
				String[] s1 = file.list(new FilenameFilter() {
		            @Override
		            public boolean accept(File dir, String name) {
		                return name.endsWith(".mp4");
		            }
		        });
		        for (String result : s1) {
		            System.out.println(result);
		        }
		B:批量修改文件名称
			File file = new File("D:\\Movie");
	        String[] s = file.list(new FilenameFilter() {
	            @Override
	            public boolean accept(File dir, String name) {
	                return name.startsWith("相对宇宙");
	            }
	        });
	        for (String result : s) {
	            System.out.println("beforeRename : " + result);
	            File file1 = new File(file,result.replaceAll("WEB.*影视\\.", ""));
	            File file2 = new File(file, result);
	            file2.renameTo(file1);
	            System.out.println("afterRename : " + file1.exists() + ", " + file1.getName());
	        }
	        ## 1. 递归(理解)
	
	(1)方法定义中调用方法本身的现象
		举例：老和尚给小和尚讲故事，我们学编程
	(2)递归的注意事项；
		A:要有出口，否则就是死递归
		B:次数不能过多，否则内存溢出
		C:构造方法不能递归使用
	(3)递归的案例：
		A:递归求阶乘
			public static int method(int i) {
		        while (i > 1) {
		            return i * method(--i);
		        }
		        return 1;
		    }
		B:兔子问题
		C:递归输出指定目录下所有指定后缀名的文件绝对路径
			public static void method(File filePath, String suffix) {
		        File[] files = filePath.listFiles();
		        for (File file : files) {
		            if (file.isDirectory()) {
		                method(file, suffix);
		            } else if (file.getName().endsWith(suffix)){
		                System.out.println(file.getName());
		            }
		        }
		    }
		D:递归删除带内容的目录(小心使用)
			public static void method(File filePath) {
		        File[] files = filePath.listFiles();
		        for (File file : files) {
		            if (file.isDirectory()) {
		                method(file);
		            } else {
		                file.delete();
		            }
		        }
		        filePath.delete();
		    }

## 2. IO流(掌握)

	(1)IO用于在设备间进行数据传输的操作	
	(2)分类：
		A:流向
			输入流	读取数据
			输出流	写出数据
		B:数据类型
			字节流	
					字节输入流
					字节输出流
			字符流
					字符输入流
					字符输出流
		注意：
			a:如果我们没有明确说明按照什么分，默认按照数据类型分。
			b:除非文件用windows自带的记事本打开我们能够读懂，才采用字符流，否则建议使用字节流。
	(3)FileOutputStream写出数据
		A:操作步骤
			a:创建字节输出流对象
			b:调用write()方法
			c:释放资源
			
		B:代码体现：
			FileOutputStream fos = new FileOutputStream("fos.txt");
			
			fos.write("hello".getBytes());
			
			fos.close();
			
		C:要注意的问题?
			a:创建字节输出流对象做了几件事情?
				调用系统功能去创建文件
				创建fos对象
				把fos对象指向这个文件
			b:为什么要close()?
				关闭此文件输出流并释放与此流有关的所有系统资源。
			c:如何实现数据的换行?
				windows:\r\n
				linux:\n
				Mac:\r
			d:如何实现数据的追加写入?
				FileOutputStream fos = new FileOutputStream("F:\\", true);
	(4)FileInputStream读取数据
		A:操作步骤
			a:创建字节输入流对象
			b:调用read()方法
			c:释放资源
			
		B:代码体现：
			FileInputStream fis = new FileInputStream("fos.txt");
			
			//方式1
			int by = 0;
			while((by=fis.read())!=-1) {
				System.out.print((char)by);
			}
			
			//方式2
			byte[] bys = new byte[1024];
			int len = 0;
			while((len=fis.read(bys))!=-1) {
				System.out.print(new String(bys,0,len));
			}
			
			fis.close();
	(5)案例：2种实现
		A:复制文本文件
			FileInputStream fis = new FileInputStream("a.txt");
	        FileOutputStream fos = new FileOutputStream("b.txt");
			//方式一
	        int i = 0;
	        while ((i = fis.read()) != -1) {
	            fos.write(i);
	        }
	        fis.close();
	        fos.close();
	        //方式二
	        int len = 0;
	        byte[] bytes = new byte[1024];
	        while ((len = fis.read(bytes)) != -1) {
	            fos.write(bytes, 0, len);
	        }
	        fis.close();
	        fos.close();
		B:复制图片
			FileInputStream fis = new FileInputStream("a.jpg");
	        FileOutputStream fos = new FileOutputStream("b.jpg");
			//方式一
	        int i = 0;
	        while ((i = fis.read()) != -1) {
	            fos.write(i);
	        }
	        fis.close();
	        fos.close();
	        //方式二
	        int len = 0;
	        byte[] bytes = new byte[1024];
	        while ((len = fis.read(bytes)) != -1) {
	            fos.write(bytes, 0, len);
	        }
	        fis.close();
	        fos.close();
		C:复制视频
			FileInputStream fis = new FileInputStream("a.mp4");
	        FileOutputStream fos = new FileOutputStream("b.mp4");
			//方式一
	        int i = 0;
	        while ((i = fis.read()) != -1) {
	            fos.write(i);
	        }
	        fis.close();
	        fos.close();
	        //方式二
	        int len = 0;
	        byte[] bytes = new byte[1024];
	        while ((len = fis.read(bytes)) != -1) {
	            fos.write(bytes, 0, len);
	        }
	        fis.close();
	        fos.close();
	(6)字节缓冲区流
		A:BufferedOutputStream
		B:BufferedInputStream
	(7)案例：4种实现
		A:复制文本文件
			BufferedInputStream bis = new BufferedInputStream(new FileInputStream("a.txt"));
	        BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream("b.txt"));
	
	        //方式三
	        int i = 0;
	        while ((i = bis.read()) != -1) {
	            bos.write(i);
	        }
			fis.close();
	        fos.close();
	        //方式四
	        int len = 0;
	        byte[] bytes = new byte[1024];
	        while ((len = bis.read()) != -1) {
	            bos.write(bytes, 0, len);
	        }
	        fis.close();
	        fos.close();
		B:复制图片
			BufferedInputStream bis = new BufferedInputStream(new FileInputStream("a.jpg"));
	        BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream("b.jpg"));
	
	        //方式三
	        int i = 0;
	        while ((i = bis.read()) != -1) {
	            bos.write(i);
	        }
			fis.close();
	        fos.close();
	        //方式四
	        int len = 0;
	        byte[] bytes = new byte[1024];
	        while ((len = bis.read()) != -1) {
	            bos.write(bytes, 0, len);
	        }
	        fis.close();
	        fos.close();
		C:复制视频
			BufferedInputStream bis = new BufferedInputStream(new FileInputStream("a.mp4"));
	        BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream("b.mp4"));
	
	        //方式三
	        int i = 0;
	        while ((i = bis.read()) != -1) {
	            bos.write(i);
	        }
			fis.close();
	        fos.close();
	        //方式四
	        int len = 0;
	        byte[] bytes = new byte[1024];
	        while ((len = bis.read()) != -1) {
	            bos.write(bytes, 0, len);
	        }
			fis.close();
	        fos.close();
## 3. 自学字符流

	IO流分类
		字节流：
			InputStream
				FileInputStream
				BufferedInputStream
			OutputStream
				FileOutputStream
				BufferedOutputStream
		
		字符流：
			Reader
				FileReader
				BufferedReader
			Writer
				FileWriter
				BufferedWriter
## 1. 字符流(掌握)

	(1)字节流操作中文数据不是特别的方便，所以就出现了转换流。
	   转换流的作用就是把字节流转换字符流来使用。
	(2)转换流其实是一个字符流
		字符流 = 字节流 + 编码表
	(3)编码表
		A:就是由字符和对应的数值组成的一张表
		B:常见的编码表
			ASCII
			ISO-8859-1
			GB2312
			GBK
			GB18030
			UTF-8
		C:字符串中的编码问题
			编码
				String -- byte[]
			解码
				byte[] -- String
	(4)IO流中的编码问题
		A:OutputStreamWriter
			OutputStreamWriter(OutputStream os):默认编码，GBK
			OutputStreamWriter(OutputStream os,String charsetName):指定编码。
		B:InputStreamReader
			InputStreamReader(InputStream is):默认编码，GBK
			InputStreamReader(InputStream is,String charsetName):指定编码
		C:编码问题其实很简单
			编码只要一致即可
	(5)字符流
		Reader
			|--InputStreamReader
				|--FileReader
			|--BufferedReader
		Writer
			|--OutputStreamWriter
				|--FileWriter
			|--BufferedWriter
	(6)复制文本文件(5种方式)
		public class CopyDemo {
	    public static void main(String[] args) throws IOException {
	        File srcFile = new File("a.txt");
	        File destFile = new File("b.txt");
	
	        method1(srcFile, destFile);
	        method2(srcFile, destFile);
	        method3(srcFile, destFile);
	        method4(srcFile, destFile);
	        method5(srcFile, destFile);
	    }
	
	    private static void method5(File srcFile, File destFile) throws IOException{
	        BufferedReader br = new BufferedReader(new FileReader(srcFile));
	        BufferedWriter bw = new BufferedWriter(new FileWriter(destFile));
	
	        String s = null;
	        while ((s = br.readLine()) != null) {
	            bw.write(s);
	        }
	        br.close();
	        bw.close();
	    }
	
	    private static void method4(File srcFile, File destFile) throws IOException {
	        BufferedReader br = new BufferedReader(new FileReader(srcFile));
	        BufferedWriter bw = new BufferedWriter(new FileWriter(destFile));
	
	        int len = 0;
	        char[] chars = new char[1024];
	        while ((len = br.read(chars)) != -1) {
	            bw.write(chars, 0, len);
	        }
	        br.close();
	        bw.close();
	    }
	
	    private static void method3(File srcFile, File destFile) throws IOException {
	        BufferedReader br = new BufferedReader(new FileReader(srcFile));
	        BufferedWriter bw = new BufferedWriter(new FileWriter(destFile));
	
	        int by = 0;
	        while ((by = br.read()) != -1) {
	            bw.write(by);
	        }
	        br.close();
	        bw.close();
	    }
	
	    private static void method2(File srcFile, File destFile) throws IOException {
	        FileReader fr = new FileReader(srcFile);
	        FileWriter fw = new FileWriter(destFile);
	
	        int len = 0;
	        char[] bytes = new char[1024];
	        while ((len = fr.read(bytes)) != -1) {
	            fw.write(bytes, 0, len);
	        }
	        fr.close();
	        fw.close();
	    }
	
	    private static void method1(File srcFile, File destFile) throws IOException {
	        FileReader fr = new FileReader(srcFile);
	        FileWriter fw = new FileWriter(destFile);
	
	        int by = 0;
	        while ((by = fr.read()) != -1) {
	            fw.write(by);
	        }
	        fr.close();
	        fw.close();
	    }
	}												
## 2. IO流小结(掌握)

	IO流
		|--字节流
			|--字节输入流
				InputStream
					int read():一次读取一个字节
					int read(byte[] bys):一次读取一个字节数组
				
					|--FileInputStream
					|--BufferedInputStream
			|--字节输出流
				OutputStream
					void write(int by):一次写一个字节
					void write(byte[] bys,int index,int len):一次写一个字节数组的一部分
					
					|--FileOutputStream
					|--BufferedOutputStream
		|--字符流
			|--字符输入流
				Reader
					int read():一次读取一个字符
					int read(char[] chs):一次读取一个字符数组
					
					|--InputStreamReader
						|--FileReader
					|--BufferedReader
						String readLine():一次读取一个字符串
			|--字符输出流
				Writer
					void write(int ch):一次写一个字符
					void write(char[] chs,int index,int len):一次写一个字符数组的一部分
					
					|--OutputStreamWriter
						|--FileWriter
					|--BufferedWriter
						void newLine():写一个换行符
						
						void write(String line):一次写一个字符串

## 3. 案例(理解 练习一遍)

	A:复制文本文件 5种方式(掌握)
		private static void method5(File srcFile, File destFile) throws IOException{
	        BufferedReader br = new BufferedReader(new FileReader(srcFile));
	        BufferedWriter bw = new BufferedWriter(new FileWriter(destFile));
	
	        String s = null;
	        while ((s = br.readLine()) != null) {
	            bw.write(s);
	        }
	        br.close();
	        bw.close();
	    }
	
	    private static void method4(File srcFile, File destFile) throws IOException {
	        BufferedReader br = new BufferedReader(new FileReader(srcFile));
	        BufferedWriter bw = new BufferedWriter(new FileWriter(destFile));
	
	        int len = 0;
	        char[] chars = new char[1024];
	        while ((len = br.read(chars)) != -1) {
	            bw.write(chars, 0, len);
	        }
	        br.close();
	        bw.close();
	    }
	
	    private static void method3(File srcFile, File destFile) throws IOException {
	        BufferedReader br = new BufferedReader(new FileReader(srcFile));
	        BufferedWriter bw = new BufferedWriter(new FileWriter(destFile));
	
	        int by = 0;
	        while ((by = br.read()) != -1) {
	            bw.write(by);
	        }
	        br.close();
	        bw.close();
	    }
	
	    private static void method2(File srcFile, File destFile) throws IOException {
	        FileReader fr = new FileReader(srcFile);
	        FileWriter fw = new FileWriter(destFile);
	
	        int len = 0;
	        char[] bytes = new char[1024];
	        while ((len = fr.read(bytes)) != -1) {
	            fw.write(bytes, 0, len);
	        }
	        fr.close();
	        fw.close();
	    }
	
	    private static void method1(File srcFile, File destFile) throws IOException {
	        FileReader fr = new FileReader(srcFile);
	        FileWriter fw = new FileWriter(destFile);
	
	        int by = 0;
	        while ((by = fr.read()) != -1) {
	            fw.write(by);
	        }
	        fr.close();
	        fw.close();
	    }
	B:复制图片(二进制流数据) 4种方式(掌握)
		private static void method4(File srcFile, File destFile) throws IOException{
	        BufferedInputStream bis = new BufferedInputStream(
	        	new FileInputStream(srcFile));
	        BufferedOutputStream bos = new BufferedOutputStream(
	        	new FileOutputStream(destFile));
	
	        int len = 0;
	        byte[] bytes = new byte[1024];
	        while ((len = bis.read()) != -1) {
	            bos.write(bytes, 0, len);
	        }
	        bis.close();
	        bos.close();
	    }
	
	    private static void method3(File srcFile, File destFile) throws IOException{
	        BufferedInputStream bis = new BufferedInputStream(
	        	new FileInputStream(srcFile));
	        BufferedOutputStream bos = new BufferedOutputStream(
	        	new FileOutputStream(destFile));
	
	        int by = 0;
	        while ((by = bis.read()) != -1) {
	            bos.write(by);
	        }
	        bis.close();
	        bos.close();
	    }
	
	    private static void method2(File srcFile, File destFile) throws IOException{
	        FileInputStream fis = new FileInputStream(srcFile);
	        FileOutputStream fos = new FileOutputStream(destFile);
	
	        int len = 0;
	        byte[] bytes = new byte[1024];
	        while ((len = fis.read(bytes)) != -1) {
	            fos.write(bytes,0,len);
	        }
	        fis.close();
	        fos.close();
	    }
	
	    private static void method1(File srcFile, File destFile) throws IOException{
	        FileInputStream fis = new FileInputStream(srcFile);
	        FileOutputStream fos = new FileOutputStream(destFile);
	
	        int by = 0;
	        while ((by = fis.read()) != -1) {
	            fos.write(by);
	        }
	        fis.close();
	        fos.close();
	    }
	C:把集合中的数据存储到文本文件
		File srcFile = new File("a.txt");
	    List<String> list = new ArrayList<String>();
	
	    list.add("hello");
	    list.add("world");
	    list.add("java");
		//方式一
	    FileOutputStream fos = new FileOutputStream(srcFile);
	    for (String s : list) {
	        fos.write((s).getBytes());
	    }
	    fos.close();
	    //方式二
	    FileWriter fw = new FileWriter(srcFile);
	    for (String s : list) {
	        fw.write(s.toCharArray());
	        fw.flush();
	    }
	    fw.close();
	    //方式三
	    BufferedWriter bw = new BufferedWriter(new FileWriter(srcFile));
	    for (String s : list) {
	        bw.write(s);
	        bw.flush();
	    }
	    bw.close();
	D:把文本文件中的数据读取到集合并遍历集合
		File srcFile = new File("a.txt");
	    List<String> list = new ArrayList<String>();
	
	    BufferedReader br = new BufferedReader(new FileReader(srcFile));
	    String s = null;
	    while ((s = br.readLine()) != null) {
	        list.add(s);
	    }
	    br.close();
	E:复制单级文件夹
		File srcPath = new File("F:\\struts-1.2.7");
	    File destPath = new File("F:\\test1");
	
	    File[] srcFiles = srcPath.listFiles();
	    BufferedInputStream bis = null;
	    BufferedOutputStream bos = null;
	    if (!destPath.exists()) {
	        destPath.mkdir();
	    }
	    for (File srcFile : srcFiles) {
	        if (srcFile.isFile()) {
	             bis = new BufferedInputStream(new FileInputStream(srcFile));
	             bos = new BufferedOutputStream(
	             	new FileOutputStream(new File(destPath,srcFile.getName())));
	            int len = 0;
	            byte[] bytes = new byte[1024];
	            while ((len = bis.read(bytes)) != -1) {
	                bos.write(bytes, 0, len);
	                bos.flush();
	            }
	        }
	    }
	    bis.close();
	    bos.close();
	F:复制单级文件夹中指定的文件
		File srcPath = new File("F:\\test");
	    File destPath = new File("F:\\test1");
	
	    File[] srcFiles = srcPath.listFiles(new FilenameFilter(){
	
	        @Override
	        public boolean accept(File dir, String name) {
	            return dir.isFile()&&name.endsWith(".java");
	        }
	    });
	    BufferedInputStream bis = null;
	    BufferedOutputStream bos = null;
	    if (!destPath.exists()) {
	        destPath.mkdir();
	    }
	    for (File srcFile : srcFiles) {
	        if (srcFile.isFile()) {
	             bis = new BufferedInputStream(new FileInputStream(srcFile));
	             bos = new BufferedOutputStream(
	             	new FileOutputStream(new File(destPath,srcFile.getName())));
	            int len = 0;
	            byte[] bytes = new byte[1024];
	            while ((len = bis.read(bytes)) != -1) {
	                bos.write(bytes, 0, len);
	                bos.flush();
	            }
	        }
	    }
	    bis.close();
	    bos.close();
	G:复制多级文件夹
		public class CopyDemo {
	    public static void main(String[] args) throws IOException {
	        File srcPath = new File("F:\\test");
	        File destPath = new File("F:\\test1");
	
	        copyFolder(srcPath,destPath);
	
	    }
	
	    public static void copyFolder(File srcPath, File destPath) throws IOException{
	        if (!destPath.exists()) {
	            destPath.mkdir();
	        }
	        File[] files = srcPath.listFiles();
	        for (File file : files) {
	            if (file.isDirectory()) {
	
	                copyFolder(file,new File(destPath,file.getName()));
	            } else if (file.isFile()) {
	                BufferedInputStream bis = new BufferedInputStream(new FileInputStream(file));
	                BufferedOutputStream bos = new BufferedOutputStream(
	                	new FileOutputStream(new File(destPath,file.getName())));
	                int len = 0;
	                byte[] bytes = new byte[1024];
	                while ((len = bis.read(bytes)) != -1) {
	                    bos.write(bytes,0,len);
	                    bos.flush();
	                }
	                bis.close();
	                bos.close();
	            }
	        }
	
	    }
	
	}
	H:键盘录入学生信息按照总分从高到低存储到文本文件
		public class CopyDemo {
		    public static void main(String[] args) throws IOException {
		        Scanner sc = new Scanner(System.in);
		        //比较器返回-1降序，返回1升序
		        TreeSet<Student> studentList = new TreeSet<Student>(new Comparator<Student>() {
		            @Override
		            public int compare(Student o1, Student o2) {
		                int sum1 = o1.getChinese() + o1.getEnglish() + o1.getMath();
		                int sum2 = o2.getChinese() + o2.getEnglish() + o2.getMath();
		                if (sum1 > sum2) {
		                    return -1;
		                } else if (sum1 == sum2) {
		                    if (o1.getName().compareTo(o2.getName()) >=0 ) {
		                        return -1;
		                    } else {
		                        return 1;
		                    }
		                } else {
		                    return 1;
		                }
		            }
		        });
		        for (int i = 0; i < 3; i++) {
		            Student st = new Student();
		            System.out.println("请输入学生信息:");
		            System.out.println("姓名: ");
		            st.setName(sc.nextLine());
		            System.out.println("语文: ");
		            st.setChinese(Integer.valueOf(sc.nextLine()));
		            System.out.println("数学: ");
		            st.setEnglish(Integer.valueOf(sc.nextLine()));
		            System.out.println("英语: ");
		            st.setMath(Integer.valueOf(sc.nextLine()));
		            studentList.add(st);
		        }
		        BufferedWriter bw = new BufferedWriter(new FileWriter(new File("a.txt")));
		        for (Student student : studentList) {
		            bw.write("name: " + student.getName());
		            bw.newLine();
		            bw.write("chinese: "+student.getChinese());
		            bw.newLine();
		            bw.write("english: " + student.getEnglish());
		            bw.newLine();
		            bw.write("math: "+student.getMath());
		            bw.newLine();
		            bw.write("---------------------");
		            bw.newLine();
		            bw.flush();
		        }
		        bw.close();
		    }
	}
	
	class Student {
	    private String name;
	    private int chinese;
	    private int math;
	    private int english;
	
	    public String getName() {
	        return name;
	    }
	
	    public void setName(String name) {
	        this.name = name;
	    }
	
	    public int getChinese() {
	        return chinese;
	    }
	
	    public void setChinese(int chinese) {
	        this.chinese = chinese;
	    }
	
	    public int getMath() {
	        return math;
	    }
	
	    public void setMath(int math) {
	        this.math = math;
	    }
	
	    public int getEnglish() {
	        return english;
	    }
	
	    public void setEnglish(int english) {
	        this.english = english;
	    }
	}
	I:把某个文件中的字符串排序后输出到另一个文本文件中
		File srcFile = new File("a.txt");
	    File destFile = new File("b.txt");
	
	    BufferedReader br = new BufferedReader(new FileReader(srcFile));
	    BufferedWriter bw = new BufferedWriter(new FileWriter(destFile));
	
	    StringBuilder sb = new StringBuilder();
	    String s = null;
	    while ((s = br.readLine()) != null) {
	        sb.append(s);
	    }
	    char[] ch = sb.toString().toCharArray();
	    Arrays.sort(ch);
	    bw.write(ch);
	    bw.close();
	    br.close();
	J:用Reader模拟BufferedReader的特有功能
	K:模拟LineNumberReader的特有功能
# Java多线程

## 1. 多线程(理解)

	(1)多线程：一个应用程序有多条执行路径
		进程：正在执行的应用程序
		线程：进程的执行单元，执行路径
		单线程：一个应用程序只有一条执行路径
		多线程：一个应用程序有多条执行路径
		
		多进程的意义?
			提高CPU的使用率
		多线程的意义?
			提高应用程序的使用率
	(2)Java程序的运行原理及JVM的启动是多线程的吗?
		A:Java命令去启动JVM，JVM会启动一个进程，该进程会启动一个主线程。
		B:JVM的启动是多线程的，因为它至少有两个线程启动了，主线程和垃圾回收线程。
	(3)多线程的实现方案(自己补齐步骤及代码	掌握)
		A:继承Thread类
		public class MyThread extends Thread {
		    @Override
		    public void run() {
		        for (int i = 0; i < 10; i++) {
		            System.out.println(getName() + ":" + i);
		        }
		    }
		
		    public static class MyThreadTest {
		        public static void main(String[] args) {
		            MyThread mt = new MyThread();
		            mt.start();
		        }
		    }
		}
		B:实现Runnable接口
		public class MyRunnable implements Runnable {
		    @Override
		    public void run() {
		        for (int i = 0; i < 10; i++) {
		            System.out.println(Thread.currentThread().getName() + ":" + i);
		        }
		    }
		
		    public static class MyRunnableTest {
		        public static void main(String[] args) {
		            MyRunnable mr = new MyRunnable();
		            Thread td = new Thread(mr);
		
		            td.start();
		        }
		    }
		}
	(4)线程的调度和优先级问题
		A:线程的调度
			a:分时调度
			b:抢占式调度 (Java采用的是该调度方式)
		B:获取和设置线程优先级
			a:默认是5
			b:范围是1-10（Thread.MIN_PRIORITY，Thread.MAX_PRIORITY）
	(5)线程的控制(常见方法)
		A:休眠线程：sleep()
		B:加入线程：join()
		C:礼让线程：yield()
		D:后台线程：setDaemon()
		E:终止线程(掌握)：interrupt()
	(6)线程的生命周期(参照	线程生命周期图解.bmp)
		A:新建
		B:就绪
		C:运行
		D:阻塞
		E:死亡
![线程生命周期图解](https://img-blog.csdn.net/20181003115703845?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjA1MzM2MQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

	(7)电影院卖票程序的实现
		A:继承Thread类
		public class ThreadTicket extends Thread {
		    private static int ticket = 100;
		
		    @Override
		    public void run() {
		       while (true) {
		            if (ticket > 0) {
		                System.out.println(getName() + "正在售出第" + ticket-- + "张票");
		            }
		        }
		    }
		
		    public static class ThreadTicketTest {
		        public static void main(String[] args) {
		            ThreadTicket threadTicket = new ThreadTicket();
		            ThreadTicket threadTicket1 = new ThreadTicket();
		            ThreadTicket threadTicket2 = new ThreadTicket();
		
		            threadTicket.start();
		            threadTicket1.start();
		            threadTicket2.start();
		        }
		    }
		}
		B:实现Runnable接口
		public class RunnableTicket implements Runnable {
		    private int ticket = 100;
		
		    @Override
		    public void run() {
		        while (true) {
		            if (ticket > 0) {
		                System.out.println(getName() + "正在售出第" + ticket-- + "张票");
		            }
		        }
		    }
		
		    public static class RunnableTicketTest {
		        public static void main(String[] args) {
		            RunnableTicket rt = new RunnableTicket();
		            Thread thread = new Thread(rt);
		            Thread thread1 = new Thread(rt);
		            Thread thread2 = new Thread(rt);
		
		            thread.start();
		            thread1.start();
		            thread2.start();
		        }
		    }
		}
	(8)电影院卖票程序出问题
		A:为了更符合真实的场景，加入了休眠100毫秒。
		B:卖票问题
			a:同票多次
			b:负数票
	(9)多线程安全问题的原因(也是我们以后判断一个程序是否有线程安全问题的依据)
		A:是否有多线程环境
		B:是否有共享数据
		C:是否有多条语句操作共享数据
	(10)同步解决线程安全问题
		A:同步代码块
			synchronized(对象) {
				需要被同步的代码;
			}
			
			这里的锁对象可以是任意对象。
			
		B:同步方法
			把同步加在方法上。
			
			这里的锁对象是this
			
		C:静态同步方法
			把同步加在方法上。
			
			这里的锁对象是当前类的字节码文件对象(反射再讲字节码文件对象)
	(11)回顾以前的线程安全的类
		A:StringBuffer
		B:Vector
		C:Hashtable
		D:如何把一个线程不安全的集合类变成一个线程安全的集合类
			用Collections工具类的方法即可。
			List<String> list = Collections.synchronizedList(new ArrayList<String>());
## 1. 多线程(理解)

	(1)JDK5以后的针对线程的锁定操作和释放操作
		Lock锁
		public class RunnableTicket implements Runnable {
		    private int ticket = 100;
		    private ReentrantLock lock = new ReentrantLock();
		
		    @Override
		    public void run() {
		        while (true) {
		            lock.lock();
		            if (ticket > 0) {
		            System.out.println(Thread.currentThread().getName() + "正在售出第" + ticket-- + "张票");
		                try {
		                    Thread.sleep(100);
		                } catch (InterruptedException e) {
		                    e.printStackTrace();
		                }
		            }
		            lock.unlock();
		        }
		    }
		
		    public static class RunnableTicketTest {
		        public static void main(String[] args) {
		            RunnableTicket rt = new RunnableTicket();
		            Thread thread = new Thread(rt);
		            Thread thread1 = new Thread(rt);
		            Thread thread2 = new Thread(rt);
		
		            thread.start();
		            thread1.start();
		            thread2.start();
		        }
		    }
		}
	(2)死锁问题的描述和代码体现
	public class DeadLockDemo implements Runnable {
		    boolean flag;
		
		    @Override
		    public void run() {
		        if (flag) {
		            synchronized (Lock.object1) {
		                System.out.println(Thread.currentThread().getName() + "获取了锁object1");
		                try {
		                    Thread.sleep(100);
		                } catch (InterruptedException e) {
		                    e.printStackTrace();
		                }
		                synchronized (Lock.object2) {
		                    System.out.println(Thread.currentThread().getName() + "获取了锁object2");
		                }
		            }
		        } else {
		            synchronized (Lock.object2) {
		                System.out.println(Thread.currentThread().getName() + "获取了锁object2");
		                try {
		                    Thread.sleep(100);
		                } catch (InterruptedException e) {
		                    e.printStackTrace();
		                }
		                synchronized (Lock.object1) {
		                    System.out.println(Thread.currentThread().getName() + "获取了锁object1");
		                }
		            }
		        }
		    }
		
		    public static void main(String[] args) {
		        DeadLockDemo lockDemo = new DeadLockDemo();
		        DeadLockDemo lockDemo1 = new DeadLockDemo();
		        lockDemo.flag = true;
		        Thread td1 = new Thread(lockDemo);
		        Thread td2 = new Thread(lockDemo1);
		
		        td1.start();
		        td2.start();
		    }
		}
		
		class Lock {
		    public static Object object1 = new Object();
		    public static Object object2 = new Object();
		}
	(3)生产者和消费者多线程体现(线程间通信问题)
		以学生作为资源来实现的
		
		资源类：Student
		设置数据类：SetThread(生产者)
		获取数据类：GetThread(消费者)
		测试类：StudentDemo
		
		代码：
			A:最基本的版本，只有一个数据。
			
				public class ThreadDemo {
				    public static void main(String[] args) {
				        Student student = new Student();
				        SetThread st = new SetThread(student);
				        GetThread gt = new GetThread(student);
				
				        new Thread(st).start();
				        new Thread(gt).start();
				    }
				}
				
				class Student {
				    String name;
				    int age;
				}
				
				class SetThread implements Runnable {
				    private Student student;
				
				    public SetThread(Student student) {
				        this.student = student;
				    }
				
				    @Override
				    public void run() {
				        student.name = "xmos";
				        student.age = 23;
				    }
				}
				
				class GetThread implements Runnable {
				    private Student student;
				
				    public GetThread(Student student) {
				        this.student = student;
				    }
				
				    @Override
				    public void run() {
				        for (int i = 0; i < 100; i++) {
				            System.out.println(student.name + ":" + student.age);
				        }
				    }
				}
			B:改进版本，给出了不同的数据，并加入了同步机制
				public class ThreadDemo {
				    public static void main(String[] args) {
				        Student student = new Student();
				        GetThread gt = new GetThread(student);
				        SetThread st = new SetThread(student);
				
				        new Thread(gt).start();
				        new Thread(st).start();
				    }
				}
				
				class Student {
				    String name;
				    int age;
				}
				
				class SetThread implements Runnable {
				    private Student student;
				    private int x;
				
				    public SetThread(Student student) {
				        this.student = student;
				    }
				
				    @Override
				    public void run() {
				        while (true) {
				            synchronized (student) {
				                if (x % 2 == 0) {
				                    student.name = "xmos";
				                    student.age = 23;
				                } else {
				                    student.name = "tmos";
				                    student.age = 22;
				                }
				
				                x++;
				            }
				        }
				    }
				}
				
				class GetThread implements Runnable {
				    private Student student;
				
				    public GetThread(Student student) {
				        this.student = student;
				    }
				
				    @Override
				    public void run() {
				        for (int i = 0; i < 100; i++) {
				            synchronized (student) {
				                System.out.println(student.name + ":" + student.age);
				            }
				
				        }
				    }
				}
			C:等待唤醒机制改进该程序，让数据能够实现依次的出现
				wait()
				notify()
				notifyAll() (多生产多消费)
	
				public class ThreadDemo {
				    public static void main(String[] args) {
				        Student student = new Student();
				        GetThread gt = new GetThread(student);
				        SetThread st = new SetThread(student);
				
				        new Thread(gt).start();
				        new Thread(st).start();
				    }
				}
				
				class Student {
				    String name;
				    int age;
				    boolean flag;
				}
				
				class SetThread implements Runnable {
				    private Student student;
				    private int x;
				
				    public SetThread(Student student) {
				        this.student = student;
				    }
				
				    @Override
				    public void run() {
				        while (true) {
				            synchronized (student) {
				                if (student.flag) {
				                    try {
				                        student.wait();
				                    } catch (InterruptedException e) {
				                        e.printStackTrace();
				                    }
				                }
				                if (x % 2 == 0) {
				                    student.name = "xmos";
				                    student.age = 23;
				                } else {
				                    student.name = "tmos";
				                    student.age = 22;
				                }
				                x++;
				                student.flag = true;
				                student.notify();
				            }
				        }
				    }
				}
				
				class GetThread implements Runnable {
				    private Student student;
				
				    public GetThread(Student student) {
				        this.student = student;
				    }
				
				    @Override
				    public void run() {
				        for (int i = 0; i < 100; i++) {
				            synchronized (student) {
				                if (!student.flag) {
				                    try {
				                        student.wait();
				                    } catch (InterruptedException e) {
				                        e.printStackTrace();
				                    }
				                }
				                System.out.println(student.name + ":" + student.age);
				                student.flag = false;
				                student.notify();
				            }
				        }
				    }
				}
			D:等待唤醒机制的代码优化。把数据及操作都写在了资源类中
				public class ThreadDemo {
				    public static void main(String[] args) {
				        Student student = new Student();
				        GetThread gt = new GetThread(student);
				        SetThread st = new SetThread(student);
				
				        new Thread(gt).start();
				        new Thread(st).start();
				    }
				}
				
				class Student {
				    private String name;
				    private int age;
				    private int x;
				    private boolean flag;
				
				    synchronized void setStudent() {
				        while (true) {
				            if (flag) {
				                try {
				                    wait();
				                } catch (InterruptedException e) {
				                    e.printStackTrace();
				                }
				            }
				            if (x % 2 == 0) {
				                name = "xmos";
				                age = 23;
				            } else {
				                name = "tmos";
				                age = 22;
				            }
				            x++;
				            flag = true;
				            notify();
				        }
				    }
				
				    synchronized void getStudent() {
				        for (int i = 0; i < 100; i++) {
				            if (!flag) {
				                try {
				                    wait();
				                } catch (InterruptedException e) {
				                    e.printStackTrace();
				                }
				            }
				            System.out.println(name + ":" + age);
				            flag = false;
				            notify();
				        }
				    }
				}
				
				class SetThread implements Runnable {
				    private Student student;
				
				    public SetThread(Student student) {
				        this.student = student;
				    }
				
				    @Override
				    public void run() {
				        student.setStudent();
				    }
				}
				
				class GetThread implements Runnable {
				    private Student student;
				
				    public GetThread(Student student) {
				        this.student = student;
				    }
				
				    @Override
				    public void run() {
				        student.getStudent();
				    }
				}
	(4)线程组
		public class ThreadGroupDemo {
		   public static void main(String[] args) {
		        ThreadGroup tg = new ThreadGroup("MyThreadGroup");
		        MyRunnable mr = new MyRunnable();
		        Thread th1 = new Thread(tg, mr, "xmos");
		        Thread th2 = new Thread(tg, mr, "tmos");
		
		        th1.start();
		        th2.start();
		
		    }
		}
		
		class MyRunnable implements Runnable {
		
		    @Override
		    public void run() {
		        System.out.println(Thread.currentThread().getThreadGroup().getName() + ":" 
		        	+ Thread.currentThread().getName());
		    }
		}
		(5)线程池
			public class ThreadPoolDemo {
			    public static void main(String[] args) {
			        ExecutorService pool = Executors.newFixedThreadPool(3);
			        MyRunnable mr = new MyRunnable();
			        pool.submit(mr);
			        pool.submit(mr);
			
			        pool.shutdown();
			    }
			}
			
			class MyRunnable implements Runnable{
			
			    @Override
			    public void run() {
			        System.out.println(Thread.currentThread().getName());
			    }
			}
	(6)多线程实现的第三种方案
		public class ThreadPoolDemo {
		    public static void main(String[] args) {
		        ExecutorService pool = Executors.newFixedThreadPool(3);
		        MyCallable mc = new MyCallable();
		        pool.submit(mc);
		        pool.submit(mc);
		
		        pool.shutdown();
		    }
		}
		
		class MyCallable implements Callable {
		    @Override
		    public Object call() throws Exception {
		        System.out.println(Thread.currentThread().getName());
		        return null;
		    }
		}
	(7)定时器
		案例1：
			public class TimerDemo {
			    public static void main(String[] args) throws ParseException {
			        Timer t = new Timer();
			        String s = new String("2018-10-03 12:46:00");
			        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
			        Date date = sdf.parse(s);
			        t.schedule(new Boom(), date, 100);
			
			        t.cancel();


​			
			    }
			}
		
		class Boom extends TimerTask {
		
		    @Override
		    public void run() {
		        System.out.println("Boom!");
		    }
		}
		案例2：
			public class TimerDemo {
			    public static void main(String[] args) throws ParseException {
			        Timer t = new Timer();
			        t.schedule(new Boom(t), 300, 100);
			    }
			}
			
			class Boom extends TimerTask {
			    private Timer t;
			    int i = 0;
			
			    public Boom(Timer t) {
			        this.t = t;
			    }
			
			    @Override
			    public void run() {
			        System.out.println("Boom---" + ++i);
			
			        if (i == 30) {
			            t.cancel();
			        }
			    }
			}
	(8)多线程的面试题
		## 1. 多线程有几种实现方案，分别是哪几种?
		两种。
		
		继承Thread类
		实现Runnable接口
		
		扩展一种：实现Callable接口。这个得和线程池结合。
	
		## 2. 同步有几种方式，分别是什么?
			两种。
			
			同步代码块
			同步方法
		
		## 3. 启动一个线程是run()还是start()?它们的区别?
			start();
			
			run():封装了被线程执行的代码,直接调用仅仅是普通方法的调用
			start():启动线程，并由JVM自动调用run()方法
		
		## 4. sleep()和wait()方法的区别
			sleep():必须指时间;不释放锁。
			wait():可以不指定时间，也可以指定时间;释放锁。
		
		## 5. 为什么wait(),notify(),notifyAll()等方法都定义在Object类中
			因为这些方法的调用是依赖于锁对象的，而同步代码块的锁对象是任意锁。
			而Object代码任意的对象，所以，定义在这里面。
		
		## 6. 线程的生命周期图
			新建 -- 就绪 -- 运行 -- 死亡
			新建 -- 就绪 -- 运行 -- 阻塞 -- 就绪 -- 运行 -- 死亡
			建议：画图解释。


## 2. 设计模式(理解)

	(1)面试对象的常见设计原则
		单一
		开闭
		里氏
		依赖注入
		接口
		迪米特
	(2)设计模式概述和分类
		A:经验的总结
		B:三类
			创建型
			结构型
			行为型
	(3)改进的设计模式
		A:简单工厂模式（Simple Factory Pattern）
			public abstract class Animal {
			    public abstract void eat();
			
			    public static Animal getDog() {
			        return new Dog();
			    }
			
			    public static Animal getCat() {
			        return new Cat();
			    }
			
			    public static void main(String[] args) {
			        Animal dog = Animal.getDog();
			        Animal cat = Animal.getCat();
			
			        dog.eat();
			        cat.eat();
			    }
			}
			
			class Dog extends Animal{
			
			    @Override
			    public void eat(){
			        System.out.println("eat bone");
			    }
			}
			
			class Cat extends Animal{
			
			    @Override
			    public void eat() {
			        System.out.println("eat fish");
			    }
			}
		B:工厂方法模式（Factory Method Pattern）
			public abstract class Animal {
			    public abstract void eat();
			
			    public static Animal getDog() {
			        return new Dog();
			    }
			
			    public static Animal getCat() {
			        return new Cat();
			    }
			
			    public static void main(String[] args) {
			        Animal dog = new DogFactory().getAnimal();
			        Animal cat = new CatFactory().getAnimal();
			
			        dog.eat();
			        cat.eat();
			    }
			}
			
			interface AnimalFactory {
			    Animal getAnimal();
			}
			
			class DogFactory implements AnimalFactory {
			
			    @Override
			    public Animal getAnimal() {
			        return new Dog();
			    }
			}
			
			class CatFactory implements AnimalFactory {
			
			    @Override
			    public Animal getAnimal() {
			        return new Cat();
			    }
			}
			
			class Dog extends Animal {
			
			    @Override
			    public void eat() {
			        System.out.println("eat bone");
			    }
			}
			
			class Cat extends Animal {
			
			    @Override
			    public void eat() {
			        System.out.println("eat fish");
			    }
			}
		C:单例模式(Singleton Pattern掌握)
			a:饿汉式（开发常用）
				public class TeacherDemo {
				    public static void main(String[] args) {
				        Teacher t1 = Teacher.getTeacher();
				        Teacher t2 = Teacher.getTeacher();
				
				        System.out.println(t1 == t2);
				    }
				}
				
				class Teacher {
				    private static Teacher teacher = new Teacher();
				
				    private Teacher() {
				    }
				
				    public static Teacher getTeacher() {
				        return teacher;
				    }
				}
			b:懒汉式（面试常用，容易有线程安全问题，需要线程同步）
				public class StudentDemo {
				    public static void main(String[] args) {
				        Student s1 = Student.getStudent();
				        Student s2 = Student.getStudent();
				
				        System.out.println(s1 == s2);
				    }
				}
				
				class Student {
				    private static Student student = null;
				
				    private Student() {
				    }
				
				    public synchronized static Student getStudent() {
				        if (Objects.isNull(student)) {
				            student = new Student();
				        }
				        return student;
				    }
				}
	(4)Runtime
		JDK提供的一个单例模式应用的类。
		还可以调用系统命令。
		public class RuntimeDemo {
		    public static void main(String[] args) throws IOException {
		        Runtime r = Runtime.getRuntime();
		        r.exec("touch 1.txt");
		    }
		}

# JavaGUI

# Java网络编程

## 1. 网络编程(理解)
```java
(1)网络编程：用Java语言实现计算机间数据的信息传递和资源共享
(2)网络编程模型
	应用层-表示层-会话层-传输层-网络层-数据链路层-物理层
(3)网络编程的三要素
	A:IP地址
		a:点分十进制：192.168.1.1
		b:IP地址的组成：网络号段+主机号段
		c:IP地址的分类：
			A类	1.0.0.1---127.255.255.254	
				(1)10.X.X.X是私有地址(私有地址就是在互联网上不使用，而被用在局域网络中的地址)										
				(2)127.X.X.X是保留地址，用做循环测试用的。
			B类	128.0.0.1---191.255.255.254	172.16.0.0---172.31.255.255是私有地址。169.254.X.X是保留地址。
			C类	192.0.0.1---223.255.255.254	192.168.X.X是私有地址
			D类	224.0.0.1---239.255.255.254 	
			E类	240.0.0.1---247.255.255.254
		d:dos命令
			ipconfig; telnet; ping
		e:InetAddress
			public class IPDemo {
			    public static void main(String[] args) throws UnknownHostException {
			        InetAddress ip = InetAddress.getByName("192.168.2.203");
			        System.out.println(ip.getHostName() + ":" + ip.getHostAddress());
			    }
			}
	B:端口
		是应用程序的标识。范围：0-65535。其中0-1024不建议使用。
	C:协议
		UDP:数据打包,有限制,不连接,效率高,不可靠
		TCP:建立数据通道,无限制,效率低,可靠
(3)Socket机制
	A:通信两端都应该有Socket对象
	B:所有的通信都是通过Socket间的IO进行操作的
(4)UDP协议发送和接收数据(掌握 自己补齐代码)
	发送：
		创建UDP发送端的Socket对象
		创建数据并把数据打包
		发送数据
		释放资源
	接收：
		创建UDP接收端的Socket对象
		创建数据包用于接收数据
		接收数据
		解析数据包
		释放资源
		
(5)TCP协议发送和接收数据(掌握 自己补齐代码)
	发送：
		创建TCP客户端的Socket对象
		获取输出流，写数据
		释放资源
		
	接收：
		创建TCP服务器端的Socket对象
		监听客户端连接
		获取输入流，读取数据
		释放资源
(6)案例：
	A:UDP
		a:最基本的UDP协议发送和接收数据
		b:把发送数据改进为键盘录入
		发送端：
		public class SendSocket {
		    public static void main(String[] args) throws IOException {
		        //设置socket发送的端口号，不设置的则为随机端口号
		        DatagramSocket ds = new DatagramSocket(12307);
		        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		        String s = null;
		        while ((s = br.readLine()) != null) {
		            if (Objects.equals(s, "bye")) {
		                break;
		            }
		            byte[] bytes = s.getBytes();
		            DatagramPacket dp = new DatagramPacket(
		            	bytes, bytes.length, InetAddress.getByName("192.168.2.203"), 12306);
		            ds.send(dp);
		        }
		        ds.close();
		    }
		}
		接收端：
		public class ReceiveSocket {
					    public static void main(String[] args) throws IOException {
					        //设置socket接收的端口号
					        DatagramSocket ds = new DatagramSocket(12306);
					        while (true) {
					            byte[] bytes = new byte[1024];
					            DatagramPacket dp = new DatagramPacket(bytes, bytes.length);
					            ds.receive(dp);
					            String s = new String(dp.getData(), 0, dp.getLength());
					            System.out.println(dp.getAddress().getHostAddress() + ":" + dp.getPort() + "\n" + s);
					        }
					
					    }
					}
		c:一个简易聊天小程序并用多线程改进
		public class ChatRoom {
		    public static void main(String[] args) {
		        Thread sendThread = new Thread(new Runnable() {
		            @Override
		            public void run() {
		                try {
		                    DatagramSocket ds = new DatagramSocket(12307);
		                    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		                    String s = null;
		                    while ((s = br.readLine()) != null) {
		                        if (Objects.equals(s, "bye")) {
		                            break;
		                        }
		                        byte[] bytes = s.getBytes();
		                        DatagramPacket dp = new DatagramPacket(
		                        	bytes, bytes.length, InetAddress.getByName("192.168.2.203"), 12306);
		                        ds.send(dp);
		                    }
		                    ds.close();
		                } catch (IOException e) {
		                    e.printStackTrace();
		                }
		            }
		        });
		        Thread receiveThread = new Thread(new Runnable() {
		            @Override
		            public void run() {
		                try {
		                    DatagramSocket ds = new DatagramSocket(12306);
		                    while (true) {
		                        byte[] bytes = new byte[1024];
		                        DatagramPacket dp = new DatagramPacket(bytes, bytes.length);
		                        ds.receive(dp);
		                        String s = new String(dp.getData(), 0, dp.getLength());
		                        System.out.println(dp.getAddress().getHostAddress() + ":" + dp.getPort() + "\n" + s);
		                    }
		                } catch (IOException e) {
		                    e.printStackTrace();
		                }
		            }
		        });
		
		        sendThread.start();
		        receiveThread.start();
		    }
		}
	B:TCP
		a:最基本的TCP协议发送和接收数据
		client：
		public class Client {
		    public static void main(String[] args) throws IOException {
		        Socket client = new Socket("192.168.2.203", 8809);
		        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(client.getOutputStream()));
		        
		        bw.write("hello tcp");
		        bw.close();
		    }
		}
		server：
		public class Server {
		    public static void main(String[] args) throws IOException {
		        ServerSocket server = new ServerSocket(8809);
		        Socket s = server.accept();
		        BufferedReader br = new BufferedReader(new InputStreamReader(s.getInputStream()));
		
		        System.out.println(br.readLine());
		        br.close();
		    }
		}
		b:服务器给出反馈
		client：
		public class Client {
		    public static void main(String[] args) throws IOException {
		        Socket client = new Socket("192.168.2.203", 8809);
		        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(client.getOutputStream()));
		
		        bw.write("hello tcp");
		        bw.flush();
		
		        //给服务端发送停止写入的信号，否则服务端会一直阻塞
		        client.shutdownOutput();
		
		        BufferedReader br = new BufferedReader(new InputStreamReader(client.getInputStream()));
		        System.out.println(br.readLine());
		
		        bw.close();
		        br.close();
		        client.close();
		    }
		}
		server：
		public class Server {
		    public static void main(String[] args) throws IOException {
		        ServerSocket server = new ServerSocket(8809);
		        Socket s = server.accept();
		        BufferedReader br = new BufferedReader(new InputStreamReader(s.getInputStream()));
		
		        System.out.println(br.readLine());
		
		        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(s.getOutputStream()));
		        bw.write("已收到");
		        bw.flush();
		
		        bw.close();
		        br.close();
		        server.close();
		        server.close();
		    }
		}
		c:客户端键盘录入服务器控制台输出
		client：
		public class Client {
		    public static void main(String[] args) throws IOException {
		        Socket client = new Socket("192.168.2.203", 8809);
		        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(client.getOutputStream()));
		
		        String s = null;
		        while ((s = br.readLine()) != null) {
		            if (Objects.equals(s, "bye")) {
		                break;
		            }
		            bw.write(s);
		            bw.newLine();
		            bw.flush();
		        }
		
		        //给服务端发送停止写入的信号，否则服务端会一直阻塞
		        client.shutdownOutput();
		
		        br.close();
		        bw.close();
		        client.close();
		    }
		}
		server：
		public class Server {
		    public static void main(String[] args) throws IOException {
		        ServerSocket server = new ServerSocket(8809);
		        Socket s = server.accept();
		        BufferedReader br = new BufferedReader(new InputStreamReader(s.getInputStream()));
		
		        String client = null;
		        while ((client = br.readLine()) != null) {
		            System.out.println(client);
		        }
		
		        br.close();
		        s.close();
		        server.close();
		    }
		}
		d:客户端键盘录入服务器写到文本文件
		client：
		public class Client {
		    public static void main(String[] args) throws IOException {
		        Socket s = new Socket("192.168.2.203",8809);
		        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(s.getOutputStream()));
		
		        String msg = null;
		        while ((msg = br.readLine()) != null){
		            if (Objects.equals(msg, "bye")) {
		                break;
		            }
		            bw.write(msg);
		            bw.newLine();
		            bw.flush();
		        }
		
		        s.shutdownOutput();
		
		        BufferedReader br1 = new BufferedReader(new InputStreamReader(s.getInputStream()));
		        System.out.println(br1.readLine());
		
		        br.close();
		        br1.close();
		        bw.close();
		        s.close();
		    }
		}
		server：
		public class Server {
		    public static void main(String[] args) throws IOException {
		        ServerSocket ss = new ServerSocket(8809);
		        Socket s = ss.accept();
		
		        BufferedWriter bw = new BufferedWriter(new FileWriter("test.txt"));
		        BufferedReader br = new BufferedReader(new InputStreamReader(s.getInputStream()));
		
		        String msg = null;
		        while ((msg = br.readLine()) != null) {
		            bw.write(msg);
		            bw.newLine();
		            bw.flush();
		        }
		
		        BufferedWriter bw1 = new BufferedWriter(new OutputStreamWriter(s.getOutputStream()));
		        bw1.write("已全部接收！");
		        bw1.newLine();
		        bw1.flush();
		
		        br.close();
		        bw.close();
		        bw1.close();
		        s.close();
		        ss.close();
		    }
		}
		e:客户端读取文本文件服务器控制台输出
		client：
		public class Client {
		    public static void main(String[] args) throws IOException {
		        Socket client = new Socket("localhost", 8808);
		
		        BufferedReader br = new BufferedReader(new InputStreamReader(new FileInputStream("1.txt")));
		        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(client.getOutputStream()));
		
		        String s = null;
		        while ((s = br.readLine()) != null) {
		            bw.write(s);
		            bw.newLine();
		            bw.flush();
		        }
		
		        bw.close();
		        br.close();
		        client.close();
		    }
		}
		server：
		public class Server {
			public static void main(String[] args) throws IOException {
				ServerSocket server = new ServerSocket(8808);

				Socket client = server.accept();

				BufferedReader br = new BufferedReader(new InputStreamReader(client.getInputStream()));

				String s = null;
				while ((s = br.readLine()) != null) {
					System.out.println(s);
				}
			}
			}
		f:客户端读取文本文件服务器写到文本文件
		g:上传图片
		h:多线程改进上传文件
```
# Java反射
## 1. 反射(理解)
```java
(1)类的加载及类加载器
(2)反射：
	通过字节码文件对象，去使用成员变量，构造方法，成员方法
(3)反射的使用
	A:通过反射获取构造方法并使用
	B:通过反射获取成员变量并使用
	C:通过反射获取成员方法并使用
(4)反射案例
	A:通过反射运行配置文件的内容
	B:通过反射越过泛型检查
	C:通过反射给任意的一个对象的任意的属性赋值为指定的值
(5)动态代理
```
## 2. 设计模式
```java
(1)装饰设计模式
	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	
	Scanner sc = new Scanner(System.in);
(2)模版设计模式
```
## 3. JDK新特性
```java
(1)JDK5(掌握)
	装箱和拆箱
	泛型
	增强for
	静态导入
	可变参数
	枚举
(2)JDK6(了解)
(3)JDK7(理解)
	二进制的表现形式
	用_分隔数据
	switch语句可是用字符串
	泛型推断(菱形泛型)
	多catch的使用
	自动释放资源的用法
(4)JDK8(了解)
	可以去网上了解资料
```