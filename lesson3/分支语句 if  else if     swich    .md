# 分支

默认从上往下执行，有时候会需要程序走分支条件、重复操作。

## if单分支语句

```java
if(boolean 为真){
    //做...
}
```

## if else 双分支

```java
if(boolean 为真){
    //做...
}else{
    //否则做...
}
```



# 多分支

## if else if

多分支n选1

```java
if(条件A){
        //满足A做A事
}else if（条件B）{
       //满足B做B事
}else if（条件C）{
       //满足C做C事
}else{
      //啥条件都没满足，只能最后一项可以做啦
}

```

```java
练习1：输入一个成绩，成绩>80得到A，成绩>70得到B，成绩>60得到C，成绩<60是小垃圾。
import java.util.Scanner;
public class fish{
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        System.out.println("请输入一个成绩");
        int score=scan.nextDouble();
        if(score>=80){//当达到80分以上时
            System.out.println("A");
        }else if(score>=70){//当达到70分以上时
            System.out.println("B");
        }else if(score>=60){//当达到60分以上时
            System.out.println("C");
        }else{
            System.out.println("你是小垃圾");
        }
    }
}
```

```JAVA
练习2：输入星期几，打印安排：
1.做作业2.看综艺3.做饭4.洗碗5.睡觉6.打游戏7.转圈
import java.util.Scanner;
public class fish{
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        System.out.println("请输入一个数字");
        int number=scan.nextInt();
        if(1<=number&&number<=7){
            if(number==1){
                System.out.println("做作业");
            }else if(number==2){
                System.out.println("看综艺");
            }else if(number==3){
                System.out.println("做饭");
            }else if(number==4){
                System.out.println("洗碗");
            }else if(number==5){
                System.out.println("睡觉");
            }else if(number==6){
                System.out.println("打游戏");
            }else{
                System.out.println("转圈");
            }
        }else{
            System.out.println("看来你是个骚东西");
        }
    }
}
```

## switch

也属于多分支语句，case条件也可以有多个

```java
switch(要去匹配的内容){
    case 值A；
    满足A做A事；
    break; //结束 跳出
    case 值B；
    满足B做B事；
     break;
   default;
   //啥条件都没满足，只能最后一项可以做啦
    break;
}
```

```java
练习1：输入一个月份，1月2月3月是春天，4月5月6月是夏天，7月8月9月是秋天，10月11月12月是冬天。
//可以这样：case1,2,3将多个case选项以逗号分隔，小心版本不兼容。
import java.util.Scanner;
public class fish{
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        System.out.println("请输入一个月份");
        int number=scan.nextInt();
        switch(number){ //表示要去匹配接收来的number的值
            case 1,2,3:
                System.out.println("春天");//用户输入1-3月份的时候是春天
                break;
            case 4,5,6:
                System.out.println("夏天");//用户输入4-6月份的时候是夏天
                break;
            case 7,8,9:
                System.out.println("秋天");//用户输入7-9月份的时候是秋天
                break;
            case 10,11,12:
                System.out.println("冬天");//用户输入10-12月份的时候是冬天
                break;
            default:
                System.out.println("四季都困");//当用户输入不符合条件的数字将会得到最后提示
        }
    }
}
//可以这样：case 1:    case 2:     case 3:    System.out.println("春天");     break;
import java.util.Scanner;
public class fish{
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        System.out.println("请输入一个月份");
        int number=scan.nextInt();
        switch(number){ //表示要去匹配接收来的number的值
            case 1:
            case 2:
            case 3:
                System.out.println("春天");
                break;
            case 4:
            case 5:
            case 6:
                System.out.println("夏天");
                break;
            case 7:
            case 8:
            case 9:
                System.out.println("秋天");
                break;
            case 10:
            case 11:
            case 12:
                System.out.println("冬天");
                break;
            default:
                System.out.println("四季都困");
                 break;
        }
    }
}
```

当有多个case做同一件事情，可以不每个case都写上break结束；default也可以不要。

case的选项也是可以调换的。

同一作用域变量不可重名解决办法：

1.把各自的case分别 { } 包起来

2.把变量 s 声明出去，提升 s 作用域

3.把各自的case进行不同的命名，如：s1 ，s2 ， s3

```java
练习2：输入一个按键，按键为1-3，输入1，得到三角形面积，输入2，得到长方形面积，输入3，得到圆形面积。
import java.util.Scanner;
public class fish{
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        System.out.println("请进行选择：1，三角形2.长方形3.圆形");//提醒用户输入数字1.三角形 2.长方形 3.圆柱
        int number=scan.nextInt();
        double s=0;//会有一个值放在s里
        switch(number){
            case 1://1是三角形计算面积
                System.out.println("请输入三角形的底");
                int d=scan.nextInt();
                System.out.println("请输入三角形的高");
                int h=scan.nextInt();
                s=d*h/2;
                break;
            case 2://2是长方形计算面积
                System.out.println("请输入长方形的长");
                int a=scan.nextInt();
                System.out.println("请输入长方形的宽");
                int b=scan.nextInt();
                s=a*b;
                break;
            case 3://3是圆形计算面积
                System.out.println("请输入圆形的半径");
                int r=scan.nextInt();
                double PI=3.14;
                s=PI*r*r;
                break;
            default:
                System.out.println("你是个妖怪");
                 break;
        } System.out.println("所得到的面积是"+s);//将得出来的体积打印出来
    }
}
```

```java
练习3：运输公司对用户计算运费，路程越远每公里运费越低。
每公里每吨货物基本运费是 p（自定义基础运费），货物重量为 w 吨，距离为 s 公里，折扣为 d，总运费 f = pws(1-d)
s < 250km          折扣为0
250<= s < 500                  2%
500<= s < 1000                 5%
1000<= s < 2000                 8%
2000<= s < 3000                 10%
3000<= s                        15%
    
    
import java.util.Scanner;
public class fish{
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        System.out.println("请输入距离");
        int s = scan.nextInt();
        System.out.println("请输入货物重量");
        int w = scan.nextInt();
        int p = 8;//基础运费
        double d = 0;
        if(250<=s&& s<500){//满足98折的条件
            d =0.02;
        } else if (500<=s&&s<1000) {//满足95折的条件
            d= 0.05;
        } else if (1000<= s&& s < 2000 ) {//满足92折的条件
            d= 0.08;
        } else if (2000<= s&& s< 3000) {//满足9折的条件
            d= 0.1;
        }else if (3000<= s){//满足85折的条件
            d=1.5;
        }
        double f = p*w*s*(1-d) ;
        System.out.println("总运费是：" +f);
        }
        }
```

```java
练习4：企业发放奖金，根据利润 profit （万元）提成 commission，规则如下：

利润 < 10万                       提成10%
10万<=利润 < 20万           7.5%
20万<=利润 < 40万           5%
40万<=利润 < 60万           3%
60万<=利润 < 100万          1.5%
100万<=利润                  1%
输入员工创造的利润，求出他的提成。


import java.util.Scanner;

public class fish {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        System.out.println("请输入利润:");
        int profit = scan.nextInt();
        double commission = 0;
        double sum = 0;
        if (profit < 100000) {//利润小于10W时，提成为利润*0.1；
            commission = 0.1;
            sum = profit * 0.1;
        } else if (profit < 200000) {//当利润高于等于10w低于20w时，提成为（利润-10万）*0.075+10w*0.1；
            commission = 0.075;
            sum = (profit - 100000) * 0.075 + 100000 * 0.1;
        } else if (profit < 400000) {//当利润高于等于20w低于40w时，提成为（利润-20万）*0.05+10w*0.075+10w*0.1；
            commission = 0.05;
            sum = (profit - 200000) * 0.05 + (200000-100000)*0.075+100000*0.1;
        } else if (profit < 600000) {
            //当利润高于等于40w低于60w时，提成为（利润-40万）*0.03+20w*0.05+10w*0.075+10w*0.1；
            commission = 0.03;
            sum = (profit - 400000) * 0.03 + (400000-200000)*0.05+(200000-100000)*0.075+100000*0.1;
        } else if (profit < 1000000) {
            //当利润高于等于60w低于100w时，提成为（利润-60万）*0.015+20w*0.03+20w*0.05+10w*0.075+10w*0.1；
            commission = 0.015;
            sum = (profit - 600000) * 0.015 + (600000 - 400000) * 0.03 + (400000 - 200000) * 0.05 + (200000 - 100000) * 0.075 + 100000 * 0.1;
        } else { //当利润高于等于100w时，提成为（利润-100万）*0.01+40w*0.015+20w*0.03+20w*0.05+10w*0.075+10w*0.1；
            commission = 0.01;
            sum = (profit - 1000000) * 0.01 + (1000000 - 600000) * 0.015 + (600000 - 400000) * 0.03 + (400000 - 200000) * 0.05 + (200000 - 100000) * 0.075 + 100000 * 0.1;
        }
        System.out.println("该员工的提成是"+sum);
    }
}

```

# 