1. 横屏显示结果仿照实践视频

2. 横屏到竖屏的切换

    我使用的是一种打开新视图的方法，设计了两个继承ViewController的类PortraitViewController 和 LandscapeViewController，在其中设置
    
        NotificationCenter.default.addObserver
    
    监测横竖屏情况。使用如下代码：

        let sb = UIStoryboard(name:"Main", bundle: nil)
        let vc = sb.instantiateViewController(withIdentifier: "landscapeViewController") as! LandscapeViewController
        self.present(vc, animated: true, completion: nil)

    以及：
    
        self.dismiss(animated: true, completion:nil)

    当然，我觉得我的方法有些取巧，希望老师能够指点更好的写法

3. 双目运算符的优先级

    我以加减乘除为低级，指数幂次运算为高级，设置了枚举元素
    
        HighBinaryOp((Double,Double) -> Double?)

    因此需要两种临时存储
        
        var pendingOp1: Intermediate? = nil
        var pendingOp2: Intermediate? = nil

    在具体的操作函数中，进行了繁琐的讨论，实在是源于能力不足

4. 弧度制与角度制转换

    在LandscapeViewController中设置按钮反应

        @IBAction func radPressed(_ sender: UIButton) {
        calculatoroperation.radOperation()//对rad变量操作

        ...
        
        }

    同时设置三角函数枚举

        case TriOp((Double,Bool) -> Double?)

    根据rad进行运算

5. 双目操作符替代

    连按双目操作符应该用后一个操作符替代前一个，设置

        var flag: Bool = false

    按下双目操作符置false，按下数字和单目操作符置true

6. 括号运算

    科学计算器应完成简单的括号运算，设置了LeftOp
    和RightOp枚举，设置了stack结构

        var operationStack:[(Double, Double) -> Double?] = []
        var typeStack:[Int] = []
        var numberStack:[Double] = []

    按下左括号，就将临时存储的操作符与操作数压栈，并确定类型，读到右括号就根据类型取出相应的操作符与操作数

7. 2nd的操作

    通过settitle变换按钮值

8. 圆形按钮的设置

    在storyboard中button设置key path属性layer.cornerRadius 

9. [演示视频](https://raw.githubusercontent.com/iwork-2021/iw01-Direction-cy/main/test.mov)

