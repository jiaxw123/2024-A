---
title: 高等数学讲义(下)
author: 胡煜成
description: 首都师范大学2025春季学期高等数学A
"og:description": 浏览器版和手机版
"og:image": https://vlook-doc.pages.dev/pic/vlook-og.png
keywords:
- 高等数学,微积分,讲义
vlook-chp-autonum: h1{{第 ### 节 }},h3{{### }}
vlook-query: vdl=on
vlook-query: ws=off
---

[回到主页面](index.html)


# 多元函数的积分

> [!TIP]
>
> 多元函数的积分体系（如二重积分、三重积分、曲线与曲面积分）建立在三大分析学基础之上：**微分**用于刻画向量场的局部性质（如梯度、散度、旋度），**积分**将局部信息通过区域叠加扩展为全局量（如质量、通量、环流量），而**极限**则贯穿于积分定义与收敛性分析中。
>

### 场(field)
> [!TIP]
>
> - **标量场(scalar field)**:一个仅用其大小就可以完整表征的场
> - **向量场(vector field)**:在空间的每一个点都和一个向量相关联的场
> > **判断**
> > > 引力场：向量场
> > > 密度场：标量场
> > > 温度场：标量场
> > > 电磁场：向量场
> > > 流场：向量场
> 
> > **例1**
> 
> > **例2**

### 曲线积分（标量场）
> [!TIP]
> 图
>  $$ \int_{L} f(x,y) \, \mathrm{d}x $$   
>  $ L $ 为平面曲线，$ f(x,y) $ 是定义在 $ L $ 上的标量场，则积分可表示为极限形式：  
> $$
\int_{L} f(x,y) \, \mathrm{d}x = \lim_{N \to \infty} \sum_{i=1}^{N} f(x_i, y_i)  \mathrm{d}s_i $$
> 若曲线 $ L $ 的参数方程为 $ x = x(t) $, $ y = y(t) $，且$x(t),y(t)$在$[t_0,t_1]$上具有一阶连续导数，$x'^2(t)+y'^2(t)\neq 0$,则弧长$$\mathrm{d}s = \sqrt{[x'(t)]^2 + [y'(t)]^2} \, \mathrm{d}t$$此时曲线积分可转换为对参数 \( t \) 的定积分：    
> \[
\int_{L} f(x,y) \, \mathrm{d}s = \int_{t_0}^{t_1} f(x(t), y(t)) \cdot \sqrt{[x'(t)]^2 + [y'(t)]^2} \, \mathrm{d}t
\]  
>
> > **例1**
> > 计算曲线积分  
\[ \int_L \sqrt{y} \, ds \]  
其中 \( L \) 是抛物线 \( y = x^2 \) 上点 \( O(0,0) \) 与点 \( B(1,1) \) 之间的一段弧（如图所示）
> > >**解**  
由于 \( L \) 由方程：  
\[ y = x^2 \quad (0 \leq x \leq 1) \]  
给出，因此  
\[
\begin{aligned}
\int_L \sqrt{y} \, ds 
&= \int_0^1 \sqrt{x^2} \sqrt{1 + \left( \frac{dy}{dx} \right)^2} \, dx \\
&= \int_0^1 x \sqrt{1 + 4x^2} \, dx \\
&= \left[ \frac{1}{12} (1 + 4x^2)^{3/2} \right]_0^1 \\
&= \frac{1}{12} (5\sqrt{5} - 1)
\end{aligned}
\] 
> 
> > **例2**
> > 计算曲线积分 \(\int_{\Gamma} (x^2 + y^2 + z^2) \, ds\)，其中 \(\Gamma\) 为螺旋线：$
x = a \cos t、y = a \sin t、z = kt$
上相应于 \(t\) 从 \(0\) 到 \(2\pi\) 的一段弧。
> > > **解**
\[
\begin{aligned}
\int_{\Gamma} (x^2 + y^2 + z^2) \, ds 
&= \int_{0}^{2\pi} \left[ (a \cos t)^2 + (a \sin t)^2 + (kt)^2 \right] \sqrt{(-a^2 \sin t)^2  + (a \cos t)^2 + k^2} \, dt \\
&= \int_{0}^{2\pi} (a^2 + k^2 t^2) \sqrt{a^2 + k^2} \, dt \\
&= \sqrt{a^2 + k^2} \left[ a^2 t + \frac{k^2}{3} t^3 \right]_{0}^{2\pi} \\
&= \frac{2}{3} \pi \sqrt{a^2 + k^2} (3a^2 + 4\pi^2 k^2)
\end{aligned}
\]

### 曲线积分（向量场，2D）
> [!TIP]
>  图
> 设向量场为  
> \[
\vec{F}(x,y) = P(x,y)\vec{i} + Q(x,y)\vec{j},
\]  
> 力对质点沿曲线 \( L \) 所做的功 \( W \) 定义为：  
> \[
W = \int_{L} \vec{F} \cdot \mathrm{d}\vec{r} = \lim_{N \to \infty} \sum_{i=1}^{N} \vec{F}_i \cdot \Delta \vec{r}_i,
\]     
> 将点积展开并分离坐标分量：  
> $$
\begin{aligned}
W &= \int_{L} \vec{F} \cdot \mathrm{d}\vec{r} = \sum_{i=1} \vec{F}_i \cdot \Delta \vec{r}_i 
\end{aligned}
$$
> 其中，$\mathrm{d}\vec{r}=(\mathrm{d}x,\mathrm{d}y)^T,\Delta\vec{r}=(\Delta x,\Delta y)^T$,从而
$$
\begin{aligned}
W&= \sum_{i} \left( P \Delta x_i + Q \Delta y_i \right) \\
&= \int_{L} P(x,y) \, \mathrm{d}x + Q(x,y) \, \mathrm{d}y.
\end{aligned}
$$ 
> 若曲线 \( L \) 由参数方程 \( x = x(t) \), \( y = y(t) \) 描述，且$x(t),y(t)$在$[t_1,t_2]$上具有一阶连续导数，$x'^2(t)+y'^2(t)\neq 0$  ，则
> \[
\Delta \vec{r}_i = \left[ x'(t)\vec{i} + y'(t)\vec{j} \right] \mathrm{d}t.
\]      
> 且
> \[
\begin{aligned}
W &= \int_{t_1}^{t_2} \left[ P(x,y) x'(t) + Q(x,y) y'(t) \right] \mathrm{d}t \\
&= \int_{t_1}^{t_2} \left[ P(x(t), y(t)) x'(t) + Q(x(t), y(t)) y'(t) \right] \mathrm{d}t.
\end{aligned}
\]  
> > **例1**
> > 计算$$W = \int_{L} \vec{F} \cdot \mathrm{d}\vec{r}$$
> > 其中，$F=-y\vec{i}+x\vec{j}$,$x=t,y=t^2$
> > >**解**  
> > > $$
\begin{aligned}
W &= \int_{L} \vec{F} \cdot \mathrm{d}\vec{r}\\
&= \int_L-y\mathrm{d}x+x\mathrm{d}y\\
&= \int_0^1-y\mathrm{d}t+x \cdot 2t\mathrm{d}t\\
&= \int_0^1(-t^2+2t^2)\mathrm{d}t\\
&= \frac{1}{3}
\end{aligned}
$$
> > > **Note**:
> > > **(1)与曲线的参数化无关，积分只依赖于曲线$L$**
> > > 若改为$$
\begin{cases}
x=sin \theta  \\
y=sin^2 \theta
\end{cases},0\leq\theta\leq \frac{\pi}{2}
$$
> > > 积分结果不变
> > > **(2)依赖曲线$L$的方向**
> >
> > **例2**
> > 计算 $$ \int_{L} xy\,dx $$其中 \( L \) 为抛物线 \( y^2 = x \) 上从点 \( A(1, -1) \) 到点 \( B(1, 1) \) 的一段弧
> > 图
> > >**解法一**  
> > > 将所给积分转化为对$x$的定积分来计算：$$
\begin{aligned}
\int_{L} xy\,dx &= \int_{AO} xy\,dx + \int_{OB} xy\,dx \\
&= \int_{1}^{0} x(-\sqrt{x})\,dx + \int_{0}^{1} x\sqrt{x}\,dx \\
&= 2 \int_{0}^{1} x^{\frac{3}{2}}\,dx\\
&= \frac{4}{5}
\end{aligned}
$$
> >>**解法二**  
将所给积分化为对 \( y \) 的定积分来计算
$$
\begin{aligned}
\int_{L} xy\,dx &= \int_{-1}^{1} y^2 y (y^2)'\,dy \\
&= 2 \int_{-1}^{1} y^4\,dy \\
&= 2 \left[ \frac{y^5}{5} \right]_{-1}^{1} \\
&= \frac{4}{5}
\end{aligned}
$$
> >
> > **例3**
> >设一个质点在点 \( M(x,y) \) 处受到力 \( F \) 的作用，\( F \) 的大小与点 \( M \) 到原点 \( O \) 的距离成正比，\( F \) 的方向恒指向原点。此质点由点 \( A(a,0) \) 沿椭圆 \( \frac{x^2}{a^2} + \frac{y^2}{b^2} = 1 \) 按逆时针方向移动到点 \( B(0,b) \)，求力 \( F \) 所作的功 \( W \)
> > > 图
> > >由题意，力的表达式为：  
\[
\overrightarrow{F} = -k(x\mathbf{i} + y\mathbf{j}),
\]  
其中 \( k > 0 \) 为比例常数。功的表达式为：  
\[
W = \int_{AB} \overrightarrow{F} \cdot d\mathbf{r} = -k \int_{AB} (x\,dx + y\,dy).
\]  
> > >利用椭圆的参数方程：  
\[
\begin{cases}
x = a \cos \theta, \\
y = b \sin \theta,
\end{cases} \quad \theta \in \left[0, \frac{\pi}{2}\right],
\]  
计算微分：  
\[
dx = -a \sin \theta\,d\theta, \quad dy = b \cos \theta\,d\theta.
\]  
代入积分式：  
$$
\begin{aligned}
W &= -k \int_{0}^{\frac{\pi}{2}} \left[ a \cos \theta (-a \sin \theta) + b \sin \theta (b \cos \theta) \right] d\theta \\ 
&= k(a^2 - b^2) \int_{0}^{\frac{\pi}{2}} \sin \theta \cos \theta \,d\theta \\
&= \frac{1}{2} k(a^2 - b^2)\int_{0}^{\frac{\pi}{2}} \sin 2\theta \,d\theta \\
&= \frac{1}{2}k(a^2 - b^2) \left[ -\frac{\cos 2\theta}{2} \right]_{0}^{\frac{\pi}{2}}\\ 
&= \frac{k}{2}(a^2 - b^2).
\end{aligned}
$$ 

### 封闭曲线
> [!TIP]
> 图
> $$\vec{F}(x,y)=y\vec{i}+x\vec{j}$$  
> $$\oint_{C}\vec{F} \cdot \mathrm{d}\vec{r}=\int_{C_1}\vec{F} \cdot \mathrm{d}\vec{r}+\int_{C_2}\vec{F} \cdot \mathrm{d}\vec{r}+\int_{C_3}\vec{F} \cdot \mathrm{d}\vec{r}$$  
> 其中，$$\int_{C_1}\vec{F} \cdot \mathrm{d}\vec{r}=0$$
> 对于$C_2$,其参数方程为
> $$
\begin{cases}
x=acos\theta \\
y=asin\theta
\end{cases},0\leq\theta\leq\frac{\pi}{4}
$$
>从而
> $$
\begin{cases}
\mathrm{d}x=-asin\theta \mathrm{d}\theta \\
\mathrm{d}y=acos\theta \mathrm{d}\theta
\end{cases}
$$
> 则
> $$
\begin{aligned}
\int_{C_2}\vec{F} \cdot \mathrm{d}\vec{r}
&= \int_0^{\frac{\pi}{4}}(-yasin\theta+xacos\theta)\mathrm{d}\theta \\
&=\int_0^{\frac{\pi}{4}}(-a^2sin^2\theta+a^2cos^2\theta)\mathrm{d}\theta \\
&= a^2\int_0^{\frac{\pi}{4}}\frac{1+cos2\theta-1+cos2\theta}{2}\mathrm{d}\theta \\
&=\frac{a^2}{2}\int_0^{\frac{\pi}{4}}cos2\theta\mathrm{d}\theta \\
&=\frac{a^2}{2}\left[sin2\theta\right]_0^{\frac{\pi}{4}} \\
&=\frac{a^2}{2}
\end{aligned}
$$
> 对于$C_3$,其参数方程为
> $$
\begin{cases}
x=\frac{\sqrt{2}}{2}a-\frac{\sqrt{2}}{2}t \\
y=\frac{\sqrt{2}}{2}a-\frac{\sqrt{2}}{2}t
\end{cases},0 \leq t \leq a 
$$
> 从而
> $$
> \begin{cases}
\mathrm{d}x=-\frac{\sqrt{2}}{2}\mathrm{d}t \\
\mathrm{d}y=-\frac{\sqrt{2}}{2}\mathrm{d}t
> \end{cases}
> $$
> 则$$
\begin{aligned}
\int_{C_3}y\mathrm{d}x+x\mathrm{d}y
&=-\frac{\sqrt{2}}{2}\int_{C_3}(\frac{\sqrt{2}}{2}a-\frac{\sqrt{2}}{2}t)\mathrm{d}t+(\frac{\sqrt{2}}{2}a-\frac{\sqrt{2}}{2}t)\mathrm{d}t\\
&=\int_0^a(t-a)\mathrm{d}t\\
&=\left[\frac{1}{2}t^2-at\right]_0^a\\
&=-\frac{a^2}{2}\\
\end{aligned}
$$
> 综上，$$I=0+\frac{a^2}{2}-\frac{a^2}{2}=0$$


### 两类曲线积分之间的关系
> [!TIP]
> 图
> $$W=\int_L\vec{F}\cdot \mathrm{d}\vec{r}=\int_L\vec{F} \cdot \vec{\tau}\mathrm{d}s$$
> > **例1**
> > **(1)保守场**：已知$\vec{F}=x\vec{i}+y\vec{j}$，求$W=\int_L\vec{F}\cdot \mathrm{d}\vec{r}$，曲线$L$如下图所示：
> > 图
> > > **解**：
> > > $$W=\int_L\vec{F}\cdot \mathrm{d}\vec{r}=0$$
> >
> > **(2)非保守场**：已知$\vec{F}=-y\vec{i}+x\vec{j}$，求$W=\int_L\vec{F} \cdot \vec{\tau}\mathrm{d}s$，曲线$L$如下图所示：
> > 图
> > > **解法一**：
> > > $$
\begin{aligned}
W &= \int_L\vec{F} \cdot \vec{\tau}\mathrm{d}s \\
&= \int_L \left|F\right | \mathrm{d}s \\
&= R \cdot 2\pi R\\
&= 2\pi R^2
\end{aligned}
$$
> > >**解法二**：
> > > 曲线的参数方程为$$
\begin{cases}
x=Rcos\theta \\
y=Rsin\theta
\end{cases}
$$
> > > 则
> > > $$
\begin{cases}
\mathrm{d}x=-Rsin\theta \mathrm{d}\theta \\
\mathrm{d}y=Rcos\theta \mathrm{d}\theta
\end{cases}
$$
> > >$$
\begin{aligned}
W &=\int_0^{2\pi}(-y\cdot -Rsin \theta + x\cdot Rcos \theta)\mathrm{d} \theta \\
&=\int_0^{2\pi}(R^2sin^2\theta+R^2cos^2\theta)\mathrm{d} \theta \\
&=\int_0^{2\pi}R^2\mathrm{d} \theta \\
&= 2\pi R^2
\end{aligned}
$$
> > 
> > **例2**
> >计算 \(\int_L y^2 \, dx\)，其中 \(L\) 为图中所示：  
> >(1) 半径为 \(a\)、圆心为原点、按逆时针方向绕行的上半圆周
> >(2) 从点 \(A(a,0)\) 沿 \(x\) 轴到点 \(B(-a,0)\) 的直线段。
> > > **解**
> > > (1)参数方程为：  
$$
\begin{cases}
x = a \cos \theta, \\
 y = a \sin \theta 
\end{cases},0 \leq \theta \leq \pi
$$  
$$
\begin{aligned}
\int_L y^2 \, dx 
&= \int_L y^2 \mathrm{d}x+0\mathrm{d}y \\
&= \int_0^\pi -a^2 \sin^2 \theta \cdot a \sin \theta \mathrm{d} \theta \\
&= a^3 \int_0^\pi (1-cos^2\theta)\mathrm{d}cos\theta \\
&= a^3[ \left[cos \theta \right]_{0}^\pi -\frac{1}{3}\left[cos^3\theta\right]_{0}^\pi ]\\
&= -2a^3+\frac{2}{3}a^3 \\
&= -\frac{4}{3} a^3.
\end{aligned}
$$
> > > (2)直线段方程为：  
$$
\begin{cases}
x=x\\
y=0
\end{cases},-a\leq x \leq a
$$   
\[
\int_L y^2 \, dx = \int_{L} 0 \, dx = 0.
\]
> > > **Note:路径相关**
> >
> > **例3**
> >计算 \(\int_{L} 2xy \, dx + x^2 \, dy\)，其中 \(L\) 为：  
> >(1) 抛物线 \(y = x^2\) 上从 \(O(0,0)\) 到 \(B(1,1)\) 的一段弧。  
> > (2) 抛物线 \(x = y^2\) 上从 \(O(0,0)\) 到 \(B(1,1)\) 的一段弧。  
> >(3) 有向折线 \(OAB\)（\(O(0,0)\), 这里$O,A,B$依次是点$(0,0),(1,0),(1,1)$
> > > **解**
> > >(1)这段弧可以表示为：
> > >$$
\begin{cases}
x=x\\
y=\sqrt{x}
\end{cases},0\leq x \leq 1
$$
> > > 从而$$
\begin{cases}
\mathrm{d}x=\mathrm{d}x\\
\mathrm{d}y=\frac{1}{2}\frac{1}{\sqrt{x}}\mathrm{d}x
\end{cases}
$$
$$
\begin{aligned}
\int_{L} 2xy \, dx + x^2 \, dy &= \int_{0}^{1} \left(2x \cdot \sqrt{x} + x^2 \cdot \frac{1}{2}\frac{1}{\sqrt{x}}\right) \mathrm{d}x \\
&= \int_{0}^{1}  (2x^{\frac{3}{2}}+\frac{1}{2}x^{\frac{3}{2}})\mathrm{d}x \\
&= \left[ x^{\frac{5}{2}} \right]_{0}^{1} \\
&= 1.
\end{aligned}
$$
> > >(2) $$\int_{L} 2xy \, dx + x^2 \mathrm{d}y = 1$$
> > >(3)  
> > > 线段$L_1:OA$
   $y = 0，x \in [0, 1]，\mathrm{d}y = 0$：  
   $$
   \int_{L_1} 2xy \mathrm{d}x + x^2 \mathrm{d}y = \int_{0}^{1} 0 \mathrm{d}x = 0.
   $$
> > >线段$L_2:AB$  
   $x = 1，y \in [0, 1]，\mathrm{d}x = 0$：  
   $$
   \int_{L_2} 2xy \mathrm{d}x + x^2 \mathrm{d}y = \int_{0}^{1} 1^2 \mathrm{d}y = \left[ y \right]_{0}^{1} = 1.
   $$
> > >最终结果：
$$
\int_{OAB} 2xy \mathrm{d}x + x^2 \mathrm{d}y = \int_{L_1} 2xy \mathrm{d}x + x^2 \mathrm{d}y + \int_{L_2} 2xy \mathrm{d}x + x^2 \mathrm{d}y = 1.
$$
> > >**Note:路径无关**


### 特殊情况：梯度场
> [!TIP]
> 若$\exist f(x,y),s.t.$
> $$\frac{\partial f}{\partial x}=P(x,y)，\frac{\partial f}{\partial y}=Q(x,y)$$
> 即
> $$\mathrm{d}f=P\mathrm{d}x+Q\mathrm{d}y$$
> 则
> $$
\begin{aligned}
\int_LP(x,y)\mathrm{d}x+Q(x,y)\mathrm{d}y
&=\int_L \mathrm{d}f\\
&=f(x(t_2),y(t_2))-f(x(t_1),y(t_1))\\
&=f(终)-f(起)
\end{aligned}
$$
> 在物理上，
> $$W=f(终)-f(起)$$
> 若$$\vec{F}=(P,Q)=\nabla f=(\frac{\partial f}{\partial x},\frac{\partial f}{\partial y})$$
> 则$\vec{F}$是$f$的梯度场
> **Note:并不是所有$\vec{F}$都是某函数的梯度场**

> [!TIP]
> **假如$\vec{F}$是某函数$f$的梯度场**,会有什么结论？以**单连通区域**为前提
> - 积分与路径无关
> - $\vec{F}$是保守场，$\oint_L\vec{F} \cdot \mathrm{d}\vec{r}=0$（对所有封闭曲线$L$）
> 证明：
> 图
> $$\int_{C_1}\vec{F} \cdot \mathrm{d}\vec{r}+\int_{C_2}\vec{F} \cdot \mathrm{d}\vec{r}=\int_{C_1}\vec{F} \cdot \mathrm{d}\vec{r}-\int_{-C_2}\vec{F} \cdot \mathrm{d}\vec{r}=0$$

> [!TIP]
> **判定向量场 \(\vec{F} = (P(x,y), Q(x,y))\) 是否为梯度场**
若存在函数 $f(x,y)$，使得 $\vec{F}$ 可以表示为该函数的梯度，即：
$$
\nabla f = \frac{\partial f}{\partial x} \mathrm{d}x + \frac{\partial f}{\partial y} \mathrm{d}y,
$$
则 $\vec{F}$ 是梯度场。此时，$\vec{F}$ 的分量满足：
$$
P = \frac{\partial f}{\partial x}, \quad Q = \frac{\partial f}{\partial y}.
$$
>由于函数 $f(x,y)$ 的二阶混合偏导数必须满足：
$$
\frac{\partial^2 f}{\partial x \partial y} = \frac{\partial^2 f}{\partial y \partial x}.
$$
将 $\vec{F}$的分量代入，可得：
$$
\frac{\partial}{\partial y}\left(\frac{\partial f}{\partial x}\right) = \frac{\partial}{\partial x}\left(\frac{\partial f}{\partial y}\right) \implies \frac{\partial P}{\partial y} = \frac{\partial Q}{\partial x}.
$$
> 因此，**判定$\vec{F}$是梯度场的条件**为：
**$$
\frac{\partial P}{\partial y} = \frac{\partial Q}{\partial x},
$$**
> > **例1**
> > 判断$<y^2,0>$是否为梯度场
> > > **解**
> > > $$P_y=2y \neq Q_x=0$$
> > > 因此，$<y^2,0>$不是梯度场
> >
> > **例2**
> >判断$<2xy,x^2>$是否为梯度场
> > > **解**
> > > $$P_y=2x=Q_x=2x$$
> > > 因此，$<2xy,x^2>$是梯度场
> >
> > **例3**
> >判断$<y,x>$是否为梯度场
> > > **解**
> > > $$P_y=1=Q_x=1$$
> > > 因此，$<y,x>$是梯度场

> [!TIP]**有问题**
> **如何计算$f$**
> 图
> 已知$\vec{F}=(y,x),f(0,0)=c$
> $$
\begin{aligned}
f(x,y)&=\int_{C_1}P\mathrm{d}x+Q\mathrm{d}y+\int_{C_2}P\mathrm{d}x+Q\mathrm{d}y+f(0,0)\\
&=\int_0^x 0 \mathrm{d}x+\int_0^y
x\mathrm{d}y + c\\
&=xy+c
\end{aligned}
$$
> 若
> $$\vec{F}(x,y)=[(x^2+axy+3),(3y^2-2x^2)]$$
> $$P_y=ax=Q_x=-4x$$
> 从而$a=-4$
> $$\vec{F}(x,y)=[(x^2-4xy+3),(3y^2-2x^2)]$$


> [!TIP]
> **$curl$**
> 定义：
> $$curl\vec{F}=Q_x-P_y=\frac{\partial Q}{\partial x}-\frac{\partial P}{\partial y}$$
> - $$curl\vec{F}=0\Leftrightarrow 保守场（梯度场）$$
> > 描述旋转
> > >(1)$\vec{F}=a\vec{i}+b\vec{j},curl\vec{F}=0$
> > >图
> >
> > > (2)$\vec{F}=x\vec{i}+y\vec{j}$
> > > 此时
> > > $$\frac{\partial x}{\partial y}=0,\frac{\partial y}{\partial x}=0$$
> > > 因此，$$curl\vec{F}=\frac{\partial y}{\partial x}-\frac{\partial x}{\partial y}=0$$
> > > 图
> >
> > > (3)$\vec{F}=-y\vec{i}+x\vec{j}$
> > > 此时
> > > $$curl\vec{F}=\frac{\partial x}{\partial x}-\frac{\partial (-y)}{\partial y}=1+1=2$$

> [!TIP]
> 我们喜欢梯度场，因为它具有简洁的数学结构与明确的物理意义，其路径积分结果仅取决于起点和终点，这一特性在解决保守场相关问题时带来了极大便利。然而需要注意的是，$curl{\vec{F}}$是关键概念且它并非梯度场——梯度场的旋度恒为零，而$curl{\vec{F}}$的非零性恰恰刻画了向量场$vec{F}$的"旋转"特性。对于一般的向量场$\vec{F}$，若想研究其曲线积分，抓住$curl{\vec{F}}$这一核心量是重要突破口：根据斯托克斯定理，向量场沿有向闭曲线的曲线积分等于其旋度通过以该曲线为边界的有向曲面的曲面积分，这一联系使得我们能够通过分析$curl{\vec{F}}$的分布与性质，更高效地求解复杂曲线积分问题，揭示向量场在空间中的动态特征。
> 图

> [!TIP]
> **格林公式(Green's theorem)**
> $$\oint_C\vec{F} \mathrm{d}\vec{r}=\iint_R curl\vec{F}\mathrm{d}A$$
> $$\oint_C P\mathrm{d}x+Q\mathrm{d}y = \iint_R (\frac{\partial Q}{\partial x}-\frac{\partial P}{\partial y})\mathrm{d}A$$
> 其中
> - $C:$闭曲线，逆时针
> - $\vec{F}:$连续可微向量场
> **Note:闭曲线，逆时针，$\vec{F}$连续**


### 格林公式
> [!TIP]
> **定理**：设闭区域$D$由分段光滑的曲线$L$围成，若函数$P(x,y)$及$Q(x,y)$在$D$上具有一阶连续偏导数，则有：
> **$$\oint_C P\mathrm{d}x+ Q\mathrm{d}y=\iint_R(Q_x-P_y)\mathrm{d}x\mathrm{d}y$$**
> 其中$L$是$D$的取正向的边界曲线.
> 上述公式称为**格林公式**.
> **证明**：
> > (1)special case:$Q=0$
> > $$\int_C P \mathrm{d}x=\iint_R -P_y \mathrm{d}A$$
> > 同理，若$P=0$，则有
> > $$\int_C Q \mathrm{d}y=\iint_R -Q_x \mathrm{d}A$$
> > (2)简化区域
> > 图
> > 如图可得：
> > $$\int_{C_1}P\mathrm{d}x=\iint_{R_1}-P_y\mathrm{d}A \\ \int_{C_2}P\mathrm{d}x=\iint_{R_2}-P_y\mathrm{d}A$$
> > 由于
> > $$\int_{C}P\mathrm{d}x=\int_{C_1}P\mathrm{d}x+\int_{C_2}P\mathrm{d}x \\ 
\iint_{R}-P_y\mathrm{d}A=\iint_{R_1}-P_y\mathrm{d}A+\iint_{R_2}-P_y\mathrm{d}A$$
> > 因此，
> > $$\int_{C}P\mathrm{d}x=\iint_{R}-P_y\mathrm{d}A$$
> > (3)主要部分
> > 要证：
> > $$\oint_C P\mathrm{d}x=\iint_R -P_y\mathrm{d}A$$
> > 其中：
> > $C:simple$
> > $R:vert\ simple$
> > 图
> > 由图可得：
> > $$\oint_C P\mathrm{d}x=\int_{C_1}P\mathrm{d}x+\int_{C_2}P\mathrm{d}x+\int_{C_3}P\mathrm{d}x + \int_{C_4}P\mathrm{d}x$$
> > 其中，
> > $$\int_{C_1}P\mathrm{d}x=0 , \int_{C_3}P\mathrm{d}x=0 \\
\int_{C_2}P\mathrm{d}x=\int_a^bP(x,f_1(x))\mathrm{d}x \\ 
\int_{C_4}P\mathrm{d}x=\int_b^aP(x,f_2(x))\mathrm{d}x=-\int_a^bP(x,f_2(x))\mathrm{d}x$$
> > 因此，
> > $$\oint_C P\mathrm{d}x=-\int_a^b[P(x,f_2(x))-P(x,f_1(x))]\mathrm{d}x$$
> > 又因为，
> > $$
\begin{aligned}
\iint_R-P_y \mathrm{d}x\mathrm{d}y&= -\int_a^b[\int_{f_1(x)}^{f_2(x)}\frac{\partial P}{\partial y}\mathrm{d}y]\mathrm{d}x\\
&=-\int_a^b[P(x,f_2(x))-P(x,f_1(x))]\mathrm{d}x
\end{aligned}
$$
> > 得证.
>
> > **例1**
> > $$\vec{F}=-y\vec{i}+x\vec{j}$$
> > > **解**
> > > $$curl\vec{F}=1+1=2$$
> > > 因此，
> > >$$\iint_Dcurl\vec{F}\mathrm{d}A=\iint_D2\mathrm{d}A=2Area=\oint_C-y\mathrm{d}x+x\mathrm{d}y$$
> >
> > **例2**
> > 计算 $$\oint_L x^2 y \mathrm{d}x - xy^2 \mathrm{d}y$$其中 $L$为正向圆周 $x^2 + y^2 = a^2$.
> > > **解**
> > >令 \(P = x^2 y\)，\(Q = -xy^2\)，则  
   $$
   \frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y} =  = -y^2 - x^2
   $$
> > >由格林公式得：  
   $$
   \begin{aligned}
   \oint_L x^2 y \mathrm{d}x - xy^2 \mathrm{d}y &= -\iint_D (x^2 + y^2) \mathrm{d}x \mathrm{d}y\\
   &=-\int_0^{2\pi} \mathrm{d}\theta \int_0^a \rho^3 \mathrm{d}\rho \\
   &= -\frac{\pi}{2} a^4
   \end{aligned}
   $$
> >
> > **例3**
> >计算 $$\oint_{L} \frac{x \, dy - y \, dx}{x^2 + y^2}$$
> >其中 $L$ 为一条无重点、分段光滑且不经过原点的连续闭曲线，$L$ 方向为逆时针
> > > **解**
> > > 令 $P = \frac{-y}{x^2 + y^2},Q = \frac{x}{x^2 + y^2}$，当 $x^2 + y^2 \neq 0$ 时，有
> > > $$\frac{\partial Q}{\partial x} = \frac{y^2 - x^2}{(x^2 + y^2)^2}, \quad \frac{\partial P}{\partial y} = \frac{y^2 - x^2}{(x^2 + y^2)^2}$$
> > >记$L$所围成的闭区域为$D$.
> > >(1)$(0,0)\notin D$
> > > 由格林公式，$$\oint_{L} \frac{x \, dy - y \, dx}{x^2 + y^2}=0$$
> > >(2)$(0,0)\in D$
> > >选取半径 $r > 0$的圆周 $l: x^2 + y^2 = r^2$（位于 $D$ 内），记 $L$ 和 $l$ 所围区域为 $D_1$.对 复连通区域$D_1$ 应用格林公式，方向均为逆时针：
> > > $$\oint_{L} \frac{x \mathrm{d}y - y \mathrm{d}x}{x^2 + y^2} - \oint_{l} \frac{x \mathrm{d}y - y \mathrm{d}x}{x^2 + y^2}=0$$
> > > 于是
> > > $$
\begin{aligned}
\oint_{L} \frac{x \mathrm{d}y - y \mathrm{d}x}{x^2 + y^2} 
&=\oint_{l} \frac{x \mathrm{d}y - y \mathrm{d}x}{x^2 + y^2}\\
&= \int_0^{2\pi} \frac{r^2 (\cos^2 \theta + \sin^2 \theta)}{r^2} \mathrm{d}\theta \\
&= 2\pi
\end{aligned}
$$
> >
> > **例4**
> > > $$\oint_C x\mathrm{d}y=\iint_R 1 \mathrm{d}A=Area$$

### 通量(flux)--另一类曲线积分（仍是第二类）
> [!TIP]
> 图
> $$
\begin{aligned}
\int_C\vec{F}\cdot \vec{n}\mathrm{d}s&=\lim_{\Delta s \to 0}\sum_iF(x_i,y_i)\cdot \vec{n_i}\Delta s_i \\
&= \lim_{\Delta s \to 0}\sum_i[-Q_i\Delta x_i+P_i\Delta y_i]
\end{aligned}
$$
> $$Flux=\int_C-Q(x,y)\mathrm{d}x+P(x,y)\mathrm{d}y$$
> 又因为$\vec{F}=(P,Q)^T$,$\vec{F}^{\perp}=(-Q,P)$与$(P,Q)$垂直
> 从而，
> $$Flux=\int_C\vec{F}^{\perp}\cdot \mathrm{d}\vec{r}$$
>
> **格林公式的flux表示**：
> 对
> $$Flux =\oint_C-Q(x,y)\mathrm{d}x+P(x,y)\mathrm{d}y$$
> 应用格林公式，可得
> $$\oint_C-Q(x,y)\mathrm{d}x+P(x,y)\mathrm{d}y=\iint_D(\frac{\partial P}{\partial x}+\frac{\partial Q}{\partial y})\mathrm{d}x\mathrm{d}y$$
> 由散度定义：
> $$div\vec{F}=(\frac{\partial}{\partial x},\frac{\partial}{\partial y})\cdot (P,Q)=\nabla \cdot \vec{F}$$
> 最终得到通量形式：
> $$Flux =\iint_D\nabla \cdot \vec{F}\mathrm{d}A$$
> > **例1**
> > 图
> > $$\vec{F}=x\vec{i}+y\vec{j}$$
> > > **解**
> > >由于 $$
\begin{aligned}
div\vec{F}&=\nabla \cdot \vec{F}\\
&=\frac{\partial P}{\partial x}+\frac{\partial Q}{\partial y}\\
&=1+1\\
&=2
\end{aligned}
$$
> > > 因此，
> > > $$
\begin{aligned}
\int_C\vec{F}\cdot \vec{n}\mathrm{d}s&=\iint_D div\vec{F}\mathrm{d}A\\
&=2\iint_D\mathrm{d}A\\
&=2Area
\end{aligned}
$$
> >
> > **例2**
> > 不可压流体
> > > $div\vec{F}=0$,$\vec{F}$是速度场，$\nabla \cdot \vec{u}=0$
> > > Navier-Stokes方程(不可压形式)：
> > > $$\frac{\partial \vec{u}}{\partial t}+\vec{u}\cdot \nabla\vec{u}=-\frac{1}{\rho}\nabla p+\nu\nabla^2\vec{u}+\vec{g}$$
> > >其中，
> > >$v=\frac{\mu}{\rho}$：粘度
> > >$P$：压强
> > >$g$：外力（重力）
>
> **3D情形**:$line \to surface$
> > **物理学家视角**：
> > >图
> > > $$Flux=\iint_S\vec{F}\cdot \vec{n}\mathrm{d}s=\lim_{\Delta s \to 0}\sum_i\vec{F}(x_i,y_i,z_i)\cdot \vec{n_i}\Delta s_i$$
> > > $\mathrm{d}s \neq \mathrm{d}A=\mathrm{d}x\mathrm{d}y$
> > >其中，$\vec{F}(x_i,y_i,z_i)\cdot \vec{n_i}$是高，$\Delta s_i$是底面积
> >
> > **数学家视角**:
> > > 先看一个简单的例子：
> > > 图
> > > $$\vec{F}=x\vec{i}+y\vec{j}+z\vec{k} \\ \vec{n}=\frac{1}{a}(x,y,z)^T$$
> > >可得
> > > $$\vec{F}\cdot \vec{n}=\left | F \right |=a$$
> > > 因此，
> > > $$\iint_S\vec{F}\cdot \vec{n}\mathrm{d}S=a\iint_S\mathrm{d}S=4\pi a^3$$
> > > （特殊情形）
> > > 再来看一般情形：
> > > 图
> > > $$\vec{F}=P(x,y,z)\vec{i}+Q(x,y,z)\vec{j}+R(x,y,z)\vec{k} $$
> > > $$\iint_S\vec{F}\cdot \vec{n}\mathrm{d}S=\iint_SR(x,y,z)\mathrm{d}x\mathrm{d}y+Q(x,y,z)\mathrm{d}y\mathrm{d}z+P(x,y,z)\mathrm{d}z\mathrm{d}x$$
> > >其中，
> > > $$\iint_SR(x,y,z)\mathrm{d}x\mathrm{d}y=\iint_{D_xy}R(x,y,z(x,y))\mathrm{d}x\mathrm{d}y \\
\iint_SQ(x,y,z)\mathrm{d}y\mathrm{d}z=\iint_{D_xz}Q(x,y(x,z),z)\mathrm{d}x\mathrm{d}z \\
\iint_SP(x,y,z)\mathrm{d}z\mathrm{d}x=\iint_{D_yz}P(x(y,z),y,z)\mathrm{d}y\mathrm{d}z$$
> > > $$
\begin{aligned}
\iint_S\vec{F}\cdot \vec{n}\mathrm{d}S&=\iint_S(\vec{F_1}+\vec{F_2}+\vec{F_3})\cdot \vec{n}\mathrm{d}S\\
&=\iint_S\vec{F_1}\cdot \vec{n}\mathrm{d}S+\iint_S\vec{F_2}\cdot \vec{n}\mathrm{d}S+\iint_S\vec{F_3}\cdot \vec{n}\mathrm{d}S
\end{aligned}
$$
> > > 以$\vec{F_1}=(0,0,R(x,y,z))^T$为例，$\vec{v_1}=(\Delta x,0,\frac{\partial z}{\partial x}\Delta x),\vec{v_2}=(0,\Delta y,\frac{\partial z}{\partial y}\Delta y)$
> > > 则
> > > $$
\begin{aligned}
\vec{n}\cdot \mathrm{d}S &= \vec{v_1}\times \vec{v_2}\\
&=
\begin{vmatrix}
\vec{i} & \vec{j} & \vec{k} \\
\Delta x & 0 & \frac{\partial z}{\partial x}\Delta x \\
0 & \Delta y & \frac{\partial z}{\partial y}\Delta y
\end{vmatrix}\\
&=(-\frac{\partial z}{\partial x},-\frac{\partial z}{\partial y},1)\Delta x \Delta y
\end{aligned}
$$
