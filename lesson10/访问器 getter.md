```java
//角色类

public class Soldier {
    //角色属性
    public String name;
    public int level;
    public int hp;
    public int atk;
    public int def;

    public Soldier() {
    }



    public Soldier(String name, int level, int hp, int atk, int def) {
        this.name = name;
        this.level = level;
        this.hp = hp;
        this.atk = atk;
        this.def = def;
    }
//角色行为，攻击
    public void attck( Soldier other) {
        int lostHp = this.atk - other.def;
        other.hp -= lostHp;
        System.out.println(this.name + "攻击" + other.name + "," + other.name + "掉了" + lostHp + "点血,还剩下" + other.hp + "点血");
    }
    
    //重载攻击行为，可以将具有use关系的武器传递进来，进行另一种具有武器的攻击行为
      public void attck (Soldier other, Weapon weapon) {
        int lostHp = this.atk + weapon.atk - other.def;
        other.hp -= lostHp;
        System.out.println(this.name + "使用了" + weapon.name + "攻击" + other.name + "," + other.name + "掉了" + lostHp + "点血,还剩下" + other.hp + "点血");
    }
}
//新建武器类
public class Weapon {
    public String name;
    public int atk;

    public Weapon() {
    }

    public Weapon(String name, int atk) {
        this.name = name;
        this.atk = atk;
    }
}



public class Game {


    public static void main(String[] args) {
        //创造两个角色、warrior  and  thief，并赋予其相应的属性
        Soldier warrior = new Soldier("战士",10,100,5,5);
        Soldier thief = new Soldier("盗贼",10,80,8,4);
      //发生了warrior的攻击行为  warrior攻击thief 
        warrior.attck(thief
             //使用弓箭  进行攻击
                Weapon bow = new Weapon("弓",10);
                warrior.attck(thief,bow);

    }
}
```

```java
//双色球 面向对象 编程
//新建球类
public class Ball {
    public String color;
    public int number;
    private  int id = 123;

    public Ball() {
    }

    public Ball(String color, int number) {
        this.color = color;
        this.number = number;
    }
}

//双色球随机发生的系统
public class RandomSystem {

    public static void main(String[] args) {
        //中奖号码
        System.out.println("中奖号码：");
        //新建一个数组，数组内数字满足红球要求
        int[] numArr = createNumbers();
        //将数组的数字赋予给球
        Ball[] winRedBalls = createRedBalls(numArr);
        System.out.println("红球：");
        for (int i = 0; i < numArr.length; i++){
            System.out.print(winRedBalls[i].number+" ");
        }
        System.out.println();
        //生成蓝球
        Ball winBlueBall = new Ball("蓝色",random(16,1));
        System.out.println("蓝球："+winBlueBall.number);
//机选号码再来一次
        System.out.println("机选号码：");
        int[] computernumArr = createNumbers();
        Ball[] computerRedBalls = createRedBalls(computernumArr);
        System.out.println("红球：");
        for (int i = 0; i < computerRedBalls.length; i++){
            System.out.print(computerRedBalls[i].number+" ");
        }
        System.out.println();
        Ball computerBlueBall = new Ball("蓝色",random(16,1));
        System.out.println("蓝球："+computerBlueBall.number);
//将球数组  和蓝球传进判断方法，进行中奖结果判断
        judge ( winBlueBall, winRedBalls, computerBlueBall, computerRedBalls);


    }
//产生随机数的方法
    public static int random(int max, int min) {
        return (int) (Math.random() * (max - min + 1) + min);
    }
//生成没有重复数的数组
    public static int[] createNumbers() {
        int[] numArr = new int[6];
        for (int i = 0; i < numArr.length; i++) {
            numArr[i] = random(33, 1);
            for (int j = i - 1; j >= 0; j--) {
                if (numArr[i] == numArr[j]) {
                    i--;
                    break;
                }
            }
        }
        return numArr;
    }
//生成球数组
    public static Ball[] createRedBalls(int[] numArr) {
        Ball[] redBalls = new Ball[6];
        for (int i = 0; i < redBalls.length; i++) {
            redBalls[i] = new Ball("红色", numArr[i]);
        }
        return redBalls;
    }
//判断中奖结果
    public static void judge ( Ball winBlueBall,Ball[] winRedBalls,Ball computerBlueBall,Ball[] computerRedBalls){
      int countRed = 0;
        for (int i =0;i<winRedBalls.length;i++){
            for (int j=0;j< computerRedBalls.length;j++){
                if (winRedBalls[i].number==computerRedBalls[j].number){
                    countRed++;
                }
            }
        }
        System.out.println(winRedBalls[1].color+"有"+countRed+"个相同");
        int countBlue = 0;
        if (winBlueBall==computerBlueBall){
            countBlue =1;
            System.out.println("蓝球相同");
        }else {
            System.out.println("蓝球不相同");
        }
        int countSum = countBlue+countRed;
        if (0 < countSum && countSum <= 3) {
            System.out.println("恭喜你，中奖5元");
        } else if (countSum == 4) {
            System.out.println("恭喜你，中奖10元");
        } else if (countSum == 5) {
            System.out.println("恭喜你，中奖200元");
        } else if (countSum == 6 && countBlue == 1) {
            System.out.println("恭喜你，中奖3000元");
        } else if (countSum == 6 && countBlue == 0) {
            System.out.println("恭喜你，中大奖奖500万元");
        } else if (countSum == 7) {
            System.out.println("恭喜你，无敌了");
        } else if (countSum == 0) {
            System.out.println("恭喜你，你很倒霉");
        }
    }


}

```



## 访问器 getter

实例属性的访问，除了打印，还可以通过访问器getter函数

右键 generate-getter

```java
 public int getNumber() {
        return number;
    }
```

实力调用完改方法，就会返回具体的值

```java
 System.out.println(a.getNumber());//得到具体的值
```

## 设置器 setter

对象属性赋值

1. 赋值符号赋值；
2. 调用设置器赋值；

```java
 public void setGender(String gender) {
      this.gender = gender;
    }
//调用设计性别的函数，通过传递参数，设置值。
s.setGender("male");
```

可以设置判断条件，对设置值的有效性进行判断、控制

```java
 public void setScore(int score) {
     if(score>=0){
            this.score = score;
     }else{
          this.score = 0;
     }
   
    }
```

## private 私有的（数据修饰符）

对于一些数据，并不想要公开给予访问、修改、把属性的访问修饰符设置为私有的private，就更好的提供了数据的安全性

```java
 private int id = 123;//私有属性
```

## Java标准类 （Java Bean 类）

规范：

1. 必须提供公共无参构造
2. 必须为私有属性提供符合命名规则的 get/set 方法
3. 必须实现 serializable 接口（通用数据保存、读取和传输的接口）