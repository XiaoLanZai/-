# 类型转换



### 自动类型转换

![image-20250624103429307](./img/image-20250624103429307.png)



### 强制类型转换

![image-20250624103542876](./img/image-20250624103542876.png)



### 对象的类型转换

父元素为大，子元素为小，所以

* `父类 变量名 = new 子类()`为自动类型转换

* `子类 变量名 = （子类）父类变量`为强制类型转换

### 表达式的自动类型转换

![image-20250624103801527](./img/image-20250624103801527.png)



# 继承

### 权限修饰符

* <font color='red'>private</font>：仅能本类访问

* <font color='red'>default</font>：同一个包的所有类可以访问

* <font color='red'>protected</font>：同一个包的所有类或者不同包的子孙类可以访问

* <font color='red'>public</font>：均能访问

|               | 本类 | 同一个包的类 | 子孙类 | 任何类 |
| ------------- | :--: | :----------: | :----: | :----: |
| private       |  √   |              |        |        |
| default(缺省) |  √   |      √       |        |        |
| protected     |  √   |      √       |   √    |        |
| public        |  √   |      √       |   √    |   √    |

> <font color='red'>父类的私有属性不会被子类所继承</font>，即不可以直接访问，但是实际上私有属性存在于子类的内存中，可以通过父类的方法来访问私有属性

 

### 继承的特点

![image-20250624162228584](./img/image-20250624162228584.png)

### 方法重写

![image-20250624162212878](./img/image-20250624162212878.png)

### 构造器

![image-20250624162934851](./img/image-20250624162934851.png)

> `super()`必须写在子类的构造函数的第一行，不写会默认写一个super（）

### 兄弟构造器

![image-20250624171518658](./img/image-20250624171518658.png)

**java不支持默认值，通过兄弟构造器可以实现cpp的默认参数值**

> `this`和`super`一样，必须写在第一行



# 多态



### 类型转换

![image-20250624190741780](./img/image-20250624190741780.png)

#####  自动类型转换：

* `父类 变量名 = new 子类()`

* 可以调用父类以及<font color='blue'>子类重写的方法</font>（<font color='red'>不能调用子类独有的方法，不能调用子类重写的属性</font>）

##### 强制类型转换

* `子类 变量名 = （子类）父类变量`

* 可以调用子类独有的方法



<font color='blue'>**对象的真实类型**</font>：new 时的类型，无论类型怎么转换，真实类型不会变

> 类型存在继承关系时，可以进行强制类型转换，编译期间不报错
>
> 但是，运行时，<font color='red'>若对象的真实类型与强转后的类型不同时，会报错</font>

```java
		Animal father=new Cat();//自动类型转换，对象的真实类型是Cat
        Cat son=(cat)father;   //强制类型转换
        son.show();            //真实类型是Cat，故可以使用Cat的方法
```

```java
		Animal father=new Animal();//自动类型转换，对象的真实类型是Animal
        Cat son=(cat)father;   //强制类型转换,编译不报错
        son.show();            //真实类型不是Cat，运行时报错
```



<font color='red'>**个人理解：实现多态就是先通过自动类型转换转成上转型对象，此时可以使用重写的方法。如果想使用独有的方法，可以通过强制类型转换转换回去，此时可以使用子类的独有的方法**</font>

# final 和 常量

### final关键字

![image-20250624200702178](./img/image-20250624200702178.png)

### 常量

* 用`static final`修饰的成员变量为常量

* java的常量类似于c中的<font color='red'>宏</font>，与c中的常量不一样 

![image-20250624200736917](./img/image-20250624200736917.png)

# 抽象

### 抽象介绍：

抽象分为抽象类和抽象方法，都用abstract修饰

* **抽象方法**：只有方法签名，没有方法体，前面要加abstract

```java
public abstract void show();
```

* **抽象类**：不能<font color='red'>实例化对象</font>，只能被继承，前面要加abstrat
  * 抽象类中可以没有抽象方法，但是<font color='red'>有抽象方法的类必须是抽象类</font>
  * 一个类继承抽象类，<font color='red'>必须重写所有抽象方法</font>，否则这个类也必须定义为抽象类
  * 成员变量、方法、构造器都可以具备（接口只能有常量和抽象方法）

![image-20250624205634210](./img/image-20250624205634210.png)

# 接口

### 接口介绍

只能有常量和抽象方法，**实现**接口必须重写方法，一个类可以**实现**多个接口。

```java
public interface Runnable {
    String name="";//属性只能有常量，变量前会自动添加public static final,不用自己添加
    void run();//方法只能是抽象方法，方法前会自动添加public abstract，不用自己添加
}
```

### jdk8后新增方法

![image-20250624213901469](./img/image-20250624213901469.png)

![image-20250624213823220](./img/image-20250624213823220.png)

### 抽象类和接口的区别

![image-20250624214309448](./img/image-20250624214309448.png)

# 代码块

分为静态代码块和实例代码块

![image-20250625095540507](./img/image-20250625095540507.png)

# 匿名内部类

![image-20250625103303465](./img/image-20250625103303465.png)

#### 匿名内部类的一个应用

![image-20250625104739116](./img/image-20250625104739116.png)

# Lamda表达式

Lamda表达式用于替换<font color='blue'>函数式接口</font>的<font color='blue'>匿名内部类</font>

> 函数式接口：只有一个抽象方法的接口
>
> ```java
> public interface swim{
>     void swimming();
> }
> ```

Lamda表达式可以简化匿名内部类的代码

##### 例子1

###### 不用Lamda

```java
swim s=new swim(){
    public void swimming(){
        System.out.println("正在游泳");
    }
}
```

###### 用Lamda

```java
swim s=()->{
    System.out.println("正在游泳");
}
```

##### 例子2

###### 不用Lamda

```java
Student[] students=new Student[5];
      students[0]=new Student("小红",10);
      students[1]=new Student("小率",14);
      students[2]=new Student("小烂",12);
      students[3]=new Student("小百",19);
      students[4]=new Student("小黄",30);

      Arrays.sort(students,new Comparator<Student>(){
        	public int compare(Student o1,Student o2){
                return o1.age-o2.age;
            }
    });
```

###### 用Lamda

```java
Student[] students=new Student[5];
      students[0]=new Student("小红",10);
      students[1]=new Student("小率",14);
      students[2]=new Student("小烂",12);
      students[3]=new Student("小百",19);
      students[4]=new Student("小黄",30);

      Arrays.sort(students, (o1,o2)->{return o1.age-o2.age;});
```

# 方法引用

[Java基础-08-函数式编程-方法引用-静态方法引用_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1gb42177hm?spm_id_from=333.788.videopod.episodes&vd_source=f9438212e2fff870501ad8163a0df926&p=90)

懒得看了，以后看吧

# 常用API

### String

#### **String 的构造方法**

![image-20250625172957306](./img/image-20250625172957306.png)

区别：

1. 双引号：会将字符串对象放到<font color='red'>字符串常量池，</font>同一个字符串的String<font color='red'>地址相同</font>

   ```java
   String str1="hh";
   String str2="hh";
   System.out.println(str1==str2);//true
   ```

   

2. 构造函数：每new一个都会为其分配一个内存，String地址不同

   ```java
   String str1=new String("hh");
   String str2=new String("hh");
   System.out.println(str1==str2);//false
   ```

#### 常用方法

![image-20250625174529209](./img/image-20250625174529209.png)

> 判断字符串是否相等用`equals`方法，不能用`==`

### ArrayList

```java
List<Integer> list = new ArrayList<>();
list.add(5);                   // 添加元素
list.add(1, 10);               // 在索引1插入
list.remove(0);                // 删除索引0元素
list.set(2, 20);               // 修改索引2元素
int val = list.get(0);         // 获取元素
int size = list.size();        // 获取大小
Collections.sort(list);        // 排序（默认升序）
Collections.reverse(list);     // 反转
list.subList(1,3).clear();     // 删除子列表
```

# 异常

### 异常体系

![image-20250626081952510](./img/image-20250626081952510.png)

> 区别**编译时异常**和**运行时异常**的代码方法：**编译时异常**没有继承`RuntimeException`,**运行时异常**继承了；如果他直接继承了`exception`那么一定是**编译时异常**	

### 自定义异常

![image-20250626100105285](./img/image-20250626100105285.png)

#### 自定义编译时异常

```java
public class MyException extends  Exception{
    public MyException(){

    }
    public MyException(String message){
        super(message);
    }
}

```

![image-20250626100536211](./img/image-20250626100536211.png)

编译时异常被`throw`时，需要在方法体`throws`异常，相当于踢皮球，自己不处理让调用这个方法的方法处理异常

#### 自定义运行时异常

```java
public class MyException extends  RuntimeException{
    public MyException(){

    }
    public MyException(String message){
        super(message);
    }
}
```

![image-20250626100903819](./img/image-20250626100903819.png)

运行时异常不用`throws`，因为编译器会自动`throws`

### 异常处理

![image-20250626102152104](./img/image-20250626102152104.png)

#### 层层抛出

将所有的异常抛出，直到最高层统一处理

![image-20250626102318030](./img/image-20250626102318030.png)

#### 尝试修复

有异常那么重新执行，直到输入正确为止

![image-20250626102427285](./img/image-20250626102427285.png)

# 泛型

### 泛型类 泛型接口

![image-20250626104412693](./img/image-20250626104412693.png)

![image-20250626104444058](./img/image-20250626104444058.png)

###  泛型方法、通配符、上下限



##### 泛型方法

定义泛型的方法为泛型方法，下图右边的不属于泛型方法，而是泛型类的普通方法，因为不是该方法定义的E

```java
public static <E> void printArray(E[] arr)
{
    for(E e:arr)
        System.out.println(e);
}
public  static void main(String[] args) {
      Student[] students=new Student[5];
      students[0]=new Student("小红",10);
      students[1]=new Student("小率",14);
      students[2]=new Student("小烂",12);
      students[3]=new Student("小百",19);
      students[4]=new Student("小黄",30);
    
      printArray(students);
    }
```

##### 通配符

在使用泛型的时候代表一切类型

![image-20250626110436271](./img/image-20250626110436271.png)

##### 上下限

限制通配符，不能代表一切类型，而是给一个范围

* 泛型上限：`? extends Car`：只能接受Car或者Car的子类
* 泛型下限：`? super Car`: 只能接受Car或者Car的父类

```java
public static void go(ArrayList<? extends Car> cars{
   
}
```



![image-20250626110011896](./img/image-20250626110011896.png)

>泛型不支持基本数据类型，只支持引用数据类型

# 包装类

![image-20250626150232483](./img/image-20250626150232483.png)

### 装箱

将<font color='blue'>基本数据类型</font>转化为<font color='blue'>包装类</font>的过程叫做<font color='red'>**装箱**</font>，分为手动装箱和**自动装箱**

* 手动装箱

```java
Integer i=Integer.valueOf(100);
```

* <font color='red'>自动装箱</font>

```java
Integer j=100;
```

即基本数据类型和包装类可以随意类型转换，故实际应用无需手动装箱



### 拆箱

将<font color='blue'>包装类</font>转化为<font color='blue'>基本数据类型</font>的过程叫做<font color='red'>**拆箱**</font>，分为手动拆箱和**自动拆箱**

* <font color='red'>自动拆箱</font>

```java
Integer i=10;
int j=i;
```



### Integer常量池(128陷阱)

Integer中有个静态内部类为IntegerCathe，也就是Integer常量池，当赋值在-128~127之间，则会直接指向常量池的数据，不会开辟新的内存

```java
	ArrayList<Integer> a=new ArrayList<>();
	a.add(127);
	a.add(127);
	a.add(128);
	a.add(128);

  	System.out.println(a.get(0)==a.get(1));//true
  	System.out.println(a.get(2) == a.get(3));//false
```

>  上例表示如果想比较值的话最好用`equals`方法，别用`==`



* Byte，short、Long的常量池都为-128~127
* Character的常量池为0~127
* Float、Double无常量池

### 其他功能

![image-20250626153336651](./img/image-20250626153336651.png)

##### 包装类->字符串

* ```java
  String str=Integer.toString(10);
  ```

* ```java
  Integer i=10;
  String str=i.toString();
  ```

* ```java
  String str=10+"";//一般用这个方法
  ```

一般不用Integer的方法，而是用`+""`转换



##### <font color='red'>字符串->包装类</font>

```java
int i=Integer.parseInt(str);//转成int
```

```java
Integer i=Integer.valueOf(str);//转成Integer
```

# 集合

 ![image-20250626200524113](./img/image-20250626200524113.png)

## Collection

![image-20250626200624175](./img/image-20250626200624175.png)

### Collection的常用方法

![image-20250626200757947](./img/image-20250626200757947.png)

### List

##### List的独有方法

因为支持索引功能，多了很多与索引有关的方法

![image-20250626200855278](./img/image-20250626200855278.png)

##### ArrayList的底层原理

![image-20250626202556573](./img/image-20250626202556573.png)

* 查询快
* 增删慢

##### LinkedList的底层原理

![image-20250626202710666](./img/image-20250626202710666.png)

* 查询慢
* 增删快

![image-20250626202915743](./img/image-20250626202915743.png)

可以实现栈，队列，双端队列

其中`addFirst`可以用`push`替换，`removeFirst`可以用`pop`替换

### Set

![image-20250626203633615](./img/image-20250626203633615.png)

#### HashSet的底层原理

![image-20250626204931225](./img/image-20250626204931225.png)

![image-20250626205031243](./img/image-20250626205031243.png)

当元素个数大于`长度*加载因子`时,会自动扩容，元素会重新分配位置

![image-20250626205212768](./img/image-20250626205212768.png)

红黑树前身是二叉平衡树，当添加元素时，红黑树会自平衡，搜索效率（二分查找）最大化

![image-20250626205247399](./img/image-20250626205247399.png)

#### HashSet存储自定义类型对象

HashSet有个关键的特性为<font color='red'>**去重**</font>

当两个元素的哈希值映射在数组的同一位置且equals方法返回true时，HashSet才会去重

所以在HashSet中**去重**是依据两个方法：`hashcode()`和`equals()`

* `hashcode()`：决定元素的哈希值
* `equals()`：决定元素是否"值相等"

如果想实现HashSet的<font color='red'>去重</font>方法，就必须让<font color='red'>值相同</font>的对象

1. <font color='blue'>返回相同的哈希值</font>
2. <font color='blue'>equals方法判等为True</font>



但是

* **默认**的`hashcode`方法是依据**<font color='blue'>内存地址</font>**来分配的，也就是哪怕对象的值一样，不同地址那么哈希值就不一样

* **默认**的`equals`方法也是依据<font color='blue'>**内存地址**</font>是否相同来判等，和`==`的效果一样。



**所以必须重写`hashcode`方法和`equals`方法**，才能实现存储自定义类型的对象



如何重写：

​	右键-> `生成` -> `equals()和hashcode() `-> 一直点下一步

#### LinkedHashSet的底层原理

LinkedHashSet只比HashSet多了一个<font color='red'>**有序性**</font>

**本质依旧是数组＋链表＋红黑树实现**，只不过多了一个<font color='red'>**双链表**</font>机制，每个元素都有一个前驱指针和后继指针记录前后元素的位置

当遍历时从头指针依次遍历至尾指针，实现了有序性

![image-20250626215805622](./img/image-20250626215805622.png)

#### TreeSet的底层原理



底层原理：**<font color='red'>红黑树</font>**



![image-20250626222213295](./img/image-20250626222213295.png)

#### TreeSet存储自定义类型对象

TreeSet比HashSet多了个排序性，所以自定类有比较的能力

两种方式：

1. 实现`Comparable`接口，重写`compareTo`方法

   ```java
   public int compareTo(Student o) {
       return Integer.compare(this.age,o.age);
   }
   ```

   小技巧：比较时只需要return 该包装类的`compare`方法即可，如果降序在前面加个负号；

2. 传入`Comparator`比较器，重写`Compare`方法

   ```java
   Set<Student> set=new TreeSet<>(new Comparator<Student>() {
       @Override
       public int compare(Student o1, Student o2) {
           return Integer.compare(o1.age,o2.age);
       }
   }) ;
   ```

   或

   ```java
   Set<Student> set=new TreeSet<>((o1,o2)->Integer.compare(o1.age,o2.age));
   ```

   

## Map

![image-20250626223818417](./img/image-20250626223818417.png)

### Map的常用方法

![image-20250626223929597](./img/image-20250626223929597.png)

关键：

* put(key,value)   //增
* remove(key)     //删
* get(key)             //查

若想修改键值对的值时，只需重新put即可覆盖，put返回原来的值

###  Map的遍历方式

![image-20250626224738062](./img/image-20250626224738062.png)

* 键找值

  通过Map的**`keySet()`**方法，返回键的set集合，通过遍历set从而遍历所有键值对

  ```java
  Map<Integer,String> map=new HashMap<>();
  map.put(1,"a");
  map.put(2,"b");
  map.put(3,"c");
  
  Set<Integer> s=map.keySet();//获取键的集合
  for(Integer i:s){           //增强for遍历
      System.out.println(i+"," + map.get(i));
  }
  ```

* 键值对

  首先，java中的对组(pair)数据类型为**`Map.Entry<K,V>`**，有两个方法`getKey()`和`getValue()`

  其次，Map中有方法**`entrySet()`**可以获取map中键值对集合

  ```java
  Map<Integer,String> map=new HashMap<>();
  map.put(1,"a");
  map.put(2,"b");
  map.put(3,"c");
  
  Set<Map.Entry<Integer,String>> s=map.entrySet();//获取键值对集合
  for(Map.Entry<Integer,String> pair:s){
      System.out.println(pair.getKey()+"," + pair.getValue());
  }
  ```

* Lamda   (forEach)

  ```java
  Map<Integer,String> map=new HashMap<>();
  map.put(1,"a");
  map.put(2,"b");
  map.put(3,"c");
  
  map.forEach((key,value)-> System.out.println(key+","+value));
  ```

### Map的底层原理

map的原理和set原理一模一样，因为set就是通过map而来的，只不过舍弃了**值**

![image-20250626230459211](./img/image-20250626230459211.png)

# Stream流

![image-20250627153954965](./img/image-20250627153954965.png)

![image-20250627154046966](./img/image-20250627154046966.png)

核心思想：链式编程

 ### 常用方法

##### 获取方法

![image-20250627163115965](./img/image-20250627163115965.png)

* 数组

  ```java
  int[] arr=new int[10];
  Arrays.stream(arr);
  ```

* 集合

  ```java
  List<Integer> list=new ArrayList<>();
  list.stream();
  ```

  

##### 中间方法

![image-20250627162657048](./img/image-20250627162657048.png)

* filter（过滤）

  ```java
   stream.filter(s->s.age>14);//lamda表达式，箭头后写筛选后满足的条件
  ```

* sorted（排序）

  ```java
  stream.filter(s->s.age>14).sorted();
  ```

* limit（获取前n个）/skip（跳过前n个)

  ```java
  stream.filter(s->s.age>14).sorted().limit(2);
  ```

* distinct(去重)（需要重写hashcode方法和equals方法）

  ```java
  stream.filter(s->s.age>14).sorted().limit(2).distinct();
  ```

以上中间方法返回的是stream流，可以实现链式编程

##### 终结方法

![image-20250627164531871](./img/image-20250627164531871.png)

![image-20250627165143714](./img/image-20250627165143714.png)

* forEach

  ```java
  stream.filter(s->s.age>14).sorted().limit(2).distinct().forEach(s->System.out.println(s));
  ```

* collect

  ```java
  List<Student> list=stream.collect(Collectors.toList());//收集至list集合中
  Set<Student> set=stream.collect(Collectors.toSet());//收集到set集合中
  ```

<font color='red'>Stream流是一次性的，一旦被终结，将无法再用</font>

# IO

### File

##### 创建File对象

![image-20250628135534787](./img/image-20250628135534787.png)

构造函数一般使用第一个



##### 获取文件信息

![image-20250628135748701](./img/image-20250628135748701.png)

##### 创建和删除文件

![image-20250628135914309](./img/image-20250628135914309.png)

**只能删除文件或者空的文件夹**

##### 遍历文件夹

![image-20250628140025692](./img/image-20250628140025692.png)

对于`listFiles()`方法

* 当File对象的**<font color='blue'>路径不存在</font>**、**<font color='blue'>是文件</font>**或者**<font color='blue'>文件夹没有读权限</font>**：返回null

* 当File对象是空文件夹，返回长度为0的File[]
* 返回的file包含隐藏文件
* 只返回一级文件对象

##### 文件递归搜索

```java
 public static void main(String[] args) {
        File file = new File("C:/");
        search(file,"QQ.exe");
    }
    public static void search(File file, String fname){
        if(file ==null) return ;
        if(file.isFile())//如果是文件，判断是否是目标文件
            if(file.getName().equals(fname))
                System.out.println(file.getAbsoluteFile());
        else{            //如果是文件夹，递归
            File[] files= file.listFiles();
            if(files==null) return;
            for (File file1 : files)
                search(file1,fname);//递归调用
        }
    }
```

### 字符集

#### 编码方式

常见为三种

* **ASCII**：<font color='blue'>一个字节</font>存一个字符，包括英文和数字，为美国使用

  >  首位为0，共可以表示128个字符

* **GBK**：一个字节存一个ASCII字符，<font color='blue'>两个字节存一个中文字符</font>，为中国使用

  > ASCII首位为0，汉字首位为1，共包含2万个中国字符

* **<font color='red'>UTF-8</font>**：可变长编码方案，共分为四个长度区：1字节,2字节,3字节,4字节，**<font color='red'>汉字占三个字节</font>**,全球通用

  > ASCII属于一字节区，汉字属于三字节区

  所有的编码方式均兼容ASCII

![image-20250628153821006](./img/image-20250628153821006.png)

![image-20250628154325772](./img/image-20250628154325772.png)

#### 编码和解码

![image-20250628155440977](./img/image-20250628155440977.png)

```java
String str="222aaa程曜智";
byte[] b=str.getBytes("UTF-8");    //以UTF-8的规则编码
System.out.println(new String(b, "GBK"));   //以GBK的规则解码
```

### IO流

#### IO流分类

![image-20250628160505561](./img/image-20250628160505561.png)

* 字节流：适合**所有类型**的文件，适合对文件的转移，但不适合读取纯文本内容，中文可能会出现乱码
* 字符流：只适合**纯文本**文件

![image-20250628160602441](./img/image-20250628160602441.png)

* 字节输入流 **`InputStream`**：读字节
* 字节输出流**`OutputStream`**：写字节
* 字符输入流**`Reader`**：读字符
* 字符输出流**`Writer`**：写字符

#### 字节输入流 `InputStream`



##### 文件字节输入流 `FileInputStream`

![image-20250628200935657](./img/image-20250628200935657.png)

* 构造器

  ```java
  File file =new File("C:/Users/xiaolanzaicyz/Desktop/Java_code/test/io/src/字符/h.txt");
  FileInputStream is=new FileInputStream(file);
  ```

* 读取 (`read`)

  ```java
  File file =new File("C:/Users/xiaolanzaicyz/Desktop/Java_code/test/io/src/字符/h.txt");
  FileInputStream is=new FileInputStream(file);
  byte[] bytes=new byte[100];
  String res=new String();
  while(is.read(bytes)!=-1)//读取至bytes字节数组中
  {
      res+=new String(bytes);//对字节数组解码
  }
  System.out.println(res);
  ```

  缺点：可能对汉字进行截断，会出现乱码，必须一次性读完全部字节才能避免

* 读取全部 (`readAllBytes`)

  ![image-20250628201820619](./img/image-20250628201820619.png)

  ```java
  bytes=is.readAllBytes();
  res=new String(bytes);
  System.out.println(res);;
  ```

  缺点：文件过大会内存超限

综上：**字节流不适合读取纯文本，但是可以转移**

##### 缓冲字节输入流`BufferedInputStream`

* 方法：内置8KB的缓冲池，减少IO次数

* 作用：用于提高`InputStream`和`FileInputSteam`的效率

* 使用：**只需要将`InputStream`包装成`BufferedInputStream`即可，其他依旧按照`InputStream`的方法使用**

  ```java
  InputStream is=new FileInputStream("C:\\Users\\xiaolanzaicyz\\Desktop\\Java_code\\test\\io\\src\\字符\\h.txt");
  BufferedInputStream bis=new BufferedInputStream(is);
  ```

* ![image-20250628213108954](./img/image-20250628213108954.png)

* ![image-20250628213620123](./img/image-20250628213620123.png)

##### 数据输入流`DataInputStream`

![image-20250629085657492](./img/image-20250629085657492.png)

#### 字节输出流`OutputStream`

##### 文件字节输出流 `FileOutputStream`

![image-20250628203126167](./img/image-20250628203126167.png)

* 若要追加，构造函数第二个参数为true

```java
FileOutputStream os=new FileOutputStream(file);
os.write("小烂仔是你爹".getBytes());
```



文件的复制：

```java
InputStream is=new FileInputStream("C:\\Users\\xiaolanzaicyz\\Desktop\\Java_code\\test\\io\\src\\字符\\h.txt");
OutputStream os=new FileOutputStream("C:\\Users\\xiaolanzaicyz\\Desktop\\Java_code\\test\\io\\src\\字符\\g.txt");
byte[] bytes=is.readAllBytes();
os.write(bytes);
```

##### 缓冲字节输出流`BufferedOutpunStream`

同理 

##### 打印流 `PrintStream`

![image-20250629084939451](./img/image-20250629084939451.png)

##### 数据输出流`DataOutStream`

![image-20250629085538121](./img/image-20250629085538121.png)

#### 字符输入流`Reader`

##### 文件字符输入流`FileReader`

![image-20250628211200659](./img/image-20250628211200659.png)

```java
Reader reader=new FileReader("C:\\Users\\xiaolanzaicyz\\Desktop\\Java_code\\test\\io\\src\\字符\\h.txt");
char[] c=new char[2];
while(reader.read(c)!=-1)
    System.out.print(new String(c));
```

##### 缓冲字符输入流`BufferedReader`

![image-20250628215421821](./img/image-20250628215421821.png)

依旧和`BufferedInputStream`一样，包装`Reader`类的，提高效率，并b 且可以把它当`Reader`使用

新增了一个方法`readline`

##### 字符输入转换流`InputStreamReader`

![image-20250629084442475](./img/image-20250629084442475.png)

#### 字符输出流`Writer`

##### 文件字符输出流`FileWriter`

![image-20250628211137467](./img/image-20250628211137467.png)

**注意：字符输出流必须得刷新才能更新文件数据**

![image-20250628211941037](./img/image-20250628211941037.png)

原因：内部形成缓冲区，当`flush`后才会将缓冲区的内容写进文件，**减少io频率**

##### 缓冲字符输出流`BufferedWriter`

![image-20250628215652697](./img/image-20250628215652697.png)

##### 打印流`PrintWriter`

![image-20250629085118249](./img/image-20250629085118249.png)

### IO框架

![image-20250629090420614](./img/image-20250629090420614.png)

![image-20250629090447468](./img/image-20250629090447468.png)

![image-20250629090304415](./img/image-20250629090304415.png)

### 资源自动释放

![image-20250628205001792](./img/image-20250628205001792.png)

![image-20250628205023383](./img/image-20250628205023383.png)

# 多线程

### 并行和并发

 ![img](./img/90646eb9e4924b719c54bdec89fca764.png)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)编辑![img](./img/ae72b85fb7bd4eec8915b70cc43b5323.png)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

* 并发：一个核做多个线程（交替)

* 并行：多个核做多个线程（同时）

### 创建线程的方法





![img](./img/2fac8e73a8794c46832d0513dcd16d40.png)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

#### 继承Thread

* 创建新类，继承Thread，**并重写run方法**；

* 主函数中new 新类，并调用start方法

#### 实现Runnable接口

* 创建新类，实现 Runnable接口，**并重写run方法**；

* 主函数中new 新类，**将新类作为参数交给Thread类**，并调用Thread的start方法

```java
public class MyRun implements Runnable{
    public void run(){
        for(int i=0;i<100;i++)
            System.out.println("hh" +i );
    }
}



Thread thread2= new Thread(new MyRun());
thread2.start();
```

#### 利用Callable接口、FutureTask类



![image-20250629161137699](./img/image-20250629161137699.png)

1. **定一个类实现Callable接口，实现call方法。**

   ```java
   public class MyCall implements Callable<String> {
       public String call(){
           int sum=0;
           for(int i=0;i<100;i++) {
               System.out.println(i);
               sum+=i;
           }
           return "线程执行完毕，结果为"+sum;
       }
   }
   ```

   > Callable接口为泛型接口，表示返回数据的类型

2. **将这个对象交给FutureTask类**

   ```java
   Callable<String> callable=new MyCall();
   FutureTask<String> futureTask=new FutureTask<>(callable);
   ```

3. **将FutureTask对象交给Thread类**

   ```java
   Thread thread=new Thread(futureTask);
   thread.start();
   ```

4. **线程执行完后，可以通过FutureTask对象的get()方法获取返回结果**

   ```java
   System.out.println(futureTask.get());
   ```

   > 若线程未执行完，这条语句会变为**<font color='blue'>阻塞状态</font>**

#### 三种方式的区别

![image-20250629161830001](./img/image-20250629161830001.png)

### Thread的常用方法

![image-20250629162134838](./img/image-20250629162134838.png)

注：

①线程的名字默认是“Thread-数字”；

②线程的抢夺是随机的，优先级越高代表抢夺线程的概率越大。

③优先级分为1~10级，默认为5

④守护线程定义：当非守护线程结束后，守护线程会随着结束（不是一瞬间，会执行一会然后结束）

使用setDaemon（true）可设置为守护线程



### 线程的生命周期

![img](./img/fcbdc7a5dfea4413aa3599e30d80c435.png)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)编辑新建

就绪

运行

阻塞

死亡

注：当sleep函数休眠结束后不会继续执行下面的代码，而是变为就绪状态；

当多个线程操作一个数据会出现异常，异常原因是其中一个线程执行完一条语句后后面的语句还没执行就被其他线程抢夺，从而导致执行顺序的异常，

这时需要一个同步代码块，让块内的语句全部执行完毕后才可以被其他线程抢夺。（有点像数据库的并发知识点）

### 同步

##### 同步代码块



![img](./img/24a0a3b3aa83457682113e560aaf57e4.png)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

括号中的锁为锁对象，可以是任意对象，但是必须唯一

![image-20250629192820431](./img/image-20250629192820431.png)



##### 同步方法

等价于让同步代码块包围整个方法

![image-20250629193513097](./img/image-20250629193513097.png)

注:

​    StringBuilder 和StringBuffer的区别在于，**StringBuffer的所有方法都是同步方法**，方法体中的代码基本一样，所以StringBuffer更具有线程安全性。

​    **故如果是单线程用StringBuilder即可，多线程必须用StringBuffer**



##### Lock锁

![img](./img/62c1cf11dfb34d46a5b763a212040b15.png)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

* lock（）关锁

* unlock（）解锁

注：

​    ①Lock是接口不能直接实例化，需要用ReentrantLock来实例化

​    ②Lock必须唯一，如果是静态方法，那么必须是static

①②可得，锁的定义如下：

  （ **static**） Lock lock=new ReentreantLock();

​    ③因为在循环体中，会出现break直接跳出循环从而没有执行unlock语句,从而使得其他线程一直处于阻塞状态，程序无法终止，故可利用try-catch块的性质：finally关键字会使得try内语句无论以哪种方式结束执行都会执行finally里的语句。**所以要把unlock语句写入finally内**



​    最终代码如下：

![img](./img/4103ec12b20b47c5af127a0dbb06546b.png)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)编辑

### 等待唤醒机制

![img](./img/5b835b1d6b1d46839ad704c1a7f12a54.png)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

![img](./img/73925d50b6a44af498ee0a93041ce2b8.png)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)编辑

在多个线程等待时，使用notify方法会随机唤醒一个线程，不稳定，建议使用notifyAll

### 线程池

#### 介绍

![image-20250629204325388](./img/image-20250629204325388.png)

通俗来讲：

* 不使用线程池就类似于来一个顾客就雇一个服务员(Thread)，顾客走了服务员就裁了，开销很大
* 使用线程池就类似于服务员常驻，来一个处理一个，处理不过来就排队

![image-20250629204528560](./img/image-20250629204528560.png)

#### 创建线程池

![image-20250629204703825](./img/image-20250629204703825.png)

##### ThreadPoolExecutor

![image-20250629204827262](./img/image-20250629204827262.png)





![image-20250629204905523](./img/image-20250629204905523.png)

###### **常用方法：**

![image-20250629205030141](./img/image-20250629205030141.png)

###### **处理Runnable任务：**

![image-20250629205130504](./img/image-20250629205130504.png)

###### 处理Callable任务

![image-20250629205425342](./img/image-20250629205425342.png)

###### 临时线程，拒绝的条件，拒绝策略

![image-20250629205211772](./img/image-20250629205211772.png)

##### Executors

![image-20250629212810254](./img/image-20250629212810254.png)

![image-20250629213038910](./img/image-20250629213038910.png)