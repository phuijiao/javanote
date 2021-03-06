# JavaGuide

# Java

## 基础

### 基础知识总结

#### 1. Java基础知识

##### 1. 面向对象和面向过程的区别

- **面向过程：面向过程性能比面向对象高。**因为类调用时需要实例化，开销比较大，比较消耗资源，所以当性能是最重要的考量因素的时候，比如单片机、嵌入式开发、Linux/Unix等一般采用面向过程开发。**但是，面向过程没有面向对象易维护、易复用、易扩展。**
- **面向对象：面向对象易维护、易复用、易扩展。**因为面向对象有封装、继承、多态的特性，所以可以设计出低耦合的系统，使系统更加灵活、更加易于维护。但是，**面向对象性能比面向过程低。**

> 这个并不是根本原因，面向过程也需要分配内存，计算内存偏移量，Java性能差的主要原因并不是因为它是面向对象语言，而是Java是半编译语言，源文件编译后产生的在JVM执行的文件并不是可以直接被CPU执行的二进制机械码。
>
> 而面向过程语言大多都是直接编译成机械码在电脑上执行，并且其他一些面向过程的脚本语言性能也不一定比Java好。



##### 2. Java语言有哪些特点？

1. 简单易学；
2. 面向对象（封装、继承、多态）；
3. 平台无关性（ Java 虚拟机实现平台无关性）；
4. 可靠性；
5. 安全性；
6. 支持多线程（C++ 从 C++11才开始支持多线程）；
7. 支持网络编程并且很方便（Java语言诞生本身就是为简化网络编程设计的）；
8. 编译与解释并存；



##### 3.  关于JVM、JDK和JRE最详细通俗的解答

###### JVM

Java虚拟机（JVM）是运行Java字节码的虚拟机。JVM有针对不同系统的特定实现（Windows、Linux、macOS），目的是使用相同的字节码，它们都会给出相同的结果。

**什么是字节码？采用字节码的好处是什么？**

> 在Java中，JVM可以理解的代码就叫做`字节码`（即扩展名为`.class`的文件），它不面向任何特定的处理器，只面向虚拟机。Java语言通过字节码的方式，在一定程度上解决了传统解释型语言执行效率低的问题，同时又保留了解释型语言可移植的特点。所以Java程序运行时比较高效，而且，由于字节码并不针对一种特定的机器，因此，Java程序无须重新编译可在多种不同操作系统的计算机上运行。

**Java程序从源码到运行一般有下面3布：**

![Java程序运行过程](.\.assets\Java 程序运行过程.png)

我们需要格外注意的是`.class` -> 机械码 这一步。在这一步JVM类加载器首先加载字节码文件，然后通过解释器逐行解释执行，这种方式的执行速度会相对比较慢。而且，有些方法和代码块是经常需要被调用的（也就是所谓的热点代码），所以后面引进了JIT编译器，而JIT编译器属于运行时编译。当JIT编译器完成第一次编译后，会将字节码对应的机械码保存下来，下次可以直接使用。而我们知道，机械码的执行效率肯定高于Java解释器的。这也解释了我们为什么经常说Java是编译与解释共存的语言。

**总结**

Java

虚拟机（JVM）是运行Java字节码的虚拟机。JVM有针对不同系统的特定实现，目的是使相同的字节码，它们都会给出相同的结果。字节码和不同系统的JVM实现是Java语言”一次编译，随处可以运行“的关键所在。



###### JDK和JRE

JDK是Java Development Kit，它是功能齐全的Java SDK。它拥有JRE所拥有的一切，还有编译器（javac）和工具（如javadoc和jdb）。它能过创建和编译程序。

JRE是Java运行时环境。它是运行已编译Java程序所需的所有内容的集合，包括Java虚拟机（JVM），Java类库，Java命令和其他一些基础构建。但是，他不能用于创建新程序。

如果只是为了运行Java程序的话，那么只需要安装JRE就可以了，如果需要进行一些Java编程方便的工作，那么就需要安装JDK了。但是，这不是绝对的，有时，即使不打算在计算机上进行任何Java开发，仍然需要安装JDK。例如，如果要使用JSP部署Web应用程序，应用服务器会将JSP转换为Java servlet，并且需要使用JDK来编译servlet。



##### 4. Oracle JDK和OpenJDK的对比

OpenJDK项目主要基于Sun捐献的HotSpot源代码。因此，OpenJDK被选为Java 7的参考实现，由Oracle工程师维护。

**总结：**

1. Oracle JDK大概每隔6个月发一次主要版本，而OpenJDK版本大概每3个月发布一次。
2. OpenJDK是一个参考模型并且是完全开源的，而Oracle JDK是OpenJDK的一个实现，并不是完全开源的。
3. Oracle JDK比OpenJDK更稳定。OpenJDK和Oracle JDK的代码几乎相同，但Oracle JDK有更多的类和一些错误修复。
4. 在响应性和JVM性能方面，Oracle JDK与OpenJDK相比提供了更好的性能。
5. Oracle JDK不会为即将发布的版本提供长期的支持，用户每次都必须通过更新到最新版本获得支持。
6. Oracle JDK根据二进制代码许可协议获得许可，而OpenJDK根据GPL v2许可获得许可。



##### Java和C++的区别

- 都是面向对象的语言，都支持封装、继承、多态。
- Java不提供指针来直接访问内存，程序内存更加安全。
- Java的类是单继承的，C++支持多重继承；虽然Java的类不可以多继承，但是接口可以多继承。
- Java有自动内存管理机制，不需要程序员手动释放无用内存。
- **在C语言中，字符串或字符数组最后都会有一个额外的字符'\0'来表示结束。但是，Java语言中没有结束符这一概念。**

> Java里面一切都是对象，是对象的话，字符串肯定就有长度，既然有长度，编译器就可以确定要输出的字符个数，当然也没有必要去浪费那1个字节的空间用于标明字符串的结束了。



##### 26， ==与equals

==：它的作用是判断两个对象的地址是不是相等。即，判断两个对象是不是同一个对象（基本数据类型的‘==’比较的是值，引用数据类型的‘==‘比较的是内存地址）。

equals()：它的作用也是判断两个对象是否相等。但它一般有两种使用情况：

- 情况1：类没有覆盖equals()方法。则通过equals()比较该类的两个对象时，等价于通过’==‘比较这两个对象。
- 情况2：类覆盖了equals()方法。一般，我们都覆盖equals()方法来比较两个对象的内容是否相等；若它们的内容相等，则返回true（即，认为这两个对象相等）。



##### 27. hashCode与equals

hashCode()的作用是获取哈希码，也称为散列码；它实际上是返回一个int整数。这个哈希码的作用是确定该对象在哈希表中的索引位置。hashCode()定义在JDK的Object.java中，这就意味着Java中的任何类都包含有hashCode()函数。

**为什么重写equals()时必须重写hashCode()方法？**

hashCode()的默认行为是对堆上的对象产生独特值。如果没有重写hashCode(),则该class的两个对象无论如何都不会相等（即使这两个对象指向相同的数据）。



##### 28. 为什么Java中只有值传递？

- 按值调用表示方法接收的是调用者提供的值，而按引用调用表示方法接收的是调用者提供的变量地址。一个方法可以修改传递引用所对应的变量值，而不能修改传递值调用所对应的变量值。
- Java程序设计语言总是采用按值调用。也就是说，方法得到的是所有参数值的一个拷贝，也就是说，方法不能修改传递给它的任何参数变量的内容。
- 一个方法不能修改一个基本数据类型的参数（即数值型或布尔型）。
- 一个方法可以改变一个对象参数的状态。
- 一个方法不能让对象参数引用一个新的对象。



##### 29. 简述线程、程序、进程的基本概念。以及它们之间关系是什么？

**线程**与进程相似，但线程是一个比进程更小的执行单位。一个进程在其执行的过程中可以产生多个线程。与进程不同的是同类的多个线程共享同一块内存空间和一组系统资源，所以系统在产生一个线程，或是在各个线程之间且换工作时，负担要比进程小得多，也正因为如此，线程也被称为轻量级进程。

**程序**是包含指令和数据的文件，被存储在磁盘或其他的数据存储设备中，也就是说程序是静态的代码。

**进程**是程序的一次执行过程，是系统运行程序的基本单位，因此进程是动态的。系统运行一个程序既是一个进程从创建、运行到消亡的过程。

线程是进程划分成的更小的运行单位。线程和进程最大的不同在于基本上各进程是独立的，而各线程则不一定，因为同一进程中的线程极有可能会相互影响。从另一角度来说，进程属于操作系统的范畴，主要是同一段时间内，可以同时执行一个以上的程序，而线程则是在同一程序内几乎同时执行一个以上的程序段。



##### 30. 线程有哪些基本状态？

| 状态名称     | 说明                                                         |
| :----------- | ------------------------------------------------------------ |
| NEW          | 初始状态，线程被构建，但是还没有调用start()方法              |
| RUNNABLE     | 运行状态，Java线程将操作系统中的就绪和运行两种状态笼统地称作“运行中” |
| BLOCKED      | 阻塞状态，表示线程阻塞于锁                                   |
| WAITING      | 等待状态，表示线程进入等待状态，进入该状态表示当前线程需要等待其他线程做出一些特定动作（通知或中断） |
| TIME_WAITING | 超时等待状态，该状态不同于WAITING，它是可以在指定的时间自行返回的 |
| TERMINATED   | 终止状态，表示当前线程已经执行完毕                           |

![Java线程状态变迁](.\.assets\Java 线程状态变迁.png)



##### 31. 关于final关键字的一些总结

final关键字主要用在三个地方：变量、方法、类。

1. 对于final变量，如果是基本数据类型的变量，则数值一旦在初始化之后便不能更改；如果是引用类型的变量，则在对其初始化之后便不能再让其指向另一个对象。
2. 当用final修饰一个类时，表明这个类不能被继承。final类中的所有成员方法都会被隐式地指定为final方法。
3. 使用final方法的原因有两个。第一个原因是把方法锁定，以防止任何继承类修改它的含义；第二个原因是效率。



##### 32. Java中的异常处理

![Java异常类层次结构图](.\.assets\exception-architechture-java.png)

**异常和错误的区别：异常能够被程序本身处理，错误是无法处理的。**



##### 33. Java序列化中如果有些字段不想进行序列化，怎么办？

对于不想进行序列化的变量，使用transient关键字修饰。

transient关键字的作用是：阻止实例中那些用此关键字修饰的变量序列化；当对象被反序列化时，被transient修饰的变量值不会被持久化和恢复。transient只能修饰变量，不能修饰类和方法。



##### 34. 获取用键盘输入常用的两种方法

方法一：通过Scanner

```java
Scanner input = new Scanner(Systen.in);
String s = input.nextline();
input.close();
```

方法二：通过BufferedReader

```java
BufferedReader input = new BufferedReader(new InputStreamReader(System.in));
String s = input.readLine();
```



##### 35. Java中IO流

###### Java中IO流分为几种？

- 按照流的流向分，可以分为输入流和输出流；
- 按照操作单元分，可以划分为字节流和字符流；
- 按照流的角色划分为节点流和处理流。

派生关系：

- InputStream/Reader:所有的输入流的基类，前者是字节输入流，后者是字符输入流。
- OutputStream/Writer:所有输出流的基类，前者是字节输出流，后者是字符输出流。

![IO-操作对象分类](.\.assets\IO-操作对象分类.png)

###### 既然有了字节流，为什么还要有字符流？

字符流是由Java虚拟机将字节转换得到的，问题就出在这个过程还算是非常耗时的，并且，如果我们不知道编码类型就很容易出现乱码问题。所以，I/O流就干脆提供了一个直接操作字符的接口，方便我们平时对字符进行流操作。如果音频文件、图片等媒体文件用字节流比较好，如果涉及到字符的话使用字符流比较好。

###### BIO、NIO、AIO有什么区别？

- BIO（Blocking I/O）：同步阻塞I/O模式，数据的读取写入必须阻塞在一个线程内等待其完成。适用于连接数不高时。可以让每一个连接专注于自己的I/O并且编程模型简单，也不用过多考虑系统的过载、限流问题。
- NIO（Non-blocking或New I/O）：NIO是一种同步非阻塞的I/O模型，它是支持面向缓冲的，基于通道的I/O操作方法。
- AIO（Asynchronous I/O）：AIO也就是NIO 2。在Java 7 中引入了NIO的改进版NIO 2，它是异步非阻塞的IO模型。异步IO是基于事件和回调机制实现的，也就是应用操作之后会直接返回，不会阻塞在那里，当后台处理完成，操作系统会通知相应的线程进行后续的操作。



##### 38. 深拷贝vs浅拷贝

1. 浅拷贝：对基本数据类型进行值传递，对引用数据类型进行引用传递般的拷贝，此为浅拷贝。
2. 深拷贝：对基本数据类型进行值传递，对引用数据类型，创建一个新的对象，并复制其内容，此为深拷贝。



#### 2. Java基础知识疑难点、易错点

##### 1. 基础

###### 1.1. 正确使用equals方法

Object的equals方法容易抛出空指针异常，应使用常量或者确定有值的对象来调用equals。

不能使用一个值为null的引用类型变量来调用非静态方法，否则会抛出异常。



###### 1.2. 整型包装类值的比较

所有整型包装类对象值的比较必须使用equals方法。

当使用自动装箱方式创建一个Integer对象时，当数值在-128~127时，会将创建的Integer对象缓存起来，当下次再出现该数值时，直接从缓存中取出对应的Integer对象。



###### 1.3. BigDecimal

**1.3.1. BigDecimal的用处**

浮点数之间的等值判断，基本数据类型不能用==来比较，包装数据类型不能用equals来判断。（存在**精度丢失**）

使用BigDecimal来定义浮点数的值，再进行浮点数的运算操作。



**1.3.2. BigDecimal的大小比较**

`a.comparaTo(b)`:返回-1表示小于，0表示等于，1表示大于。



**1.3.4. BigDecimal的使用注意事项**

在使用BigDecimal时，为了防止精度丢失，推荐使用它的BigDecimal(String)构造方法来创建对象。



**1.3.5 总结**

BigDecimal主要用来操作（大）浮点数，BigIntrger主要用来操作大整数（超过long类型）。

BigDecimal的实现利用到了BigInteger，所不同的是BigDecimal加入了小数的概念。



###### 1.4. 基本数据类型与包装数据类型的使用标准

《阿里巴巴Java开发手册》

- 【强制】所有的POJO类属性必须使用包装数据类型。
- 【强制】RPC方法的返回值和参数必须使用包装数据类型。
- 【推荐】所有的局部变量使用基本数据类型。



##### 2. 集合

###### 2.1. Arrays.asList()使用指南

`Arrays.asList()`在平时开发中还是比较常见的，我们可以使用它将一个数组转换为一个List集合。

`Arrays.asList()`将数组转换为集合后，底层其实还是数组。不能使用其修改集合的相关方法，它的add/remove/clear方法会抛出异常。

说明：asList的返回对象是Arrays内部类，并没有实现集合的修改方法。Arrays.asList体现的是适配器模式，只是转换接口，后台的数据仍是数组。



#### 3. 【选看】J2EE基础知识

##### Servlet总结

在Java Web程序中，Servlet主要负责接收用户请求。



##### 阐述Servlet和CGI的区别？

CGI：通用网关接口（Common Gateway Interface）是一个Web服务器主机提供信息服务的标准接口。

通过CGI接口，Web服务器就能够获取客户端提交的信息，转交给服务器端的CGI程序进行处理，最后返回结果给客户端。



##### Servlet接口中有哪些方法及Servlet生命周期探秘

**生命周期：Web容器加载Servlet并将其实例化后，Servlet生命周期开始，**容器运行其init()方法进行Servlet的初始化；请求到达时调用Servlet的service()方法，service()方法会根据需要调用与请求对应的doGet或doPost等方法；当服务器关闭或项目被卸载时服务器会将Servlet实例销毁，此时会调用Servlet的destroy()方法。**init方法和destroy方法只会执行一次，service方法客户端每次请求Servlet都会执行。**Servlet中有时会用到一些需要初始化与销毁的资源，因此可以把初始化资源的代码放入init方法中，销毁资源的代码放入destroy方法中，这样就不需要每次处理客户端的请求都要初始化与销毁资源。



##### get和post请求的区别

get和post请求实际上是没有区别的。

可以把get和post当作两个不同的行为，两者并没有本质的区别，底层都是TCP连接。get请求用来从服务器上获得资源，而post是用来向服务器提交数据。

GET产生一个TCP数据包；POST产生两个TCP数据包。

- 对于GET方式的请求，浏览器会把http header和data一并发送出去，服务器响应200（返回数据）；
- 而对于POST，浏览器先发送header，服务器响应100 continue，浏览器再发送data，服务器响应200 ok（返回数据）。
- 据研究，在网络环境好的环境下，发一次包的时间和发两次包的时间差别基本可以无视。而在网络环境差的情况下，两次包的TCP在验证数据包完整性上，有非常大的有点。
- 并不是所有浏览器都会在POST中发送两次包，Firefox就只发送一次。



### 重要知识点详解

#### 1. 枚举

```java
System.out.println(PizzaStatus.ORDERED.name().getClass());//class java.lang.String
System.out.println(PizzaStatus.ORDERED.getClass());//class shuang.kou.enumdemo.enumtest.PizzaStatus
```



#### 2. Java常见关键字总结：final、static、this、super

##### static关键字

###### static关键字主要有以下四种使用场景：

1. 修饰成员变量和成员方法：被static修饰的成员属于类，不属于单个这个类的某个对象，被类中所有对象共享，可以并且建议通过类名调用。被static声明的成员变量属于静态成员变量，静态成员变量存放在Java内存区域的方法区。
2. 静态代码块：静态代码块定义在类中方法外，静态代码块在非静态代码块之前执行（静态代码块 -> 非静态代码块 -> 构造方法）。该类不管创建多少对象，静态代码块只执行一次。
3. 静态内部类（static修饰类的话只能修饰内部类）：静态内部类与非静态内部类之间存在一个最大的区别：非静态内部类在编译完成之后会隐含地保存着一个引用，该引用是指向创建它的外围类，但是静态内部类却没有。没有这个引用就意味者：1.它的创建是不需要外围类的创建。2.它不能使用任何外围类的非static成员变量和方法。
4. 静态导包（用来导入类中的静态资源）：格式为：`import static`这两个关键字连用就可以指定导入某个类中的指定静态资源，并且不需要使用类名调用类中静态成员，可以直接使用类中静态成员变量和成员方法。



##### this关键字

this关键字用于引用类的当前实例。



##### super关键字

super关键字用于从子类访问父类的变量和方法。



**使用this和super要注意的问题：**

- 在构造器中使用`super()`调用父类中的其他构造方法时，该语句必须处于构造器的首行，否则编译器会报错。另外，this调用本类中的其他构造方法时，也要放在首行。
- this、super不能用在static方法中。

> 被static修饰的成员属于类，不属于单个这个类的某个对象，被类中所有对象共享。而this代表本类对象的引用，指向本类对象；而super代表对父类对象的引用，指向父类对象；所以，this和super是属于对象范畴的东西，而静态方法是属于类范畴的东西。



##### 静态代码块与非静态代码块

相同点：都是在JVM加载类时且在构造方法执行之前执行，在类中都可以定义多个，定义多个时按定义的顺序执行，一般在代码块中对一些static变量进行赋值。

> 静态代码块可能在第一次new的时候执行，但不一定只在第一次new的时候执行。比如通过`Class.forName("ClassDemo")`创建Class对象的时候也会执行。



非静态代码块与构造函数的区别是：非静态代码块是给所有对象进行统一初始化，而构造函数是给对应的对象初始化，因为构造函数是可以有多个的，运行哪个构造函数就会创建什么样的对象，但无论建立哪个对象，都会先执行相同的构造代码块。也就是说，构造代码块中定义的是不同对象共性的初始化内容。



#### 什么是反射机制？反射机制的应用场景有哪些？

##### 反射机制介绍

Java反射机制是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意一个方法和属性；这种动态获取的信息以及动态调用对象的方法的功能称为Java语言的反射机制。



##### 反射机制优缺点

- **优先：**运行期类型的判断，动态加载类，提高代码灵活度。
- **缺点：**1. 性能瓶颈：反射相当于一系列解释操作，通知JVM要做的事情，性能比直接的Java代码要慢得多。2. 安全问题：让我们可以动态操作改变类的属性同时也增加了类的安全隐患。



##### 反射的应用场景

**反射是框架设计的灵魂**

模块化的开发，通过反射去调用对应的字节码；动态代理设计模式也采用了反射机制，还有我们日常使用的Spring/Hibernate等框架也大量使用到了反射机制。



### 其他：

#### JAD反编译

基本用法：`jad xxx.class`,会生成直接可读的xxx.jad文件。



## 并发

### 面试题总结

#### 1.Java并发基础常见面试题总结

##### 2.请简要描述线程与进程的关系、区别及优缺点？

从JVM角度说进程和线程之间的额关系

###### 2.1. 图解进程和线程的关系

![img](.\.assets\JVM运行时数据区域.png)

从图中可以看出：一个进程中可以有多个线程，多个线程共享进程的堆和方法区（JDK1.8之后的元空间）资源，但是每个线程有自己的程序计数器、虚拟机栈和本地方法栈。

总结：线程是进程划分成的更小的运行单位。线程和进程最大的不同在于基本上各进程是独立的，而各线程则不一定，因为同一进程中的线程极有可能会相互影响。线程执行开销小，但不利于资源的管理和保护；而进程正相反。

###### 程序计数器为什么是私有的？

程序计数器主要有下面两个作用：

1. 字节码解释器通过改变程序计数器来依次读取指令，从而实现代码的流程控制，如：顺序执行、选择、循环、异常处理。
2. 在多线程的情况下，程序计数器用于记录当前线程执行的位置，从而当线程被切换回来的时候能够知道线程上次运行到哪了。

需要注意的是，如果执行的是native方法，那么程序计数器记录的是undefined地址，只有执行的是Java代码时程序计数器记录的才是下一条指令的地址。

所以，程序计数器私有主要是为了**线程切换后能恢复到正确的执行位置。**



#### 2. Java并发进阶常见面试题总结

##### 1. synchronized关键字

###### 1.1. 说一说自己对于synchronized关键字的了解

synchronized关键字解决的是多个线程之间访问资源的同步性，synchronized关键字可以保证被它修饰的方法或者代码块在任意时刻只能有一个线程执行。

在早期Java版本中，synchronized属于重量级锁，效率低小，因为监视器锁（monitor）是依赖于底层的操作系统的Mutex Lock来实现的，Java的线程是映射到操作系统的原生线程之上的。如果要挂起或者唤醒一个线程，都需要操作系统帮忙完成，而操作系统实现线程之间的切换时需要从用户态转换到内核态，这个状态之间的转换需要相对比较长的时间，时间成本相对较高，这也是为什么早期的synchronized效率低的原因。庆幸的是在Java 6 之后Java官方对从JVM层面对synchronized较大优化，如自旋锁、适应性自旋锁、锁消除、锁粗化、偏向锁、轻量级锁等技术来减少锁操作的开销。



###### 1.2. 说说自己是怎么使用synchronized关键字，在项目中用到了吗？

**synchronized关键字最主要的三种使用方式：**

- **修饰实例方法：**作用于当前对象实例加锁，进入同步代码前要获得当前对象实例的锁。
- **修饰静态方法：**也就是给当前类加锁，会作用于类的所有对象实例，因为静态成员不属于任何一个实例对象，是类成员。所以如果一个线程A调用一个实例对象的非静态synchronized方法，而线程B需要调用这个实例对象所属类的静态synchronized方法，是允许的，不会发生互斥现象，因为访问静态synchronized方法占用的锁是当前类的锁，而访问非静态synchronized方法占用的锁是当前实例对象锁。
- **修饰代码块：**指定加锁对象，对给定对象加锁，进入同步代码块前要获得给定对象的锁。

**总结：**synchronized关键字加到static静态方法和synchronized(class)代码块上都是给Class类上锁。synchronized关键字加到实例方法上给对象实例上锁。尽量不用使用synchronized(String a)，因为JVM中，字符串常量池具有缓冲功能。



###### 1.3. 讲一下synchronized关键字的底层原理

**①synchronized同步语句块的情况**

synchronized同步语句块的实现使用的是monitorenter和monitorexit指令，其中monitorenter指令指向同步代码块的开始位置，monitorexit指令则指明同步代码块的结束位置。

当执行monitorenter指令时，线程试图获取锁也就是获取monitor（monitor对象存在于每个Java对象的对象头中，synchronized锁便是通多这种方式获取锁的，也是为什么Java中任意对象可以作为锁的原因）的持有权。当计数器为0则可以成功获取，获取后将锁计数器设置为1也就是加1。相应的在执行monitorexit指令后，将锁计数器设置为0，表明锁被释放。如果获取对象锁失败，那当前线程就要阻塞等待，直到锁被另一个线程释放为止。

**②synchronized修饰方法的情况**

synchronized修饰的方法并没有monitorenter指令和monitorexit指令，取而代之的却是ACC_SYNCHRONIZED标识，该标识指明了该方法是一个同步方法，JVM通过该ACC_SYNCHRONIZED访问标识来辨别一个方法是否声明为同步方法，从而执行相应的同步调用。



###### 1.5. 谈谈synchronized和ReentrantLock的区别

**①两者都是可重入锁**

“可重入锁”概念是：自己可以再次获取自己的内部锁。比如一个线程获得了某个对象的锁，此时这个对象锁还没有释放，当其再次想要获取这个对象的锁的时候还是可以获取的，如果锁不可重入的话，就会造成死锁。同一个线程每次获取锁，锁的计数器都自增1，所以要等到锁的计数器下降为0时才能释放锁。

**②synchronized依赖于JVM而ReentrantLock依赖于API**

ReentrantLock是JDK层面实现的（也就是API层面，需要lock()和unlock()方法配合try/finally语句块来完成）。

**③ReentrantLock比synchronized增加了一些高级功能**

⑴等待可中断；⑵可实现公平锁；⑶可实现选择性通知（锁可以绑定多个条件）



##### 2. volatile关键字

volatile关键字的作用就是指示JVM，这个变量是不稳定的，每次使用它都到主存中进行读取。即是保证变量的可见性，还有一个作用是防止指令重排序。



###### 2.2. 并发编程的三个重要特性

1. **原子性：**一个操作或者多次操作，要么所有的操作全部都得到执行并且不会受到任何因素的干扰而中断。要么所有的操作都执行，要么都不执行。`synchronized`可以保证代码片段的原子性。
2. **可见性：**当一个变量对共享变量进行了修改，那么另外的线程都是立即可以看到修改后的最新值。`volatile`关键字可以保证共享变量的可见性。
3. **有序性：**代码在执行的过程中的先后顺序，Java在编译器以及运行期间的优化，代码的执行顺序未必就是编写代码时候的顺序。`volatile`关键字可以禁止指令进行重排序优化。



###### 2.3. 说说synchronized关键字和volatile关键字的区别

`synchronized`关键字和`volatile`关键字是两个互补的存在，而不是对立的存在：

- **volatile关键字**是线程同步的轻量级实现，所以volatile性能肯定比synchronized关键字要好。但是volatile关键字只能用于变量，而synchronized关键字可以修饰方法以及代码块。
- 多线程访问volatile关键字不会发生阻塞，而synchronized关键字可能会发生阻塞。
- volatile关键字能保证数据的可见性，但不能保证数据的原子性。synchronized关键字两者都能保证。
- volatile关键字主要用于解决变量在多个线程之间的可见性，而synchronized关键字解决的是多个线程之间访问资源的同步性。



##### 3. ThreadLocal

###### 3.1. ThreadLocal简介

通常情况下，我们创建的变量是可以被任何一个线程访问并修改的。如果想实现每一个线程都有自己的专属本地变量可用ThreadLocal类。ThreadLocal类主要解决的就是让每个线程绑定自己的值。

OOM：Out Of Memory（内存溢出）



### 必备知识点：

#### 2. Java线程池学习总结

##### 四 ThreadPoolExecutor使用示例

###### 4.3 几个常见的对比

4.3.2 execute()和submit()

1. execute()方法用于提交不需要返回值的任务，所以无法判断任务被线程池执行成功与否。
2. submit()方法用于提交需要返回值的任务。线程池会返回一个Future类型的对象，通过这个Future对象可以判断任务是否执行成功，并且可以通过Future的get()方法来获取返回值，get()方法会阻塞当前线程直到任务完成，而使用get(long timeout,TimeUnit unit)方法则会阻塞当前线程一段时间后立即返回，这时候有可能任务没有执行完成。



4.3.3 `shutdown() ` VS `shutdownNow()`

- `shutdown()`:关闭线程池，线程池的状态变为 `SHUTDOWN`。线程池不再接受新任务了，但是队列里的任务得执行完毕。
- `shutdownNow()` :关闭线程池，线程的状态变为 `STOP`。线程池会终止当前正在运行的任务，并停止处理排队的任务并返回正在等在执行的List。



##### 五 几种常见的线程池详解

###### 5.1 FixedThreadPool

5.1.3 为什么不推荐使用FixedThreadPool ?

1. 当线程池中的线程数达到 `corePoolSize`后，新任务将在无界队列中等待，因此线程池中的线程数不会超过 `corePoolSize`。
2. 由于使用无界队列时 `maximumPoolSize`将是一个 无效参数，因为不可能存在任务队列满的情况。所以，通过创建 `FixedThreadPool`的源码可以看出创建的 `FixedThreadPool`的 `corePoolSize`和 `maximumPoolSize`被设置为同一个值。
3. 由于1和2，使用无界队列时 `keepAliveTime`将是一个无效参数。
4. 运行中的 `FixedThreadPool`（未执行 `shutdown()`或 `shutdownNow()`）不会拒绝任务，在任务比较多的时候会导致OOM（内存溢出）。



#### 乐观锁与悲观锁

##### 何为悲观锁与乐观锁

###### 悲观锁

总是假设最坏的情况，每次去拿数据的时候都会认为别人会修改，所以每次在拿数据的时候都会上锁，这样别人想拿这个数据就会阻塞直到它拿到锁（共享资源；每次只给一个线程使用，其他线程阻塞，用完后再把资源转让给其他线程）。传统的关系型数据库里边就用到了很多这种锁机制，比如行锁、表锁等，读锁、写锁等，都是在做操作之前先上锁。Java中 `synchronized`和 `ReentrantLock`等独占锁就是悲观锁思想的实现。



###### 乐观锁

总是假设最好的情况，每次去拿数据的时候都认为别人不会修改，所以不会上锁，但是在更新的时候会判断一下在此期间别人有没有去更新这个数据，可以使用版本号机制和CSA算法实现。乐观锁适用于多读的应用类型，这样可以提高吞吐量，像数据库提供的类似于write_condition机制，其实都是提供的乐观锁。在Java中 `java.util.concurrent.atomic`包下面的原子变量类就是使用了乐观锁的一种实现方式CAS实现的。



##### 乐观锁常见的两种实现方式

乐观锁一般会使用版本号机制或CAS算法实现。

###### 1. 版本号机制

一般是在数据表中加上一个数据版本号version字段，表示数据被修改的次数，当数据被修改时，version值会加一。当线程A要更新数据值时，在读取数据的同时也会读取version值，在提交更新时，若刚才读取到的version值为当前数据库中的version值相等时才更新，否则重试更新操作，直到更新成功。



###### 2. CAS算法

即compare and swap （比较交换），是一种有名的无锁算法。无锁编程，即不使用锁的情况下实现多线程之间的线程同步，也就是在没有线程被阻塞的情况下实现变量的同步，所以也叫非阻塞同步。CAS算法你涉及到三个操作数：

- 需要读写的内存值V
- 进行比较的值A
- 拟写入的新值B

当且仅当V的值等于A时，CAS通过原子方式用新值B来更新V的值，否则不会执行任何操作（比较和替换是一个原子操作）。一般情况下是一个自旋操作，即不断的重试。



##### 乐观锁的缺点

###### 1 ABA问题

如果一个变量V初次读取的时候是A值，并且在准备赋值的时候检查到它仍然是A值，那我们就能说明它的值没有被其他线程修改过吗？很明显是不能的，因为在这段时间它的值可能被改为其他值，然后又改回A，那CAS操作就会误认为它没有被修改过。这个问题被称为CAS操作的“ABA”问题。



###### 循环时间长开销大

**自旋CAS（也就是不成功就一直循环执行直到成功）如果长时间不成功，会给CPU带来非常大的执行开销。**如果JVM能支持处理器提供的pause指令那么效率会有一定的提升，pause指令有两个作用，第一它可以延迟流水线执行指令（de-pipeline），使CPU不会消耗过多的执行资源，延迟的时间取决于具体实现的版本，在一些处理器上延迟时间零。第二它可以避免在退出循环的时候因内存顺序冲突（memory order violation）而引起CPU流水线被清空（CPU pipeline flush），从而提高CPU的执行效率。



###### 3 只能保证一个共享变量的原子操作

CAS只对单个共享变量有效，当操作涉及跨多个共享变量时CAS无效。但是从JDK1.5开始，提供 `AtomicReference类`来保证引用对象之间的原子性，你可以把多个变量放在一个对象里来进行CAS操作。我们可以使用锁或者利用 `AtomicReference类`把多个共享变量合并成一个共享变量来操作。



#### 4 JUC中的Atomic原子类总结

##### 1 Atomic原子类介绍

Atomic是指一个操作是不可中断的。即使是在多个线程一起执行的时候，一个操作一旦开始，就不会被其他线程干扰。



#### 5. AQS原理以及AQS同步组件总结

##### 1 ASQ简介

ASQ的全称为（AbstractQueuedSynchronized），ASQ是一个用来构建锁和同步器的框架，使用AQS能简单且高效地构造出应用广泛的大量的同步器。



##### 2 AQS原理

AQS核心思想是，如果被请求的共享资源空闲，则当前请求资源的线程设置为有效的工作线程，并且将共享资源设置为锁定状态。如果被请求的共享资源被占用，那么就需要一套线程阻塞等待以及被唤醒时锁分配的机制，这个机制AQS是用CLH队列锁实现的，即将暂时获取不到锁的线程加入到队列中。



## JVM

### 1. Java内存区域

##### 2.7 直接内存

直接内存并不是虚拟机运行时数据区的一部分，也不是虚拟机规范中定义的内存区域，但是这部分内存也被频繁地使用。而且也可能导致OutOfMemoryError错误出现。

JDK1.4中加入的NIO（New Input /Output）类，引入了一种基于通道（Channel）与缓存区（Buffer）的I/O方式，它可以直接使用Native函数库直接分配堆外内存，然后通过一个存储在Java堆中的DirectByteBuffer对象作为这块内存的引用进行操作。这样就能在一些场景中显著提高性能，因为避免了在Java堆和Native堆之间来回复制数据。



#### 9. 大白话带你认识JVM

#### 三 运行时数据区

##### 3.3 虚拟机栈和虚拟机堆

在进行回收前就要判断哪些对象还存活，哪些已经死去。下面介绍两个基础的计算方法：

1. 引用计数器计算：给对象添加一个引用计数器，每次引用这个对象时计数器加一，引用失效时减一，计数器等于零时就是不会再次使用的。不过这个方法有一种情况就是出现对象的循环引用时GC没法回收。
2. 可达性分析计算：这是一种类似于二叉树的实现，将一系列的GC ROOTS作为起始的存活对象集，从这个节点往下搜索，搜索所走过的路径成为引用链，把能被该集合引用到的对象加入到集合中。搜索当前对象到GC ROOTS没有使用任何引用链时，则说明该对象是不可用的。主流的商用程序语言，例如Java、C#等都是靠这招去判断对象是否存活的。



在Java语言汇总能作为GC ROOTS的对象分为以下几种：

1. 虚拟机栈（栈帧中的本地方法表）中引用的对象（局部变量）
2. 方法区中静态变量所引用的对象（静态变量）
3. 方法区中常量引用的对象
4. 本地方法栈（即native修饰的方法）中JNI引用的对象（JNI是Java虚拟机调用对应的C函数的方式，通过JNI函数也可以创建新的Java对象。且JNI对于对象的局部引用或者全局引用都会把他们指向的对象都标记为不可回收）
5. 已启动的且未终止的Java线程



判断一个对象的死亡至少需要两次标记：

1. 如果对象进行可达性分析之后没有发现与GC Roots相连的引用链，那它将会第一次标记并且进项一次筛选。判断的条件是决定这个对象是否有必要执行finalize()方法。如果对象有必要执行finalize()方法，则被放入F-Queue队列中。
2. GC对F-Queue队列中的对象进行二次标记。如果对象在finalize()方法中重新与引用链上的任何一个对象建立了关联，那么二次标记时则会将它移出“即将回收”集合。如果此时对象还没成功逃脱，那么只能被回收了。



##### 3.4 垃圾回收算法

###### 3.4.1 标记清除算法

标记清除算法就是分为“标记”和“清除”两个阶段。标记出所有需要回收的对象，标记结束后统一回收。

不足的方面就是标记和清除的效率比较低下。而且这种做法会让内存中的碎片非常多。这个导致了如果我们需要使用到较大的内存块时，无法分配到足够的连续内存。



###### 3.4.2 复制算法

它将可用的内存按容量划分为两等分，每次只使用其中的一块。当一块存满了，就把存活的对象copy到另一块上，然后交换指针的内容。这样就解决了碎片化的问题。



###### 3.4.3 标记整理算法

复制算法在对象存活率高的时候会有一定的效率问题，标记过程任然与“标记-清除”算法一样，但后续步骤不是直接对可回收对象进行清理，而是让所有存活的对象都向一端移动，然后直接清理掉边界以外的内存。



###### 3.4.4 分代收集算法

根据对象存活周期的不同将内存划分为几块。一般是把Java堆划分为新生代和老年代，这样就可以根据各个年代的特点采用最合适的收集算法。



## 其他

### 1.I/O:BIO,NIO,AIO总结

当你同步执行某项任务时，你需要等待其完成才能继续执行其他任务。当你异步执行某些操作时，你可以在完成另一个任务之前继续进行。

- **同步：**两个同步任务相互依赖，并且一个任务必须以依赖另一个任务的某种方式执行。比如在 `A->B`事件模型中，你需要先完成A才能执行B。在换句话说，同步调用中被调用者未处理完请求之前，调用不返回，调用者会一直等待结果的返回。
- **异步：**两个异步的任务完全独立的，一方的执行不需要等待另一方的执行。再换句话说，异步调用中一调用就返回，不需要等待结果返回，当结果返回的时候通过回调函数或者其他方式拿着结果再做相关事情。
- **阻塞：**阻塞就是发起一个请求，调用者一直等待请求结果返回，也就是当前线程会被挂起，无法从事其他任务，只有当条件就绪才能继续。
- **非阻塞：**非阻塞就是发起一个请求，调用者不用一直等待着结果返回，可以先去干其他事情。

同步/异步是从行为角度描述事物的，而阻塞和非阻塞描述的当前事物的状态（等待调用结果的状态）。

