---
title: 面向zgy的Java教程
published: 2025-10-21
description: ''
image: ''
tags: [Java笔记]
category: ''
draft: false 
lang: ''
---



> 如你所见，这是一份Java教程（其实是一道题的讲解）,主要针对的是zgy老师上课留的class Circle的作业，顺带复习类与类的相关知识。
>
> 如果你还不会上课的题目，或者你想温习一下类的用法，Let's go!



### 题目：

1. 定义一个Circle类，其中包含p(圆心)，r(半径)两个成员变量; 以及area() (计算圆的面积) 和distance()（计算到另一个圆的距离）两个方法。
2. 创建一个数组，储存三个不同的circle.
3. 输出circle的面积，以及到另一个圆的距离。



### 题目分析：

1. 首先我们需要创建一个circle类，那么如何定义一个类呢？

   ```java
   // 我们使用class关键字定义一个类
   class Circle{
       
   }
   ```

   

2. 我们知道，circle类需要两个成员变量，p(圆心),r(半径)。

   - 那么第一个问题，什么是成员变量？

     > 简单的讲，成员变量就是circle类的属性，就像圆形的属性有：圆心和 半径，人的属性有：名字，年龄，职业 and so on...

   知道了成员变量以后，我们如何设置成员变量呢？

   ```java
   class Circle{
       private Point p; //出现了“Point”?没关系，马上会解释
       private double r; // double类型的r（半径）
   }
   ```

   分析一下代码，我们在circle类中用private关键字定义了两个，成员变量，p(圆心)和r(半径)。

   - 问题来了，什么是private? 为什么要用private?

     > private代表的是这个类私有的成员变量，即只能在这个类内部使用的变量，在类的外部无法直接使用。
     >
     > 通常成员变量都是私有的，所以在这里用private

     

3. OK，回到刚刚的代码```private Point p;``` 是什么鬼？Point 是哪里来的？

   正确的，我们的Point还没有定义.

   在这里，Point就相当于一个类型，只不过是我们自定义的类型而已。

   - 什么意思？

     > 就像int是整数类型，double是小数类型一样，我们自定义一个Point类型，不妨叫它点类型。
     >
     > ❗注意：Point类型是我们自定义的，并非Java自带的类型

   所以现在，我们要定义一个Point类，还记得如何定义类吗？看看第一步

   ```java
   class Point{
       // Point (圆心)有哪些成员变量捏？没错，x坐标和y坐标
       private double x;
       private double y;
   }
   ```

   很好我们Point的成员变量写完了，但是我们该如何给成员变量赋值呢？

   我们使用**构造函数**来给成员变量赋值。

   - 你问我什么是构造函数？

     > 你可以把构造函数理解入口，通过这个入口，我们可以把值传给类里面的成员变量。
     >
     > 还是有点抽象吗？继续往下看......

   ```java
   class Point{
       // x坐标和y坐标
       private double x;
       private double y;
       
       // 构造函数
       // 入口
       public Point(int x,int y){
           this.x = x;
           this.y = y;
       }
   }
   ```

   解释一下上面的代码：

   - ```public Ponit(int x, int y)```构造函数要使用**public**声明（记住就好），并且名字要和**类**的名字一样。括号里面的内容就是即将从**外界获得**的的值。
   - ```this.x = x;``` | ```this.y = y;```这两行代码是把从外界获得的值（就是括号里的值）赋给我们的成员变量。

   有了这些还不够，Point类型还没有灵魂。由于x和y都是私有变量，我们无法直接访问，所以我们还需要两个方法来获得x和y的值。

   ```java
   class Point{
       // x坐标和y坐标
       private double x;
       private double y;
       
       // 构造函数
       // 入口
       public Point(int x,int y){
           this.x = x;
           this.y = y;
       }
       
       // 方法，获得x和y
       public double getX(){
           return x;
       }
       public double getY(){
           return y;
       }
   }
   ```

   解释一下：```public double getX()``` 首先，方法要使用public声明(或者不写也行)，double是该方法的返回值（这个方法返回的是x，x是一个double类型的数字，所以这里是double。如果返回值是字符串类型，这里就要写String以此类推）。```getX```是方法的名字，括号里是外界要给的值，但是由于这个方法不需要外界给我们值，所以括号里是空的。

   OK，还记得我们在做什么吗？我们在自定义一个名字叫Point的类型，我们现在已经把它给写好啦！

   

4. 那么现在，下面的代码你就应该能看懂啦！

   ```java
   class Circle{
       private Point p; // Point类型的p
       private double r; // double类型的r
   }
   ```



5. 我们接着继续定义circle类

   有了成员变量，我们的成员变量该从哪里获得值呢？

   没错，构造函数是入口，我们可以通过入口把值传给成员变量

   ```java
   class Circle{
       private Point p; // Point类型的p
       private double r; // double类型的r
       
       // 构造函数
       public Circle(Point p, double r){
           this.p = p;
           this.r = r;
       }
   }
   ```

   解释一下，```public Circle(Point p, double r)``` 这里，我们的成员变量有Point类型的p和double类型的r,所以括号里会有两个参数（❗注意，在括号里写参数时，要带上参数类型。例如：**Point** p，**double** r）



6. 现在，成员变量和构造函数我们都写好了，该写的是Cricle类的方法，

   都有什么方法捏？题目要求：计算面积和距离。



7. 我们先来写面积

   很简单，我们都知道，圆形的面积是: $$\pi r^2$$

   ```java
   class Circle{
       private Point p; // Point类型的p
       private double r; // double类型的r
       
       // 构造函数
       public Circle(Point p, double r){
           this.p = p;
           this.r = r;
       }
       // 方法
       // 计算面积
       // 用public声明，返回值是double类型，没有参数
       public double area(){
       	return Math.PI*r*r;
       } 
   }
   ```

   解释一下：```public double area()``` 返回值是double类型，无参数，area是方法名。

   - 你可能会问，怎么是没参数呢？半径不算参数吗？

     > 括号里额参数是外界给予的，这里的半径是圆形本身的属性，所以不用传参
     >
     > 更通俗的理解方式是：我们在使用```area()```的时候并不会给他一个半径，而是直接```cricle.area()```，括号里没有数字，所以没有传参.

   

8. 恭喜你写完了```area()```方法，接下来我们写```distances()```方法

   首先我们知道，distances()是有参数的，什么参数呢？另一个圆......

   另一个圆的类型是什么？是不是我们上面定义过的Circle类型......

   我们不妨将另一个圆形的名字叫为```c```.

   返回值是double，名字是distances

   所以我们有:

   ```java
   public double distances(Circle c){
       
   }
   ```

   我们知道，两点间的距离公式：
   $$
   d = \sqrt{(x_1-x_2)^2+(y_1-y_2)^2}
   $$
   我们不妨设$$x_1，y_1 $$是当前圆的横纵坐标，$$x_2，y_2 $$是另一个圆的横纵坐标。

   当前圆形的横纵坐标很好获得, 圆心p的```getX()```方法和```getY()```方法

   ```java
   p.getX();//x1
   p.getY();//y1
   ```

   其它圆的横纵坐标稍微复杂一点，我们要先找到其它圆，即圆```c```,再找到其圆心坐标```p```，再调用```getX()```和```getY()```方法。

   ```java
   c.p.getX();//x2
   c.p.getY();//y2
   ```

   需要的数学运算有：

   ```java
   Math.sqrt(a)//对a开方
   Math.pow(b,2)//b的平方
   ```

   故我们有

   ```java
   public double distances(Circle c){
       return Math.sqrt(Math.pow((p.getX()-c.p.getX()),2)+Math.pow((p.getY()-c.p.getY()),2));
   }
   ```

   很复杂，可以慢慢理解......

   故所有的Circle类的代码如下：

   ```java
   class Circle{
       private Point p;
       private double r;
   
       public Circle(Point p,double r){
           this.p = p;
           this.r = r;
       }
   
       double area(){
           return Math.PI*r*r;
       }
   
       double distances(Circle c){
           return Math.sqrt(Math.pow((p.getX()-c.p.getX()),2)+Math.pow((p.getY()-c.p.getY()),2));
       }
   }
   ```

   

9. 很好，我们已经完成了所有的类型

   梳理一下，我们有：

   | 类     | 成员变量           | 方法                |
   | ------ | ------------------ | ------------------- |
   | Point  | double x; double y | getX(); getY()      |
   | Circle | Point p; double r  | area(); distances() |

   

10. 我们现在回到主函数，不妨设，我们的文件名是```CircleTest```

    我们有：

    ```java
    public class CircleTest{
        public static void main(String[] args){
            
        }
    }
    ```

11. 接下来我们要创建一个组来存储三个圆形，我们不妨叫它circles

    如何创建circles呢？

    我们用```Circle[] circles = new Circle[3];```

    什么意思？```Circle[]```代表我们要创建一个储存```Circle```类型数据的组，```circles```是组的名字，```new```意味着我们要创建新的对象, ```Circle```意味着这个对象是```Circle```的数据类型，```[3]```意思是```circles```会存三个数据.

    故我们有：

    ```java
    public class CircleTest{
        public static void main(String[] args){
            Circle[] circles = new Circle[3];
        }
    }
    ```

12. 现在我们该存入数据了（刚刚只是搭建好了容器）

    我们使用```circles[0] = new Circle(new Point(0,0),1);```

    什么意思？

    ```circles[0]```意思是圆形组的第一个数据是...什么什么

    ```new``` 代表创建一个新的对象

    ```Circle```代表这个新对象是Circle类型的

    ```new Point(0,0)```意思是创建一个新的点，即圆心（❗注意这里Point(0,0)的传参是和Point的构造函数一 一对应的，不是胡写的额...）

    ```1```是圆的半径r

    ❗注意：```new Circle(new Point(0,0),1)```这里的传参是和Circle的构造函数一 一对应的

    

13. OK！

14. 以此类推我们有：

    ```java
    public class CircleTest{
        public static void main(String[] args){
            Circle[] circles = new Circle[3];
            circles[0] = new Circle(new Point(0,0),1);
            circles[1] = new Circle(new Point(2,2),2);
            circles[2] = new Circle(new Point(3,4),3);
        }
    }
    ```

    

15. 最后我们可以输出面积和距离

    ```java
    System.out.println(circles[1].area());
    System.out.println(circles[0].distances(circles[2]));
    ```

    ```circles[1]```指的是名字为```circles```的组的第二个圆形

    ```.area()```指的是调用前面的圆的```area()```方法

    ```circles[0]```指的是名字为```circles```的组的第一个圆形

    ```.distances()```指的是调用```distances()```的方法

    ```distances(circles[2])```意思是这个圆形和```circles[2]```的圆形之间的距离

16. 最终的主函数：

    ```java
    public class CircleTest {
        public static void main(String[] args) {
            Circle[] circles = new Circle[3];
            circles[0] = new Circle(new Point(0,0),1);
            circles[1] = new Circle(new Point(2,2),2);
            circles[2] = new Circle(new Point(3,4),3);
            System.out.println(circles[1].area());
            System.out.println(circles[0].distances(circles[2]));
        }
    }
    ```

    

17. 看到这里，恭喜你！💕你已经学会了zgy老师上课留的题目，也对"类"这个玩意有了更加深刻的理解。

18. 这里我附上我写的代码：

    ```java
    public class CircleTest {
        public static void main(String[] args) {
            Circle[] circles = new Circle[3];
            circles[0] = new Circle(new Point(0,0),1);
            circles[1] = new Circle(new Point(2,2),2);
            circles[2] = new Circle(new Point(3,4),3);
            System.out.println(circles[1].area());
            System.out.println(circles[0].distances(circles[2]));
        }
    }
    
    class Point{
        private double x = 0;
        private double y = 0;
    
        public Point(double x,double y){
            this.x = x;
            this.y = y;
        }
    
        public double getX(){
            return x;
        }
        public double getY(){
            return y;
        }
    }
    
    class Circle{
        private Point p;
        private double r;
    
        public Circle(Point p,double r){
            this.p = p;
            this.r = r;
        }
    
        double area(){
            return Math.PI*r*r;
        }
    
        double distances(Circle c){
            return Math.sqrt(Math.pow((p.getX()-c.p.getX()),2)+Math.pow((p.getY()-c.p.getY()),2));
        }
    }
    ```



##### 写在最后：

> 我的代码和老师的代码有些许出入，但是不影响对程序的理解。
>
> 时间匆忙，写的仓促，不免会出现些许错误，请读者批评指正（微信：wzxhahahahaha）
>
> 当其它人在厌恶Java的繁琐时，我想，我们不如静下心来，默默的感受Java和谐的美......
>
> 作者：西云fly~