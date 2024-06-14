### 7.27 java数组

```java
import java.util.Arrays;

public class JavaArrayExample {
    public static void main(String[] args) {
        // 声明和初始化一个整数数组
        int[] arr = new int[5]; // 创建包含5个元素的数组（默认值为0）
        //int[] arr = new int[]{1,2,3,4,5}
        //int[] arr;
        //int arr = new int[]
        // 将元素插入数组
        for (int i = 0; i < arr.length; i++) {
            arr[i] = i + 1;
        }

        // 打印数组元素
        System.out.println("Java中的数组元素：");
        System.out.println(Arrays.toString(arr));

        // 对数组进行排序
        Arrays.sort(arr);

        // 查找数组中的元素
        int searchKey = 3;
        int index = Arrays.binarySearch(arr, searchKey);
        System.out.println("在排序后的数组中查找元素 " + searchKey + " 的索引：" + index);
    }
}
```
 c语言数组形式

```c
#include <stdio.h>

int main() {
    // 声明和初始化一个整数数组
    int arr[5]; // 创建包含5个元素的数组（含有垃圾值）

    // 将元素插入数组
    for (int i = 0; i < 5; i++) {
        arr[i] = i + 1;
    }

    // 打印数组元素
    printf("C语言中的数组元素：\n");
    for (int i = 0; i < 5; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    // 基本查找数组中的元素
    int searchKey = 3;
    int index = -1;
    for (int i = 0; i < 5; i++) {
        if (arr[i] == searchKey) {
            index = i;
            break;
        }
    }
    printf("在数组中查找元素 %d 的索引：%d\n", searchKey, index);

    return 0;
}

```

python数组

```python
def main():
    # 声明和初始化一个整数数组（列表）
    arr = [0, 0, 0, 0, 0]  # 创建包含5个元素的列表（初始化为0）

    # 将元素插入数组
    for i in range(5):
        arr[i] = i + 1

    # 打印数组元素
    print("Python中的数组元素：")
    print(arr)

    # 对数组进行排序
    arr.sort()

    # 查找数组中的元素
    search_key = 3
    index = arr.index(search_key)
    print(f"在排序后的数组中查找元素 {search_key} 的索引：{index}")

if __name__ == "__main__":
    main()

```

### 7.28 方 法

修饰符 返回值类型 方法名(参数类型 参数名){//形参靠，连接
    ...
    方法体
    ...
    return 返回值;
}

```java
public static int sum(int a,int b){
    int c = a + b;
    return c;
}
```

方法被调用时是进入到栈内存里面的。

在Java中，参数传递可以分为两种方式：值传递（Pass by Value）和引用传递（Pass by Reference）。

值传递是指将实际参数的副本传递给方法，而引用传递是指将实际参数的引用（内存地址）传递给方法，引用类型指的是对象的引用（内存地址），而不是对象本身。

在Java中，基本数据类型采用值传递，而引用类型则采用引用传递，引用类型包括类的实例、数组以及其他引用类型（如接口、枚举等）。例如，`String`, `ArrayList`, `Object`, `int[]`, `MyClass`等都属于引用类型。



### cmd常见命令

 ```java
 E: //切换到E盘
 cd [目录] //退回到指定目录
 cd .. //退回到上级目录
 cd / //退回到根目录
 cls //清屏
 dir //展示当前目录下的所有内容
 Ctrl + C //中断当前输入命令
 ```

### Linux常用命令

```java
ls //列出当前目录中的文件和子目录
ls -l  //以详细列表形式显示所有文件，包括隐藏文件
ls -a  //显示所有文件，包括隐藏文件
cd /path/to/directory //切换到指定目录
pwd //显示当前工作目录的路径
mkdir directory_name//创建一个新目录
rm file_name  //删除文件
rm -r directory_name  //递归删除目录及其内容
cp source_file destination //复制文件
cp -r source_directory destination_directory  //递归复制目录及其内容
mv old_name new_name //移动文件或重命名
mv file_name /path/to/new_location
touch file_name //创建一个空文件
cat file_name //查看文件内容
nano file_name //编辑文件（使用 nano 或 vi 编辑器）
vi file_name
grep "search_text" file_name  //在文件中搜索特定的字符串
ps aux  //查看运行中的进程
top  //实时查看系统资源使用情况和进程（使用 top 或 htop 工具）
htop
kill process_id  //终止进程
chmod permissions file_name  //修改文件权限
chown new_owner file_name  //更改文件所有者
df -h  //显示磁盘空间使用情况（以人类可读的格式）
du -h file_name  //估算文件或目录的磁盘使用量（以人类可读的格式）
wget URL //下载文件
ssh username@remote_host  //通过 SSH 远程登录到另一台计算机

```



 ### jdK组成

JDK（java development kit）：java开发工具包，包括开发工具和JRE

JRE（java runtime enviroment）：java运行环境，包括核心类库和JVM

JVM（java virtual machine）：java运行的虚拟环境

核心类库：java之前写好的程序

### idle快捷键

| **快捷键**                        | **功能效果**                     |
| --------------------------------- | -------------------------------- |
| main/psvm、sout、…                | 快速键入相关代码                 |
| Ctrl + D                          | 复制当前行数据到下一行           |
| Ctrl + Y                          | 删除所在行，建议用Ctrl + X       |
| Ctrl + ALT + L                    | 格式化代码                       |
| ALT + SHIFT + ↑ , ALT + SHIFT + ↓ | 上下移动当前代码                 |
| Ctrl + / , Ctrl + Shift + /       | 对代码进行注释(讲注释的时候再说) |

### 静态方法

静态方法（static method）和非静态方法（instance method）

静态方法需要使用static关键字声明，静态方法属于类本身而不是类的实例，所以调用静态方法无需创建类实例。

### 输入输出

```258
//生成一组字符串
String code = "";
Random r = new Random();
code += (char)(r.nextInt(bound:26) + 65);
```

标准输入输出流（System.in and System.out）

```java
System.out.println("");
```

```java
import java.util.Scanner;
public class Main(){
	public static void main(String[] args){
	Scanner scanner = new Scanner(System.in);
        String name = scanner.nextLine;//读取用户输入的文本
        int age = scanner.nextInt();
    }
}

```



### 字符串

```java
//字符串大小写切换。
for (int i = 0; i < charArray.length; i++) {
	if (charArray[i] >= 'A' && charArray[i] <= 'Z') {
    	charArray[i] = (char) (charArray[i] + 32); // 转换为小写
    }
}
/*
	在 ASCII 编码中，每个字符都对应一个数值。字符 'A' 对应的数值是 65，'B' 对应的数值是 66，以此类推。小写字母 'a' 对应的数值是 97，'b' 对应的数值是 98，依此类推。
*/
```



### 面向对象

创建的对象存储的是地址

```java
System.out.println(s1);
```

项目(Project)-模块(Module)-软件包(Package)-java类

### this关键字的使用

![7642fcb5d52dbea5f88311455e7778bc](D:\Typora\notes\javaNote.assets\7642fcb5d52dbea5f88311455e7778bc.png)

### 封装

用类设计对象处理事务时，将数据和行为涉及到一个对象中去，通过public/private，合理隐藏，合理暴露

```java
package FengZhuaung;

public class Student {
    private double score;

    public void setScore(double score){
        if(score >= 0 && score <= 100){
            this.score = score;
        }else{
            System.out.println("数据非法~");
            System.exit(0);
        }
    }

    public double getScore(){
        return this.score;
    }

    public void printPass(double score){
        System.out.println(score >= 60 ? "成绩合格" : "成绩不合格" );
    }

}

package FengZhuaung;

public class Test {
    public static void main(String[] args) {
        Student s1 = new Student();
        s1.setScore(101);
        s1.printPass(s1.getScore());
        // s1.printPass(89);
    }

}
```



### 基础语法

```java
public class Text //类名大写，且每个单词首位字母大写
public static void main(String[] args) //方法小写字母开头，后续单词首位字母大写	
                 //软件包小写
```

#### 类的构造

```java
// 类的定义
// 访问修饰符（可选） class 类名 {
//     属性（字段），类中的变量，用于存储对象的状态或数据。
//     构造方法/构造器，默认时为空构造器
//     方法，方法是类中的函数，用于执行特定的操作或行为
// }
```



#### 方法的构造

![3b9d0aa3dc3d62c5d40149bebf4f6390](D:\Typora\notes\javaNote.assets\3b9d0aa3dc3d62c5d40149bebf4f6390.png)

![e8e5aa32e1b9e860537e51df15a62459](D:\Typora\notes\javaNote.assets\e8e5aa32e1b9e860537e51df15a62459.png)static：

final：变量一旦赋值不能被重新赋值，类似C语言静态变量，final方法可以被继承但不能被重写，final类不能被继承。

#### 数据类型

一般分为基本数据类型Primitive Data Types和引用数据类型Reference Data Types

基本数据类型：整数、浮点数、字符、布尔

引用数据类型：类、接口、数组、枚举、字符串和集合等。

#### switch语句

```java
switch (expression) {
    case value1:
        // 执行当 expression 等于 value1 时的代码
        break;
    case value2:
        // 执行当 expression 等于 value2 时的代码
        break;
    // 可以有更多的 case 分支
    default:
        // 执行当没有任何 case 匹配时的代码
}
```



### 构造器

```java
public class Car {
    private String make;
    private String model;
    private int year;

    // 无参数构造器（默认构造器）自动提供
    public Car() {
        make = "Unknown";
        model = "Unknown";
        year = 0;
    }

    // 带参数的构造器
    public Car(String make, String model, int year) {
        this.make = make;
        this.model = model;
        this.year = year;
    }

    // 构造器重用
    public Car(String make, String model) {
        this(make, model, 0);
    }

    public String getMake() {
        return make;
    }

    public String getModel() {
        return model;
    }

    public int getYear() {
        return year;
    }

    public static void main(String[] args) {
        Car car1 = new Car(); // 使用默认构造器
        Car car2 = new Car("Toyota", "Camry", 2022); // 使用带参数的构造器
        Car car3 = new Car("Honda", "Civic"); // 使用构造器重用

        System.out.println(car1.getMake() + " " + car1.getModel() + " " + car1.getYear());
        System.out.println(car2.getMake() + " " + car2.getModel() + " " + car2.getYear());
        System.out.println(car3.getMake() + " " + car3.getModel() + " " + car3.getYear());
    }
}

```

### 实体类

```java
package com;

public class Test {
    
    Student s1 = new Student();
    s1.setName("哈利波特");
    s1.setScore(99);
    StudentOperator operator = new StudentOperator(s1);
    operator.printPass();
}

package com;

public class Student{
    private String name;
    private double score;
    
    public Student(){
        
    }
    
    public Student(string name,double score){
        this.name =name;
        this.score = score;
    }
    
    public void Setname(String name){
        this.name = name;
    }
    public void setscore(double score){
        this.score = score;
    }
    
    public String getname(){
		return name;
    }
    public double getscore(){
        return score;
    }
    
    
}

package com;

public class StudentOperator {
    private Student student;
    
    public StudentOperator(Student student){
        this.student = student;
    }
    
    public void printPass(){
        if(student.getscore() >= 60){
            System.out.println(student.getName() + "学生成绩合格");
        }else{
            System.out.println(student.getNaame() + "学生成绩不合格");
        }
	}
}
```

### 包

软件包：用来分门别类管理不同程序

![05a7f4f367e08002d671c949ec834388](D:\Typora\notes\javaNote.assets\05a7f4f367e08002d671c949ec834388.png)

### 判断字符串相等注意事项

在判断字符串相等时，应使用equals()方法，而不是使用==，因为==比较的是两个字符串的地址是否相同，" ... "定义的字符串存储在字符串常量池中，而new创建的在堆中。

```java
String str1 = "Hello";
String str2  = "Hello";
String str3 = new String("Hello");
String str4 = "A";
String str5 =  "A" + "b";
String str6 = str4 + "b";
String str7 = "Ab";
System.out.println(str5==str7); //true
System.out.println(str6==str7); //flase,这是由于编译器的编译优化机制
System.out.println(str1 == str2);       //true
System.out.println(str2 == str3);       //false
System.out.println(str3.equals(str2));  //true
```

### Random类方法

```java
Random random = new Random();
int r1 = random.nextInt(); // 生成一个随机整数
int r2 = random.nextInt(max - min + 1) + min; // 生成 [min, max] 范围内的随机整数
```

### 泛型类型参数

在 Java 中，`E` 是一种泛型类型参数，通常用于表示集合或类中的元素类型。在你提到的 `public E set(int index, E element)` 方法中，`E` 表示要设置到指定索引位置的元素的类型。

- `E` 是一个占位符，表示一个类型参数。它可以被实际的类型替代，具体取决于使用该方法时传入的实际类型。
- 在 `public E set(int index, E element)` 方法中，`E` 表示返回值的类型，也就是设置前位于给定索引位置的元素的类型。通常情况下，这个返回值会是被替换的旧元素。
- 同样，`E element` 表示传递给该方法的新元素的类型。
- 泛型是 Java 中的一种机制，允许在定义类、接口、方法时指定类型参数，从而使代码更具通用性和类型安全性。使用泛型可以在编译时强制检查数据类型，并避免在运行时出现类型转换错误。

```java
ArrayList<String> list = new ArrayList<>();
list.add("apple");

String newElement = "orange";
String replacedElement = list.set(1, newElement);

System.out.println("被替换的元素：" + replacedElement);
System.out.println("更新后的列表：" + list);
//Arraylist<Object> list = new Arraylist();//Obeject表示存储所有类型的数据，
```

## 常用的API

### String

```java
String str = ""
```



### Arraylist

```java
/**
*1.创建ArrayLIst容器对象
*2.调用ArrayList类的常用方法对容器的数据进行操作
*/

ArrayList list = new ArrayList();
//添加数据
list.add("hello");
list.add(1," world");
//查找集合某处索引位置的值
String string = list.get(1); //结果为 world
//集合的大小
int size = list.size();
//删除值
System.out.println(list.remove(1));//返回值的大小
System.out.println(list.remove("hello"));//返回true或者false
//修改值
SYstem.out.println(list.set(1," China!"));//返回原来的值
```



### Scanner

```java
Scanner sc = new Scanner(System.in);
String a = sc.next();
double b = sc.nextDouble();
int c= sc.nextInt();
```





