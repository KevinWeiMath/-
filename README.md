# 讨论了常微分方程初值问题的单步法和Runge-Kutta法

## 一阶常微分方程初值问题
设 $f(t,u)$ 在区域 $0\leq t\leq T,\quad |u|<\infty$ 上连续，求 $u=u(t)$ 满足：

$$\frac{du}{dt}=f(t,u),\quad 0\leq \leq T\tag{1}$$

$$u(0)=u_0\tag{2}$$

其中 $u_0$ 是给定的初值，这就是一阶常微分方程的初值问题。

为使问题 $(1)-(2)$ 的解存在、唯一且连续依赖初值 $u_0$ ，还必须对右端 $ f(t,u)$ 加适当的限制

通常要求 $f$ 关于 $u$ 满足 $Lipschitz$ 条件：存在常数 $L$ 使得：

$$|f(t,u_1)-f(t,u_2)|\leq L|u_1-u_2\tag{3}|$$

对任意的 $t\in [0,T]$ 和 $u_1,u_2 \in (-\infty,+\infty)$ 都成立.

本文中总假设满足上述条件。
## 单步法和 $Runge-Kutta$ 法
### 单步法
设初值问题:

$$\left\{\begin{matrix}
u^{\prime}=f(t,u) \\
u(t_0)=u_0
\end{matrix}\right.$$

的解充分光滑

将 $u(t)$ 在 $t_0$ 处用 $Taylor$ 公式展开：

$$
u(t_1)=u(t_0)+hu^{\prime}(t_0)+\frac{h^2}{2!}u^{(2)}(t_0)+\cdots+\frac{h^p}{p!}u^{(p)}(t_0)+O(h^{p+1}),\tag{4}
$$

其中 $u(t_0)=u_0,\quad u^{\prime}(t_0)=f(t_0,u(t_0))=f(t_0,u_0)$ ,

$$
{(2)}(t_0)=\frac{d}{dt}f|_{t_0}=[f_t+f_u\cdot u^{\prime}(t)]_{t=t_0}=f_t(t_0,u_0)+f(t_0,u_0)f_u(t_0,u_0),\tag{5}
$$

 和
 
$$
u^{(3)}(t_0)=f_{tt}(t_0,u_0)+2f(t_0,u_0)f_{tu}(t_0,u_0)+f^2(t_0,u_0)f_{uu}(t_0,u_o)\\+f_t(t_0,u_0)f_u(t_0,u_0)+f(t_0,u_0)f^2(t_0,u_0),\tag{6}
$$

令：

$$
\phi(t,u(t),h)=\sum^p_{i=1}\frac{h^{j=1}}{j!}\frac{d^{j-1}}{dt^{j-1}}f(t,u(t))\tag{7}
$$

则可将 $(4)$ 改写为：

$$
u(t_0+h)-u(t_0)=h\phi(t_0,h(t_0),h)+O(h^{p+1})\tag{8}
$$

舍去余项 $O(h^{p+1})$，建立数值方法：

$$
u_1-u_0=h\phi(t_0,u-0,h)
$$

一般说来，若已知 $u_n$ ，则：

$$
u_{n+1}-u_n=h\phi(t_n,u_n,h),\quad n=0,1,\cdots\tag{9}
$$

这是一个单步法，局部截断误差为 $O(h^{p+1})$

将初值问题写成积分形式：

$$
u(t+h)-u(t)=\int^{t+h}_tf(\tau,u(\tau))\,d\tau,\quad u(t_0)=u_0\tag{10}
$$

若有一确定的函数 $\phi(t,u,h)$ ，使初值问题的任意解 $u(t)$ 满足：

$$
u(t+h)-u(t)=h\phi(t,u(t),h)+O(h^{p+1})\tag{11}
$$

其中 $p\geq 1$ 是使得 $(11)$ 成立的**最大整数**，则称算法

$$
u_{n+1}=u_n+h\phi(t_n,u_n,h),\quad n=0,1,\cdots,T/h\tag{12}
$$

为 ==$p$ 阶单步法==
