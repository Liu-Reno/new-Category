# Introduction

范畴论$(\text{Category theory})$起源于这样一种观察:即数学系统中的很多性质可以使用箭头图表的方式进行统一表示与简化.每个箭头$(\text{arrow})f : X \to Y$代表一个函数,即一个集合$X$,一个集合$Y$以及一个规则$x \mapsto fx$,该规则为每个元素$x \in X$赋予一个元素$fx \in Y$与之对应(只要是可能的,我们就省去括号,只写$fx$而不写$f(x)$).集合与函数的典型图解是

![image-20230919182504238](S:/Math%20Note/new-Category/Image/Introduction/1.png)

当$h = g \circ f$时我们称上述图表是交换的,其中$g \circ f$是常见的复合函数$g \circ f : X\to Z$定义为$x \mapsto g(f(x))$.同样的图表也可以应用于其他的数学背景;因此,在所有拓扑空间的"范畴"中,字母$X,Y$和$Z$代表拓扑空间,$f,g$和$h$代表连续映射.同样地,在所有群的"范畴"中,$X,Y$和$Z$代表群,$f,g$和$h$代表群同态.

数学结构的许多性质都可以使用图表的泛性质$(\text{universal properties})$来表述.考虑两个集合$X,Y$之间的笛卡尔积$(\text{Cartesian product})$,它由所有$x \in X$且$y \in Y$的有序对$<x,y>$组成.在其"轴"$X$和$Y$上的射影为$<x,y> \mapsto x, <x,y>\mapsto y$是一个函数$p : X \times Y \to X$,$q: X \times Y \to Y$.任何从第三个集合出发的函数$h : W \to X \times Y$是由其复合$p \circ h$以及$q \circ h$唯一确定的.相反,给定下述图表中的$W$以及两个函数$f,g$,就只有唯一一个函数$h$使得图表交换,即对于每个$w \in W$有$hw = <fw,gw>$

![image-20230919183706957](S:/Math%20Note/new-Category/Image/Introduction/2.png)

因此,给定$X$和$Y$,$<p,q>$在某个集合到$X,Y$的函数对中是"泛"的,因为任何其他这样的函数对$<f,g>$都可以唯一的(通过$h$)由有序对$<p,q>$所确定.这个性质唯一地描述了$X \times Y$的笛卡尔积(直到双射);同样地图,在拓扑空间范畴或群范畴中,唯一的描述了空间的积或群的直积.

伴随性是这些泛性质的另一种表达方式.若我们将所有$f : W \to X$的函数所构成的集合写为$\text{Hom}(W,X)$,以及所有函数对$f : U \to X$以及$g : V\to Y$所构成的集合记为$\text{Hom}(<U,V>,<X,Y>)$那么上图所示的对应关系$h \mapsto <ph,qh> = <f,g>$是一个双射
$$
\text{Hom}(W,X \times Y)\cong \text{Hom}(<W,W>,<X,Y>)
$$
这种双射是"自然的$(\text{natural})$"(稍后将更加精确的说明)因为它是以"同样的方式"所有的集合$W$以及所有的集合对$<X,Y>$(当解释为拓扑空间或者群时,它同样是"自然的").这个自然的双射涉及到集合上的两个结构:

* 结构$W \mapsto <W,W>$将每个集合发送到对角对$\Delta W = <W,W>$上
* 结构$<X,Y> \mapsto X\times Y$将每对集合发送到它的笛卡尔积上.

给定上面的双射,我们说结构$X \times Y$是结构$\Delta$的右伴随$\text{(right adjoint)}$.而结构$\Delta$是这个乘积的左伴随.我们将发现伴随概念在数学中随处可见.



结构"笛卡尔积"被称为是函子$(\text{functor})$,因为它适用于集合以及集合之间的函数:对于两个函数$k : X \to X'$以及$l : Y \to Y'$有一个函数$k \times l$作为它们的笛卡尔积
$$
k \times l :X \times Y \to X' \times Y' , <x,y> \mapsto <kx,ly>
$$
同样可以注意到一个单点集$1 = \{0\}$作为一个在"笛卡尔积"下的运算是恒等的.考虑双射
$$
\begin{equation}
1 \times X \xrightarrow{\lambda}X \xleftarrow{\varrho}X \times 1
\end{equation}
$$
由$\lambda<0,x> = x$与$\varrho <x,0> = x$给出

在范畴理论中,幺半群$(\text{monoid})$(一个有单位元的半群$(\text{semigroup})$)概念起着重要作用.一个幺半群$M$可以被描述为一个集合$M$与两个函数
$$
\begin{equation}
\mu : M \times M \to M, \eta :1\to M
\end{equation}
$$
使得以下两个图表在$\mu$和$\eta$下交换

![image-20230919192425258](S:/Math%20Note/new-Category/Image/Introduction/3.png)

此处$1 \times \mu$中的$1$是一个恒等映射$M\to M$,而$1 \times M$中的$1$是一个单点集$1 = \{0\}$,当$(1)$所示的$\lambda$和$\varrho$都为双射时,就说这些图交换意味着以下组合是相等的:
$$
\mu \circ (1 \times \mu) = \mu \circ (\mu \times 1),\mu \circ (\eta \times 1) = \lambda, \mu \circ(1 \times \eta) = \varrho
$$
这些图可以用元素重写,将函数$\mu$(视)为一个乘积$\mu (x,y) = xy$对于$x,y \in M$,并且将单点集$1 = \{0\}$上的函数$\eta$替换为其唯一值$\eta(0) = u \in M$.上面的图表就变为了

![image-20230919194023982](S:/Math%20Note/new-Category/Image/Introduction/4.png)

这个就是我们所熟悉的幺半群上的公理系统,乘法满足结合律且元素$u$是左右侧的单位元.

这表明,相反的,代数恒等式可以使用交换图表来表示.同样的过程也可以运用到其他的角色上.比如将群描述为一个带有函数$\zeta : M \to M$(即函数$x \mapsto x^{-1}$)的幺半群使得下述图表交换.

![image-20230919194651924](S:/Math%20Note/new-Category/Image/Introduction/5.png)

此处$\delta : M \to M\times M$是一个对角函数$x \mapsto <x,x>$.而未命名的箭头$M \to 1 = \{0\}$是一个显然(且唯一的)$M$到单点集$1 = \{0\}$上的函数.正如右图所示,这幅图确实说明了$\zeta$给每个元素$x \in M$分配了一个右逆$x^{-1}$.

在这种交换图中,由箭头$\mu,\eta$以及$\zeta$所表示的群定义并没有明确的提到群元素,因此也适用于其他情况.如果字母$M$代表一个拓扑空间(而不仅仅是一个集合),箭头表示连续映射(不仅仅是函数),那么图$(3)$和$(4)$定义了一个拓扑群 $-$ 因为它们规定了$M$是一个具有代数运算$\mu$的拓扑空间,它是连续的(同时在它的参数中)且具有连续的右逆,都满足通常使用的群公理.此外,若字母$M$代表一个可微流形($C^{\infty}$类),而$1$为单点流形,那么箭头$\mu,\eta$以及$\zeta$是流形的光滑映射.那么图$(3)$和$(4)$就成为了$\text{Lie}$群的定义.因此在集合,拓扑空间以及可微流形的各自范畴之内,群,拓扑群以及$\text{Lie}$群都可以被描述为"图解"群.

范畴中群的这个定义(对于$(4)$的逆)依赖于对角映射$\delta : M \to M \times M$到笛卡尔积$M \times M$上.这个幺半群定义可以变得更宽泛,因为$M \times M$中的笛卡尔积$\times$可以被任意一个其他使两个对象满足结合律的运算$\square$所取代,并且在同构$(1)$所规定的意义上具有单位$1$.我们将系统中的幺半群记为$(C,\square,1)$,其中$C$是一个范畴,$\square$是一个运算以及$1$是它的单位.

例如,考虑一个$(\bold{Ab},\otimes,\Z)$上的幺半群$M$,其中$\bold{Ab}$是一个$\text{Abel}$群构成的范畴,$\times$被通常的阿贝尔群张量积所取代,$1$被整数加群$\Z$所取代,则$(1)$可以被立即替换为我们所熟悉的同构
$$
\Z\otimes X \cong X \cong X \otimes \Z,X\text{为 Abel群}
$$
那么在$(\bold{Ab},\otimes,\Z)$上的幺半群$M$,我们称它是一个环.对于给定态射$\mu : M \otimes M \to M$,根据$\otimes$的定义,这只是一个函数$M\times M \to M$,称其为乘法,它是具有双线性的;即在左右两侧的加法上都满足分配律,而$\text{Abel}$群中的态射$\eta : \Z \to M$则完全由$M$中的一个元素所决定.交换图$(3)$现在就断言了在$\text{Abel}$群中乘法$\mu$是满足结合律的且$u$具有左右单位,换句话说,$M$确实是一个环.(幺元 = 单位)

代数系统中的(同)态也可以使用图表来描述,若$<M,\mu,\eta>$以及$<M',\mu',\eta'>$是两个幺半群,每一个都可以用上述的图表来描述,那么从第一个(幺半群)到第二个(幺半群)的态射可以被定义为使下图交换的函数$f : M \to M'$

![image-20230919203324457](S:/Math%20Note/new-Category/Image/Introduction/6.png)

在元素方面,它断言$f(xy) = (fx)(fy)$以及$fu = u'$其中$u$和$u'$均为单位.因此同态通常只是一个保持复合以及单位的函数.若$M$和$M'$为$(\bold{Ab},\otimes,\Z)$的幺半群,也就是环,那么此处的定义就是一个环上的态射(保持单位).

最后,一个幺半群$<M,\mu,\eta>$在集合$S$上的作用$(\text{action})$被定义为使得下图交换的函数$v : M \times S \to S$

![image-20230919203718355](S:/Math%20Note/new-Category/Image/Introduction/7.png)

如果我们用$v(x,s) = x\cdot s$来表示幺半群元素$x$作用于元素$s \in S$的结果,这些图也就说明了
$$
x \cdot (y \cdot s) = (xy)\cdot s , u \cdot s = s
$$
对于所有的$x,y \in M$以及所有的$s \in S$成立.这些是幺半群作用于集合上的常用条件,尤其在群作为一组变换作用于集合的情况下更为常见.若我们从集合的范畴转移到拓扑空间中的范畴,我们就得到了一个拓扑幺半群$M$到拓扑空间$S$的连续作用,若我们将$<M,\mu,\eta>$作为$(\bold{Ab},\otimes,\Z)$的幺半群,那么$M$对于一个$\bold{Ab}$中的对象$S$的作用也就是环$M$上的左模$_MS$.