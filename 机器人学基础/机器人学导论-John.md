:star:[本书答案](https://www.studocu.com/row/document/air-university/financial-reporting/john-j-craig-solutions-manual-to-introduction-to-robotics-mechanics-and-control-pearson-2005/19754862)

# 机器人学导论——学习笔记

## 第 1 章 概述

### 1.1 背景

### 1.2 操作臂的力学与控制

### 1.3 符号



---

## 第 2 章 空间描述和变换

### 2.1 引言

存在一个**世界坐标系**，使得我们定义的位置与姿态都是能够参照世界坐标系或者有由界坐标系定义的笛卡尔坐标系

### 2.2 描述：位置、姿态与位姿

#### 位置描述

 我们可以使用一个3×1的**位置矢量**对世界坐标系的任何点定位

矢量的各个元素用下标$x、y和z$来标明
$$
^{A}P=\begin{pmatrix}
 p_x\\
 p_y\\
p_z
\end{pmatrix}
$$

#### 姿态描述

描述连体坐标系$\{B\}$的一种方法是利用坐标系$\{A\}$的三个主轴单位矢量来表示。

我们用$\hat{X_B} 、\hat{Y_B}和\hat{Z_B}$来表示坐标系$\{B\}$主轴方向的单位矢量。当用坐标系$\{A\}$作参考坐标系时，它们被写作$^{A}\hat{X_B} 、^A\hat{Y_B}和^A\hat{Z_B}$。将这三个单位矢量按顺序排列组成有个3×3矩阵。我们称这个矩阵为**旋转矩阵**。该矩阵是$\{B\}$相对于$\{A\}$的表达，所以我们用符号$_B^AR$来表示
$$
_{B}^{A} R=\left(\begin{array}{} ^A\hat{X}_{B} & ^{A} \hat{Y}_{B} & ^{A} \hat{Z}_{B}
\end{array}\right)=\left(\begin{array}
\hat{X}_{B} \cdot \hat{X}_{A} & \hat{Y}_{B} \cdot \hat{X}_{A} & \hat{Z}_{B} \cdot \hat{X}_{A} \\
\hat{X}_{B} \cdot \hat{Y}_{A} & \hat{Y}_{B} \cdot Y_{A} & \hat{Z}_{B} \cdot \hat{Y}_{A} \\
\hat{X}_{B} \cdot \hat{Z}_{A} & \hat{Y}_{B} \cdot Z_{A} & \hat{Z}_{B} \cdot \hat{Z}_{A}
\end{array}\right)
$$

$$
_{B}^{A} R=\left(\begin{array}{} ^A\hat{X}_{B} & ^{A} \hat{Y}_{B} & ^{A} \hat{Z}_{B}
\end{array}\right)=\left(\begin{array}{}
^B{\hat{X}^T_A}
\\^B{\hat{Y}^T_A}
\\^B{\hat{Z}^T_A}
\end{array}\right)
$$

$$
_{B}^{A} R =_{A}^{B} R^T=_{A}^{B} R^{-1};
\\_{B}^{A} R _{A}^{B} R^T = I_3
$$

![image-20230503225116727](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230503225116727.png)

#### 位姿描述

位置与姿态的组合称为位姿。
$$
\{B\}=\{^A_BR,^AP_{BORG}\}
\\^AP_{BORG}使确定位姿\{B\}的原点位置矢量
$$


### 2.3 映射：从一个坐标系到另一坐标系的变换

![image-20230503230108563](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230503230108563.png)

#### 坐标平移：

$$
^AP={}^BP+{}^AP_{BORG}
$$



#### 坐标旋转

${}^AP$的每个分量就是其坐标系上==单位矢量方向的投影==
$$
^AP_x={}^B\hat{X}_A\cdot{}^BP
\\^AP_y={}^B\hat{Y}_A\cdot{}^BP
\\^AP_z={}^B\hat{Z}_A\cdot{}^BP
$$
简化得


$$
^AP=^A_BR^BP
$$

### 一般变换

![image-20230503231103289](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230503231103289.png)
$$
{}^AP={}^A_BR{}^BP+{}^AP_{BORG}
$$
或
$$
{}^AP={}^A_BT{}^BP
$$

$$
\left(\begin{array}{}^AP
\\1\end{array}\right)=


\left[\begin{array}{ccc:c}
&{}^A_BR && {}^AP_{BORG}\\
\hdashline0&0&0  & 1 
\end{array}\right]=

\left(\begin{array}{}^BP
\\1
\end{array}\right)
$$

式中4×4矩阵被称为**齐次变换矩阵**。

### 2.4 算子：平移、旋转与变换

用于坐标系间点的映射的通用数学表达式称为**算子**。

#### 平移算子

$$
{}^AP_2=D_{Q}(q){}^AP_1
$$

其中
$$
D_Q(q)=\left(\begin{array}{}1&0&0&q_x
\\0&1&0&q_y
\\0&0&1&q_x
\\0&0&0&1
\end{array}\right)
\\\\
q=\sqrt{q_x^2+q_y^2+q_z^2}
$$

#### 旋转算子

$$
{}_AP_2=R_K(\theta){}^AP_1
$$

符号$R_K(\theta)$是一个旋转算子，它表示绕$\hat{K}$轴旋转$\theta$角度。可将这个算子写盛齐次变换矩阵，其中位置矢量的分量为零。

#### 变换算子

$$
{}^AP_2=T{}^AP_1
$$

$T$只涉及一个坐标系，故不需上下标

### 2.5 总结和说明

齐次变换矩阵的三种解释

1. 它是位姿的描述。（坐标系间）
2. 它是变换映射。（坐标系间）
3. 它是变换算子。（坐标系内）


### 2.6 变换的计算

#### 复合变换

$$
{}^AP={}^A_CT{}^CP
\\{}^A_CT={}^A_BT{}^B_CT
$$

#### 逆变换

$$
{}^B_AT=


\left[\begin{array}{ccc:c}
&{}^A_BR^T && -{}^A_BR^T{}^AP_{BORG}\\
\hdashline0&0&0  & 1 
\end{array}\right]
$$

注意，使用符号：
$$
{}^B_AT={}^A_BT^{-1}
$$

### 2.7 变换方程

如果有一个箭头与串联方向相反，就先求出它的逆。



### 2.8 其他姿态描述

旋转矩阵是一种特殊的各列相互正交的单位阵，行列式恒为+1，被称为**标准正交阵。**

由线性代数的结论（正交阵的凯莱公式）可知，任何正交阵$R$存在一个**反对称阵**$S$，满足
$$
R=(I_3-S)^{-1}(I_3+S)
$$
三维反对称阵（即$S=-S^T$）可由是三个参数$(s_x,s_y,s_z)$表示为
$$
S=\left(\begin{array}{}0&-s_z&s_y
\\s_z&0&-s_x
\\-s_y&s_x&0

\end{array}\right)
$$
故旋转矩阵可由三个参数简便的表示出来。



需要注意的是旋转一般不遵循交换律，即${}_B^AR{}^B_CR$与${}^B_CR{}_B^AR$不同。

毋庸置疑矩阵的顺序是重要的，进一步说，这是因为矩阵相乘一般不满足交换律，所以我们经常使用矩阵表示旋转。



#### X-Y-Z固定角

首先将坐标系$\{B\}$和一个已知参考坐标系$\{A\}$重合。先将$\{B\}$绕$\hat{X}_A$旋转$\gamma$角，再绕$\hat{Y}_A$、旋转$\beta$角，最后绕$\hat{Z}_A$旋转$\alpha$角。（==注意顺序==）

每个旋转都是绕固定参考坐标系$\{A\}$的轴，我们规定指针姿态的表示法为$X-Y-Z$固定角，有时把它们定义为**回转角、俯仰角、偏转角**。

![image-20230504173918674](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230504173918674.png)

可直接推导等价旋转矩阵(==注意从右开始==)
$$
\begin{aligned}
{ }_{B}^{A} R_{X Y Z}(\gamma, \beta, \alpha) & =R_{Z}(\alpha) R_{Y}(\beta) R_{X}(\gamma) \\
& =\left(\begin{array}{ccc}
c \alpha & -s \alpha & 0 \\
s \alpha & c \alpha & 0 \\
0 & 0 & 1
\end{array}\right)\left(\begin{array}{ccc}
c \beta & 0 & s \beta \\
0 & 1 & 0 \\
-s \beta & 0 & c \beta
\end{array}\right)\left(\begin{array}{ccc}
1 & 0 & 0 \\
0 & c \gamma & -s \gamma \\
0 & s \gamma & c \gamma
\end{array}\right)
\\& =\left(\begin{array}{ccc}
c \alpha c \beta & c \alpha s \beta s \gamma-s \alpha c \gamma & c \alpha s \beta c \gamma+s \alpha s \gamma \\s\alpha c\beta  & s \alpha s \beta s \gamma+c \alpha c \gamma & s \alpha s \beta c \gamma-c \alpha s \gamma \\
-s \beta & c \beta s \gamma & c \beta c \gamma
\end{array}\right)
\\& =\left(\begin{array}{lll}
r_{11} & r_{12} & r_{13} \\
r_{21} & r_{22} & r_{23} \\
r_{31} & r_{32} & r_{33}
\end{array}\right)
\end{aligned}
$$
通过计算 $ r_{11}  和  r_{21}  $的平方和的平方根, 可求得$  \cos \beta  $。然后用$  -r_{31}  $除以$  \cos \beta  $求其反正切可求得$  \beta  $。那么, 只要 $ c \beta \neq 0$ , 就可以用$  r_{21} / c \beta  $除以  $r_{11} / c \beta$  再求其反正切得到 角, 用$  r_{32} / c \beta  除以  r_{33} / c \beta  $再求其反正切得到$  \gamma $ 角。
总之
$$
\begin{array}{l}
\beta=\operatorname{Atan} 2\left(-r_{31}, \sqrt{r_{11}^{2}+r_{21}^{2}}\right) \\
\alpha=\operatorname{Atan} 2\left(r_{21} / c \beta, r_{11} / c \beta\right) \\
\gamma=\operatorname{Atan} 2\left(r_{32} / c \beta, r_{33} / c \beta\right)
\end{array}
$$


式中$\operatorname{Atan} 2(y,x)$是一个双参变量的反正切函数。（可根据$x,y$的符号判别求得的角所在的象限）

#### Z-Y-X欧拉角

首先将坐标系$\{B\}$和一个已知参考坐标系$\{A\}$重合。先将$\{B\}$绕$\hat{Z}_B$旋转$\alpha$角，再绕$\hat{Y}_B$旋转$\beta$角，最后绕$\hat{X}_B$旋转$\gamma$角。（==注意顺序==）

在这种表示法中，每次都是绕运动坐标系$\{B\}$的各轴旋转而不是绕固定坐标系$\{A\}$的各轴旋转。这样三个一组的旋转被称作**欧拉角**。注意每次旋转所绕的轴的姿态取决于上一次的旋转。由于三个旋转分别是绕着$\hat{Z}、\hat Y和\hat X$所以称这种表示法为$ Z-Y-X $欧拉角。

![image-20230504214634714](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230504214634714.png)

用中间坐标系$\{B^{'}\}$和$\{B^{''}\}$来表达${ }_{B}^{A} R_{Z^{\prime} Y^{\prime} X^{\prime}}(\alpha,\beta,\gamma)$
$$
{ }_{B}^{A} R={ }_{B^{\prime}}^{A} R{ }_{B^{''}}^{B^{\prime}} R{ }_{B}^{B^{''}} R
$$



$$
\begin{aligned}
{ }_{B}^{A} R_{Z^{\prime} Y^{\prime} X^{\prime}} & =R_{Z}(\alpha) R_{Y}(\beta) R_{X}(\gamma) \\
& =\left(\begin{array}{ccc}
c \alpha & -s \alpha & 0 \\
s \alpha & c \alpha & 0 \\
0 & 0 & 1
\end{array}\right)\left(\begin{array}{ccc}
c \beta & 0 & s \beta \\
0 & 1 & 0 \\
-s \beta & 0 & c \beta
\end{array}\right)\left(\begin{array}{ccc}
1 & 0 & 0 \\
0 & c \gamma & -s \gamma \\
0 & s \gamma & c \gamma
\end{array}\right)
\\&=\left(\begin{array}{ccc}
c \alpha c \beta & c \alpha s \beta s \gamma-s \alpha c \gamma & c \alpha s \beta c \gamma+s \alpha s \gamma \\
s\alpha c \beta & s \alpha s \beta s \gamma+c \alpha c \gamma & s \alpha s \beta c \gamma-c \alpha c \gamma \\
-s \beta & c \beta s \gamma & c \beta c \gamma
\end{array}\right)
\end{aligned}
$$
注意这个结果与以相反顺序绕固定轴旋转三次得到的结果完全相同，所以无须通过旋转矩阵的反复计算去求  Z-Y-X  欧拉角。



#### Z-Y-Z欧拉角

坐标系$  \{B\}  $的另一种表示法如下：
首先将坐标系$  \{B\}  $和一个已知的参考坐标系$  \{A\}  $重合。先将$  \{B\}  $绕$  \hat{Z}_{B}  $旋转$  \alpha  $角, 再绕$  \hat{Y}_{B}  $旋转$  \beta  $角, 最后绕$  \hat{Z}_{B}  $旋转$  \gamma  $角。相对运动坐标系$  \{B\}  $的旋转描述是一组欧拉角描述。因为三个旋转是依次绕$  \hat{Z} 、 \hat{Y}  和  \hat{Z}$ , 所以称此描述为$ Z-Y-Z $欧拉角。


$$
{ }_{B}^{A} R_{Z^{\prime} Y^{\prime} Z^{\prime}}(\alpha, \beta, \gamma)=&\left(\begin{array}{ccc}
c a c \beta c \gamma-s a s \gamma & -c \alpha c \beta s \gamma-s a c \gamma & c a s \beta \\
\operatorname{sac} \beta c \gamma+c a s \gamma & -s a c \beta s \gamma+c a c \gamma & s a s \beta \\
-s \beta c \gamma & s \beta s \gamma & c \beta
\end{array}\right)=\left(\begin{array}{lll}
r_{11} & r_{12} & r_{13} \\
r_{21} & r_{22} & r_{23} \\
r_{31} & r_{32} & r_{33}
\end{array}\right)
$$
如果$  \sin \beta \neq 0 $, 可得

$$
\begin{array}{l}
\beta=\operatorname{Atan} 2\left(\sqrt{r_{31}^{2}+r_{32}^{2}}, r_{33}\right) \\
\alpha=\operatorname{Atan} 2\left(r_{23} / s \beta, r_{13} / s \beta\right) \\
\gamma=\operatorname{Atan} 2\left(r_{32} / s \beta,-r_{31} / s \beta\right)
\end{array}
$$

#### 其他转角组合

在前一小节中，已经介绍了三种表示姿态的常用方法:$X-Y-Z $固定角、$Z-Y-X $欧拉角和$Z-Y-Z $欧拉角。每个表示法均需要按一定顺序进行绕主轴的三个旋转。这些表示法是24种表示法中的典型方法，且都被称作**转角排列设定法**。其中，12 种为固定角设定法另12种为欧拉角设定法。注意到由于二者的**对偶性**，对于绕主轴连续旋转的旋转矩阵实际上只有 12种唯一的参数设定法。没有特别的理由优先采用何种表示法，不同作者可以采用不同的表示法，所以把所有 24 种设定法的等效旋转矩阵列出来是有用的。附录 B(在本书后面)给出了所有24种设定法的等效旋转矩阵。

![image-20230504225147354](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230504225147354.png)

![image-20230504225250872](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230504225250872.png)

#### 等效角度—轴线表示法

首先将坐标系$\{B\}$和一个已知的参考坐标系$\{A\}$重合。将$\{B\}$相对矢量${}^A\hat{K}$按右手定则转$\theta$角。

$\{B\}$相对于$\{A\}$的一般姿态可用${}^A_BR(\hat K,\theta)$或$R_K(\theta)$

当选择$\{A\}$的主轴中的一个轴作为旋转轴时，则等效旋转矩阵为：
$$
\begin{aligned}
R_{X}(\theta) & =\left(\begin{array}{ccc}
1 & 0 & 0 \\
0 & \cos \theta & -\sin \theta \\
0 & \sin \theta & \cos \theta
\end{array}\right) \\
R_{Y}(\theta) & =\left(\begin{array}{ccc}
\cos \theta & 0 & \sin \theta \\
0 & 1 & 0 \\
-\sin \theta & 0 & \cos \theta
\end{array}\right) \\
R_{Z}(\theta) & =\left(\begin{array}{ccc}
\cos \theta & -\sin \theta & 0 \\
\sin \theta & \cos \theta & 0 \\
0 & 0 & 1
\end{array}\right)
\end{aligned}
$$


当旋转轴为一般轴时，则等效旋转矩阵为：
$$
R_{K}(\theta)=\left(\begin{array}{ccc}
k_{x} k_{x} v \theta+c \theta & k_{x} k_{y} v \theta-k_{z} s \theta & k_{x} k_{z} v \theta+k_{y} s \theta \\
k_{x} k_{y} v \theta+k_{z} s \theta & k_{x} k_{y} v \theta+c \theta & k_{y} k_{z} v \theta-k_{x} s \theta \\
k_{x} k_{z} v \theta-k_{y} s \theta & k_{y} k_{z} v \theta+k_{x} s \theta & k_{z} k_{z} v \theta+c \theta
\end{array}\right)
$$
式中,$  c \theta=\cos \theta, s \theta=\sin \theta, v \theta=1-\cos \theta $, 并且$  { }^{A} \hat{K}=\left(k_{x} \quad k_{y} \quad k_{z}\right)^{\mathrm{T}} $。$ \theta $的符号由右手定则 确定, 即大拇指指向$  { }^{A} \hat{K}  $的正方向。

令
$$
{ }_{B}^{A} R_{K}(\theta)=\left(\begin{array}{lll}
r_{11} & r_{12} & r_{13} \\
r_{21} & r_{22} & r_{23} \\
r_{31} & r_{32} & r_{33}
\end{array}\right)
$$
则
$$
\theta=A \cos \left(\frac{r_{11}+r_{22}+r_{33}-1}{2}\right)
\\\hat{K}=\frac{1}{2 \sin \theta}\left(\begin{array}{l}
r_{32}-r_{23} \\
r_{13}-r_{31} \\
r_{21}-r_{12}
\end{array}\right)
$$


由上式总可以计算出一个在==0 度到 180 度==之间的$  \theta  $值。对于任意一对轴线-角度$  \left({ }^{A} \hat{K}, \theta\right)$ , 存在另一对轴线-角度, 即$ \left(-{ }^{A} \hat{K},-\theta\right) $, 它们在空间中的姿态相同, 可用同样的旋转矩阵描述。但对于小角度的旋转。轴将变得不确定。当$\theta$等于0度或180时，则无解。

#### 欧拉参数

​	另一种姿态表示法是通过4个数值来表示的，称为**欧拉参数**

​	根据等效旋转轴$\hat{K}=(\begin{array}{}k_x&k_y&h_z)\end{array}^T$和等效旋转角$\theta$得到欧拉角参数
$$
\varepsilon _1=k_x\sin{\frac{\theta}{2}}
\\\varepsilon _2=k_y\sin{\frac{\theta}{2}}
\\\varepsilon _3=k_z\sin{\frac{\theta}{2}}
\\\varepsilon _4=\cos{\frac{\theta}{2}}
$$
很显然，这4个参数是==不独立==的
$$
{\varepsilon _1}^2+{\varepsilon _2}^2+{\varepsilon _3}^2+{\varepsilon _4}^2=1
$$
用欧拉参数组表示的旋转矩阵$R_\varepsilon$是
$$
R_{\varepsilon}=\left(\begin{array}{ccc}
1-2 \varepsilon_{2}^{2}-2 \varepsilon_{3}^{2} & 2\left(\varepsilon_{1} \varepsilon_{2}-\varepsilon_{3} \varepsilon_{4}\right) & 2\left(\varepsilon_{1} \varepsilon_{3}+\varepsilon_{2} \varepsilon_{4}\right) \\
2\left(\varepsilon_{1} \varepsilon_{2}+\varepsilon_{3} \varepsilon_{4}\right) & 1-2 \varepsilon_{1}^{2}-2 \varepsilon_{3}^{2} & 2\left(\varepsilon_{2} \varepsilon_{3}-\varepsilon_{1} \varepsilon_{4}\right) \\
2\left(\varepsilon_{1} \varepsilon_{3}-\varepsilon_{2} \varepsilon_{4}\right) & 2\left(\varepsilon_{2} \varepsilon_{3}+\varepsilon_{1} \varepsilon_{4}\right) & 1-2 \varepsilon_{1}^{2}-2 \varepsilon_{2}^{2}
\end{array}\right)
$$
给定旋转矩阵, 得到对应的欧拉参数是
$$
\begin{array}{l}
\varepsilon_{1}=\frac{r_{32}-r_{23}}{4 \varepsilon_{4}} \\
\varepsilon_{2}=\frac{r_{13}-r_{31}}{4 \varepsilon_{4}} \\
\varepsilon_{3}=\frac{r_{21}-r_{12}}{4 \varepsilon_{4}} \\
\varepsilon_{4}=\frac{1}{2} \sqrt{1+r_{11}+r_{22}+r_{33}}
\end{array}
$$

#### 示教与预定义姿态

### 2.9 自由矢量的变换

如果两个矢量具有相同的维数、大小与方向，则这两个矢量相等；

如果两个矢量在某一功能上产生了相同的作用效果，那么这两个矢量在这一特定功能方面来讲就是等效的。

**线矢量**值与作用线有关的矢量，其作用效果取决于矢量的大小与方向，如力矢量，

**自由矢量**是指可能出现在空间任意的矢量，如果它的大小与方向保持不变，那么它的意义也不变，如纯力矩矢量，我们不关心原点的相对位移

### 2.10 计算问题









## 第3章 操作臂运动学

### 3.1 引言

运动学研究操作臂的运动特性，而不考虑使操作臂产生运动时施加的力。

### 3.2 连杆的描述

当两个刚体之间的相对运动是两个平面互相之间的相对滑动时，连接相邻两个刚体的运动副称为**低副**。

大部分操作臂包括**转动关节**或**移动关节**。

一个连杆运动可用两个参数来描述，这两个参数定义了空间中两个关节轴之间的相对位置。一个是两个轴之间的**距离**，另一个是连杆**扭转角**。

三维空间中的任意两个轴之间的距离均为一个确定值，两个轴之间的距离即为两轴之间**公垂线**的长度。两轴之间的公垂线总是存在的，当两轴不平行时，两轴之间的公垂线**只有一条**。当两关节轴平行时，则存在**无数条**长度相等的公垂线。

假设作一个平面，并使该平面与两关节轴之间的公垂线垂直，然后把关节轴$ i-1 $和关节轴$i$投影到该平面上，在平面内按照右手法则从轴$ i-1$绕$a_{i-1}$转向轴$i$测量两轴线之间的夹角，用转角$\alpha_{i-1}$定义连杆$i-1$的扭转角。

![image-20230506202405378](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230506202405378.png)

### 3.3 连杆连接的描述

#### 处于运动链中间位置的连杆

相邻的两个连杆之间有一个公共的关节轴。沿两个相邻连杆公共轴线方向的距离可以用一个参数描述，该参数称为**连杆偏距**。在关节轴上的连杆偏距记为$d$。用另一个参数描述两相邻连杆绕公共轴线旋转的夹角，该参数称为**关节角**，记为$\theta$。

#### 运动链中首端连杆和末端连杆

对于运动链中的两端的连杆，其参数习惯设定为0，即$a_0=a_n=0.0,\alpha_0=\alpha_n=0.0$。

#### 连杆参数

因此，机器人的每个连杆都可以用4个运动学参数来描述，其中两个参数用于描述连杆本身，另两个参数用于描述连杆之间的连接关系。

通常，对于**转动关节**，$\theta_i$ 为**关节变量**，其他三个连杆参数是固定不变的;对于**移动关节**，$d_i$为**关节变量**，其他三个连杆参数是固定不变的。这种用连杆参数描述机构运动关系的规则称为 Denavit-Hartenberg 方法.

根据上述方法，可以确定任意机构的 Denavit-Hartenberg 参数，并用这些参数来描述该机构。例如，对于一个6关节机器人，需要用 18 个参数就可以完全描述这些固定的运动学参数。如果是6个转动关节的机器人，这时 18 个固定参数可以分6 组$(a_i,\alpha_i,d_i)$表示。

### 3.4 连杆坐标系的定义

#### 运动链中间位置连杆坐标系的定义

通常按照下面的方法确定连杆上的固连坐标系:坐标系$\{i\}$的$\hat Z$轴称为$\hat Z_{i}$，并与关节轴$i$重合，坐标系$\{i\}$的原点位于公垂线$a_i$与关节轴$i$的交点处。$\hat X_i$沿$a_i$方向由关节$i$指向关节$i+1$。

![image-20230507114358559](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230507114358559.png)

#### 运动链中首端连杆和末端连杆坐标系的定义

参考坐标系$\{0\}$可以任意设定，但是为了使问题简化，通常设定$\hat Z_0$轴沿关节轴$ 1$的方向，并且当关节变量$1$为0时，设定参考坐标系$\{0\}$与坐标系$\{1\}$重合。按照这个规定，总有$a_0=0.0和\alpha_0=0.0$。另外，当关节1为转动关节时，$d1=0.0$;当关节1为移动关节时，$\theta_1 =0.0$。

#### 连杆参数在连杆坐标系中的表示方法

如果按照上述方法将连杆坐标系固连于连杆上时，连杆参数可以定义为:
$$
a_i=沿\hat X_i轴,从\hat Z_i移动到\hat Z_{i+1}的距离\\
\alpha_i=绕\hat X_i轴,从\hat Z_i旋转到\hat Z_{i+1}的角度\\
d_i=沿\hat Z_i轴,从\hat X_{i-1}移动到\hat X_i的距离\\
\theta_i=绕\hat Z_i轴,从\hat X_{i-1}旋转到\hat X_i的角度
$$

#### 建立连杆坐标系的步骤

==(坐标轴的建立与D-H参数并不是唯一的)==

1)找出各关节轴，并标出(或画出)这些轴线的延长线。在下面的步骤 2至步骤5中，仅考虑两个相邻的轴线(关节轴i和i+1)。
2)找出关节轴i和i+1之间的公垂线或关节轴i和i+1的交点，以关节轴i和i+1的交点或公垂线与关节轴i的交点作为连杆坐标系计的原点
3)规定$\hat Z_i$轴沿关节轴i的指向。
4)规定$\hat X_i$轴沿公垂线的指向，如果关节轴i和i+1相交，则规定$\hat X_i$轴垂直于关节轴i和i+1所在的平面。
5)按照右手定则确定$\hat Y_i$轴。
6)当第一个关节变量为0时，规定坐标系$\{0\}$和$\{1\}$重合。对于坐标系(N)，其原点和X~的方向可以任意选取。但是在选取时，通常尽量使连杆参数为0。



### 3.5操作臂运动学

#### 连杆变换的推导

为求解${^{i-1}_{i}T}$，我们将其分解为4个子问题，4个变换中的每一个变换都是仅有一个连杆参数的函数，通过观察能够很容易的写出他的形式。首先我们给每个连杆定义3个中间坐标系——$\{P\}、\{Q\}和\{R\}$。

则
$$
{}^{i-1}P={}^{i-1}_RT{}^R_QT{}^Q_PT{}^P_iT{}^iP
$$
或
$$
{}^{i-1}P={}^{i-1}_iT{}^iP
$$
考虑每一个变换矩阵，可以写成
$$
{}^{i-1}_iT=R_X(\alpha_{i-1})D_X(a_{i-1})R_Z(\theta_i)D_Z(d_i)
$$
或
$$
{}^{i-1}_iT=Screw_X(\alpha_{i-1},a_{i-1})Screw_Z(\theta_i,d_i)
$$
这里$Screw_Q(r,\phi)$代表沿$\hat Q$轴平移$r$，再绕$\hat Q$轴旋转角度$\phi$的组合变换。

由上可得到${}^{i-1}_iT$的一般表达式
$$
{}^{i-1}_iT=\left(\begin{array}{cccc}c\theta_i&-s\theta_i&0&a_{i-1}
\\s\theta_ic\alpha_{i-1}&c\theta_ic\alpha_{i-1}&-s\alpha_{i-1}&-s\alpha_{i-1}d_i
\\s\theta_is\alpha_{i-1}&c\theta_is\alpha_{i-1}&c\alpha_{i-1}&c\alpha_{i-1}d_i
\\0&0&0&1
\end{array}\right)
$$






![image-20230507153016853](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230507153016853.png)

#### 连杆变换的连乘

$$
{}^0_NT={}^0_1T{}^1_2T{}^2_3T\cdot\cdot\cdot{}^{N-1}_NT
$$

### 3.6 驱动器空间、关节空间和笛卡尔空间

对于一个具有$ n $个自由度的操作臂来说，它的所有连杆位置可由一组$ n$个关节变量加以确定。这样的一组变量常被称为$ nX1$的**关节向量**。所有关节向量组成的空间称为**关节空间**。至此，我们关心的是如何将已知的关节空间描述转化为在**笛卡儿空间**中的描述，有时称为任务空间和操作空间。

### 3.7 实例：两种工业机器人的运动学问题

#### PUMA 560

PUMA 560 是一个六自由度机器人，所有关节均为转动关节

<img src="https://pic1.zhimg.com/v2-6d32cf8818f3795c66e6fc65da7c4666_720w.jpg?source=d16d100b" style="zoom: 100%" />

![在这里插入图片描述](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/16480d4a87c64f4183b25eacd4e30202.png)



![在这里插入图片描述](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/d017a0f8af84489995d2c5876fcda4df.jpeg)

![在这里插入图片描述](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/69c3cee0be8648e894d5fff839f4ad2b.jpeg)

![image-20230507165110437](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230507165110437.png)

![image-20230507165226192](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230507165226192.png)

#### Yasukawa Motoman L-3

太难了:cry:

### 3.8 坐标系的标准命名

![image-20230508121129524](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230508121129524.png)

#### 基坐标系{B}

操作臂的基座，有时称为连杆0。

#### 固定坐标系{S}

此坐标系与任务相关，是一个通用坐标系，机器人的所有运动都是相对于它来执行的。有时称它为**任务坐标系、世界坐标系**或**通用坐标系**。固定坐标系通常根据基坐标系确定，即${}^B_ST$

#### 腕部坐标系{W}

操作臂的末端连杆，有时也可称为坐标系$\{N\}$。由基坐标系确认，即$\{W\}={}^B_WT={}^0_NT)$

#### 工具坐标系{T}

附于机器人所夹持工具的末端，当手部没有夹持工具时，原点位于机器人的指尖之间。工具坐标系通常相对于腕部坐标系来确定。

#### 目标坐标系{G}

是对机器人移动工具到达的位置描述。目标坐标系通常由固定坐标系确定。

![image-20230508122428097](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230508122428097.png)

### 3.9 工具的位置

$$
{}^S_TT={}^B_ST^{-1}{}^B_WT{}^W_TT
$$

### 3.10 计算问题



## 第四章 操作臂逆运动学

### 4.1 引言

本章探究的问题是求出要要求的关节角，是的工具坐标系$\{T\}$位于固定坐标系$\{S\}$的特定位姿，该问题可分为两部分：

+ 首先，进行坐标系变换求出相对于基坐标系$\{B\}$的腕部坐标系$\{W\}$
+ 然后，应用逆运动学求关节角



### 4.2 解的存在性

#### 解的存在性

解是否存在的问题首先要提到操作臂的**工作空间**，工作空间是操作臂末端执行器所能到达的范围。若要求解存在，则被指定的目标点必须在工作空间内。

**灵活工作空间**指机器人的末端执行器能够从各个方向到达的空间区域。

**可达工作空间**是机器人至少从一个方向上可以到达空间的子集。



若腕部坐标系的期望位置与姿态在工作空间内，则至少存在一个解。





#### 多解问题

在存在多解时比较合理的是，选择**最近解**。但是最“近”解可能有几种定义方式。

例如，典型的机器人有 3个大连杆，附带3个小连杆，调整姿态的连杆靠近末端执行器。在这种情况下，计算“较近”解时需要==加权==，使得这种选择主要移动小连杆而不是移动大连杆。在存在障碍的情况下，“较近”解可能发生碰撞，这时只能选择“较远”解一一为此，一般需要计算全部可能的解。

通常，连杆的非零参数越多，到达某一特定目标的方式也越多。以一个具有 6个旋转关节的操作臂为例，解的最大数目与等于零的连杆长度参数$(a_i)$的数目有关。非零参数越多，解的最大数目就越大。对于一个全部为旋转关节的6自由度操作臂来说，可能多达16种解

![image-20230509155727211](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230509155727211.png)

#### 解法

与线性方程组不同，非线性方程组没有通用的求解算法。针对解法问题，最好对已知操作臂“解”的构成形式加以定义。

对于多解情况，这个定义的要点正是我们要求它能求得所有的解。因此，在求解操作臂问题时我们不考虑某些数值迭代程序，即这些方法不能保证求出全部的解。

我们把操作臂的全部求解方法分成两大类:**封闭解**和**数值解**。由于数值解的迭代性质，因此它一般要比相应封闭解的求解速度慢得多。

下面主要讨论*封闭解*方法。在本书中，“封闭形式”意指基于解析形式的解法，或者对于不高于$ 4$次的多项式不用迭代便可完全求解。可将封闭解的求解方法分为两类:**代数法**和**几何法**。有时它们的区别并不明显，在几何方法中引人了代数描述，因此这两种方法是相似的。这两种方法或许*仅是求解过程不同*。



### 4.3 当n<6时操作臂子空间的描述

对于一个给定的操作臂来说，一系列可达目标坐标系构成了可达工作空间。对于一个$n$自由度操作臂($n$<6)，可达工作空间可看成是n自由度**子空间**$R^n$的一部分。
确定$n$自由度操作臂子空间的一种方法就是给出腕部坐标系或工具坐标系的表达式它是含有$n$个变量的函数。如果将这$n$个变量看作自由变量，那么它们所有的可能取值就构成了这个子空间。

对具有n自由度操作臂的目标点进行定义，我们通常采用$n$个参数来确定这个目标点。

因此，对于少于6个自由度的操作臂来说，当确定一般目标点时，求解方法如下:

1) 已知一般目标坐标系${}^S_GT$，计算一个修正的目标坐标系${}^S_{G^{'}}T$，使得${}^S_{G^{'}}T$位于操作臂的子空间内，并且和${}^S_GT$尽可能“靠近”。应预先确定“靠近”标准。
2) 将${}^S_{G^{'}}T$作为期望目标，计算逆运动学来求关节角。注意，如果目标点不在操作臂的工作空间内，将可能没有解。



### 4.4 代数解法和几何解法

#### 代数解法

以三连杆平面操作臂为例

![image-20230509210254422](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230509210254422.png)

机械臂的运动学方程
$$
{ }_{W}^{B} T={ }_{3}^{0} T=\left(\begin{array}{cccc}
c_{123} & -s_{123} & 0.0 & l_{1} c_{1}+l_{2} c_{12} \\
s_{123} & c_{123} & 0.0 & l_{1} s_{1}+l_{2} s_{12} \\
0.0 & 0.0 & 1.0 & 0.0 \\
0 & 0 & 0 & 1
\end{array}\right)
$$
由于我们研究的是平面操作臂, 因此通过确定三个量$  x 、 y  和  \phi  $很容易确定这些目标点的位置, 其中$  \phi  $是连杆$ 3 $在平面内的姿态 (与$  +\hat{X}  $轴相关)。因 此, 与其给出通用的  { }_{W}^{B} T  作为目标点的描述, 还不如假定变换矩阵具有如下形式:
$$
{ }_{W}^{B} T=\left(\begin{array}{cccc}
c_{\phi} & -s_{\phi} & 0.0 & x \\
s_{\phi} & c_{\phi} & 0.0 & y \\
0.0 & 0.0 & 1.0 & 0.0 \\
0 & 0 & 0 & 1
\end{array}\right)
$$
所有可达目标点必须位于上式描述的子空间上。 令两式相等, 可以求得$ 4 $个非线性方 程, 进而求出$  \theta_{1} 、 \theta_{2}  和  \theta_{3}$:

$$
\begin{aligned}
c_{\phi} & =c_{123} \\
s_{\phi} & =s_{123} \\
x & =l_{1} c_{1}+l_{2} c_{12} \\
y & =l_{1} s_{1}+l_{2} s_{12}
\end{aligned}
$$
由
$$
x^2+y^2=l_1^2+l_2^2+2l_1l_2c_2
$$
解得
$$
c_2=\frac{x^2+y^2-l_1^2-l_2^2}{2l_1l_2}
$$
需要注意的是，有解的条件是上式右边的值必须在-1~1。

假定目标在工作空间内，$s_2$的表达式是
$$
s_2=\pm \sqrt{1-c_2^2}
$$
可得
$$
\theta_2=Atan2(s_2,c_2)
$$
由
$$
\begin{array}{l}
x=k_{1} c_{1}-k_{2} s_{1} \\
y=k_{1} s_{1}+k_{2} c_{1}
\end{array}
$$
式中
$$
\begin{array}{l}
k_{1}=l_{1}+l_{2} c_{2} \\
k_{2}=l_{2} s_{2}
\end{array}
$$
若
$$
r=+\sqrt{k_1^2+k_2^2}
$$
且
$$
\gamma=\operatorname{Atan} 2\left(k_{2}, k_{1}\right)
$$
则
$$
\begin{array}{l}
k_{1}=r \cos \gamma \\
k_{2}=r \sin \gamma
\end{array}
$$
则
$$
\begin{array}{l}
\frac{x}{r}=\cos \gamma \cos \theta_{1}-\sin \gamma \sin \theta_{1} \\
\frac{y}{r}=\cos \gamma \sin \theta_{1}+\sin \gamma \cos \theta_{1}
\end{array}
$$
因此
$$
\begin{array}{l}
\cos \left(\gamma+\theta_{1}\right)=\frac{x}{r} \\
\sin \left(\gamma+\theta_{1}\right)=\frac{y}{r}
\end{array}
$$
利用双变量反正切公式，得
$$
\gamma+\theta_{1}=\operatorname{Atan} 2\left(\frac{y}{r}, \frac{x}{r}\right)=\operatorname{Atan} 2(y, x)
$$
从而
$$
\theta_{1}=\operatorname{Atan} 2(y, x)-\mathrm{A} \tan 2\left(k_{2}, k_{1}\right)
$$
注意, $ \theta_{2}  $符号的选取将导致$k_2$符号的变化, 因此影响到$  \theta_{1}  $。同时注意, 如果$  x=y=0 $, 则上式无定义, 此时$  \theta_{1}$可取任意值。
$$
\theta_{1}+\theta_{2}+\theta_{3}=\operatorname{Atan} 2\left(s_{\phi}, c_{\phi}\right)=\phi
$$

#### 几何解法

对于下图只有3自由度的操作臂来说，由于操作臂是平面的，因此我们可以利用平面几何关系直接求解。

![image-20230510091137676](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230510091137676.png)

对于实现表示的三角形，利用余弦定理求解$\theta_2$：
$$
x^2+y^2=l_1^2+l_2^2-2l_1l_2\cos(180+\theta_2)
$$
则
$$
c_2=\frac{x^2+y^2-l_1^2-l_2^2}{2l_1l_2}
$$
为使该三角形成立，到目标点的距离$\sqrt{x^2+y^2}\le l_1+l_2$
$$
\beta=\operatorname{Atan} 2\left(y,x\right)
$$

$$
\cos\psi=\frac{x^2+y^2+l_1^2-l_2^2}{2l_1\sqrt{x^2+y^2}}
\\0\le\psi\le180^{\circ}
$$

$$
\theta_1=\beta\pm\psi
$$

当$\theta_2<0$时，取”$+$“号；当$\theta_2>0$时，取“$-$”号
$$
\theta_1+\theta_2+\theta_3=\phi
$$
($\phi=180^\circ$maybe)由上式得到$\theta_3$

### 4.5 简化成多项式的代数解法

即使只有一个变量(如$\theta$)，超越方程往往也很难求解，因为它一般常以$\sin{\theta}$和$\cos\theta$的形式出现。可进行下列变换，用单一变量$u$来表示:
$$
u=\tan{\frac{\theta}{2}}
\\\cos\theta=\frac{1-u^2}{1+u^2}
\\\sin\theta=\frac{2u}{1+u^2}
$$
例如：将超越方程$a\cos{\theta}+b\sin\theta=c$变成含半角正切的多项式，以求解$\theta$。

取$u$的幂次排序
$$
(a+c)u^2-2bu+(c-a)=0
$$
则
$$
\theta=2\tan^{-1}(\frac{b\pm\sqrt{b^2+a^2-c^2}}{a+c})
$$


注意在利用$\operatorname{Atan}$求解$\theta$是，如果分母为零，那么反正切的自变量会无限大，因此$\theta=180^{\circ}$。在程序中应先检查分母是否为零。

4次多项式便具有*封闭形式*的解，使用能够用4阶（或低于4阶）的代数方程求解的操作臂是相当简单的，它们被称为有**封闭解**的操作臂

### 4.6 三轴相加的Pieper解法

该种方法是针对6个关节均为旋转关节且后面3个轴相交的操作臂。

当最后3个轴相交时，连杆坐标系$\{4\}、\{5\}$和$\{6\}$的原点均位于这个交点上。这个点在基坐标系中的位置是
$$
{}^0P_{4ORG}={}^0_1T{}^1_2T{}^2_3T{}^3P_{4ORG}=\left[
\begin{array}{c}
x
\\y
\\z
\\1
\end{array}
\right]
$$
或者，当$i=4$时

由
$$
{}^{i-1}_iT=\left(\begin{array}{cccc}c\theta_i&-s\theta_i&0&a_{i-1}
\\s\theta_ic\alpha_{i-1}&c\theta_ic\alpha_{i-1}&-s\alpha_{i-1}&-s\alpha_{i-1}d_i
\\s\theta_is\alpha_{i-1}&c\theta_is\alpha_{i-1}&c\alpha_{i-1}&c\alpha_{i-1}d_i
\\0&0&0&1
\end{array}\right)
$$
可得
$$
{ }^{0} P_{4 O R G}={ }_{1}^{0} T_{2}^{1} T_{3}^{2} T\left(\begin{array}{c}
a_{3} \\
-d_{4} s \alpha_{3} \\
d_{4} c \alpha_{3} \\
1
\end{array}\right)
$$
或
$$
{ }^{0} P_{4 O R G}={ }_{1}^{0} T{ }_{2}^{1} T\left(\begin{array}{c}
f_{1}\left(\theta_{3}\right) \\
f_{2}\left(\theta_{3}\right) \\
f_{3}\left(\theta_{3}\right) \\
1
\end{array}\right)
$$
式中
$$
\left(\begin{array}{c}
f_{1} \\
f_{2} \\
f_{3} \\
1
\end{array}\right)={ }_{3}^{2} T\left(\begin{array}{c}
a_{3} \\
-d_{4} s \alpha_{3} \\
d_{4} c \alpha_{3} \\
1
\end{array}\right)
$$
对于上式可得出
$$
\begin{array}{l}
f_{1}=a_{3} c_{3}+d_{4} s \alpha_{3} s_{3}+a_{2} \\
f_{2}=a_{3} c \alpha_{2} s_{3}-d_{4} s \alpha_{3} c \alpha_{2} c_{3}-d_{4} s \alpha_{2} c \alpha_{3}-d_{3} s \alpha_{2} \\
f_{3}=a_{3}s\alpha_{2} s_{3}-d_{4} s \alpha_{3} s \alpha_{2} c_{3}+d_{4} c \alpha_{2} c \alpha_{3}+d_{3} c \alpha_{2} \\
\end{array}
$$
则
$$
{ }^{0} P_{4 O R G}=\left(\begin{array}{c}
c_{1} g_{1}-s_{1} g_{2} \\
s_{1} g_{1}+c_{1} g_{2} \\
g_{3} \\
1
\end{array}\right)
$$
式中
$$
\begin{array}{l}
g_{1}=c_{2} f_{1}-s_{2} f_{2}+a_{1} \\
g_{2}=s_{2} c \alpha_{1} f_{1}+c_{2} c \alpha_{1} f_{2}-s \alpha_{1} f_{3}-d_{2} s \alpha_{1} \\
g_{3}=s_{2} s \alpha_{1} f_{1}+c_{2} s \alpha_{1} f_{2}+c \alpha_{1} f_{3}+d_{2} c \alpha_{1}
\end{array}
$$
现在写出  ${ }^0 P_{4 O R G}  $绝对值平方的表达式, 这里$  r=x^{2}+y^{2}+z^{2} $,由上式可以得到
$$
r=g_{1}^{2}+g_{2}^{2}+g_{3}^{2}
$$
所以对于$g_i$
$$
r=f_{1}^{2}+f_{2}^{2}+f_{3}^{2}+a_{1}^{2}+d_{2}^{2}+2 d_{2} f_{3}+2 a_{1}\left(c_{2} f_{1}-s_{2} f_{2}\right)
$$
现在，写出Z方向分量的方程，那么表示这个方程组的两个方程如下：

$$
\begin{array}{l}
r=\left(k_{1} c_{2}+k_{2} s_{2}\right) 2 a_{1}+k_{3} \\
z=\left(k_{1} s_{2}-k_{2} c_{2}\right) s \alpha_{1}+k_{4}
\end{array}
$$
式中

$$
\begin{array}{l}
k_{1}=f_{1} \\
k_{2}=-f_{2} \\
k_{3}=f_{1}^{2}+f_{2}^{2}+f_{3}^{2}+a_{1}^{2}+d_{2}^{2}+2 d_{2} f_{3} \\
k_{4}=f_{3} c \alpha_{1}+d_{2} c \alpha_{1}
\end{array}
$$
上面很有用，因为它消去了因变量$\theta_1$，并且因变量$\theta_2$的关系式简单

现在讨论如何由上式求解$\theta$，分三种情况:

1)若$a_1=0$，则$y=k_3$，这里r是已知的。右边$k_3$仅是关于$\theta_3$的函数。包含$\tan{\frac{\theta_3}{2}}$的二次方程可以解出$\theta_3$。

2)若 $s\alpha_1=0$，则$z=k_4$，这里$z$是已知的。利用上面的一元二次方程可以解出$\theta_3$。
3)否则，从上式中消去$s_2$和$c_2$，得到
$$
\frac{(r-k_3)^2}{4a_1^2}+\frac{(z-k_4)^2}{s^2\alpha_1}=k_1^2+k_2^2
$$
可得到一个4次方程，由此可解出$\theta_3$。

解出$\theta_3$后，就可以依次解出$\theta_2$与$\theta_1$。为了完成求解工作，还需要求出$\theta_4、\theta_5、\theta_6$。由于这些轴相交，故这些关节角只影响末端连杆的方向，我们只需要${}^0_6R$的旋转分量就计算出这三个角度。在求出$\theta_1、\theta_2、\theta_3$ 后，可以由$\theta_4=0$时连杆坐标系$\{4\}$相对于基坐标系的方向计算出${}^4_6R|_{\theta_4=0}={}^4_6R^{-1}|_{\theta_4=0}{}^0_6R$。坐标系$\{6\}$的期望方向与连杆坐标系$\{4\}$的方向的差别仅在于最后三个关节的作用。由于${}^0_6R$ 已知，因此这个问题可以通过如下计算得出结果:
$$
{}^4_6R|_{\theta_4=0}={}_4^0R^{-1}|_{\theta_4=0}{}_6^0R
$$
对于大多数操作臂来说，完全可以将第2章介绍的$Z-Y-Z $欧拉角解法应用于${}^4_6R|_{\theta_4=0}$解出最后三个关节角。对于任何一个 4、5、6 轴相交的操作臂来说，最后三个关节角能够通过一组合适的欧拉角来定义。最后的三个关节通常有两种解，因此这种操作臂解的总数就是前三个关节解的数量的 2倍。

### 4.7 操作臂逆运动学实例 

#### Unimation PUMA 560 机器人

当${}^0_6T$中的数值已知时，我们希望通过下列方程解出$\theta_i$。
$$
{}^0_6T=\left[\begin{array}{cccc}
r_{11}&r_{12}& r_{13}&p_x
\\r_{21}&r_{22}&r_{23}&p_y
\\r_{31}& r_{32}&r_{33}&p_z
\\0&0&0&1
\end{array}\right]={}^0_1T(\theta_1){}^1_2T(\theta_2){}^2_3T(\theta_3){}^3_4T(\theta_4){}^4_5T(\theta_5){}^5_6T(\theta_6)
$$
对于$\theta_1$
$$
\left[\begin{array}
{cccc}
c_1&s_1&0&0\\
-s_1&c_1&0&0\\
0&0&1&0\\
0&0&0&1
\end{array}\right]
\left[\begin{array}
{cccc}
r_{11}&r_{12}& r_{13}&p_x
\\r_{21}&r_{22}&r_{23}&p_y
\\r_{31}& r_{32}&r_{33}&p_z
\\0&0&0&1
\end{array}\right]
={}_6^1T
$$
令两边的元素（2,4）相等，得到
$$
-s_1p_x+c_1p_y=d_3
$$
为求解这种形式的方程，可进行三角恒等变换
$$
p_x=\rho\cos{\phi}
\\p_y=\rho\sin{\phi}
$$
式中


$$
\rho=\sqrt{p_x^2+p_y^2}
\\\phi=\operatorname{Atan}2(p_y,p_x)
$$
得
$$
c_1s_\phi-s_1c_\phi=\frac{d_3}{\rho}
$$
由差角公式得
$$
\sin(\phi-\theta_1)=\frac{d_3}{\rho}
$$
因此
$$
\cos(\phi-\theta_1)=\pm\sqrt{1-\frac{d_3^2}{\rho^2}}
$$
则
$$
\phi-\theta_1=\operatorname{Atan2}\left(\frac{d_3}\rho,\pm\sqrt{1-\frac{d_3^2}{\rho^2}}\right)
$$
最后$\theta_1$的解可以写成
$$
\theta_1=\operatorname{Atan2}(p_x,p_y)-\operatorname{Atan2}(d_3,\pm\sqrt{p_x^2+p_y^2-d_3^2})
$$
注意到上式的正负号，$\theta_1$可以有两种解。现在$\theta_1$已知，则式(84)的左边已知。若令式(84)两边的元素(1,4)(3,4)分别相等，得
$$
c_1p_x+s_1p_y=a_3c_{23}-d_4s_{23}+a_2c_2
\\-p_z=a_3s_{23}+d_4c_{23}+a_2s_2
$$
将式(93)与(85)平方后相加，得
$$
a_3c_3-d_4s_3=K
$$
式中
$$
K=\frac{p_x^2+p_y^2+p_x^2-a_2^2-a_3^2-d_3^2-d_4^2}{2a_2}
$$
注意，式（94）已消去$\theta_1$有关的项，式（94）与式（85）形式相同，因此采用同样的三角恒等变换可以得出$\theta_3$的解：
$$
\theta_3=\operatorname{Atan2}(a_3,d_4)-\operatorname{Atan2}(K,\pm\sqrt{a_3^2+d_4^2-K^2})
$$
式中的正负号使得$\theta_3$有两个不同的解。重新整理式（83）,使得$\theta_2$以及左边所有的函数均为已知：
$$
[{}_3^0T(\theta_2)]^{-1}{_6^0}T={}^3_4T(\theta_4){}^4_5T(\theta_5){}^5_6T(\theta_6)
$$
或
$$
\left[\begin{array}
{cccc}
c_1c_{23}&s_1c_{23}&-s_{23}&-a_2c_3\\
-c_1s_{23}&-s_1s_{23}&c_{23}&a_2s_3\\
-s_1&c_1&0&-d_3\\
0&0&0&1
\end{array}\right]
\left[\begin{array}
{cccc}
r_{11}&r_{12}& r_{13}&p_x
\\r_{21}&r_{22}&r_{23}&p_y
\\r_{31}& r_{32}&r_{33}&p_z
\\0&0&0&1
\end{array}\right]
={}_6^3T
$$
令上式两边元素（1,4）（2,4）相等，得到
$$
c_1c_{23}p_x+s_1c_{23}p_y-s_{23}p_z-a_2c_3=a_3
\\-c_1s_{23}p_x-s_1s_{23}p_y-c_{23}p_z+a_2s_3=d_4
$$
由上式解出$s_{23}$与$c_{23}$，结果为
$$
\begin{array}{l}
s_{23}=\frac{\left(-a_{3}-a_{2} c_{3}\right) p_{z}+\left(c_{1} p_{x}+s_{1} p_{y}\right)\left(a_{2} s_{3}-d_{4}\right)}{p_{z}^{2}+\left(c_{1} p_{x}+s_{1} p_{y}\right)^{2}} \\
c_{23}=\frac{\left(a_{2} s_{3}-d_{4}\right) p_{z}-\left(a_{3}+a_{2} c_{3}\right)\left(c_{1} p_{x}+s_{1} p_{y}\right)}{p_{z}^{2}+\left(c_{1} p_{x}+s_{1} p_{y}\right)^{2}}
\end{array}
$$
上式分母相等，且为正数，所以可以求得$\theta_2$和$\theta_3$
$$
\begin{array}{l} 
\theta_{23}= \operatorname{Atan} 2[(-a_{3}-a_{2} c_{3}) p_{z}-(c_{1} p_{x}+s_{1} p_{y})(d_{4}-a_{2} s_{3})
(a_{2} s_{3}-d_{4}) p_{z}-(a_{3}+a_{2} c_{3})(c_{1} p_{x}+s_{1} p_{y})]
\end{array}
$$
根据$\theta_1$和$\theta_3$解的4种组合，由式（101）算出4个$\theta_{23}$的值。然后，计算$\theta_2$的4个可能的解为
$$
\theta_2=\theta_{23}-\theta_3
$$
现在，式（98）左边已知，令式（98）两边的元素（1,3）和（3,3）分别相等，得
$$
r_{13}c_1c_{23}+r_{23}s_1c_{23}-r_{33}s_{23}=-c_4s_5
\\-r_{13}s_1+r_{23}c_1=s_4s_5
$$
只要$s_5\neq0$，就可以解出$\theta_4$
$$
\theta_{4}=A \tan 2\left(-r_{13} s_{1}+r_{23} c_{1},-r_{13} c_{1} c_{23}-r_{23} s_{1} c_{23}+r_{33} s_{23}\right)
$$
当$\theta_5=0$，操作臂处于奇异位形，此时关节轴4 和关节轴6 共线，引起机器人末端连杆相同的运动。在这种情况下，所有结果(所有可能的解)都是$\theta_4$与$\theta_6$的和或差。这种情况可以通过检查式(106)中 Atan2 的两个变量是否都接近零来判断。如果是，则$\theta_4$可以任意选取，当计算出$\theta_6$时，相应地选取$\theta_4$。
改写式(3)，使公式左边均为$\theta_4$和其他已知量的函数，即
$$
[{}_4^0T(\theta_2)]^{-1}{_6^0}T={}^4_5T(\theta_5){}^5_6T(\theta_6)
$$
式中，$[{}_4^0T(\theta_2)]^{-1}$由下式给出
$$
\left[
\begin{array}{cccc}
c_1c_{23}c_4+s_1s_4&s_1c_{23}c_4-c_1s_4&-s_{23}c_4&-a_2c_3c_4+d_3s_4-a_3c_4
\\-c_1c_{23}s_4+s_1c_4&-s_1c_{23}s_4-c_1c_4&s_{23}s_4&a_2c_3s_4+d_3c_4+a_3s_4
\\-c_1s_{23}&-s_1s_{23}&-c_{23}&a_2s_3-d_4
\\0&0&0&1
\end{array}
\right]
$$
令式（105）两边元素（1,3）（3,3）分别相等，得
$$
r_{13}(c_1c_{23}c_4+s_1s_4)+r_{23}(s_1c_{23}s_4-c_1s_4)-r_{33}(s_{23}c_4)=-s_5\\
r_{13}(-c_1s_{23})+r_{23}(-s_1s_{23})+r_{33}(-c_{23})=c_5
$$
由此可求出$\theta_5$
$$
\theta_5=\operatorname{Atan2}(s_6,c_6)
$$
式中
$$
\begin{aligned}
s_{6}= & -r_{11}\left(c_{1} c_{23} s_{4}-s_{1} c_{4}\right)-r_{21}\left(s_{1} c_{23} s_{4}+c_{1} c_{4}\right)+r_{31}\left(s_{23} s_{4}\right) \\
c_{6}= & r_{11}\left[\left(c_{1} c_{23} c_{4}+s_{1} s_{4}\right) c_{5}-c_{1} s_{23} s_{5}\right]+r_{21}\left[\left(s_{1} c_{23} c_{4}-c_{1} s_{4}\right) c_{5}-s_{1} s_{23} s_{5}\right] \\
& -r_{31}\left(s_{23} c_{4} c_{5}+c_{23} s_{5}\right)
\end{aligned}
$$
由于在式 (92) 和式 (96) 中出现了$ \pm $号, 因此这些方程会有 4 种解。此外, 由于操作臂“翻转”腕关节可得到另外 4 个解。对于以上计算出的 4 种解，由腕关节翻转可得到  
$$
\theta_{4}^{\prime}=\theta_{4}+180^{\circ}
\\
\theta_{5}^{\prime}=-\theta_{5} \\

\theta_{6}^{\prime}=\theta_{6}+180^{\circ}
$$

计算出所有 8 种答案以后, 由于关节运动范围的限制要将其中的一些解 (甚至全部) 舍去。在余下的有效解中, 通常选取一个最接近于当前操作臂位形的解。

### 4.8 标准坐标系

1）确认固定坐标系的位置

2）给定工具坐标系的参数

3）给定目标坐标系

4）计算一系列关节角度使关节运动到目标位置

### 4.9 操作臂求解

SOLVE 函数可进行笛卡儿变换，也称为逆运动学函数。基本逆运动学求解相对于基坐标系的腕部坐标系。
给定目标坐标系${}^S_TT$，SOLVE 应用工具坐标系和固定坐标系的定义来计算$\{W\}$相对于$\{W\}$的位置${}^B_wT$:
$$
{}_W^BT={}_S^BT{}^S_TT{}^S_WT^{-1}
$$


然后，逆运动学将员${}^B_wT$作为输人，计算$\theta_1$到$\theta_n$。

### 4.10 重复精度和精度

示教点是操作臂运动实际要达到的点，同时关节位置传感器读取关节角并存储。当命令机器人返回这个空间点时，每个关节都移动到已存储的关节角的位置。当制造商在确定操作臂返回示教点的精度时，就是在确定操作臂的**重复精度**。

只要目标位置和姿态是用笛卡儿坐标来确定的，为了求出关节角，就必须要计算逆运动学问题。对于可用笛卡儿坐标描述目标位置的系统，它可以将操作臂移动到工作空间中不曾示教过的点，这些点或许以前从未达到过。我们称这些点为**计算点**。到达这个计算点的精度就被称作为操作臂的精度。

操作臂的精度不会超过其重复精度。通过对操作臂运动学参数做辨识，标定技术可以提高操作臂的精度。

### 4.11 计算问题

因此，计算效率是一个重要问题。这些速度上的要求并不包括应用数值计算技术的影响(实际上是迭代算法)，因此，在此对这个问题不做讨论。对于逆运动学问题，一个关于Atan2的查表法子程序经常被用于提高计算速度。
多解的计算结构也十分重要。并行计算所有的解通常效率是相当高的，而不是依次顺序计算。当然在某些应用中，如果并不需要所有的解，则只计算一个解就可以节省不少的计算时间。
当用几何方法求逆运动学解时，在得到第一个解后，有时可以通过对各种角度做简单操作来计算多解问题。即第一个解的计算是相当费时的，但是通过计算角度的和或差以及加减$\pi$等方法可以很快求得其余的解。

## 第5章 雅克比：速度和静力

### 5.1 引言

### 5.2 时变位置和姿态的符号表示

#### 位置矢量的导数

$$
{}^BV_Q=\frac{d}{dt}{}^BQ=\lim_{\bigtriangleup t \to 0} \frac{{}^BQ(t+\bigtriangleup t)-{}^BQ(t)}{\bigtriangleup t}
$$

变换
$$
{}^A({}^BV_Q)={}^A_BR{}^BV_Q
$$
经常讨论的是一个坐标系原点的速度，这个坐标系是相对某个常见的世界参考坐标系的，而不考虑相对于任意坐标系中一般的点的速度。对于这种情况，定义一个缩写符号
$$
v_C={}^UV_{CORG}
$$
式中的点为坐标系$\{C\}$的原点，参考坐标系为$\{U\}$。例如，用符号$u_C$表示坐标系$\{C\}$的速度${}^Au_C$是坐标系$\{C\}$的原点在坐标系$\{A\}$中表示的速度(尽管求导是相对于坐标系$\{U\}$进行的).

![image-20230511165754755](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230511165754755.png)

#### 角速度矢量

**角速度矢量**，用符号$\Omega $表示
$$
\omega_C={}^U\Omega_C
$$

### 5.3 刚体的线速度与角速度

#### 线速度

$$
{}^AV_Q={}^AV_{BORG}+{}^A_BR{}^BV_Q
$$

上式只适用于坐标系$\{B\}$和坐标系$\{A\}$的姿态保持不变的情况。

#### 角速度

在两坐标系原点始终重合、相对线速度为零的情况下，且${}^BV_Q=0$时。

![image-20230512141704443](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230512141704443.png)

![image-20230512143654828](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230512143654828.png)

由图可计算从$\{A\}$中观测的矢量的方向和大小变化。第一，显然${}^AQ$的微分增量一定垂直于${}^AQ_B$和${}^AQ$；第二由图可以看出微分增量的大小为
$$
|\bigtriangleup Q|=(|{}^AQ|\sin\theta)(|{}^A\Omega_B|\bigtriangleup t)
$$
式中${}^A\Omega_B$为$\{B\}$相对于$\{A\}$旋转速度。

有了大小与方向这些条件即可得到矢量叉积。这些矢量大小与方向满足
$$
{}^AV_Q={}^A\Omega_B\times{}^AQ
$$
一般情况下，矢量$Q$是相对于坐标系$\{B\}$变化的，因此需要加上此分量，得
$$
{}^AV_Q={}^A({}^BV_Q)+{}^A\Omega_B\times{}^AQ
$$
利用旋转矩阵消掉双上标，注意在任一瞬时矢量${}^AQ$的描述为${}^A_BR{}^BQ$最后得到
$$
{}^AV_Q={}^A_BR{}^BV_Q+{}^A\Omega_B\times{}^A_BR{}^BQ
$$

### 5.4 对角速度的进一步研究

#### 正交矩阵导数的性质

正交阵$R$的导数与反对称阵$S$之间存在如下特性，可写作
$$
S=\dot{R}R^T
$$
其中
$$
S=\left[
\begin{array}{ccc}
0& -\Omega_z&\Omega_y
\\\Omega_z&0&-\Omega_x
\\-\Omega_y&\Omega_x&0
\end{array}
\right]
$$

#### 旋转参考坐标系的点速度

假定固定矢量${}^BP$相对于坐标系$\{B\}$是不变的，在另一个坐标系$\{A\}$中的描述为
$$
{}^AP={}^A_BR{}^BP
$$
如果坐标系$\{B\}$是旋转的(${}^A_B\dot{R}$的导数非零)，${}^AP$也是变化的，即使${}^BP$为常数，即
$$
{}^A\dot{P}={}^A_B\dot{R}{}^BP
$$
或用速度符号写为
$$
{}^AV_P={}^A_B\dot{R}{}^BP
$$
代入${}^BP$表达式
$$
{}^AV_P={}^A_B\dot{R}{}^A_B{R}^{-1}{}^AP
$$
对于正交矩阵利用式(5.19)，有
$$
{}^AV_P={}^A_BS{}^AP
$$


式中用S的上下标表明它是与旋转矩阵$ {}^A_BR$有关的反对称矩阵。且为了便于理解，这里所说的反对称矩阵通常称为**角速度矩阵**。

#### 反对称矩阵与矢量叉积

定义$3\times1$的列矢量
$$
\Omega=\left[
\begin{array}{c}
\Omega_x
\\\Omega_y
\\\Omega_z
\end{array}
\right]
$$
则
$$
SP=\Omega\times P
$$
与角速度矩阵相对应的矢量$\Omega$称为**角速度矢量**

因此，上式可写成
$$
{}^AV_P={}^A\Omega_B\times{}^AP
$$

#### 角速度矢量的物理意义

角速度矢量$\Omega$的物理意义是在任一时刻，旋转坐标系姿态的变化可以看作是绕某个轴$\hat{K}$的旋转。这个**瞬时旋转轴**，可作为单位矢量，与绕这个轴的旋转速度标量$(\dot\theta)$构成角速度矢量。
$$
\Omega=\left[
\begin{array}{c}
\Omega_x
\\\Omega_y
\\\Omega_z
\end{array}
\right]
=\left[
\begin{array}{c}
k_x\dot{\theta}
\\k_y\dot{\theta}
\\k_y\dot{\theta}
\end{array}
\right]
=\dot{\theta}\hat K
$$

#### 角速度的其他表示方法

角速度的其他表示是可能的，例如，假设一个旋转刚体的角速度可以用$Z-Y-Z$欧拉角速率表示。通过这种形式的描述，或应用 24 种**角度组合**当中的任意一种描述，就可以推导出相应的角速度矢量。
$$
\dot{R} R^{\mathrm{T}}=\left(\begin{array}{ccc}
0 & -\Omega_{z} & \Omega_{y} \\
\Omega_{z} & 0 & -\Omega_{x} \\
-\Omega_{y} & \Omega_{x} & 0
\end{array}\right)
$$
从这个矩阵方程可以得到3个独立的方程，即
$$
\begin{aligned}
\Omega_{x} & =\dot{r}_{31} r_{21}+\dot{r}_{32} r_{22}+\dot{r}_{33} r_{23} \\
\Omega_{y} & =\dot{r}_{11} r_{31}+\dot{r}_{12} r_{32}+\dot{r}_{13} r_{33} \\
\Omega_{z} & =\dot{r}_{21} r_{21}+\dot{r}_{22} r_{12}+\dot{r}_{23} r_{13}
\end{aligned}
$$
通过上式和按照角度组合符号表示$ R$，可以得到角度组合速度和相应的角速度矢量两者之间关系的表达式。该结果可以化成矩阵形式，例如，对于$Z-Y-Z$ 欧拉角
$$
\Omega=E_{Z^{\prime} Y^{\prime} Z^{\prime}}\left(\Theta_{Z^{\prime} Y^{\prime} Z^{\prime}}\right) \dot{\Theta}_{Z^{\prime} Y^{\prime} Z^{\prime}}
$$
式中，$E(\cdot)$是一个雅可比矩阵，它表示了角度组合速度矢量和角速度矢量的关系，同时它也是这个角度组合瞬时值的函数。$E(\cdot)$的形式取决于给定的角坐标系，因此，用一个上标表示这个角坐标系。

### 5.5 机器人连杆的运动

在考虑机器人连杆运动时，一般使用连杆坐标系$\{0\}$作为参考坐标系。因此，$v_i$是连杆坐标系$\{i\}$原点的线速度，$\omega_i$是连杆坐标系$\{i\}$的角速度。
在任一瞬时，机器人的每个连杆都具有一定的线速度和角速度。

### 5.6 连杆之间的速度“传递”

对于旋转关节
$$
{}^{i+1}\omega_{i+1}={}^{i+1}_iR{}^i\omega_i+\dot{\theta}_{i+1}{}^{i+1}\hat Z_{i+1}\\
{}^{i+1}v_{i+1}={}^{i+1}_iR({}^iv_i+{}^i\omega_i\times{}^iP_{i+1})
$$
对于平移关节
$$
{}^{i+1}\omega_{i+1}={}^{i+1}_iR{}^i\omega_i\\
{}^{i+1}v_{i+1}={}^{i+1}_iR({}^iv_i+{}^i\omega_i\times{}^iP_{i-1})+\dot d_{i+1}{}^{i+1}\hat{z}_{i+1}
$$

### 5.7 雅可比

雅可比矩阵是多维形式的导数。例如, 假设有$ 6 $个函数, 每个函数都有$ 6 $个独立的变量：
$$
\begin{array}{l}
y_{1}=f_{1}\left(x_{1}, x_{2}, x_{3}, x_{4}, x_{5}, x_{6}\right) \\
y_{2}=f_{2}\left(x_{1}, x_{2}, x_{3}, x_{4}, x_{5}, x_{6}\right) \\
\vdots \\
y_{6}=f_{6}\left(x_{1}, x_{2}, x_{3}, x_{4}, x_{5}, x_{6}\right)
\end{array}
$$
也可以用矢量符号表示这些等式:
$$
Y=F(X)
$$
现在, 如果想要计算出$  y_{i}  $的微分关于$  x_{j}  $的微分的函数, 可简单应用多元函数求导法则计算，得到
$$
\begin{array}{l}
\delta y_{1}=\frac{\partial f_{1}}{\partial x_{1}} \delta x_{1}+\frac{\partial f_{1}}{\partial x_{2}} \partial x_{2}+\cdots+\frac{\partial f_{1}}{\partial x_{6}} \partial x_{6} \\
\delta y_{2}=\frac{\partial f_{2}}{\partial x_{1}} \delta x_{1}+\frac{\partial f_{2}}{\partial x_{2}} \delta x_{2}+\cdots+\frac{\partial f_{2}}{\partial x_{6}} \delta x_{6} \\
\vdots \\
\delta y_{6}=\frac{\partial f_{6}}{\partial x_{1}} \delta x_{1}+\frac{\partial f_{6}}{\partial x_{2}} \delta x_{2}+\cdots+\frac{\partial f_{6}}{\partial x_{6}} \delta x_{6} \\
\end{array}
$$
将上述式子写成更为简单的矢量表达式:
$$
\delta Y=\frac{\partial F}{\partial X} \delta X
$$
式中的$  6 \times 6  $偏微分矩阵就是我们所说的**雅可比矩阵**。注意到, 如果$  f_{1}(X)  $到$  f_{6}(X)  $都是非线性函数, 那么这些偏微分都是$  x_{i}  $的函数, 因此可以采用如下表示
$$
\delta Y=J(X) \delta X
$$
将上式两端同时除以时间的微分, 可以将雅可比矩阵看成$  X  $中的速度向$Y$中速度的映射:
$$
\dot{Y}=J(X) \dot{X}
$$
在任一瞬时, $ X  $都有一个确定的值, $ J(X)  $是个线性变换。在每一个新时刻, 如果$  X  $改变, 线性变换也会随之而变。所以, 雅可比是**时变**的线性变换。

在机器人学中, 通常使用雅可比将关节速度与操作臂末端的笛卡儿速度联系起来, 例如
$$
{ }^{0} v={ }^{0} J(\Theta) \dot{\Theta}
$$
式中, $ \Theta  $是操作臂关节角矢量, $ v  $是笛卡儿速度矢量。注意到, 对于任意已知的操作臂位形, 关节速度和操作臂末端速度的关系是线性的, 然而这种线性关系仅是瞬时的, 因为在下一刻, 雅可比矩阵就会有微小的变化。

对于通常的6关节机器人, 雅可比矩阵是$ 6 \times 6  $维的,$  \dot{\Theta}  $是$  6 \times 1  $维的, $ { }^{0} v  $也是$  6 \times 1$维的。这个$ 6 \times 1  $笛卡儿速度矢量是由一个$  3 \times 1  $的线速度矢量和一个$  3 \times 1  $的角速度矢量排列起来的:
$$
{}^0v=\left[
\begin{array}{c}
{}^0\nu
\\{}^0\omega
\end{array}
\right]
$$
可以定义任何维数的雅可比矩阵(包括非方阵形式)。雅可比矩阵的行数等于操作臂在笛卡儿空间中的**自由度数量**，雅可比矩阵的列数等于操作臂的**关节数量**。例如，对于平面操作臂，雅可比矩阵不可能超过3行，但对于冗余度平面操作臂，可以有任意多个列(列
数和关节数相等)。

#### 雅可比矩阵参考坐标系的变换

已知坐标系$  \{B\}  $中的雅可比矩阵, 即
$$
\left(\begin{array}{l}
^B\nu \\
{ }^B{\omega}
\end{array}\right)={ }^{B} v={ }^{B} J(\Theta) \dot{\Theta}
$$
我们关心的是给出雅可比矩阵在另一个坐标系$  \{A\}  $中的表达式。首先, 注意到已知坐标系$  \{B\} $ 中的$  6 \times 1  $笛卡儿速度矢量可以通过如下变换得到相对于坐标系$  \{A\}  $的表达式
$$
\left(\begin{array}{l}
{}^A{\nu} \\
{}^A{\omega}
\end{array}\right)=\left(\begin{array}{c|c}
{ }_{B}^{A} R & 0 \\
\hline 0 & { }_{B}^{A} R
\end{array}\right)\left(\begin{array}{l}
{}^B{\nu} \\
{}^B{\omega}
\end{array}\right)
$$
因此
$$
\left(\begin{array}{c}
{}^A{\nu} \\
{}^A{\omega}
\end{array}\right)=\left(\begin{array}{c|c}
{ }_{B}^{A} R & 0 \\
\hline 0 & { }_{B}^{A} R
\end{array}\right){}^{B} J(\Theta) \dot{\Theta}
$$

$$
{ }^{A} J(\Theta)=\left(\begin{array}{c|c}
{ }_{B}^{A} R & 0 \\
\hline 0 & { }_{B}^{A} R
\end{array}\right){ }^{B} J(\Theta)
$$

### 5.8 奇异性

在非奇异性的时候有
$$
\dot{\Theta}=J^
{-1}(\Theta)v
$$
但在机器人控制系统中应用上式的危险之处在于，在奇异位形，雅可比矩阵的逆不存在，此时，关节速度会趋于无穷大

1) **工作空间边界的奇异位形**出现在操作臂完全展开或者收回使得末端执行器处于或非常接近工作空间边界的情况。
2) **工作空间内部的奇异位形**总是远离工作空间的边界，通常是由于两个或两个以上的关节轴线共线引起的。

当操作臂处于奇异位形时，它会失去一个或多个自由度(在笛卡儿空间中观察)。这也就是说，在笛卡儿空间的某个方向上(或某个子空间中)，无论选择什么样的关节速度，都不能使机器人手臂运动。显然，这种情况也会在机器人工作空间边界发生。

为了求出机构的奇异点，必须首先计算机构的雅可比矩阵行列式的值。在行列式为0时，雅可比矩阵非满秩，也就是奇异的。

### 5.9 操作臂的静力

我们所讨论的关节静力和静力矩是由施加在最后一个连杆上的静力或静力矩(或两者共同)引起的，例如，当操作臂的末端执行器和环境接触时就是这样的。
我们为相邻杆件所施加的力和力矩定义以下特殊的符号:
$f_i = $连杆$i-1$施加在连杆$i$上的力，
$n_i=$连杆$i-1$施加在连杆$i$上的力矩。
我们按照惯例建立连杆坐标系。下图所示为施加在连杆$i$的静力和静力矩(除了重力以外)。将这些力相加并令其和为 0，有
$$
{}^if_i-{}^if_{i+1}=0
$$
将绕坐标系$\{i\}$原点的力矩相加，有
$$
{}^in_i-{}^in_{n+1}-{}^iP_{i+1}\times{}^if_{i+1}=0
$$


![image-20230513215356899](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230513215356899.png)

连杆之间的静力”传递“表达式：
$$
{}^if_i={}^i_{i+1}R{}^{i+1}f_{i+1}
$$

$$
{}^in_i={}^i_{i+1}R{}^{i+1}n_{i+1}+{}^iP_{i+1}\times{}^if_{i+1}
$$

为了求出保持系统静平衡的关节力矩，应计算关节轴矢量和施加在连杆上的力矩矢量的点乘:
$$
\tau_i={}^in_i^T{}^i{\hat Z}_i
$$
对于关节$i$是移动关节的情况，也可算出关节驱动力为
$$
\tau_i={}^if_i^T{}^i\hat{Z}_i
$$
注意，即使对于线性的关节力，我们也使用符号$\tau$

通常将使关节角增大的旋转方向定义为关节力矩的正方向。

### 5.10 力域中的雅可比

当力作用在机构上时，如果机构经过一个位移，就作了功(从技术意义上讲)。功被定义为作用力通过一段距离，它是以能量为单位的标量。如令位移趋向于无穷小就可以用**虚功**原理来描述静止的情况。功具有能量的单位，所以它在任何广义坐标系下的测量值都相同。特别是在笛卡儿空间作的功应当等于关节空间作的功。在多维空间中，功是一个力或力矩矢量与位移矢量的点积。于是有
$$
\mathcal{F} \cdot \delta \chi=\tau \cdot \delta \Theta
$$
式中$  \mathcal{F}  $是一个作用在末端执行器上的$  6 \times 1  $维笛卡儿力-力矩矢量,$  \delta \chi  $是末端执行器$  6 \times 1  $维无穷小笛卡儿位移矢量,$  \tau  $是$  6 \times 1  $维关节力矩矢量, $ \delta \Theta  $是$  6 \times 1  $维无穷小的关节位移矢量。上式也可写成
$$
\mathcal{F}^{\mathrm{T}} \delta \chi=\tau^{\mathrm{T}} \delta \Theta
$$
雅可比矩阵的定义为
$$
\delta \chi=J \delta \Theta
$$
因此可写出
$$
\mathcal{F}^{\mathrm{T}} J \delta \Theta=\tau^{\mathrm{T}} \delta \Theta
$$
对所有的$  \delta \Theta $,上式均成立, 因此有
$$
\mathcal{F}^{\mathrm{T}} J=\tau^{\mathrm{T}}
$$
对两边转置, 可得:
$$
\tau=J^{\mathrm{T}} \mathcal{F}
$$
当得到相对于坐标系$\{0\}$的雅可比矩阵后，可以由下式对坐标系$\{0\}$中的力矢量进行变换:
$$
\tau={}^0J^{\mathrm{T}} {}^0\mathcal{F}
$$
当雅可比矩阵不满秩时，存在某些特定的方向，末端执行器在这些方向上不能施加期望的静态力。即如果上式中的雅可比矩阵奇异，$\mathcal F$在某些方向(这些方向定义了雅可比矩阵的零空间)上的增大或减小与所求的值无关。这也意味着，在奇异位形的附近，机械特性趋向于无穷大，以致只要很小的关节力矩就可在末端执行器产生很大的力。因此，在力域中和在位置域中奇异都是存在的。

### 5.11 速度和静力的笛卡尔变换

考虑$6\times1$维的广义力矢量表达式，即
$$
\mathcal F=\left(
\begin{array}{}
F
\\N
\end{array}
\right)
$$
式中$F$是一个$3\times1$力矢量，$N$是一个$3\times1$力矩矢量

将已知坐标系$  \{B\} $ 中描述的广义力矢量变换为坐标系$  \{A\}  $中的描述，即为
$$
\left(
\begin{array}{}
{}^AF_A
\\{}^AN_A
\end{array}
\right)=\left(
\begin{array}{}
{}^A_BR&0
\\{}^AP_{BORG}&{}^A_BR
\end{array}
\right)
\left(
\begin{array}{}
{}^BF_B
\\{}^BN_B
\end{array}
\right)
$$
可以写成紧凑形式
$$
{}^A\mathcal F_A={}^A_BT_f{}^B\mathcal F_B
$$
式中$T_f$用来表示一个**力—力矩变换**。



## 第6章 操作臂动力学

### 6.1 引言

关于操作臂的动力学存在两个问题以待解决。第一个问题，已知一个轨迹点，$\Theta$（操作臂关节角矢量）、$\dot{\Theta}$和 $\ddot{\Theta}$，并且希望求出期望的关节力矩矢量$\tau$。此动力学方程对操作臂控制问题(见第 10 章)很有用。第二个问题是计算在施加一组关节力矩下机构将如何运动。也就是说，已知一个力矩矢量，计算出操作臂的运动结果$\Theta$、$\dot{\Theta}$和 $\ddot{\Theta}$，这对操作的仿真很有用。

### 6.2 刚体的加速度

当刚体所处的瞬时参考坐标系为世界坐标系$\{U\}$时，可用下列符号表示刚体的速度，即
$$
\dot v_A={}^U\dot V_{AORG}
$$

$$
\dot\omega_A={}^U\dot\Omega_A
$$

#### 线线速度

在坐标系$\{A\}$的原点与坐标系$\{B\}$的原点重合时,速度矢量${}^BQ$可表示为：
$$
{}^AV_Q={}^A_BR{}^BV_Q+{}^A\Omega_B\times{}^A_BR{}^BQ
$$
式子左边描述的是矢量${}^AQ$随着时间变化的情况。由于两个坐标系的原点重合因此可以写成
$$
\frac{d}{dt}({}^A_BR{}^BQ)={}^A_BR{}^BV_Q+{}^A\Omega_B\times{}^A_BR{}^BQ
$$
对上上式进行求导得
$$
{}^A\dot V_Q=\frac{d}{dt}({}^A_BR{}^BV_Q)+{}^A\dot\Omega_B\times{}^A_BR{}^BQ+{}^A\Omega_B\times\frac{d}{dt}({}^A_BR{}^BQ)
$$
对上式的第一项和最后一项应用上上式，则上式的右边变为：
$$
({}^A_BR{}^B\dot V_Q+{}^A\Omega_B\times{}^A_BR{}^BV_Q)+{}^A\dot\Omega_B\times{}^A_BR{}^BQ+{}^A\Omega_B\times({}^A_BR{}^BV_Q+{}^A\Omega_B\times{}^A_BR{}^BQ)
$$
对上式的同类项进行合并，得
$$
{}^A_BR{}^B\dot V_Q+2{}^A\Omega_B\times{}^A_BR{}^BV_Q+{}^A\dot\Omega_B\times{}^A_BR{}^BQ+{}^A\Omega_B\times({}^A\Omega_B\times{}^A_BR{}^BQ)
$$
将结论推广到两个坐标系不重合的一般情况，我么需要附加一个表示坐标系$\{B\}$原点线加速度的项，最终得到一般表达式
$$
{}^A\dot V_{BORG}+{}^A_BR{}^B\dot V_Q+2{}^A\Omega_B\times{}^A_BR{}^BV_Q+{}^A\dot\Omega_B\times{}^A_BR{}^BQ+{}^A\Omega_B\times({}^A\Omega_B\times{}^A_BR{}^BQ)
$$
值得指出的是，当${}^BQ$为常量时，有
$$
{}^BV_Q={}^B\dot V_Q=0
$$
则表达式可以简化为
$$
{}^A\dot V_{BORG}={}^A\dot V_{BORG}+{}^A\dot\Omega_B\times{}^A_BR{}^BQ+{}^A\Omega_B\times({}^A\Omega_B\times{}^A_BR{}^BQ)
$$
上式常用于计算旋转关节操作臂的线加速度。当操作臂为移动关节是，使用式（172）的一般形式。

#### 角加速度

假设坐标系$\{B\}$以角速度${}^A\Omega_B$相对于坐标系$\{A\}$转动，同时坐标系$\{C\}$以角速度${}^B\Omega_C$相对于坐标系$\{B\}$转动。为求${}^A\Omega_C$，在坐标系$\{A\}$中进行矢量相加:
$$
{}^A\Omega_C={}^A\Omega_B+{}^A_BR{}^B\Omega_C
$$
对上式求导，得
$$
{}^A\dot\Omega_C={}^A\dot\Omega_B+{}^A_BR{}^B\dot\Omega_C+{}^A\Omega_B\times{}^A_BR{}^B\Omega_C
$$
上式用于计算操作臂连杆的角加速度。

### 6.3 质量分布

对于定轴转动的情况，经常用到惯性矩这个概念。对一个可以在三维空间自由移动的刚体来说，可能存在无穷个旋转轴。在一个刚体绕任意轴做旋转运动时，我们需要一种能够表征刚体质量分布的方式。在这里，我们引入**惯性张量**，它可以看作是对一个物体惯性矩的广义度量。

现在我们定义一组参量，给出刚体质量在参考坐标系中分布的信息。下图表示一个刚体，坐标系建立在刚体上。惯性张量可以在任何坐标系中定义，但一般在这个刚体坐标系中定义惯性张量。这里，重要的是用左上标表明已知惯性张量所在的坐标系。坐标系$\{A\}$中的惯性张量可用$3\times3$矩阵表示如下
$$
{ }^{A} I=\left(\begin{array}{rrr}
I_{x x} & -I_{x y} & -I_{x z} \\
-I_{x y} & I_{y y} & -I_{y z} \\
-I_{x z} & -I_{y z} & I_{z z}
\end{array}\right)
$$
矩阵中，各元素为(单位为$长度^2\cdot 质量$，$dv=dxdydz$)
$$
\begin{array}{l}
I_{x x}=\iiint_{V}\left(y^{2}+z^{2}\right) \rho \mathrm{d} v \\
I_{y y}=\iiint_{V}\left(x^{2}+z^{2}\right) \rho \mathrm{d} v \\
I_{z z}=\iiint_{V}\left(x^{2}+y^{2}\right) \rho \mathrm{d} v \\
I_{x y}=\iiint_{V} x y \rho \mathrm{d} v \\
I_{x z}=\iiint_{V} x z \rho \mathrm{d} v \\
I_{y z}=\iiint_{V} y z \rho \mathrm{d} v
\end{array}
$$
![image-20230514164128654](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230514164128654.png)

$I_{xx}、I_{yy}$和$I_{zz}$称为**惯性矩**。它们是单元体质量$\rho dv$乘以单元体到相应转轴垂直距离的平方在整个刚体上的积分。其余3个交叉项称为**惯量积**。对于一个刚体来说，这6个相互独立的参量取决于所在坐标系的位置和姿态。当任意选择坐标系的姿态时，可能会使刚体的惯量积为零。此时，坐标系的轴被称为**主轴**，而相应的惯量矩被称为**主惯性矩**。

惯性张量是参考坐标系位置和姿态的函数。因此，众所周知的**平行移轴**定理就是惯性张量在整个参考坐标系中平移时的计算方法。平行移轴定理描述了一个以刚体质心为原点的坐标系平移到另一个坐标系时惯性张量的变换关系。假设$\{C\}$是以刚体质心为原点的坐标系，$\{A\}$为任意平移后的坐标系，则平行移轴定理可以表示为
$$
{}^AI_{zz}={}^CI{zz}+m({x_c^2}+y_c^2)
\\{}^AI_{xy}={}^CI_{xy}-mx_cy_c
$$
式中，矢量$P_c=(x_c,y_c,z_c)^T$表示刚体质心在坐标$\{A\}$中的位置。平行移轴定理又可表示成为矢量—矩阵形式
$$
{}^AI={}^CI+m(P_c^TP_cI_3-P_cP_c^T)
$$
惯性张量还有其他一些性质:

1) 如果坐标系的两个坐标轴构成的平面为刚体质量分布的对称平面，则垂直于这个对称平面的坐标轴与另一个坐标轴的惯性积为零
2) 惯性矩永远是正值。惯量积可能是正值或也可能是负值
3) 无论参考坐标系姿态如何变化，三个惯量矩的和保持不变
4) 惯性张量的特征值为刚体的主惯性矩，相应的特征矢量为主轴。

大多数操作臂连杆的几何形状及结构组成都比较复杂，因而很难直接进行求解。一般是使用测量装置(例如惯性摆)来测量每个连杆的惯性矩，而不是通过计算求得。

### 6.4 牛顿方程和欧拉方程

我们把组成操作臂的连杆都看作刚体。如果知道了连杆质心的位置和惯性张量，那么它的质量分布特征就完全确定了。牛顿方程以及描述旋转运动的欧拉方程描述了力、惯量和加速度之间的关系。

#### 牛顿方程

刚体质心正以加速度$\dot v_C$作加速运动。此时，由牛顿方程可得作用在质心上的力F引起刚体的加速度为
$$
F=m\dot v_C
$$
其中$m$代表刚体总质量

#### 欧拉公式

一个旋转刚体，其角速度和角加速度分别为$\omega、\dot \omega$。此时，由欧拉方程可得作用在刚体上的力矩$N$引起刚体的转动为
$$
N={}^CI{\dot\omega}+\omega\times{}^CI\omega
$$
式中${}^CI$是刚体在坐标系$\{C\}$中的惯性张量。坐标系$\{C\}$的原点在刚体的质心。

### 6.5 牛顿—欧拉递推动力学方程

假设已知关节的位置、速度和加速度($\Theta,\dot{\Theta},\ddot{\Theta}$)

#### 计算角速度和加速度的外推法

可应用递推方法完成这些计算。首先对连杆1进行计算，接着计算下一个连杆，这样一直**外推**到连杆n。

已知
$$
{}^{i+1}\omega_{i+1}={}^{i+1}_iR{}^i\omega_i+\dot{\theta}_{i+1}{}^{i+1}\hat Z_{i+1}
$$
连杆之间的角加速度变换方程:
$$
{}^{i+1}\dot\omega_{i+1}={}^{i+1}_{i}R{}^i\dot \omega_i+{}^{i+1}_iR{}^i\omega_i\times\dot{\theta}_{i+1}{}^{i+1}\hat Z_{i+1}+\ddot \theta_{i+1}{}^{i+1}\hat Z_{i+1}
$$
当第$i+1$个关节是移动关节时，上式可简化为
$$
{}^{i+1}\dot\omega_{i+1}={}^{i+1}_{i}R{}^i\dot \omega_i
$$
每个连杆坐标系原点的线加速度:
$$
{}^{i+1}\dot v_{i+1}={}^{i+1}_{i}R[{}^i\dot \omega_i\times{}^iP_{i+1}+{}^i\omega_i\times({}^i\omega_i\times {}^iP_{i+1})+{}^i\dot v_i]
$$
当第$i+1$个关节是移动关节时，
$$
{}^{i+1}\dot v_{i+1}={}^{i+1}_{i}R[{}^i\dot \omega_i\times{}^iP_{i+1}+{}^i\omega_i\times({}^i\omega_i\times {}^iP_{i+1})+{}^i\dot v_i]\\+2{}^{i+1}\omega_{i+1}\times\dot{d}_{i+1}{}^{i+1}\hat Z_{i+1}+\ddot d_{i+1}{}^{i+1}{}\hat Z_{i+1}
$$
每个连杆质心的线加速度：
$$
{}^i\dot v_{C_i}={}^i\dot \omega_i\times{}^iP_{C_i}+{}^i\omega_i\times({}^i\omega_i\times{}^iP_{C_i})+{}^i\dot v_i
$$
假定坐标系$\{C_i\}$附加于连杆$i$上，坐标系原点位于连杆质心，且各坐标轴方向与原连杆坐标系$\{i\}$方向相同。由于上式与关节的运动无关，因此无论是旋转关节还是移动关节上式对于第$i+1$个连杆来说也是有效的。
注意，第1个连杆的方程非常简单，因为${}^0\omega_0={}^0\dot\omega_0=0$

#### 作用在连杆上的力和力矩

$$
F_i=m\dot v_{C_i}
\\N={}^CI{\dot\omega}+\omega\times{}^CI\omega
$$

#### 计算力和力矩的内推法

$f_i = $连杆$i-1$施加在连杆$i$上的力，
$n_i=$连杆$i-1$施加在连杆$i$上的力矩。
力平衡方程：
$$
{}^iF_i={}^if_i-{}^i_{i+1}R{}^{i+1}f_{i+1}
$$
力矩平衡方程：
$$
{}^iN_i={}^in_i-{}^in_{i+1}+(-{}^iP_{C_i})\times{}^if_{i}-({}^iP_{i+1}-{}^iP_{C_i})\times{}^if_{i+1}
$$

则
$$
{}^iN_i={}^in_i-{}^i_{i+1}R{}^{i+1}n_{i+1}-{}^iP_{C_i}\times{}^iF_{i}-{}^iP_{i+1}\times{}^i_{i+1}R{}^{i+1}f_{i+1}
$$


最后, 重新排列力和力矩方程, 形成相邻连杆从高序号向低序号排列的迭代关系:
$$
\begin{array}{l}
{ }^{i} f_{i}={ }_{i+1}^{i} R^{i+1} f_{i+1}+{ }^{i} F_{i} \\
{ }^{i} n_{i}={ }^{i} N_{i}+{ }_{i+1}^{i} R^{i+1} n_{i+1}+{ }^{i} P_{C_{i}} \times{ }^{i} F_{i}+{ }^{i} P_{i+1} \times{ }_{i+1}{ }^{i} R^{i+1} f_{i+1}
\end{array}
$$
在静力学中, 可通过计算一个连杆施加于相邻连杆的力矩在$  \hat{Z} $ 方向的分量求得关节力矩:
$$
\tau_{i}={ }^{i} n_{i}^{\mathrm{T}}{ }^{i} \hat{Z}_{i}
$$
对于移动关节$  i$ , 有
$$
\tau_{i}={ }^{i} f_{i}^{\mathrm{T} i} \hat{Z}_{i}
$$
式中符号$  \tau  $表示线性驱动力。

#### 牛顿—欧拉递推动力学算法

牛顿-欧拉递推动力学算法
Lا
由关节运动计算关节力矩的完整算法由两部分组成。第一部分是对每个连杆应用牛 顿-欧拉方程, 从连杆 1 到连杆  n  向外递推计算连杆的速度和加速度的。第二部分是从连 杆  n  到连杆 1 迭代计算连杆间的相互作用力和力矩以及关节驱动力矩。对于转动关节来 说, 这个算法归纳如下:
外推:$  i: 0 \rightarrow 5 $
$$
\begin{array}{l}
{ }^{i+1} \omega_{i+1}={ }_{i}^{i+1} R^{i} \omega_{i}+\dot{\theta}_{i+1}{ }^{i+1} \hat{Z}_{i+1} \\
{ }^{i+1} \dot{\omega}_{i+1}={ }^{i+1} R{ }^{i} \dot{\omega}_{i}+{ }_{i}^{i+1} R^{i} \omega_{i} \times \dot{\theta}_{i+1}{ }^{i+1} \hat{Z}_{i+1}+\ddot{\theta}_{i+1}{ }^{i+1} \hat{Z}_{i+1} \\
{ }^{i+1} \dot{v}_{i+1}={ }^{i+1} R\left({ }_{i}^{i} \dot{\omega}_{i} \times{ }^{i} P_{i+1}+{ }^{i} \omega_{i} \times\left({ }^{i} \omega_{i} \times{ }^{i} P_{i+1}\right)+{ }^{i} \dot{v}_{i}\right) \\
{ }^{i+1} \dot{v}_{C_{i+1}}={ }^{i+1} \dot{\omega}_{i+1} \times{ }^{i+1} P_{C_{i+1}} +{ }^{i+1} \omega_{i+1} \times\left({ }^{i+1} \omega_{i+1} \times{ }^{i+1} P_{C_{i+1}}\right)+{ }^{i+1} \dot{v}_{i+1} \\
{ }^{i+1} F_{i+1}= m_{i+1}{ }^{i+1} \dot{v}_{C_{i+1}} \\
{ }^{i+1} N_{i+1}= {}^{C_{i+1}} I_{i+1}{ }^{i+1} \dot{\omega}_{i+1}+{ }^{i+1} \omega_{i+1} \times{ }_{C_{i+1}} I_{i+1}{ }^{i+1} \omega_{i+1}
\end{array}
$$
内推 :$  i: 6 \rightarrow 1 $
$$
\begin{array}{l}
{ }^{i} f_{i}={ }_{i+1}^{i} R^{i+1} f_{i+1}+{ }^{i} F_{i} \\
{ }^{i} n_{i}={ }^{i} N_{i}+{ }_{i+1}^{i} R^{i+1} n_{i+1}+{ }^{i} P_{C_{i}} \times{ }^{i} F_{i}+{ }^{i} P_{i+1} \times{ }_{i+1}{ }^{i} R^{i+1} f_{i+1}
\end{array}
$$

$$
\tau_{i}={ }^{i} n_{i}{ }^{\mathrm{T}}{ }^{i} \hat{Z}_{i}
$$

#### 考虑重力的动力学算法

令${}^0\dot{v}_0=G$就可以将作用在连杆上的重力因素包括到动力学方程中去，其中G与重力矢量大小相等，而方向相反。这等价于机器人正以1g 的加速度在做向上加速运动。这个假想的向上加速度与重力作用在连杆上的效果是相同的。因而，不需要其他额外的计算开销，就可以计算重力的影响。

### 6.6 迭代形式与封闭形式

已知关节位置、速度和加速度，就可以计算所需的关节力矩。牛顿—欧拉递推动力学算法的方程主要应用于两个方面:进行数值计算或作为一种分析方法用于符号方程的推导。

将这些方程用于数值计算是很有用的，因为这些方程适用于任何机器人。只要将待求操作臂的惯性张量、连杆质量、矢量$P_{C_i}$以及矩阵${}^{i+1}_{i}R$代入这些方程中，就可以直接计算出任何运动情况下的关节力矩。
然而，我们经常需要对方程的结构进行研究。例如，重力项的形式是什么?重力影响与惯性力影响相比较哪一个影响较大?为了研究诸如此类的问题，经常需要给出封闭形式的动力学方程。应用牛顿-欧拉方程递推算法对$\Theta$、$\dot{\Theta}$和 $\ddot{\Theta}$进行符号推导即可得到这些方程。这与第5章中推导符号形式的雅可比矩阵相似。

### 6.7 封闭形式的动力学方程应用举例

![image-20230515000153889](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230515000153889.png)

这里我们计算上图所示平面二连杆操作臂的封闭形式的动力学方程。为简单起见，假设操作臂的质量分布非常简单:每个连杆的质量都集中在连杆的末端，设其质量分别为$m_1$和$m_2$
首先，确定牛顿-欧拉递推公式中的各参量的值。每个连杆质心的位置矢量
$$
{}^1P_{C_1}=l_1\hat X_1
\\{}^2P_{C_2}=l_2\hat X_2
$$
由于假设为集中质量，因此每个连杆质心的惯性张量为零矩阵:
$$
{}^{C_1}I_1=0
\\{}^{C_2}I_2=0
$$
末端执行器上没有作用力，因而有
$$
f_3=0
\\n_3=0
$$
机器人基座不旋转，因此有
$$
\omega_0=0\\
\dot\omega_0=0
$$
包括重力因素，有
$$
{}^0\dot v_0=g\hat Y_0
$$
相邻连杆坐标系之间的相对转动由下式给出：
$$
{}^i_{i+1}R=\left[\begin{array}
{cccc}
c_{i+1}&-s_{i+1}&0\\
s_{i+1}&c_{i+1}&0\\
0&0&1
\end{array}\right]
\\{}_i^{i+1}R=\left[\begin{array}
{cccc}
c_{i+1}&s_{i+1}&0\\
-s_{i+1}&c_{i+1}&0\\
0&0&1
\end{array}\right]
$$
对连杆1用外推法求解如下：
$$
{}^1\omega_1=……
\\{}^1\dot\omega_1=……
\\{}^1\dot v_1=……
\\{}^1v_{\dot C_1}=……
\\{}^1F_1=……
\\{}^1N_1=……
$$
对连杆2用外推法求解如下：
$$
{}^2\omega_2=……
\\{}^2\dot\omega_2=……
\\{}^2\dot v_2=……
\\{}^2v_{\dot C_2}=……
\\{}^2F_2=……
\\{}^2N_2=……
$$
对连杆2用内推法求解如下：
$$
{}^2f_2={}^2F_2
\\{}^2n_2=……
$$
对连杆1用内推法求解如下：
$$
{}^1f_1=……
\\{}^1n_1=……
$$
取${}^in_i$中的$\hat Z$方向分量，得关节力矩
$$
\tau_1=……
\\\tau_2=……
$$
上式将驱动力矩表示为关于关节位置、速度和加速度的函数。注意，如此复杂的函数表达式描述的竟是一个最简单的操作臂。可见，一个封闭形式的6自由度操作臂的动力学方程将是相当复杂的。

### 6.8 操作臂动力学方程的结构

通过忽略一个方程中的某些细节而仅显示方程的某些结构，可以很方便地表示操作臂的动力学方程。

#### 状态空间方程

当牛顿-欧拉方程对操作臂进行分析时，动力学方程可以写成如下形式
$$
\tau=M(\Theta)\ddot\Theta+V(\Theta,\dot\Theta)+G(\Theta)
$$
式中$M(\Theta)$为操作臂的$n\times n$**质量矩阵**，$V(\Theta,\dot \Theta)$是$n\times 1$的离心力和哥氏力矢量，$G(\Theta)$是$n\times 1$重力矢量。上式称为**状态空间方程**，这是因为式中的矢量$V(\Theta,\dot \Theta)$取决于位置和速度。
$M(\Theta)$和$G(\Theta)$中的元素都是关于操作臂所有关节的位置的复杂函数。而$V(\Theta,\dot \Theta)$中的元素都是关于$\Theta $和$\dot \Theta$的复杂函数
可以将操作臂动力学方程中不同类型的项划分为质量矩阵、离心力和哥氏力矢量以及重力矢量。

#### 位形空间方程

将动力学方程中的速度项$V(\Theta,\dot\Theta)$写成另外一种形式如下
$$
\tau=M(\Theta)\ddot\Theta+B(\Theta)(\dot\Theta\dot\Theta)+C(\Theta)(\dot\Theta^2)+G(\Theta)
$$
式中$B(\Theta)$是$n\times n(n-1)/2$阶的哥氏力系数矩阵，$(\dot\Theta\dot\Theta)$是$n(n-1)/2\times1$阶的关节速度矢量，即
$$
(\dot\Theta\dot\Theta)=(\dot\theta_1\dot\theta_2\dot\theta_1\dot\theta_3…\dot\theta_{n-1}\dot\theta_n)^T
$$
$C(\Theta)$是$n\times n$阶离心力系数矩阵，而$(\dot\Theta^2)$是$n\times 1$阶矢量，即
$$
(\dot\theta_1^2\dot\theta_2^2…\dot\theta_n^2)^T
$$
改写后的式子称为位形空间方程，因为它的系数矩阵仅是操作臂位置的函数。

### 6.9 操作臂动力学的拉格朗日方程

对第$i$个连杆的动能$k_i$可以表示为
$$
k_i=\frac{1}{2}m_iv^T_{C_i}v_{C_i}+\frac{1}{2}{}^i\omega_i^T{}^{C_i}I_i{}^i\omega_i
$$
即
$$
k=\sum_{i=1}^{n}k_i
$$
式中$v_{C_i}$和${}^i\omega_i$是$\Theta$和$\dot\Theta$的函数。由此我们可知操作臂的动能$k(\Theta,\dot\Theta)$可以描述为关节位置和速度的标量函数。事实上操作臂的动能可以写成
$$
k(\Theta,\dot\Theta)=\frac{1}{2}\dot \Theta^TM(\Theta)\dot \Theta
$$
这里$M(\Theta)$是$n\times n$操作臂质量矩阵。上式是一种**二次型**，也就是说，将矩阵展开后，方程全部是由$\dot \theta_i$的二次项组成的。而且，由于总动能永远是正的，因此操作臂的质量矩阵一定是**正定**矩阵。正定矩阵的二次型永远是正的。

对第$i$个连杆的势能$u_i$可以表示为
$$
u_i=-m_i{}^0g^T{}^0P_{C_i}+u_{{ref}_i}
$$
式中${}^0g$是$3\times 1$的重力矢量，${}^0P_{c_i}$是位于第$i$个连杆质心的矢量，$u_{{ref}_i}$是使$u_i$的最小值为零的常数。操作臂的总势能为各个连杆势能之和，即
$$
u=\sum_{i=1}^{n}u_i
$$
操作臂的势能$u(\Theta)$可以描述为关节位置的标量函数,我们称这个标量函数为**拉格朗日函数**，即一个机械系统的动能和势能的差值。
$$
\mathcal{L}(\Theta,\dot\Theta)=k(\Theta,\dot\Theta)-u(\Theta)
$$
则操作臂的运动方程为
$$
\frac{d}{dt}\frac{\partial\mathcal L}{\partial\dot\Theta}-\frac{\partial\mathcal L}{\partial\Theta}=\tau
$$
这里$\tau$是$n\times 1$的激励力矩矢量。对于操作臂来说，方程变为
$$
\frac{d}{dt}\frac{\partial k}{\partial\dot\Theta}-\frac{\partial k}{\partial\Theta}+\frac{\partial u}{\partial\Theta}=\tau
$$
为了简化起见，这里省略了$k(\cdot)$和$u(\cdot)$的自变量。

### 6.10 笛卡尔空间中的操作臂动力学

上述动力学方程均是按照操作臂关节角度(即关节空间)对位置和时间的导数建立的其一般形式为
$$
\tau=M(\Theta)\ddot\Theta+B(\Theta)(\dot\Theta\dot\Theta)+C(\Theta)(\dot\Theta^2)+G(\Theta)
$$
建立关节空间方程的目的是便于应用串联机构的性质推导动力学方程。本节将讨论笛卡儿空间中末端执行器的加速度与笛卡儿空间中力和力矩之间关系的动力学方程。

#### 笛卡尔状态空间方程

$$
\mathcal F=M_x(\Theta)\ddot{\chi}+V_x(\Theta,\dot\Theta)+G_x(\Theta)
$$

这里$\mathcal F$是机器人末端执行器上的力—力矩方程，$\chi$是一个能够恰当表达末端执行器位置和姿态的笛卡尔矢量。$M_x(\Theta)$是**笛卡尔质量矩阵**，$V_x(\Theta,\dot\Theta)$是笛卡尔空间的速度项矢量，$G_x(\Theta)$是笛卡尔空间中的重力项矢量

作用于末端执行器的虚拟力$\mathcal F$实际上可以用关节驱动器的驱动力表示，即
$$
\tau=J^T(\Theta)\mathcal F
$$
这里的雅可比矩阵的坐标系与$\mathcal f、\ddot\chi$相同，这个坐标系常常为工具坐标系$\{T\}$

经过求解，可得笛卡尔空间动力学方程中各项的表达式
$$
M_x(\Theta)=J^{-T}(\Theta)M(\Theta)J^{-1}(\Theta)
\\V_x(\Theta,\dot\Theta)=J^{-T}(\Theta)(V(\Theta,\dot\Theta)-M(\Theta)J^{-1}(\Theta)\dot J(\Theta)\dot\Theta)\\
G_x(\Theta)=J^{-T}(\Theta)G(\Theta)
$$

#### 笛卡尔位形空间中的力矩方程

由于
$$
\tau=J^T(M_x(\Theta)\ddot{\chi}+V_x(\Theta,\dot\Theta)+G_x(\Theta))
$$
将上式改写
$$
\tau=J^TM_x(\Theta)\ddot{\chi}+B_x(\Theta)(\dot\Theta\dot\Theta)+C_x(\Theta)(\dot\Theta^2)+G(\Theta)
$$
式中$B_x(\Theta)$是$n\times n(n-1)/2$阶的哥氏力系数矩阵，$(\dot\Theta\dot\Theta)$是$n(n-1)/2\times1$阶的关节速度矢量，即
$$
(\dot\Theta\dot\Theta)=(\dot\theta_1\dot\theta_2\dot\theta_1\dot\theta_3…\dot\theta_{n-1}\dot\theta_n)^T
$$
$C_x(\Theta)$是$n\times n$阶离心力系数矩阵，而$(\dot\Theta^2)$是$n\times 1$阶矢量，即
$$
(\dot\theta_1^2\dot\theta_2^2…\dot\theta_n^2)^T
$$
注意式中，$G\Theta$与关节空间中的相同，$B_x(\Theta)\neq B(\Theta)$,$C_x(\Theta)\neq C(\Theta)$

### 6.11 考虑非刚体影响

上面所推导出的方程未能包含所有作用的机械臂上的力，然而摩擦轮也是一种重要的力
$$
\tau_{ftiction}=csgn(\dot\theta)+v\dot\theta
$$
式中$v$是黏性摩擦系数，$c$是库仑摩擦系数，当$\dot\theta=0$时，$c$一般取1，称为静摩擦系数；当$\dot\theta\neq0$时，$c$小于1，称为动摩擦系数。

在有些时候，摩擦力也与节点的位置有关。如机械问题导致摩擦力不均，因此一个比较复杂的摩擦力模型为
$$
\tau_{ftiction}=f(\theta,\dot\theta)
$$
将这些摩擦力模型附加到刚体力学模型中的动力学项中，得到一个更加完整的模型
$$
\mathcal F=M(\Theta)\ddot{\chi}+V(\Theta,\dot\Theta)+G(\Theta)+F(\Theta,\dot\Theta)
$$
其他影响因素在本书中不做讨论

### 6.12 动力学仿真

动力学方程中的加速度
$$
\ddot{\Theta}=M^{-1}(\Theta)[\tau-V(\Theta, \dot{\Theta})-G(\Theta)-F(\Theta, \dot{\Theta})]
$$
可以应用几种已知的**数值积分**方法对加速度积分, 计算出位置和速度。
已知操作臂运动的初始条件, 通常为下面的形式
$$
\begin{array}{l}
\Theta(0)=\Theta_{0} \\
\dot{\Theta}(0)=0
\end{array}
$$
用步长$  \Delta t  $对加速度$\ddot\Theta$进行数值积分。数值积分的方法有许多种。这里, 我们介绍最简单的一种数值积分方法, 称为**欧拉积分法**: 从$  t=0  $开始, 进行迭代计算
$$
\begin{array}{l}
\dot{\Theta}(t+\Delta t)=\dot{\Theta}(t)+\ddot{\Theta}(t) \Delta t \\
\Theta(t+\Delta t)=\Theta(t)+\dot{\Theta}(t) \Delta t+\frac{1}{2} \ddot{\Theta}(t) \Delta t^{2}
\end{array}
$$
式中, 对于每次迭代, 要由计算一次$  \dddot{\Theta}  $。这样, 由已知的输人力矩函数, 用数值积分方法即可求出操作臂的位置、速度和加速度。

### 6.13 计算问题

#### 关于计算效率的历史讨论

#### 封闭形式方程与迭代方程计算效率的比较

#### 高效的动力学仿真

#### 存储方法

## 第7章 轨迹生成

### 7.1引言

**轨迹**指的是每个自由度的位置、速度和加速度的时间历程，

### 7.2 关于路径描述和路径生成综述

操作臂的运动看做是工具坐标系$\{T\}$相对于固定坐标系$\{S\}$的运动。

### 7.3 关节空间的规划方法

#### 三次多项式

操作臂的初始位置是已知的，并用一组关节角进行描述现在需要确定每个关节的运动函数，其在$t_0$时刻的值为该关节的初始位置，在$t_f$时刻的值为该关节的期望目标位置。有多种平滑函数$\theta(t)$均可用于对关节角进行插值。

为了获得一条确定的光滑运动曲线，显然至少需要对$\theta(t)$施加 4个约束条件。
$$
\theta(0)=\theta_0
\\\theta(t_f)=\theta_f
\\\dot\theta(0)=0
\\\dot\theta(t_f)=0
$$
![image-20230516131123953](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230516131123953.png)

次数至少为3的多项式才能满足这4个约束条件。（三次多项式有4个系数）
$$
\theta(t)=a_0+a_1t+a_2t^2+a_3t^3
$$
将约束方程代入，解出$a_i$
$$
a_0=\theta_0
\\a_1=0
\\a_2=\frac{3}{t^2_f}(\theta_f-\theta_0)
\\a_3=-\frac{2}{t^3_f}(\theta_f-\theta_0)
$$

#### 用于具有中间点的路径的三次多项式

一般而言，希望确定包含中间点的路径。如果已知各关节在中间点的期望速度，那么就可像前面一样构造出三次多项式，但是，这时在每个终止点的速度限制条件不再为零，而是已知的速度。于是，限制条件变成:
$$
\theta(0)=\theta_0
\\\theta(t_f)=\theta_f
\\\dot\theta(0)=\dot\theta_0
\\\dot\theta(t_f)=\dot\theta_f
$$
求解$a_i$，得
$$
a_0=\theta_0
\\a_1=\dot\theta_0
\\a_2=\frac{3}{t^2_f}(\theta_f-\theta_0)-\frac{2}{t_f}
\dot\theta_0-\frac{1}{t_f}\dot\theta_f
\\a_3=-\frac{2}{t^3_f}(\theta_f-\theta_0)+\frac{1}{t^2_f}(\dot\theta_f+\dot\theta_0)
$$

#### 高次多项式

有时用高次多项式作为路径曲线段。例如，如果要确定在路径曲线段的起始点和终止点的位置、速度和加速度，则需要用一个五次多项式进行插值，即
$$
\theta(t)=a_0+a_1t+a_2t^2+a_3t^3+a_4t^4+a_5t^5
$$
其约束条件为
$$
\begin{array}{l}
\theta_{0}=a_{0} \\
\theta_{f}=a_{0}+a_{1} t_{f}+a_{2} t_{f}^{2}+a_{3} t_{f}^{3}+a_{4} t_{f}^{4}+a_{5} t_{f}^{5} \\
\dot{\theta}_{0}=a_{1}
\\
\dot{\theta}_{f}=a_{1}+2 a_{2} t_{f}+3 a_{3} t_{f}^{2}+4 a_{4} t_{f}^{3}+5 a_{5} t_{f}^{4} \\
\ddot{\theta}_{0}=2 a_{2} \\
\ddot{\theta}_{f}=2 a_{2}+6 a_{3} t_{f}+12 a_{4} t_{f}^{2}+20 a_{5} t_{f}^{3}
\end{array}
$$
求解$a_i$得
$$
\begin{array}{l}
a_{0}=\theta_{0} \\
a_{1}=\dot{\theta}_{0} \\
a_{2}=\frac{\ddot{\theta}_{0}}{2} \\
a_{3}=\frac{20 \theta_{f}-20 \theta_{0}-\left(8 \dot{\theta}_{f}+12 \dot{\theta}_{0}\right) t_{f}-\left(3 \ddot{\theta}_{0}-\ddot{\theta}_{f}\right) t_{f}^{2}}{2 t_{f}^{3}} \\
a_{4}=\frac{30 \theta_{0}-30 \theta_{f}+\left(14 \dot{\theta}_{f}+16 \dot{\theta}_{0}\right) t_{f}+\left(3 \ddot{\theta}_{0}-2 \ddot{\theta}_{f}\right) t_{f}^{2}}{2 t_{f}^{4}} \\
a_{5}=\frac{12 \theta_{f}-12 \theta_{0}-\left(6 \dot{\theta}_{f}+6 \dot{\theta}_{0}\right) t_{f}-\left(\ddot{\theta}_{0}-\ddot{\theta}_{f}\right) t_{f}^{2}}{2 t_{f}^{5}}
\end{array}
$$

#### 带有抛物线过渡的线性函数

为了生成一条位置和速度都连续的平滑运动轨迹，在使用线性函数进行插值时，应该在每个路径点的邻域内增加一段抛物线作为过渡



![image-20230516152852885](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230516152852885.png)

在运动轨迹的过渡区段内，将使用恒定的加速度平滑地改变速度。

所以有
$$
\ddot\theta t_b=\frac{\theta_h-\theta_b}{t_h-t_b}
$$
式中$t_h$为时间中点，$\theta_h$为位置中点

而
$$
\theta_b=\theta_0+\frac{1}{2}\ddot\theta t_b^2
$$
联立上式，可得
$$
\ddot\theta t_b^2-\ddot\theta tt_b+(\theta_f-\theta_0)=0
$$
式中$t=2t_h$是期待的运动时间。对于任意给定的$\theta_f、\theta_0$和$t$，可通过选取任意的$\ddot\theta$和$t_b$来获取路径。注意选取的加速度要足够高，否则解不存在
$$
t_b=\frac{1}{2}-\frac{\sqrt{\ddot\theta^2t^2-4\ddot\theta(\theta_f-\theta_0)}}{2\ddot\theta}
$$

$$
\ddot\theta\ge\frac{4(\theta_f-\theta_0)}{t^2}
$$

#### 带有抛物线过渡的线性函数用于经过中间点的路径

现在考虑带有抛物线过渡的直线路径，路径上指定了任意数量的中间点在关节空间中为某个关节$\theta$的运动指定了一组中间点。每两个中间点之间使用线性函数相连，而各中间点附近使用抛物线过渡。

在这里将使用以下符号:用$j$、$k$和$l$表示三个相邻的路径点。位于路径点$k$处的过渡区段的时间间隔为$t_k$。位于点$j$和$k$之间的直线部分的时间间隔为$t_{jk}$。点$j$和$k$之间总的时间间隔为$t_{djk}$。直线部分的速度为$\dot\theta_{jk}$，而在点处过渡区段的加速度为$\ddot\theta_j$，

与单段路径的情形相似，存在有许多可能解，这取决于每个过渡区段的加速度值。已知所有的路径点$\theta_k$、期望的时间区间$t_{djk}$以及每个路径点处加速度的模值$|\ddot\theta_k|$，则可计算出过渡区段的时间间隔$t_k$。对于那些内部的路径点，可直接使用下列公式计算:
$$
\dot\theta_{jk}=\frac{\theta_k-\theta_j}{t_{djk}}
\\\ddot\theta_k=\operatorname{SGN}(\dot\theta_{kl}-\dot\theta_{jk})|\ddot\theta_k|\\
t_k=\frac{\dot\theta_{kl}-\dot\theta_{jk}}{\ddot\theta_k}
$$
式中$\operatorname{SGN}$为取符号函数

![image-20230516162345627](https://gitee.com/passing-the-world-with-you/typora_pictures/raw/master/img/image-20230516162345627.png)
$$
t_{jk}=t_{djk}-\frac{1}{2}t_j-\frac{1}{2}t_k
$$
但是，对于第一个路径段和最后一个路径段的处理与上式稍有不同，因为轨迹端部个过渡区的持续时间都必须计入这一路径段中。对于第一个路径段，令线性区段速度的两个表达式相等来求解$t_1$:
$$
\frac{\theta_{2}-\theta_{1}}{t_{d 12}-\frac{1}{2} t_{1}}=\ddot{\theta}_{1} t_{1}
$$


由此可解出在起始点处的过渡时间$  t_{1} $, 然后即可解出$  \dot{\theta}_{12}  $和$  t_{12}  $:
$$
\begin{aligned}
\ddot{\theta}_{1} & =\operatorname{SGN}\left(\theta_{2}-\theta_{1}\right)\left|\ddot{\theta}_{1}\right| \\
t_{1} & =t_{d 12}-\sqrt{t_{d 12}^{2}-\frac{2\left(\theta_{2}-\theta_{1}\right)}{\ddot{\theta}_{1}}} \\
\dot{\theta}_{12} & =\frac{\theta_{2}-\theta_{1}}{t_{d 12}-\frac{1}{2} t_{1}} \\
t_{12} & =t_{d 12}-t_{1}-\frac{1}{2} t_{2}
\end{aligned}
$$
同样, 对于最后一个路径段 (连接点$  n-1  $到$  n  $), 有:
$$
\frac{\theta_{n-1}-\theta_{n}}{t_{d(n-1) n}-\frac{1}{2} t_{n}}=\ddot{\theta}_{n} t_{n}
$$
据上式可求出
$$
\begin{aligned}
\ddot{\theta}_{n} & =\operatorname{SGN}\left(\theta_{n-1}-\theta_{n}\right)\left|\ddot{\theta}_{n}\right| \\
t_{n} & =t_{d(n-1) n}-\sqrt{t_{d(n-1) n}^{2}+\frac{2\left(\theta_{n}-\theta_{n-1}\right)}{\ddot{\theta}_{n}}} \\
\dot{\theta}_{(n-1) n} & =\frac{\theta_{n}-\theta_{n-1}}{t_{d(n-1) n}-\frac{1}{2} t_{n}} \\
t_{(n-1) n} & =t_{d(n-1) n}-t_{n}-\frac{1}{2} t_{n-1}
\end{aligned}
$$

### 7.4 笛卡儿空间规划方法

执行笛卡儿规划的计算量很大，因为在运行时必须以实时更新路径的速度求出运动学逆解，即在笛卡儿空间生成路径后，作为最后一步，通过求解逆运动学来计算出期望的关节角度。

#### 笛卡儿直线运动

如果能让工具在相隔较远的中间点之间走直线则会更为方便一些。这种定义和执行路径的模式被称作**笛卡儿直线运动**。

使用直线来定义运动是更为一般意义上的**笛卡儿运动**的子集。在笛卡儿运动中，可以使用笛卡儿变量关于时间的任意函数来定义路径。如果操作臂可以作一般意义的笛卡儿运动，则可以执行诸如椭圆或正弦的运动。

### 7.5 笛卡儿路径的几何问题

使用**角度-轴线**的表示方法可以只需三个数来定义姿态。如果把这种姿态的表示方法与$3\times 1$的笛卡儿位置表示方法相结合，就可得到$6\times 1$的笛卡儿位置与姿态的表示方法。考虑一个中间点，其相对于固定坐标系的定义为${}^S_AT$。坐标系$\{A\}$定义了一个中间点，在该点处末端执行器的位置由${}^SP{AORG}$给定，姿态由${}^S_AR$给定。该旋转矩阵可被转换成“角度-轴线”的表示方法:$\operatorname{ROT}({}^S\hat K_A,\theta_{SA})$一一或简写成${}^S K_A$。这里使用符号$\chi$代表该$6\times 1$的笛卡儿位置与姿态矢量。于是，得到:
$$
{}^S\chi_A=\left(\begin{array}{c}
{}^SP_{AORG}
\\{}^SK_A
\end{array}\right)
$$
其中，${}^SK_A$为旋转量$\theta_{SA}$模与单位矢量${}^S\hat K_A$相乘。如果每个路径点均使用这种方法来表示那么就可以选择适当的样条函数，使这6个分量随时间从一个路径点平滑地移动到下一个路径点。如果采用带有抛物线过渡的直线函数，那么中间点之间的路径则为直线。当经过中间点时，末端执行器的线速度与角速度将作平滑地变化。

### 7.6 路径的实时生成

在**实时运行**时，路径生成器不断产生用$\theta$、$\dot\theta$和$\ddot\theta$构造的轨迹，并且将此信息输送至操作臂的控制系统。路径计算的速度应能满足路径更新速率的要求。

#### 关节空间路径的生成

$$
\theta(t)=a_0+a_1t+a_2t^2+a_3t^3
$$

对于三次样条，路径生成器只需随t的变化不断计算上式。当到达路径段的终点时，调用新路径段的三次样条系数，重新把$t$置成零，继续生成路径。
对于带抛物线过渡的直线样条曲线，每次更新轨迹时，应首先检测时间$t$的值以判断当前是处在路径段的直线区段还是抛物线过渡区段。在直线区段，对每个关节的轨迹计算如下:
$$
\theta=\theta_j+\dot\theta_{jk}t
\\\dot\theta=\dot\theta_{jk}
\\\ddot\theta=0
$$
其中，$t$是自第$j$个中间点算起的时间，$\dot\theta_{jk}$的值在轨迹规划时按$式(250)$计算。在过渡区段，对各关节的轨迹计算如下:
$$
t_{inb}=t-(\frac{1}{2}t_j+t_{jk})
\\\theta=\theta_j+\dot\theta_{jk}(t-_{inb})+\frac{1}{2}\ddot\theta_kt_{inb}^2
\\\dot\theta=\dot\theta_{jk}+\ddot\theta_kt_{inb}
\\\ddot\theta=\ddot\theta_k
$$
其中$\dot\theta_{jk}$、$\ddot\theta_k$、$t_j$和$t_{jk}$在轨迹规划时根据$式(250)-式(255)$计算。当进入一个新的直线区段时，将$t$重置成$\frac{1}{2}t_k$，继续计算，直到计算出所有表示路径段的数据集合。

#### 笛卡儿空间路径的生成

使用路径生成器生成了带有抛物线过渡的直线样条曲线。但是，计算得到的数值表示的是笛卡儿空间的位置和姿态而不是关节变量值，所以这里使用符号来表示笛卡儿位姿矢量的一个分量，并重写$式(258)$和$式(259)$。在曲线的直线区段，工中的每个自由度按下式计算下:
$$
\begin{array}{l}
x=x_{j}+\dot{x}_{j k} t \\
\dot{x}=\dot{x}_{j k} \\
\ddot{x}=0
\end{array}
$$
其中,$  t $是自第$  j  $个中间点算起的时间, 而$  \dot{x}_{j k}  $是在轨迹规划过程中由类似于$式 (250) $的方程求出的。在过渡区段中, 每个自由度的轨迹计算如下:
$$
t_{\mathrm{inb}} =t-\left(\frac{1}{2} t_{j}+t_{j k}\right) \\
x  =x_{j}+\dot{x}_{j k}\left(t-t_{\mathrm{inb}}\right)+\frac{1}{2} \ddot{x}_{k} t_{\text {inb }}^{2} \\
\dot{x}  =\dot{x}_{j k}+\ddot{x}_{k} t_{\mathrm{inb}} \\
\ddot{x}  =\ddot{x}_{k}
$$
其中,$  \dot{x}_{j k} $、$ \ddot{x}_{k} $、$ t_{j} $、$ t_{j k}  $的值在轨迹规划过程中计算出, 与关节空间的情况完全相同。

最后, 这些笛卡儿空间的路径$  (\chi, \dot{\chi}, \ddot{\chi})  $必须被等价变换为关节空间的变量。对此, 可以通过运动学反解得到关节位移; 用逆雅可比矩阵计算关节速度, 用逆雅可比矩阵及其导数计算角加速度。

在实际中经常使用的简单方法为: 根据路径更新的速率, 将$ \chi  $转化成等价的坐标系表示: $ { }_{G}^{S} T $ 。然后使用$ \operatorname{SOLVE}$算法求出所需的关节角矢量$  \Theta $。然 后用数值微分计算出$\dot{\Theta}  $和 $ \ddot{\Theta}$。于是, 算法为
$$
\chi \to { }_{G}^{S} T \\
\Theta(t)  =\operatorname{SOLVE}\left({ }_{G}^{S} T\right) \\
\dot{\Theta}(t)  =\frac{\Theta(t)-\Theta(t-\delta t)}{\delta t} \\
\ddot{\Theta}(t) =\frac{\dot{\Theta}(t)-\dot{\Theta}(t-\delta t)}{\delta t}
$$
然后把$  \Theta$ 、$ \dot{\Theta} $、$ \ddot{\Theta} $输人给操作臂的控制系统。
