## `math.random()`

```java
//生成随机数猜大小   只能猜五次，
Scanner scan = new Scanner(System.in);
        int number = (int) (Math.random() * 50 + 1);
        for (int i = 1; i <= 5; i++) {
            System.out.println("请猜第" + i + "次");
            int iptNumber = scan.nextInt();
            if (number < iptNumber) {
                System.out.println("猜大了");
            } else if (number > iptNumber) {
                System.out.println("猜小了");
            } else if (number == iptNumber) {
                System.out.println("猜对了");
                break;
            }
        }
        System.out.println("正确答案：" + number);
```



`math.random()`数学对象随机数方法，每次调用得到0-1且不到1的数字

`math.random()` * 最大数 + 最小数（要得到整数  需要（int）强转）

## 循环嵌套

```java
for (int i = 1; i <= 3; i++) {
    System.out.println("i:" + i);
    for (int j = 1; j <= 5; j++) {
        System.out.println("j:" + j);
    }
}
/*
	i:1 j:12345
	i:2 j:12345
	i:3 j:12345
*/ 
```

在嵌套循环中需要注意的点：

1. 几重循环看的是循环**嵌套**的层级，而不是循环的个数；
2. 在语法上循环嵌套的层次是可以无限的，但是在现实开发当中，最多达到三重循环；嵌套层次过多会导致程序流程控制力度下降，算法可读性降低；
3. 嵌套循环的关键，在于搞清楚循环执行的顺序。外层循环执行1次，内层循环执行1圈;
   内层循环可以访问外层循环的循环控制变量；
   外层循环不能访问内层循环的循环控制变量；
4. 循环控制变量命名，最外层的用i，第二层用j，第三层用k，依次类推，这是“约定俗成”的规范； 同层循环可以使用同名的循环控制变量；
5. break 和 continue，只能对本层循环起作用

```java
//输出2到100之间的质数    
for (int i = 2; i <= 100; i++) {
            int a = 0;
            for (int j = 1; j < i; j++) {
                if (i % j == 0) {
                    a++;
                }
            }
            if (a == 1) {
                System.out.println(i);
            }
        }
```



```java
//99乘法表
        for (int i = 1; i <= 9; i++) {
            String str = "";
            for (int j = 1; j <= i; j++) {
                str = str + j + "*" + i + "=" + (i*j) + " ";
            }
            System.out.println(str);
        }
```

```java
for (int i = 0; i<3;i++){
          System.out.println("i:"+i);
          for (int j = 0; j<10 ; j++){
              if (j==3){break;
              }
              System.out.println("j:"+j);
          }
          System.out.println(666);
      }
        System.out.println(886);
// 0 0 1 2 666
// 1 0 1 2 666
// 2 0 1 2 666 886
```



## 字符串和基本数据类型之间的转换

```java
String str = "123";
// 字符串 -> int
int num = Integer.parseInt(str);
// 字符串 -> double
double weight = Double.parseDouble(str);
```

## GUI

Java 在 javax.swing 包自带了 GUI(graph user interface) 图形开发的 API，使用 `JOPtionPane` 类弹窗，可以替代 Scanner 接收用户信息。

- 消息框：`showMessageDialog()` 替代 System.out.printLn() `JOptionPane.showMessageDialog(null, "显示文字")`
- 输入框：替代 Scanner `JOptionPane.showInputDialog(null, "提示内容");`
- 确认框：`JOptionPane.showConfirmDialog(null,"确认的消息");` 返回值是 int 值，取消 2 否 1 确认 0

```java
//ATM 2.0
String username = "zhangsan";
        String password = "123";
        boolean a = true;
        while (a) {
            //获取用户名、密码
            String iptName = JOptionPane.showInputDialog(null, "用户名");
            String iptpasaword = JOptionPane.showInputDialog(null, "密码");
            //判断登陆成功或者失败
            if (username.equals(iptName) && password.equals(iptpasaword)) {
                JOptionPane.showMessageDialog(null, "登录成功");
                a = false;//用户名、密码正确结束循环
            } else {
                JOptionPane.showMessageDialog(null, "登录失败");
            }
        }
        //进入atm系统
        int money = 500;
        while (!a) {
            String number = JOptionPane.showInputDialog(null, "请选择你要做的事 1、取钱   2、存钱    3、查询余额  4、推出");
            switch (number) {
                //取钱
                case "1":
                    String out = JOptionPane.showInputDialog(null, "输入取出的金额");
                    //金额由字符串转成整型
                    int nout = Integer.parseInt(out);
                    if (nout > money) {
                        JOptionPane.showMessageDialog(null, "余额不足");
                    } else {
                        money -= nout;
                        JOptionPane.showMessageDialog(null, "取出" + nout + "元，剩余" + money + "元");
                    }
                    break;
                //存钱
                case "2":
                    String save = JOptionPane.showInputDialog(null, "输入存入的金额");
                    //金额由字符串转成整型
                   double nsave = Integer.parseInt(save);

                    if (nsave < 0) {
                        JOptionPane.showMessageDialog(null, "输入错误");
                    } else {
                        money += nsave;
                        JOptionPane.showMessageDialog(null, "存入" + nsave + "元，剩余" + money + "元");
                    }
                    break;
                //查询余额
                case "3":
                    JOptionPane.showMessageDialog(null, "余额为：" + money);
                    break;
                //推出
                case "4":
                    //询问用户是否退出系统
                    int exit = JOptionPane.showConfirmDialog(null,"是否退出系统");
                    if (exit==0){
                        JOptionPane.showMessageDialog(null, "再见");
                        a = true;//推出结束循环
                    }
                    break;
                //其他无效输入情况
                default:
                    JOptionPane.showMessageDialog(null, "输入错误");
                    break;
            }
        }
```

