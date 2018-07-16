javaBasic


 # 02 # 

classpath
-------------
	搜索类的路径
	javac.exe			  java.exe
*.java  ----------> .class   ----------> 进程


clasapth: . 
javac.exe -cp HelloWorld.java			//文件名
javac -cp d:\x\x\xx\x HelloWorld.java

java -cp xx\x\x\xx HelloWorld		//

//
class HelloWorld{
	public static void main(String[] args){
		System.out.println("hello world"); //line 		
	}
}

 # 05 # 

面向对象的特征
-------------------
	1.封装
	2.继承
	3.多态 Parent p = new Child();
java栈默认是1m，至少是108k，

类成员
------------
	1.成员变量
	2.成员函数
	3.构造函数
	4.构造代码块
	5.静态代码块
		在类加载过程中调用，而且只调用一次。


对象创建过程
----------------
	new Dog();
	1.在内存中分配内存空间。
	2.对成员变量赋默认值.
	3.执行构造代码块或赋值语句,执行顺序从上到下。
	4.构造函数.

内部类的class文件命名是：主类＋$＋内部类名
匿名类的class文件命名是：主类＋$＋(1,2,3....)
java提高篇(十)-----详解匿名内部类 https://www.cnblogs.com/chenssy/p/3390871.html


 # 07 # 
抽象类和接口
https://www.cnblogs.com/dolphin0520/p/3811437.html

1.语法层面上的区别

1）抽象类可以提供成员方法的实现细节，而接口中只能存在public abstract 方法；
2）抽象类中的成员变量可以是各种类型的，而接口中的成员变量只能是public static final类型的；
3）接口中不能含有静态代码块以及静态方法，而抽象类可以有静态代码块和静态方法；
4）一个类只能继承一个抽象类，而一个类却可以实现多个接口。

2.设计层面上的区别

　　1）抽象类是对一种事物的抽象，即对类抽象，而接口是对行为的抽象。抽象类是对整个类整体进行抽象，包括属性、行为，但是接口却是对类局部（行为）进行抽象。举个简单的例子，飞机和鸟是不同类的事物，但是它们都有一个共性，就是都会飞。那么在设计的时候，可以将飞机设计为一个类Airplane，将鸟设计为一个类Bird，但是不能将 飞行 这个特性也设计为类，因此它只是一个行为特性，并不是对一类事物的抽象描述。此时可以将 飞行 设计为一个接口Fly，包含方法fly( )，然后Airplane和Bird分别根据自己的需要实现Fly这个接口。然后至于有不同种类的飞机，比如战斗机、民用飞机等直接继承Airplane即可，对于鸟也是类似的，不同种类的鸟直接继承Bird类即可。从这里可以看出，继承是一个 "是不是"的关系，而 接口 实现则是 "有没有"的关系。如果一个类继承了某个抽象类，则子类必定是抽象类的种类，而接口实现则是有没有、具备不具备的关系，比如鸟是否能飞（或者是否具备飞行这个特点），能飞行则可以实现这个接口，不能飞行就不实现这个接口。

　　2）设计层面不同，抽象类作为很多子类的父类，它是一种模板式设计。而接口是一种行为规范，它是一种辐射式设计。什么是模板式设计？最简单例子，大家都用过ppt里面的模板，如果用模板A设计了ppt B和ppt C，ppt B和ppt C公共的部分就是模板A了，如果它们的公共部分需要改动，则只需要改动模板A就可以了，不需要重新对ppt B和ppt C进行改动。而辐射式设计，比如某个电梯都装了某种报警器，一旦要更新报警器，就必须全部更新。也就是说对于抽象类，如果需要添加新的方法，可以直接在抽象类中添加具体的实现，子类可以不进行变更；而对于接口则不行，如果接口进行了变更，则所有实现这个接口的类都必须进行相应的改动。


 # 08 # 
多态：
Parent p = new Child();


 # 9 # 
打jar包方法

堆是存放对象的地方
栈是运行方法  线程|栈
所谓并发 就是同时开启了多个栈

对线程
--------------------
进程	:运行时概念，运行的应用程序。进程间不能共享内存。
线程	:应用程序内部并发执行的代码段，共享内存。

yield		:放弃cpu抢占权，有谦让之意.
join		:等指定的线程执行完之后继续运行。 join方法的原理就是调用相应线程的wait方法进行等待操作的，例如A线程中调用了B线程的join方法，则相当于在A线程中调用了B线程的wait方法，当B线程执行完（或者到达等待时间），B线程会自动调用自身的notifyAll方法唤醒A线程，从而达到同步的目的。
sleep		:静态方法，让线程休眠毫秒数。
daemon		:守护线程.如果应用程序剩余的线程都是守护线程，则程序结束。
通过上述方法可以实现线程间的通讯


 # 10 # 
多线程
wait notify
https://www.cnblogs.com/hapjin/p/5492645.html
多线程中测试某个条件的变化用 if 还是用 while？
说是要把if换成while的理由，应该是wait线程被唤醒之后，会继续从wait那里往下面执行，如果是if的话，就会直接往下面执行，不会再判断if的状态了；但是如果是while的话，从wait那里往下面执行，然后还会判断while中的条件，如果==0的话，还是会继续阻塞，如果是>0，则会执行while语句块外面的remove吧？！其中关键就是被notify唤醒之后，是否会执行条件判断



 # 13 # 

常用collection的对比和特点

![test](https://tanhanqing.github.io/img/note/collection.png)

[Java：集合，Array、Collection(List/Set/Queue)、Map的遍历，比如：ArrayList,LinkedList,HashSet,HashMap](http://www.cnblogs.com/nayitian/archive/2013/03/08/2950730.html)

	一般大家都知道ArrayList和LinkedList的大致区别： 
	     1.ArrayList是实现了基于动态数组的数据结构，LinkedList基于链表的数据结构。 
	     2.对于随机访问get和set，ArrayList觉得优于LinkedList，因为LinkedList要移动指针。 
	     3.对于新增和删除操作add和remove，LinedList比较占优势，因为ArrayList要移动数据。 

	     ArrayList，Vector主要区别为以下几点： 
	（1）：Vector是线程安全的，源码中有很多的synchronized可以看出，而ArrayList不是。导致Vector效率无法和ArrayList相比； 
	（2）：ArrayList和Vector都采用线性连续存储空间，当存储空间不足的时候，ArrayList默认增加为原来的50%，Vector默认增加为原来的一倍； 
	（3）：Vector可以设置capacityIncrement，而ArrayList不可以，从字面理解就是capacity容量，Increment增加，容量增长的参数。

	List：1.可以允许重复的对象。
	    2.可以插入多个null元素。
		3.是一个有序容器，保持了每个元素的插入顺序，输出的顺序就是插入的顺序。
		4.常用的实现类有 ArrayList、LinkedList 和 Vector。ArrayList 最为流行，它提供了使用索引的随意访问，而 LinkedList 则对于经常需要从 List 中添加或删除元素的场合更为合适。

	Set：1.不允许重复对象
	     2. 无序容器，你无法保证每个元素的存储顺序，TreeSet通过 Comparator  或者 Comparable 维护了一个排序顺序。
		3. 只允许一个 null 元素
		4.Set 接口最流行的几个实现类是 HashSet、LinkedHashSet 以及 TreeSet。最流行的是基于 HashMap 实现的 HashSet；TreeSet 还实现了 SortedSet 接口，因此 TreeSet 是一个根据其 compare() 和 compareTo() 的定义进行排序的有序容器。

	1.Map不是collection的子接口或者实现类。Map是一个接口。
	2.Map 的 每个 Entry 都持有两个对象，也就是一个键一个值，Map 可能会持有相同的值对象但键对象必须是唯一的。
	3.TreeMap 也通过 Comparator  或者 Comparable 维护了一个排序顺序。
	4.Map 里你可以拥有随意个 null 值但最多只能有一个 null 键。
	5.Map 接口最流行的几个实现类是 HashMap、LinkedHashMap、Hashtable 和 TreeMap。（HashMap、TreeMap最常用）

	HashMap
	  HashMap 是一个最常用的Map，它根据键的HashCode 值存储数据，根据键可以直接获取它的值，具有很快的访问速度。遍历时，取得数据的顺序是完全随机的。
	  HashMap最多只允许一条记录的键为Null；允许多条记录的值为 Null。
	  HashMap不支持线程的同步（即任一时刻可以有多个线程同时写HashMap），可能会导致数据的不一致。如果需要同步，可以用 Collections的synchronizedMap方法使HashMap具有同步的能力，或者使用ConcurrentHashMap。
	  Hashtable与 HashMap类似，它继承自Dictionary类。不同的是：它不允许记录的键或者值为空；它支持线程的同步（即任一时刻只有一个线程能写Hashtable），因此也导致了 Hashtable在写入时会比较慢。



	LinkedHashMap
	  LinkedHashMap保存了记录的插入顺序，在用Iterator遍历LinkedHashMap时，先得到的记录肯定是先插入的。也可以在构造时带参数，按照应用次数排序。
	在遍历的时候会比HashMap慢，不过有种情况例外：当HashMap容量很大，实际数据较少时，遍历起来可能会比LinkedHashMap慢。因为LinkedHashMap的遍历速度只和实际数据有关，和容量无关，而HashMap的遍历速度和他的容量有关。



	TreeMap
	  TreeMap实现SortMap接口，能够把它保存的记录根据键排序。
	  默认是按键值的升序排序，也可以指定排序的比较器，当用Iterator 遍历TreeMap时，得到的记录是排过序的。




	1. Vector & ArrayList 
	1）Vector的方法都是同步的(Synchronized),是线程安全的(thread-safe)，而ArrayList的方法不是，由于线程的同步必然要影响性能，因此,ArrayList的性能比Vector好。 
	2）当Vector或ArrayList中的元素超过它的初始大小时,Vector会将它的容量翻倍,而ArrayList只增加50%的大小，这样,ArrayList就有利于节约内存空间。

	2. Hashtable & HashMap 
	Hashtable和HashMap它们的性能方面的比较类似 Vector和ArrayList，比如Hashtable的方法是同步的,而HashMap的不是。



	对于PriorityQueue ，观察帮助文档，可以发现，这是jdk1.5以后引入的，
	由此可知，它容量没有界限，且默认排序是自然排序，队头元素是最小元素，故我们可以拿来作为小根堆使用。
	（要注意：默认的PriorityQueue并非保证了整个队列都是有序的，只是保证了队头是最小的）
	对于大根堆，就要借助于comparator比较器，来实现大根堆。（使用默认的初始容量：11）
	 PriorityQueue <Integer> maxHeap = new PriorityQueue<Integer>(11, new Comparator<Integer>() {  

	    @Override  
	    public int compare(Integer o1, Integer o2) {  
		// TODO Auto-generated method stub  
		return o2.compareTo(o1);  
	    }  

	});  


 # 15 # 

图说设计模式
http://design-patterns.readthedocs.org/zh_CN/latest/index.html
如何通俗理解设计模式及其思想?
https://juejin.im/post/5b3cddb6f265da0f8145c049

 # 16 # 

字节流 字符流讲解
*https://blog.csdn.net/nightcurtis/article/details/51324105  
https://www.cnblogs.com/runningTurtle/p/7088125.html


 # 18  # 
socket
IBM Rose

 # 19 # 
 # 20 # 
实现简单聊天工具

 # 21 # 
JDBC MySql
表设计原则 https://my.oschina.net/dongzerun/blog/289736
命名规范 https://my.oschina.net/dongzerun/blog/289664



数据库访问性能优化  索引相关 http://www.cnblogs.com/easypass/archive/2010/12/08/1900127.html

 # 22 # 

事务性
----------------
	Transaction:事务
				commit			//提交
				rollback		//回滚.
	和db之间一组操作。
	四个特性acid:

	atomic		//原子性,不可分割.
	consistent	//一致性,不能破坏掉.
	isolate		//隔离型,事务独立的。
	durable		//永久性,永久有效.

jdbc的事务处理
-----------------
	conn.setAutocommit(false);		//关闭自动提交

	conn.commit();					//提交事务

	conn.rollback(SavePoint sp);	//回滚事务


 # 23 # 
事务并发的现象&锁
事务并发执行,三个现象
------------
脏读			//读未提交,
				//一个事务读取了另外一个事务改写还未提交的数据，
				//如果另外一个事务在稍后时刻回滚则脏读发生了。

不可重复读		//读不回去
				//一个事务在进行相同条件的查询连续的两次或者两次以上，
				//每次结果都不同。
				//查询期间，有其他事务进行update操作.


幻读			//读多了
				//一个进行相同条件查询，在后来的查询中会发现原来的记录。
				//查询期间，有其他事务进行insert操作.


隔离级别 : isolation level
--------------------------
	1.1,read uncommitted,读未提交,导致脏读.
	2.2,read committed,读已提交，避免了脏读，不可重复和幻读还能发生。
	3.4,repeatable read,可以重复读，避免了不可重复读，幻读还能发生。
	4.8,serializable,串行，避免了了以上现象。


 # 24 # 
JVM 

所以堆与栈的区别很明显：

1.栈内存存储的是局部变量而堆内存存储的是实体；
2.栈内存的更新速度要快于堆内存，因为局部变量的生命周期很短；
3.栈内存存放的变量生命周期一旦结束就会被释放，而堆内存存放的实体会被垃圾回收机制不定时的回收。


反射
见文件夹java24

//加载类,返回Class对象
Class clazz = Class.forName("com.thq.java24.jvm.Person");

//通过Class动态创建对象.
Object obj = clazz.newInstance();

//得到setName(String x);
Method m = clazz.getDeclaredMethod("setName",String.class,String.class);

//设置可访问性
m.setAccessible(true);

//等价于obj.setName("tom");
m.invoke(obj, "t","om");

 # 25 # 
内省 针对get/set方法
//得到bean信息
BeanInfo bi = Introspector.getBeanInfo(Person.class);
//得到属性描述符
PropertyDescriptor[] pds = bi.getPropertyDescriptors();
//
for(PropertyDescriptor pd : pds){
	//得到属性名
	System.out.println(pd.getName());
	//取得getXxx方法
	System.out.println(pd.getReadMethod());
	//取得setXxx方法
	System.out.println(pd.getWriteMethod());
}

 # 26 # 
NIO的本质 是非阻塞
