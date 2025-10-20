---
title: 关于Java中GUI的一点点教程
published: 2025-10-21
description: ''
image: ''
tags: [Java笔记]
category: ''
draft: false 
lang: ''
---

> 如你所见，这是一篇关于Java中与应用界面有关的一篇教程。因为Java中有关于GUI的信息过于丰富，我觉的有必要写一个文档来对我们所学的知识进行一个简单的梳理。
>
> 如果你上课懵懵懂懂不知道老师在讲什么，或是干脆就没上课，又或者是你只是单纯想复习一些上课学的知识，那么这份教程一定非常适合你。
>
> OK，整理好心情。Let's go!

 我会将老师的课后作业作为例题进行讲解，力求简单易懂。

### 知识清单：

1. 窗口的创建
2. 窗口属性的设置
3. 图像的绘制
4. 窗口的布局
5. 面板的用法
6. 按钮的创建
7. 按钮动作监听器



### 题目：

创建一个窗口，在上面绘制出正态分布的图像，在窗口的底部放置三个按钮：red，blue和green，按下按钮，让正态分布的图像变成相应的颜色。



### 开始做题：

1. 那么第一步，一个Java程序必要的东西是什么？没错，是main函数，那么我们需要先构建main函数：

   ```java
   public class Q2{ // 在这里我的文件名是Q2.java,记得文件名和主类名保持一致
       public static void main(String[] args){
           ...
       }
   }
   ```

2. 现在我们可以创建一个窗口的对象了，还记的怎么创建对象吗？在Java中，我们使用`class`创建一个对象
   ❗注意：在Java中`class`是同一级的，所以窗口class和主函数所在的class应该是同一级的，所以不要把窗口class给放在主class里面

   ```java
   public class Q2{ // 在这里我的文件名是Q2.java,记得文件名和主类名保持一致
       public static void main(String[] args){
           ...
       }
   }
   
   class GUIFrame extends JFrame{
       
   }
   ```

   在这一步，我们创建了一个名字为`GUIFrame`的对象，这个对象继承了`JFrame`。至于为什么要继承`JFrame`，是因为它封装了创建窗口所需的基本功能，我们很容易就可以创建自己想要的窗口。

3. 好的，我们现在有了一个窗口对象，我们还需要设置一些窗口必要的参数。想一想，窗口必要的参数有哪些？

   - title
   - size

   大概基础的参数只有这些，我们现在要设置这些参数

   ```java
   class GUIFrame extends JFrame{
       public GUIFrame(){
           setSize(900, 530);
           setTitle("Normal Distribution");
       }
   }
   ```

   ❗注意：我们现阶段对Frame的所有操作都是在它的构造函数下进行的

   解释一下上面的代码

   - `public GUIFrame(){}` 构造函数，我们对这个窗口所有的操作，都在它的构造函数之下
   - `setSize(900, 530);` 设置窗口尺寸，第一个参数是长，第二个是宽。另一种说法是第一个参数是宽，第二个参数是高。都可以看个人习惯了。
   - `setTitle("I am title");` 设置窗口的标题，括号里面要填标题的内容

4. 这些参数还不够，我们还需要两个参数

   - `setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);`  这个用来设置关闭窗口使程序退出，这个记住就好
   - `setVisible(true);` 这个设置是为了让窗口可以被看见，不然窗口无法显示在你的电脑屏幕上

5. 这样的话差不多了， 我们整理一下代码

   ```java
   public class Q2{ // 在这里我的文件名是Q2.java,记得文件名和主类名保持一致
       public static void main(String[] args){
           
       }
   }
   
   class GUIFrame extends JFrame{
       public GUIFrame(){
           setSize(900, 530);
       	setTitle("Normal Distribution");
     	    setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
       	setVisible(true);
       }
   }
   ```

6. 运行一下，发现窗口没有显示。。。
   先别破防，我来解释一下。
   我们现在只是创建好了一个窗口对象，但是我们并没有在主函数中调用它。
   在主函数中加入`GUIFrame frame = new GUIFrame();`来创建一个窗口。
   我们现在应该都能看懂这行代码在干什么：创建一个名字为`frame`，类型为`GUIFrame`的对象。

   OK，现在的代码如下

   ```java
   public class Q2{ // 在这里我的文件名是Q2.java,记得文件名和主类名保持一致
       public static void main(String[] args){
           GUIFrame frame = new GUIFrame();
       }
   }
   
   class GUIFrame extends JFrame{
       public GUIFrame(){
           setSize(900, 530);
       	setTitle("Normal Distribution");
     	    setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
       	setVisible(true);
       }
   }
   ```

7. 然后你会发现，在编辑器中，`JFrame`被标红了，你可以在鼠标放在红色的`JFrame`上面，编辑器会显示一个框，在框的下面有一行小字：`快速修复`点他，这时会出现一个下拉框，选择导入(import)必要的包。这样，编辑器就会自动在你程序的最上面导入相关的包了。(后续所有的导入包都可以通过这种方式来操作)
   如果编辑器无法显示，或者是没有显示“import”选项的话，在你的代码的最上面加上`import javax.swing.JFrame;`这样就好啦！
   最终代码演示：

   ```java
   import javax.swing.JFrame;
   
   public class Q2{ // 在这里我的文件名是Q2.java,记得文件名和主类名保持一致
       public static void main(String[] args){
           GUIFrame frame = new GUIFrame();
       }
   }
   
   class GUIFrame extends JFrame{
       public GUIFrame(){
           setSize(900, 530);
       	setTitle("Normal Distribution");
     	    setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
       	setVisible(true);
       }
   }
   ```

   恭喜你🎉！你成功创建了一个窗口。

8. 接下来我们要在窗口上添加正态分布的图像，我们使用这样的思路：首先创建一个面板，在面板上画好正态分布的图像，再将面板添加到我们的窗口中。

9. OK，我们先来创建一个面板。面板是一个对象，所以面板class和主class和Frame的class是平级的，没有嵌套关系，代码如下：

   ```java
   import javax.swing.JFrame;
   
   public class Q2{ // 在这里我的文件名是Q2.java,记得文件名和主类名保持一致
       public static void main(String[] args){
           GUIFrame frame = new GUIFrame();
       }
   }
   
   class MyCanvas extends JPanel{ // 在这里我们创建了名称为MyCanvas继承了JPanel的一个面板
       ...
   }
   
   class GUIFrame extends JFrame{
       public GUIFrame(){
           setSize(900, 530);
       	setTitle("Normal Distribution");
     	    setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
       	setVisible(true);
       }
   }
   ```

10. 接下来，我们需要覆写面板中的绘制组件

    ```java
    class MyCanvas extends JPanel{
        protected void paintComponent(Graphics g) {
            
    }
    ```

    至于为什么要使用protected，我也不清楚，似乎是使用public也行，你可以自己试一试。

    `protected void paintComponent(Graphics g)`,分析一下这行代码，我们覆写了`paintComponent()`，并且传了一个Graphics类型的参数g。
    `g`就相当于是我们的画笔，我们可以通过`g.xxx()`的方法来控制画笔。

11. 我们还得记住一行代码：`super.paintComponent(g);`记住就好，不加上的话会有奇怪的事情发生。

12. 所以，基础的代码框架如下

    ```java
    class MyCanvas extends JPanel{
        protected void paintComponent(Graphics g) {
            super.paintComponent(g);
            ...
    }
    ```

13. 因为我们要实现按下按钮改变颜色的功能，所以我们需要一个成员变量来记录画笔的颜色。

    ```java
    class MyCanvas extends JPanel{
        private Color x = Color.BLUE; // 在这里记录画笔的颜色
        protected void paintComponent(Graphics g) {
            super.paintComponent(g);
            ...
        }
    }
    ```

    分析一下新增的这行代码：`private Color x = Color.BLUE`

    - 通常来讲成员变量都是`private`类型，所以我们使用`private`关键字
    - 创建了一个名字为`x`的`color`类型的对象
    - `color.BLUE`的意思是颜色是蓝色，`color.xxx`这种用法还能表示很多种颜色，你可以自行尝试。 

14. 在有了成员变量之后，很自然的我们就想到：需要通过写一个函数来设置这个成员变量，实现对成员变量的更改

    ```java 
    void setColor(Color a){
        this.x = a;
    }
    ```

    我们设置了一个名字为`setColor`的方法，这个操作没有返回值所以是`void`类型.

    设置参数为`Color a`, 这个参数需要在调用这个方法的时候传入。

    我们将传入的参数传递给给成员变量`x`, 这样我们就实现了通过`setColor`改变画笔颜色的方法.

15. 所以现在的代码如下：

    ```java
    class MyCanvas extends JPanel{
        private Color x = Color.BLUE; // 在这里记录画笔的颜色
        protected void paintComponent(Graphics g) {
            super.paintComponent(g);
            ...
        }
        
        // 设置画笔颜色
        void setColor(Color a){
        	this.x = a;
    	}
    }
    ```

16. 下面我们可以通过画笔开始绘制图像了了。

17. 我们先来绘制坐标轴

    ```java
    g.setColor(Color.BLACK);
    g.drawLine(0, 390, 900, 390);// x轴
    g.drawLine(450, 0, 450, 430);// y轴
    ```

    - 注意一下，第1行在这里调用的`setColor`函数，不是我们所刚写的`setColor`而是`g`画笔自带的`setColor`。 括号里填画笔的颜色，这里我们坐标轴是黑色的，所以我们使用`BLACK`
    - `g.drawLine()`括号里有4个参数，按顺序分别是X1、 Y1、 X2、 Y2。 X1，Y1指的是起始点的坐标，X2,Y2指的是终点的坐标。
      `g.drawLine()`实现的是从起点到终点画一条线的功能。 
    - 至于为什么X轴Y轴的起点和终点要这样设置，大家可以自己思考一下

    ❗补充：在Java窗口中，左上角是零点，从左往右是X轴正方向，从上往下是Y轴的正方向，以此来构建坐标系

    

18. 整理一下目前的代码：

    ```java
    import java.awt.Color;
    import java.awt.Graphics;
    import javax.swing.JFrame;
    import javax.swing.JPanel;
    
    public class Q2{ // 在这里我的文件名是Q2.java,记得文件名和主类名保持一致
        public static void main(String[] args){
            GUIFrame frame = new GUIFrame();
        }
    }
    
    class MyCanvas extends JPanel{
        private Color x = Color.BLUE;
        @Override // 这行的意义在于提示编辑器，这里是覆写的部分，有没有这一行对程序运行没有影响
        protected void paintComponent(Graphics g) {
            super.paintComponent(g);
            g.setColor(Color.BLACK);
            g.drawLine(0, 390, 900, 390);
            g.drawLine(450, 0, 450, 430);
        }
    
        void setColor(Color a){
            this.x = a;
        }
    }
    
    class GUIFrame extends JFrame{
        public GUIFrame(){
            setSize(900, 530);
        	setTitle("Normal Distribution");
      	    setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        	setVisible(true);
        }
    }
    ```

    截止到目前，你应该已经对上面的代码有了充分的了解，（如果没有，回去重新看看呢宝贝。。）

19. 现在你兴冲冲的把上面的代码复制到编辑器里，运行之后发现屏幕上只显示了一个空白的界面，并没有显示坐标轴。。。

20. 于是你接着往下看。。。

21. 为什么没有画出坐标轴呢？是因为我们已经把图像画在的面板上，但是我们并没有把面板给添加到窗口中，所以我们需要把面板给添加到窗口中去

22. 于是我们回到这里:

    ```java
    class GUIFrame extends JFrame{
        public GUIFrame(){
            setSize(900, 530);
        	setTitle("Normal Distribution");
      	    setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        	setVisible(true);
        }
    ```

    首先我们要为我们的面板创建一个新的对象：
    `MyCanvas canvas = new MyCanvas();`
    接下来，我们要把`canvas`给添加到窗口中：`add(canvas);`

    还没完，我们需要重绘面板，不然还是无法显示：`repaint();`

23. 将上面的代码都放在GUIFrame的构造函数里：

    ```java
    class GUIFrame extends JFrame{
        public GUIFrame(){
            setSize(900, 530);
        	setTitle("Normal Distribution");
      	    setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        	setVisible(true);
            MyCanvas canvas = new MyCanvas();
            add(canvas);
            repaint();
        }
    }
    ```

24. 再次汇总一下代码：

    ```java
    import java.awt.Color;
    import java.awt.Graphics;
    import javax.swing.JFrame;
    import javax.swing.JPanel;
    
    public class Q2{ // 在这里我的文件名是Q2.java,记得文件名和主类名保持一致
        public static void main(String[] args){
            GUIFrame frame = new GUIFrame();
        }
    }
    
    class MyCanvas extends JPanel{
        private Color x = Color.BLUE;
        @Override
        protected void paintComponent(Graphics g) {
            super.paintComponent(g);
            g.setColor(Color.BLACK);
            g.drawLine(0, 390, 900, 390);
            g.drawLine(450, 0, 450, 430);
        }
    
        void setColor(Color a){
            this.x = a;
        }
    }
    
    class GUIFrame extends JFrame{
        public GUIFrame(){
            setSize(900, 530);
        	setTitle("Normal Distribution");
      	    setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        	setVisible(true);
            MyCanvas canvas = new MyCanvas();
            add(canvas);
            repaint();
        }
    }
    ```

    恭喜你🎉，你已经在一个窗口上画出了坐标轴！

25. 接下来，我们要在窗口上绘制出正态分布的图像了。还记得在那个类下面进行绘图的操作吗？

    没错，在`MyCanvas`类下面覆写的`paintComponent()`中对画笔`g`进行操作。

26. 回到那个类：

    ```java
    class MyCanvas extends JPanel{
        private Color x = Color.BLUE;
        @Override
        protected void paintComponent(Graphics g) {
            super.paintComponent(g);
            g.setColor(Color.BLACK);
            g.drawLine(0, 390, 900, 390);
            g.drawLine(450, 0, 450, 430);
            
            // 要在这里添加新的代码
            // ......
        }
    
        void setColor(Color a){
            this.x = a;
        }
    }
    ```

27. 第一步我们要设置画笔的颜色
    `g.setColor(x);`这里的`x`是`MyCanvas`类中储存颜色信息的成员变量，这样做是为了后期方便对画笔颜色进行修改

28. 接下来该绘制正态分布的图像了，先来看看正态分布的公式：
    $$
    f(x) = \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}
    $$

29. 我们先来设置一些基础的参数

    - `double sigma = 50.0;`设置 $ \sigma $
    - `double mu = 450.0;`设置$\mu$

    为什么要这么设置？

    首先，$\mu$是正态分布的对称轴，我们想让图像保持在窗体的最中间，所以$\mu$的值应当是窗体长度的一半

    $\sigma$决定了图像的宽度，这里取50个像素点（其它的值当然也可以）

30. 正态分布的曲线是一条平滑的曲线，我们该如何绘制呢？不难想象，我们可以使用很多的点来绘制出它
    于是我们有以下代码：

    ```java
    for(double x=0; x<=900; x=x+0.01){
                double y = (1.0 / (sigma * Math.sqrt(2 * Math.PI))) * Math.exp(-Math.pow(x - mu, 2) / (2 * Math.pow(sigma, 2)));
                g.fillOval((int)x, (int)(y), 3, 3);
            }    
    ```

    看不懂？没关系，我们一步一步分析

    - `for(double x=0; x<=900; x=x+0.01)` `x`从0到900不断加0.01，以每一个`x`作为一个很小的圆(可以视为一个点)的圆心的横坐标，算出来的`y`作为圆心纵坐标，这样我们就能得到一条比较平滑的曲线啦
    - `double y = (1.0 / (sigma * Math.sqrt(2 * Math.PI))) * Math.exp(-Math.pow(x - mu, 2) / (2 * Math.pow(sigma, 2)));`这一行代码就仅仅是正态分布数学公式的代码形式了，大家可以自己分析一下
    - `g.fillOval((int)x, (int)(y), 3, 3);`这一行代码的意思是，绘制一个椭圆，x,y是椭圆中心的横纵坐标，接着的两个参数是长和宽，当长和宽一致时，椭圆便成为了圆。
      ❗注意：这里x和y两个参数都必须是整数，所以我们要加`(int)`

31. 如果你现在运行了代码，你会发现，正太分布的图像还是无法正确显示。。。

32. 为什么呢？
    别忘了，Java中窗口的坐标系是从左上角开始的，而我们希望坐标轴显示在窗口的中间，所以我们要对坐标轴设置偏移量。同时由于我们的单位是像素，比较小，正太分布的图像浮动不大，所以我们还需要设置放大的倍数

33. 于是我们得到如下代码：

    ```java
    for(double x=0; x<=900; x=x+0.01){
                double y = (1.0 / (sigma * Math.sqrt(2 * Math.PI))) * Math.exp(-Math.pow(x - mu, 2) / (2 * Math.pow(sigma, 2)));
                g.fillOval((int)x, (int)(390-y*35000), 3, 3);// 在这里，我们设置了偏移量和放大倍数
            }    
    ```

34. 整理一下代码，我们有：

    ```java
    import java.awt.Color;
    import java.awt.Graphics;
    import javax.swing.JFrame;
    import javax.swing.JPanel;
    
    public class Q2{ // 在这里我的文件名是Q2.java,记得文件名和主类名保持一致
        public static void main(String[] args){
            GUIFrame frame = new GUIFrame();
        }
    }
    
    class MyCanvas extends JPanel{
        private Color x = Color.BLUE;
        @Override
        protected void paintComponent(Graphics g) {
            super.paintComponent(g);
            g.setColor(Color.BLACK);
            g.drawLine(0, 390, 900, 390);
            g.drawLine(450, 0, 450, 430);
            
            
            g.setColor(x);
            double sigma = 50.0;
            double mu = 450.0;
            for(double x=0; x<=900; x=x+0.01){
                double y = (1.0 / (sigma * Math.sqrt(2 * Math.PI))) * Math.exp(-Math.pow(x - mu, 2) / (2 * Math.pow(sigma, 2)));
                g.fillOval((int)x, (int)(390-y*35000), 3, 3);
            }        
        }
    
        void setColor(Color a){
            this.x = a;
        }
    }
    
    class GUIFrame extends JFrame{
        public GUIFrame(){
            setSize(900, 530);
        	setTitle("Normal Distribution");
      	    setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        	setVisible(true);
            MyCanvas canvas = new MyCanvas();
            add(canvas);
            repaint();
        }
    }
    ```

35. 如果代码运行之后，你的电脑上显示了下图的样子，那么恭喜你，你已经绘制出了一个正态分布的图像🎉

    ![image-20250530164826050](C:\Users\31325\AppData\Roaming\Typora\typora-user-images\image-20250530164826050.png)



36. 哇塞！能看到这里很不容易呢。先得表扬你一下👍

37. 接下来我们该干什么呢？没错，设置三个按钮，把三个按钮放在窗口的下方

38. 首先我们需要三个button, 因为button要添加在窗口中，所以我们在`GUIFrame`的类的构造函数中添加代码
    ```java
    JButton red = new JButton("red");
    JButton green = new JButton("green");
    JButton blue = new JButton("blue");
    ```

    我们使用`JButton` 创建了变量名为`red`显示”red“...三个按钮，第一个red是这个Button的变量名，第二个”red“是这个Button显示出来之后，上面要显示的东西。

39. 如果我们直接使用add()把button给添加到窗口中的话，三个按钮会重叠到一起，最终只能显示最后加上去的那一个。

40. 所以我们要再创建一个面板，采用`flowlayout`把button加进去。
    什么是`flowlayout`?
    它是一种布局的形式，使用`flowlayout`,按钮就不会重叠

41. 所以我们先创建一个新的面板用来储存button
    `JPanel btn = new JPanel();`
    解释一下：使用`JPanel`创建一个名称为`btn`的面板。 

42. 把三个button加到面板里面
    ```java
    btn.add(red);
    btn.add(green);
    btn.add(blue);
    ```

43. 还没完，我们要把这个面板添加到窗口中去
    `add(btn, BorderLayout.SOUTH);`
    `BorderLayout.SOUTH`是什么意思？
    其实，它是窗口（Frame）的默认布局形式，有EAST,WEST,SOUTH,NORTH,CENTER,五个地方，按照上北下南左西右东对应。
    因为按钮面板要放在窗口的最下面，所以我们把它添加到SOUTH里

44. 代码的最后要加上一行`validate();`用来刷新界面

45. 整理一下代码：
    ```java
    import java.awt.BorderLayout;
    import java.awt.Color;
    import java.awt.Graphics;
    import javax.swing.JButton;
    import javax.swing.JFrame;
    import javax.swing.JPanel;
    
    public class Q2{ // 在这里我的文件名是Q2.java,记得文件名和主类名保持一致
        public static void main(String[] args){
            GUIFrame frame = new GUIFrame();
        }
    }
    
    class MyCanvas extends JPanel{
        private Color x = Color.BLUE;
        @Override
        protected void paintComponent(Graphics g) {
            super.paintComponent(g);
            g.setColor(Color.BLACK);
            g.drawLine(0, 390, 900, 390);
            g.drawLine(450, 0, 450, 430);
            
            
            g.setColor(x);
            double sigma = 50.0;
            double mu = 450.0;
            for(double x=0; x<=900; x=x+0.01){
                double y = (1.0 / (sigma * Math.sqrt(2 * Math.PI))) * Math.exp(-Math.pow(x - mu, 2) / (2 * Math.pow(sigma, 2)));
                g.fillOval((int)x, (int)(390-y*35000), 3, 3);
            }        
        }
    
        void setColor(Color a){
            this.x = a;
        }
    }
    
    class GUIFrame extends JFrame{
        public GUIFrame(){
            setSize(900, 530);
        	setTitle("Normal Distribution");
      	    setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        	setVisible(true);
            MyCanvas canvas = new MyCanvas();
            add(canvas);
            repaint();
            
            // 这里是新添加的代码
            JPanel btn = new JPanel();
            JButton red = new JButton("red");
            JButton green = new JButton("green");
            JButton blue = new JButton("blue");
            btn.add(red);
            btn.add(green);
            btn.add(blue);
            add(btn, BorderLayout.SOUTH);
            validate();
        }
    }
    ```

46. 呕吼，现在我们在窗口上添加了三个按钮！（如果运行不了的话，检查一下该导入的包有没有导入。）

47. 但是现在，按下按钮之后，没有任何反应，因为我们还没有为它添加动作监听器
    通过动作监听器，我们可以判断按钮有没有被按下，我们就知道它什么时候让图像变色。

48. 怎么添加动作监听器呢？

49. 很简单，代码如下：
    ```java
    red.addActionListener(new ActionListener() {
        public void actionPerformed(ActionEvent e) {
            canvas.setColor(Color.RED);
            canvas.repaint();
        }
    });
    ```

    首先确认要添加监听器的对象，我们以`red`为例

    - `red.addActionListener()`这行代码是为`red`添加了监听器\
    - 但是目前还没有可用的监听器，所以我们要`new`一个监听器`new ActionListener(){}`
    - 在大括号中，我们覆写`actionPerformed()`函数，其实这个函数的本质就是告诉程序，按钮被按下之后，该执行什么
    - `actionPerformed()`中有一个参数`ActionEvent e`这其实是在读取一个`按下`的事件。
    - 大括号中写的是在按钮按下之后程序该做的事情，它该做什么呢？没错把颜色修改为红色，然后重绘，所以是
      `canvas.setColor(Color.RED);`和`canvas.repaint();`

50. 同理可得
    ```java
    red.addActionListener(new ActionListener() {
        @Override
        public void actionPerformed(ActionEvent e) {
            // TODO Auto-generated method stub
            canvas.setColor(Color.RED);
            canvas.repaint();
        }
    })
    green.addActionListener(new ActionListener() {
        @Override
        public void actionPerformed(ActionEvent e) {
            // TODO Auto-generated method stub
            canvas.setColor(Color.GREEN);
            canvas.repaint();
        }
    })
    blue.addActionListener(new ActionListener() {
        @Override
        public void actionPerformed(ActionEvent e) {
            // TODO Auto-generated method stub
            canvas.setColor(Color.BLUE);
            canvas.repaint();
        }
    });
    ```

51. 恭喜你🎉完成了题目，超级棒哒！

52. 最终代码如下：

    ```java
    import java.awt.BorderLayout;
    import java.awt.Color;
    import java.awt.Graphics;
    import java.awt.event.ActionEvent;
    import java.awt.event.ActionListener;
    import javax.swing.JButton;
    import javax.swing.JFrame;
    import javax.swing.JPanel;
    
    public class Q2{
        public static void main(String[] args) {
            GUIFrame frame = new GUIFrame();
        }
    }
    
    class MyCanvas extends JPanel{
        private Color x = Color.BLUE;
        @Override
        protected void paintComponent(Graphics g) {
            // TODO Auto-generated method stub
            super.paintComponent(g);
            g.setColor(Color.BLACK);
            g.drawLine(0, 390, 900, 390);
            g.drawLine(450, 0, 450, 430);
            
            
            g.setColor(x);
            double sigma = 5.0;
            double mu = 450.0;
            for(double x=0; x<=900; x=x+0.01){
                double y = (1.0 / (sigma * Math.sqrt(2 * Math.PI))) * Math.exp(-Math.pow(x - mu, 2) / (2 * Math.pow(sigma, 2)));
                g.fillOval((int)x, (int)(390-y*35000), 3, 3);
            }        
        }
    
        void setColor(Color a){
            this.x = a;
        }
    }
    
    class GUIFrame extends JFrame{
        public GUIFrame(){
            setSize(900, 530);
            setTitle("Normal Distribution");
            setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    
            MyCanvas canvas = new MyCanvas();
            add(canvas);
            canvas.repaint();
            setVisible(true);
    
            JPanel btn = new JPanel();
            JButton red = new JButton("red");
            JButton green = new JButton("green");
            JButton blue = new JButton("blue");
            btn.add(red);
            btn.add(green);
            btn.add(blue);
            add(btn, BorderLayout.SOUTH);
            validate();
    
            red.addActionListener(new ActionListener() {
                @Override
                public void actionPerformed(ActionEvent e) {
                    // TODO Auto-generated method stub
                    canvas.setColor(Color.RED);
                    canvas.repaint();
                }
            });
    
            green.addActionListener(new ActionListener() {
                @Override
                public void actionPerformed(ActionEvent e) {
                    // TODO Auto-generated method stub
                    canvas.setColor(Color.GREEN);
                    canvas.repaint();
                }
            });
    
            blue.addActionListener(new ActionListener() {
                @Override
                public void actionPerformed(ActionEvent e) {
                    // TODO Auto-generated method stub
                    canvas.setColor(Color.BLUE);
                    canvas.repaint();
                }
            });
        }
    }
    ```

53. 现在的你应该已经对上面的代码非常熟悉了，不妨把这个代码作为参考，自己去试试吧！

#### 写在最后

> 读到这里，我们从搭建一个一无所有的窗口，到实现了一个比较复杂的项目。
>
> 我想说，你确实做到了！
>
> 时间匆忙，写的仓促，不免会出现些许错误，请读者批评指正（微信：wzxhahahahaha）
>
> 作者：西云fly~

### ❗重要声明：

我非常不建议你把最后的代码作为答案直接提交到学习通，应为我已经交了【狗头】

修改几个参数，看看图像会有什么变换，又或者是尝试其它的写法，都是不错的选择哦！
