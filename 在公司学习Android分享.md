学习Android几个过程

- Java基础知识。 如 集合、io、网络、线程等
- Android基础知识。  如  几大布局 、 常用的控件 、 四大组件、动画、网络等


开发安卓需要Java语言， kotlin语言也行，但是目前的情况还是一Java为主。  


##基础语法

###包声明

Java :   com.wuming.platform.kotlin

kotlin :  源文件可以放在任意目录下。 还有就是文件名可以和类名不一样。
### 定义变量

Java 

	//可变变量
     String name="android";
    //不可变
     final String ="android";
kotlin 

    //可变
     var name: String ="Android"
    //可以根据值来推断类型
      var name="Android"
    //不可变
      val name:String ="Android"

> 局部变量：只声明（编译阶段）不会报错，但是使用时必须初始化。 成员变量： Java可以不初始化，jvm会加载类的时候会初始化，kotlin会报错，必须初始化。


### 定义函数

Java 

 	public int add(int a, int b){
        return a+b;
    }

kotlin
      
    fun add(a: Int , b: Int):Int{
        return a+b
    }
    //没有返回值
    fun add(a: Int):Unit{
    }
    //Unit 可省略
    fun add(a: Int){
    }

    //表达式作为函数体。 返回类型自动判断
    fun add(a: Int,b :Int)=a+b


###  数据类型 


 kotlin 
 
>Byte、Short、Int、Long、Float、Double

 Java 

>byte、short、int 、long、 float 、double、 boolean 、char 


###条件和循环控制

Java ： if..else ,while, do...while, for 

kotlin ： if...else , while , do...while , when 

 kotlin 用法

		//条件
 		var x:Int =0
        if (x>0){
            println("x 大于 0")
        }else if(x==0){
            println("x 等于 0")
        }else {
            println("x 小于 0") 
        } 

		var a=1
        var b=2
        var c= if (a>=b) a else b
        println("取 a ，b 中最大值为$c" )

		var d=4
        if (d in 1..8){
            println("$d 在期间")
        }else{
            println("$d 不在期间")
        }

        var e=1
		 when(e){
            1 -> println("e==1")
            2-> println("e==2")
            else -> println("e 既不是 1 也不是 2 ")
        }
        when(e){
            1,2 -> println("e ==1 or e==2")
            else -> println("e 既不是 1 也不是 2 ")
        }
		//循环
		 for (i in 1..4) print(i)//打印结果 1234
         for (i in 4 downTo 2) print(i)//4321
         for (i in 1..4 step 2) print(i)//13
         for (i in 4 downTo 1 step 2) print(i)//42
         var arr= arrayOf(1,2,3,4,5)
         for ( m in arr) print(m)//12345
		 var x = 5
    	 while (x > 0) {
         println( x--)//54321
   		 }
    	var y = 5
   		do {
        println(y--)//54321
    	} while(y>0)

###java

		//条件
 		int x=0;
        if (x>0){
           System.out.println("x 大于 0");
        }else if(x==0){
            System.out.println("x 等于 0");
        }else {
            System.out.println("x 小于 0");
        }

        int a=3;
        int b=2;
        int c= a>b? a :b;
        System.out.println("取 a ，b 中最大值为"+c);

        int d =2;
        switch (d){
            case 1:
                System.out.println("e==1");
                break;
            case 2:
                System.out.println("e==2");
                break;
            default:
                System.out.println("e 既不是1 也不是2 ");
        }
		//循环
 	    String arr[]={"1","2","3","4","5"};
        for (int i=0 ; i>arr.length;i++){
            System.out.println(arr[i]);
        }
        List<String> list=new ArrayList();
        for ( String i:list){
            System.out.println(i);
        }
        list.stream().forEach(s->System.out.println(s));


>return : 直接返回  break ：终止循环  continue :  继续下次循环。
> kotlin if可以有返回值， Java不行。

### 类
- 类的定义

 Java 

	public class People {
    String name;
    
    public People(){}
    public People(String name){
		this.name=name;
	 }
    
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
	}

kotlin 

 	class People private constructor(var name: String){
     var mName =name
     init { }
    constructor( age:Int):this("zhangsan"){}
	}

1. class 前面可以添加修饰符， 默认为 public。
2. People后面constructor是主构造器，没有修饰符时  可以省略constructor。
3. mName 成员变量必须要初始化，可以用 name变量。
4. 其他部分的constructor为次构造器，参数不可以var和val修饰，次构造器必须直接或间接的调用主构造器。
5. 没有主构造器，会默认地创建一个无参构造器。

> 成员函数  kotlin 默认实现 set和get 方法


- 类的实例化

Java 

    People p=new People("zhangsan");

kotlin

	var p:People=People("zhangsan")


###继承 重写 

 Java的父类是Object, kotlin是 Any  都只能是单继承。

Java

	public class Student extends People {
    public Student() {
        super();
    }
    @Override
    public String getName() {
        return super.getName();
    }
	}

kotlin

	open  class Student(age: Int) : People(age) {
    override fun getAge(): String {
        return super.getAge()
    }
	}

> kotlin： 默认是final ，方法和类 如需重写的话， 必须是open修饰。 子类同样也是，方法重写的话必须用override修饰，不然报错

### 可见性修饰符

 Java 

- public ： 包内和包外都能访问
- protected ： 在同一个包内，包外的类继承该类的子类也能访问
- 默认 : 默认值  同一个包内，包外不能访问。
- private : 只能在该类中和子类访问

kotlin 

- public : 默认值，包内和包外都能访问
- protected: 只能在该类中和子类访问
- private : 只能在该类内部访问
- internal ： 同一模块下访问


##Android 

###Android概述 

Android是一个开源的，基于Linux的移动设备操作系统， Android是由谷歌及其他公司带领的开放手机联盟开发的。

### Android 开发环境搭建
- 下载JDK  并配置
- 下载Android studio  并安装
- 下载SDK  并配置
- 如用kotlin开发， 在Android studio下载kotlin插件



 ![avatar](/img/f.jpg)

### Android 应用程序组件


- Activity : 简单来说就是界面，用来处理用户和屏幕之间的交互
- Sevices: 处理与应用之间关联的后台操作
- BroadcastReceivers: 处理Android操作系统和应用之间的通信
- Content Provider : 处理数据库与数据库管理方面的问题

activity



- activity生命周期

![avatar](/img/a1.gif)

  创建一个Activity。 继承AppCompatActivity就行

	public class AppActivity extends AppCompatActivity {

	}


- services 

> 运行在后台，没有界面，一般执行长时间的操作。 如播放音乐。
> 
	
	public class AppService extends Service {
 	@Override
    public void onReceive(Context context, Intent intent) {

    }
	}

- broadcastreceices

> 响应其他的应用或系统的发来的广播消息。 

	public class AppReceiver extends BroadcastReceiver {

    @Override
    public void onReceive(Context context, Intent intent) {
    
    }
	}

- contentproviders

>为不同的应用之间提供数据共享，提供统一的接口。

	public class AppContentProvider extends ContentProvider {
    public AppContentProvider() {
    }



## Android 应用

- 效果

![avatar](/img/c.gif)      ![avatar](/img/d.gif)

- 项目结构 

![avatar](/img/a1.png)  

- 布局

![avatar](/img/a2.png)  
![avatar](/img/a3.png)  




- demo 源码

[https://github.com/songshuilin/WeatherDemo](https://github.com/songshuilin/WeatherDemo)





