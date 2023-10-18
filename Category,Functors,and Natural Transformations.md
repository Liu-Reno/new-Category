# Category,Functors,and Natural Transformations

## $\S 1\,Axioms\,\, fo\,\, Categories$

首先,我们不使用集合论,而是直接使用公理来描述范畴,称它们为"元范畴".实际上,我们将从一个更简单的概念开始,一个(元)图

一个元图($\text{metagraph}$)由对象$a,b,c,\cdots$,箭头$f,g,h,\cdots,$以及两种如下所示的操作组成:

$Domain$(定义域),它给每个箭头$f$分配一个$\text{object }a = \text{dom }f$;

$Codomian$(值域),它给每个箭头$f$分配一个$\text{object }b = \text{dom }f$;

对$f$的这些操作最好通过将$f$表示为从其定义域(或"源头"$\text{source}$)出发并以其值域(或"目标"$\text{target}$)结束的真正的箭头来表示.
$$
f: a \to b \text{或} a \xrightarrow{f}b 
$$
一个有限图可以很容易地被表述出来:即$\cdot \to \cdot \to \cdot$或$\cdot \rightrightarrows \cdot$.



元范畴是具有两个附加操作的元图

* 恒等映射($\text{Identity}$),它为每个对象$a$赋值一个箭头$\text{id}_a = 1_a : a\to a$;

* 复合($\text{Composition}$),它给每一对箭头$<g,f>$分配$\text{dom }g = \text{cod }f$,箭头$g \circ f: \text{dom }f \to \text{cod }g$称为它们的合成.这个操作可以被下述交换图表所表示

  ![image-20230920133622713](./Image/Category,Functors,and%20Natural%20Transformations/1.png)

  它展示了所有涉及的定义域以及值域

  

元范畴中的这些操作遵循以下两个公理

* 结合律($\text{Associativity}$):对于构造($\text{configuration}$)中给定的对象以及箭头
  $$
  a\xrightarrow{f}b\xrightarrow{g}c\xrightarrow{k}d
  $$
  总是有下述等式成立
  $$
  \begin{equation}
  k \circ (g \circ f) = (k \circ g)\circ f
  \end{equation}
  $$
  这个公理断言了结合律适用于任何有意义的复合运算(即$(1)$中两侧所定义的运算),这个方程可以图解地展示为下面的图表交换.

  <img src="./Image/Category,Functors,and%20Natural%20Transformations/2.png" alt="image-20230920134433194" style="zoom:50%;" />

* 单位律($\text{Unit law}$):对于所有箭头$f : a \to b$与$g : b \to c$与恒等箭头$1_b$的复合为
  $$
  \begin{equation}
  1_b \circ f = f \text{以及} g \circ 1_b = g
  \end{equation}
  $$
  这个公理断言,只要有意义,每个对象$b$的恒等箭头$1_b$也可以充当一个复合操作的恒等元.

  $(2)$可以被图解地表示为以下的交换图表.

  ![image-20230920134934903](./Image/Category,Functors,and%20Natural%20Transformations/3.png)

我们将使用许多这样的由顶点(由一个范畴中的对象所标记)和边(由同一范畴中的箭头所标记)的图表.若每一对顶点$c$和$c'$,从$c$到$c'$的任意两条由有向边所组成的路径(经过箭头组合后)等同于一个从$c$到$c'$的箭头时,我们称这样的图表是可交换的.

范畴方法的有效性在很大程度上取决于这样一个事实:这种图表在每种情况下都可以生动地展示其上箭头的作用.

若$b$为元范畴$C$的任意对象,则其对应的恒等箭头由$(2)$唯一确定.因此,有时将恒等箭头$1_b$表示为$b$自身,记为$b : b \to b$.因此,方便起见,$1_b = b = \text{id}_b$.

原范畴就是满足上述公理的任何解释.一个例子是集合的元范畴,它的对象均为集合,箭头就是函数,通常表示为恒等函数以及具有常规结构的函数的复合.此处的"函数"指的是具有特定定义域以及值域的函数.因此,一个函数$f : X \to Y$由一个集合$X$(它的定义域),集合$Y$(它的值域)以及一个规则$x \mapsto fx$(即一个合适的有序对集合$<x,fx>$)这条规则给每个元素$x \in X$赋一个值$fx \in Y$.方便起见.这些值被写为$fx,f_x$或$f(x)$.举个例子,对于任意集合$S$,对于任意的$s \in S$赋值$s \mapsto s$表示恒等函数$1_S : S\to S$.若$S$是$Y$的一个子集,赋值函数$s \mapsto s$表示一个包含或者插入函数$S \to Y$,在$S \neq Y$时这两个函数是不同的.给定函数$f : X \to Y$以及$g : Y \to Z$.其上的复合$g \circ f:X\to Z$定义为$(g\circ f)x = g(fx)$对于所有的$x \in X$成立.观察到$g \circ f$首先使用$f$函数,而后调用$g$函数 $-$ 按照惯例,每个函数$f$都写在其参数的左边.然而,有很多作者的习惯是反过来放置.

总结一下,所有集合的元范畴的对象就是所有的集合,箭头是所有具有常规结构的函数.所有群的元范畴也可以得到类似的描述:对象为所有的群$G,H,K$;箭头是所有从集合$G$到集合$H$的群同态$f : G \to H$.此外还有种类繁多的元范畴:以所有连续函数为箭头的所有拓扑空间;所有具有相同空间的紧$\text{Hausdorff}$空间;所有环空间以及它们之间的态射等等.元范畴中任意箭头常常被称为其上的态射($\text{morphism}$).

因为元范畴的对象完全对应于其恒等箭头.因此从技术上来讲,抛弃对象而只处理箭头是可行的.一个只有箭头的元范畴的资料由箭头,某些有序对$<g,f>$(称为箭头的合成对)以及一个可以对于合成对$<g,f>$赋值为其合成箭头$g \circ f$的操作组成.我们称"$g,f$是被定义的"为"$<g,f>$是合成对".

有了上述资料,我们就可以定义$C$的一个恒等映射$u$,它是一个箭头使得当复合$f \circ u$有定义时,$f \circ u = f$以及当复合$u \circ g$有定义时,$u \circ g = g$.此外,我们要求资料需要满足以下几条公理.

1. 复合$(k \circ g)\circ f$被定义当且仅当复合$k \circ (g \circ f)$被定义(即只要定义一个另一个就是有定义的).当其中一个被定义时,它们两个就是相等的(这个三元复合被记为$kgf$)
2. 三元复合$kgf$是在复合$kg$以及复合$gf$都被定义时才有定义的.
3. 对于$C$中的每个箭头$g$都存在$C$中的恒等箭头$u$以及$u'$使得$u' \circ g$以及$g \circ u$被定义.

根据前文给出的恒等箭头的明确定义,可以发现最后一个公理是一个强而有力的公理;它表明$u'$和$u$在3.下是唯一的,并且它为每个箭头$g$都赋予了一个定义域$u'$和值域$u$.这三条公理与前面的两条公理是等价的.更准确的说,给定一个具有对象以及箭头的元范畴,它的全体箭头(在给定了复合的前提下)满足"只有箭头"版本的公理;反过来,当我们考虑一个以前文定义的恒等箭头为对象的"只有箭头"的元范畴,它也满足"具有对象和箭头"版本的公理(留作习题).

## $\S 2\,Categories$

范畴(有别于元范畴)是指集合论中对于范畴公理的任何解释.详细说来,一个有向图(也称为一个$\text{diagram scheme}$)是对象集$O$,箭头集$A$以及两个函数
$$
\begin{equation}
a \overset{\text{dom}}{\underset{\text{cod}}{\rightrightarrows}} b 
\tag{1}
\end{equation}
$$
在这个图中,可组合的箭头对的集合是集合
$$
A \times_O A = \{<g,f>: g,f \in A \text{且} \text{dom } g = \text{cod } f\}
$$
称为"$O$的乘积".



一个范畴是指带有两个附加函数的图左侧称为恒等态射,右侧称为复合(简写为$gf$),使得
$$
\begin{equation}
\begin{array}
\\O &\xrightarrow{\text{id}}&A, \quad A \times_O A &\xrightarrow{\circ}&A,
\\c &\longmapsto& \text{id}_c ,  \quad <g,f> &\longmapsto& g \circ f
\end{array}
\tag{2}
\end{equation}
$$
对于所有对象$a \in O$以及所有箭头的合成对$<g,f> \in A \times_O A$都满足
$$
\begin{equation}
\text{dom}(\text{id } a) = a = \text{cod}(\text{id }a), \text{dom}(g \circ f) = \text{dom }f, \text{cod}(g \circ f) = \text{cod }g
\tag{3}
\end{equation}
$$
此外满足结合律以及单位律公理成立.

在处理范畴$C$时,我们经常省略字母$A$以及$O$,并且写
$$
\begin{equation}
c \in C , f\text{ in }C
\tag{4}
\end{equation}
$$
来表示"$c$是$C$中的一个对象"以及"$f$是$C$中的一个箭头".我们也用
$$
\begin{equation}
\text{Hom}(b,c) = \{f: f \text{ in }C,\text{dom }f = b ,\text{cod }f = c\}
\tag{5}
\end{equation}
$$
表示从$b$到$c$的所有箭头所组成的集合.

范畴可以直接根据作用于这些"$\text{Hom}$集"的复合来定义($\S 8$);我们不会遵循这个习惯,因为我们并不把重点放在集合范畴(一个相当特殊的范畴)上,而是放在公理,箭头以及箭头所构成的图上.稍后,我们将观察到我们对于范畴的定义等同于说(在引言所述的一般意义上)一个范畴是以$\times_O$为乘积的幺半群.接下来,我们考虑一些例子.

$\bold{0}$是一个空范畴(没有对象,没有箭头);

$\bold{1}$ $\dot{\circlearrowright}$是只有一个对象$\cdot$及其恒等态射$\circlearrowright$的范畴;

$\bold{2}$ $\dot{\circlearrowright}^{\rightarrow}\dot{\circlearrowright}$是有两个对象$a,b$以及只有一个不为恒等态射的箭头$a \to b$的范畴;

$\bold3$ 是有三个对象且其非恒等态射的箭头可以被编为一个三角形<img src="./Image/Category,Functors,and%20Natural%20Transformations/4.png" alt="image-20230920164706786" style="zoom:33%;" />的范畴;

$\downdownarrows$是有两个对象$a,b$且有两个不是恒等态射的箭头$a \rightrightarrows b$的范畴,我们称两个这样的箭头为平行箭头.

在上述每种情况下,复合只有一种可能的定义.

| 常见范畴                             | 解释                                                         |
| ------------------------------------ | :----------------------------------------------------------- |
| $Discrete \,\, Categories$(离散范畴) | 当一个范畴中每一个箭头都是恒等态射时,称其为离散的.每个集合$X$是一个离散范畴的对象集(只需要对于$x \in X$添加一个恒等态射$x \to x$就可以得到一个离散范畴),并且每一个离散范畴都是由其对象集所确定的,因此离散范畴是集合 |
| $Monoid$(幺半群)                     | 一个幺半群是一个只有一个对象的范畴,因此每个幺半群都由其所有箭头(通过恒等态射以及箭头的合成)所组成的集合所唯一确定.由于任意两个箭头都存在一个合成,那么一个幺半群可以被描述为一个集合$M$,其上有一个满足结合律的二元运算$M \times M \to M$(实际上就为态射的合成).且$M$上有幺元(恒等态射 = 单位) |
| $Groups$(群)                         | 一个群是一个只有一个对象的范畴,其中每个箭头都对于组合有一个(双向的)逆元 |
| $Matrices$(矩阵)                     | 对于每个交换环$K$,所有元素取自$K$的矩形矩阵(量子力学中貌似有不为矩形的矩阵)所构成的集合$\bold{Matr_K}$是一个范畴;其对象是全体正整数$m,n,\cdots$并且将每个$m \times n$矩阵$A$视为一个箭头$n \to m$,因而复合就是通常的矩阵乘积 |
| $Sets$(集合)                         | 如果$V$为任意集合所构成的集合,我们取$\bold{Ens_V}$为对象为$V$中所有集合$X \in V$,箭头为所有的函数$f : X\to Y$的范畴,其复合就是函数的复合运算.使用$\bold{Ens}$表示任何一种这样的范畴 |
| $Preorders$(预序)                    | 我们所说的预序是指一个范畴$P$,其上给定对象$p$和$p'$最多存在一个箭头$p \to p'$.对于任意预序$P$,在$P$的对象上定义一个二元关系$\leq$,$p\leq p'$当且仅当$P$中有一个箭头$p \to p'$.这个二元运算是自反的(因为每个$p$都有一个恒等态射$p \to p$)并且是传递的(因为箭头可以组合).因此,预序是一个集合(对象集)上配备了一个自反和传递的二元关系.相反,任何具有这样关系的集合$P$决定了一个预序,其中箭头$p \to p'$就是那些$p\leq p'$所对应的有序对$<p,p'>$由于这个关系是传递的因此有唯一一种方式组合这些箭头;因为其是自反的,因此需要恒等态射. |
| 预序注                               | 预序包含了偏序(预序加上一条反对称公理)以及线序(全序,对于预序中任意两个元素$p,p'$都有$p\leq p'$或$p' \leq p$) |
| $Ordinal\,\, Numbers$(序数)          | 我们把序数$n$视为前面的所有序数所构成的集合,即$n = \{0,1,\cdots ,n-1\}$;特别地,$0$是一个空集,而第一个无穷序数为$w = \{0,1,2,\cdots\}$.每一个序数$n$都是线序的,因此其构成了一个范畴(预序).举个例子,前文所述的范畴$\bold{1}$,$\bold2$以及$\bold3$就是属于(线序)序数$1,2,3$的预序.另一个例子就是线序$w$.作为一个范畴$0 \to 1\to 2\to \cdots$,它由箭头和它们的复合组成,且每个对象都有一个恒等态射. |
| $\Delta$                             | $\Delta$是一个对象为全体有限序数且箭头$f : m \to n$为全体保序映射(保持序结构不变的映射,对$m$中的$i \leq j$在$n$中有$f_i \leq f_j$)这个范畴$\Delta$,有时也称为单纯范畴($\text{simplicial category}$)在$\text{Chapter VII}$中扮演重要角色 |
| $\bold{Finord = Set}_w$              | 一个对象为全体有限序数,箭头$f : m \to n$为全体$m$到$n$的函数的范畴.这本质上是所有有限集合的范畴,对于每个有限基数$n$都对应着一个有限集合$n$ |



$Large \,\, Categories$. 除所有集合(这不是一个集合)的元范畴之外,我们需要一个切实存在的范畴$\bold{Set}$,这个范畴是所有小($\text{small}$)集合的范畴:我们先假设有这么一个足够大的集合$U$,将其称为"宇宙($\text{universe}$)",然后将集合$x$是宇宙中的成员,那么它就足够"小".接下来取$\bold{Set}$为集合$U$(所有小集合的集合)为对象集,用箭头表示一个小集合到另一个小集合的所有函数.通过这种方法(详见$\S 7$)我们构造出了所有熟悉的大范畴($\text{Large Categories}$)

| 大范畴名称                         | 解释                                                         |
| ---------------------------------- | ------------------------------------------------------------ |
| $\bold{Set}$(集合范畴)             | 对象:全体小集合,箭头:它们之间的所有函数                      |
| $\bold{Set}_*$(带基点的集合范畴)   | 对象:每一个小集合并且每个小集合都有一个选定的基点;箭头:保持基点的函数 |
| $\bold{Ens}$                       | (带变量)集合$V$内所有集合与函数的范畴                        |
| $\bold{Cat}$(范畴的范畴)           | 对象:全体小范畴;箭头:全体函子$\S 3$                          |
| $\bold{Mon}$(幺半群范畴)           | 对象:全体小幺半群;箭头:幺半群之间的态射                      |
| $\bold{Grp}$(群范畴)               | 对象:全体小群;箭头:群之间的态射                              |
| $\bold{Ab}$($\text{Abel}$群范畴)   | 对象:全体小(可加)$\text{Abel}$群;箭头:它们之间的态射         |
| $\bold{Rng}$(环范畴)               | 对象:全体小环;箭头:环态射(保持单位)                          |
| $\bold{CRng}$(交换环范畴)          | 对象:全体小交换环;箭头:环态射                                |
| $R-\bold{Mod}$(左$R$模范畴)        | 对象:环$R$上的全体小左$R$模;箭头:线性映射                    |
| $\bold{Mod}-R$(右$R$模范畴)        | 类似可得                                                     |
| $K - \bold{Mod}$(交换环上的模范畴) | 对象:交换环$K$上的全体小右$R$模                              |
| $\bold{Top}$(拓扑范畴)             | 对象:全体小拓扑空间;箭头:连续映射                            |
| $\bold{hTop}$(同伦范畴)            | 对象:全体小拓扑空间;箭头:连续函数的同伦类                    |
| $\bold{Top}_*$(基点拓扑范畴)       | 对象:具有选定基点的拓扑空间;箭头:保留基点的连续映射          |

特定的范畴(比如这些)总是喜欢用粗体字来表示,也有作者喜欢使用大写字母来表示类别.

## $\S3\,Functors$

函子($\text{Functors}$)是范畴之间的态射.具体来说,对于范畴$C$与$B$,一个函子$T: C \to B$的定义域$C$和值域$B$由两个适当且相关(两个指对象和箭头两个集合,适当代表有定义,相关则代表互相关联)的函数组成:对象函数($\text{object function}$)$T$,它给每个范畴$C$中的对象$c$赋予一个$B$中的对象$Tc$与之对应;箭头函数($\text{arrow function}$,也写为$T$)给$C$中的箭头$f: c \to c'$赋予一个$B$中的箭头$Tf:Tc \to Tc'$与之对应,使得
$$
\begin{equation}
\tag{1}
T(1_c) = 1_{Tc}, T(g \circ f) = Tg \circ Tf
\end{equation}
$$
后者是在复合运算$g \circ f$在$C$中有定义时成立的.一个函子,就像一个范畴,它也可以用"只有箭头"的方式来描述:它是一个函数$T$将$C$中的箭头$f$映射到$B$中的箭头$Tf$上,它将$C$上的恒等映射映射到$B$的恒等映射上以及将$C$中的组合对$<g,f>$映射到$B$中的组合对$<Tg,Tf>$上,且有$Tg \circ Tf = T(g \circ f)$.

一个简单的例子是幂集函子$\mathscr{P}: \bold{Set} \to \bold{Set}$.它的目标函数赋给每个集合$X$通常的幂集$\mathscr{P}X$(其元素是全体的子集$S \subset X$).它的箭头函数赋予每个$f : X \to Y$一个映射$\mathscr{P}f : \mathscr{P}X \to \mathscr{P}Y$将每个$S \subset X$映射到其像$fX \in Y$上.因为同时有$\mathscr{P}(1_X) = 1_{\mathscr{P}X}$且$\mathscr{P}(g \circ f) = \mathscr{P}g \circ \mathscr{P}f$.这清楚地定义了一个函子$\mathscr{P}: \bold{Set} \to \bold{Set}$.

函子首先在代数拓扑中被明确的认识,当几何性质被代数不变量描述时,它们自然就出现了.例如,给定维数$n$($n$为自然数)的奇异同调赋值一个$\text{Abel}$群$H_n(X)$,即$X$的$n$次同调群,并为空间上的每个连续映射$f : X \to Y$赋值一个相应的群同态$H_n(f):H_n(X)\to H_n(Y)$,通过这个方式使得$H_n$变成了一个函子$\bold{Top}\to \bold{Ab}$.更具体的例子是:若$X = Y = S^1$为圆,$H_1(S^1) = \Z$,所以群同态$H_1 (f) : \Z \to \Z$被一个整数$d$($1$的像)所决定;这个整数是连续映射$f : S^1 \to S^1$通常的"度($\text{degree}$)".在这种情况以及一般情况下,同伦映射$f,g : X \to Y$产生相同的同态$H_n(X)\to H_n(Y)$,因此$H_n$实际上可以被看做是一个函子$\bold{Toph \to Grp}$定义在一个同伦范畴上.关于同调的$\text{Elienberg-Steenrod}$定理,从对于每一个自然数$n$,$H_n$是$\bold{Toph}$上的函子;而后我们继续讨论这些函子的附加性质.最近发展的超同调($\text{extraordinary homology}$)以及上同调($\text{cohomology}$)理论也是$\bold{Toph}$上的函子.空间$X$上的同伦群$\pi_n(X)$也可以视为函子;因为它们依赖于$X$中基点的选择,所以它们为$\bold{Top_*}\to \bold{Grp}$的函子.在拓扑中使用函子的主要思想是$H_n$或$\pi_n$不仅仅将拓扑空间代数化,还将它们之间的连续映射进行了代数化.

函子在代数中是自然出现的.对于任意的可交换环$K$,所有的元素完全取自$K$中的$n \times n$非奇异矩阵(即可逆矩阵)所构成的集合是一个一般线性群$\text{GL}_n(K)$.此外,环的每一个同态$f : K\to K'$也就明显的产生了一个群同态$\text{GL}_n f : \text{GL}_n(K) \to \text{GL}_n(K')$.这些资料为每个自然数定义了一个函子$\text{GL}_n: \bold{CRng} \to \bold{Grp}$.对于任何群$G$,所有换位子$xyx^{-1}y^{-1}(x,y \in G)$的乘积构成了一个集合$[G,G]$,它是集合$G$的正规子群,称为导出子群.因为任意群同态$G \to H$都将一个换位子转化为另一个换位子($H$上的换位子).因此,若我们考虑$G \mapsto [G,G]$,它就定义了一个明显的函子$\bold{Grp} \to \bold{Grp}$,而$G \mapsto G/[G,G]$也定义了一个函子$\bold{Grp} \to \bold{Ab}$,即换位子函子.然而,请注意$G$的中心$Z(G)$(对于所有的$a \in G$都满足$ax = xa$的$x \in G$所构成的集合)并不能自然地定义一个函子$\bold{Grp}\to \bold{Grp}$,因为同态$G \to H$可能将$G$中心的一个元素带到一个不在$H$中心的元素上.(考虑群同态$G \to H' \leq H$,其中$G \to H'$为同构).

简单地"忘记($\text{forgets}$)"一个代数对象的部分或全部结构的函子称为遗忘函子($\text{forgetful functor}$或$\text{underlying functor}$).因此,遗忘函子$U : \bold{Grp} \to \bold{Set}$将每一个群$G$变为一个包含其内所有元素的集合$UG$(忘记了乘法,也就忘记了群结构),并将相同的函数$f$赋给群范畴上的每一个态射$f : G\to G'$,仅仅将其视为一个集合上的函数.遗忘函子$U : \bold{Rng} \to \bold{Ab}$将$R$变为一个加法群.并且把环同态变为保持加法的群同态.

函子是可以组合的.为了明确这一点,给定介于范畴$A,B,C$的函子
$$
C \xrightarrow{T}B \xrightarrow{S}A
$$
在对象$c$与箭头$f$上的复合函数
$$
c\mapsto S(Tc)\quad f \mapsto S(Tf)
$$
定义了一个函子$S \circ T : C \to A$,称为一个(依照这个顺序)$S$和$T$的复合.这个复合是满足结合律的.对于每一个范畴$B$都有一个恒等函子$\text{id}_B : B \to B$,它作为这个复合的一个恒等映射.因此,我们可以考虑所有范畴的元范畴:它的对象是全体范畴,箭头为全体具有上述组合的函子.同样,我们可以构成所有小范畴的范畴$\bold{Cat}$-它不是所有范畴的范畴.

范畴上的同构($\text{isomorphism}$)$T: C\to B$是一个从$C$到$B$的双射(无论是对象还是箭头上都是双射)的函子.此外,等价的有一个函子$T: C \to B$是一个同构当且仅当存在一个函子$S: B \to C$使得无论是$S \circ T$还是$T \circ S$都是恒等函子;那么$S$就是$T$的一个双边逆($\text{two-sided inverse}$)$S = T^{-1}$.

但是在实际使用中,我们一般用一种比同构弱的多的特性.

若对于$C$中的每一对对象$c,c'$以及$B$中的每一个箭头$g:Tc \to Tc'$都存在一个$C$中的箭头$f : c \to c'$使得$g = Tf$,那么这个函子$T : C \to B$被称为是全($\text{full}$)的,显然,两个全函子的复合还是一个全函子.

若对于$C$中的每一对对象$c,c'$以及每一对平行箭头$f ,f' : c \to c'$等式$Tf_1 = Tf_2 : Tc \to Tc'$可以推出$f_1 = f_2$,那么这个函子$T : C \to B$被称为是忠实($\text{faithful}$)的,同样,忠实函子的复合函子也是忠实的.例如,遗忘函子$\bold{Grp} \to \bold{Set}$是忠实函子但是不是满函子,并且不是对象上的双射.

这两条性质可以使用$\text{Hom}$集代替(见$(2.5)$)给定$C$中的一对对象$c,c'\in C$,箭头上的函数$T: C \to B$给每一个$f : c \to c'$赋予了一个箭头$Tf : Tc \to Tc'$从而我们定义了一个函数
$$
T_{c,c'}: \text{Hom}(c,c') \to \text{Hom}(Tc,Tc'),f \mapsto Tf
$$
那么当每一个这样的函数都是满射时,$T$是全函子,并且当每一个这样的函数都是单射时,$T$是忠实函子.对于一个全忠实(又是全函子,又是忠实函子)函子,每一个这样的函数都是一个双射,但是这并不意味着这样的函子就是范畴的同构,因为$B$的对象可能不在$T$的像中.

范畴$C$的一个子范畴$S$是一些对象和箭头的集合,它不仅仅包括了每一个箭头$f$还包括了对象$\text{dom }f$和$\text{cod }f$(每个对象都被视为它恒等映射的箭头$1_s$)以及它们箭头的组合对$s \to s' \to s''$的组合.这些条件确保了这些对象以及箭头本身构成了一个范畴$S$.此外,嵌入(包含)映射$S \to C$是一个函子,即包含函子,它将$S$的每一个对象和每一个箭头发送到$C$中它的位置上.这个包含函子是自动忠实的.当包含函子$S \to C$是满的时候,我们说$S$是$C$中的一个全子范畴($\text{full subcategory}$).一个给定的$C$中的全子范畴由其对象的集合来确定,因为任意$C$中两个对象$s,s'$之间的箭头为所有态射$s \to s'$.举个例子,所有有限集合的范畴$\bold{Set}_f$是范畴$\bold{Set}$的一个全子范畴

### Exercise

1. 说明如何将下列每一种结构视为一个函子:整环的分式域,$\text{Lie}$群的$\text{Lie}$代数.

   分式域定义:

   给定整环$R$,记$R$中没有乘法逆元的元素所构成的集合记为$S$,对任意的$s \in S$,定义新元素$s^{-1}$,其运算规则由$s \cdot s^{-1} = 1_R$所确定.把所有$s^{-1}$所构成的集合记为$S'$,考虑$R \cup S'$由加法与乘法所生成的集合$<R \cup S'>$这时称其为$R$的分式域,记为$\text{Frac}(R)$其内元素记为$[r,s]$.

   考虑函数$\text{Frac}: R \to \text{Frac}(R)$.

   考虑两个整环$R,R'$之间的环同态$f: R \to R'$.由于$\text{Frac}(R)$中的元素本质上均来源于$R$.

   由于$f$为同态,因此$f(ss') = f(s)f(s')$对于所有的$s,s' \in R$成立.

   因此考虑$s' \in S'$由于$f(ss') = f(1_R) = 1_{R'}$因而我们可以扩充得到$f(s')\in \text{Frac}(R')$.

   那么考虑$\text{Frac }f : \text{Frac}(R) \to \text{Frac}(R')$.

   考虑$\varphi : \text{Frac }R \to \text{Frac } R'$,它将$[r,s] \in \text{Frac }R$映射到$[f(r),f(s)] \in \text{Frac }R'$,因此$\text{Frac } f$为一个$\text{Frac}(R) \to \text{Frac}(R')$的同态,

   因此我们可以得到$\text{Frac}$是一个整环范畴到分式域所构成的范畴的函子.

   

   至于$\text{Lie}$群和$\text{Lie}$代数暂未接触,不作考虑

   

2. 证明函子$\bold{1} \to C$,$\bold{2}\to C$以及$\bold{3} \to C$分别对应于$C$中的对象,箭头以及可组合的箭头对.

   $\bold{1} \to C$将$1$映射到$C$中的对象$c$上,将箭头映射为$c$自身的恒等映射,也就是对象自身.

   $\bold{2} \to C$将$1,2$映射到$C$中的两个对象$c,c'$上其间的箭头正好被映射为$c \to c'$的箭头,考虑只有箭头的范畴可以得知$\bold{2} \to C$对应于$C$中的箭头.

   同理得到$\bold{3}$的情况

   

3. 在下列特殊类型的范畴中解释"函子":

   a. 两个预序之间的函子是一个单调函数$T$($p \leq p'$蕴含$Tp \leq Tp'$)

   若不然,则会造成$p,p'$之间的箭头$f$在经过函子$T$后不再为$Tp$和$Tp'$间的箭头.

   

   b. 两个群(单对象范畴)之间的函子是群的态射

   使用函子满足结合律和$T(1) = 1_{T}$这两条性质可以直接证明

   

   c. 如果$G$是群,则函子$G \to \bold{Set}$是$G$的置换表示,$G \to \bold{Matr_K}$是$G$的矩阵表示.

   考虑$T : G \to \bold{Set}$不难发现它将$G$映射到$\bold{Set}$中的一个元素$S$上.

   而群$G$的元素被赋值为集合$S$到自身的变换$f$,由于每一个元素都有逆元,因此$f$为双射,不难发现$f$可视为群$G$的一个置换表示.

   矩阵表示类似可得.

   

4. 证明没有函子$\bold{Grp} \to \bold{Ab}$将$G$映射到它的中心上

   假设存在一个函子$T : \bold{Grp} \to \bold{Ab}$

   使得$G \to Z(G)$.

   那么我们考虑$S_2 = \{(1),(12)\}$以及$S_3 = \{(1),(12),(23),(13),(123),(132)\}$.

   不难发现$Z(S_3) = \{(1)\}$而$Z(S_2) = S_2$因此考虑$S_2 \to S_3 \to S_2 \simeq S_3/\left<(123)\right>$得到$TS_2 \to TS_3 \to TS_2$但是$TS_3 \to TS_2$的像不为$TS_2$,这与$S_3 \to S_2$的像为$S_2$相矛盾.

   

5. 找到两个不同的函子$T: \bold{Grp} \to \bold{Grp}$对象上的函数为$T(G) = G$为$G$的恒等映射.

   构建一个恒等函子,一个不为全忠实的函子即可,比方说考虑箭头$f:G \to H$其实蕴含了$f : G \to e \lhd H$等其他态射,将这些态射划归为$f: G \to H$就得到了一个不为全忠实的函子 .

## $\S4 \, Natural\,\,Transformations$ 

给定两个函子$S,T : C \to B$,一个自然变换($\text{Natural Transformations}$)$\tau: S \xrightarrow{\bullet } T$为一个对$C$中每个对象$c$都赋予一个$B$中的箭头(即"逐点"的赋予箭头)$\tau_c = \tau c: Sc \to Tc$使得$C$中的每个箭头$f:c \to c'$都产生一个交换图表

![image-20230925102028710](./Image/Category,Functors,and%20Natural%20Transformations/5.png)

当这个特性成立时,我们也称$\tau_c : Sc \to Tc$在$c$上是自然的.若我们认为函子$S$给出了$B$中$C$的(所有对象和箭头)的图像,那么自然变换$\tau$就是一个将图像$S$映射(或说平移)到图像$T$的一组箭头,下图中所有的正方形(以及平行四边形)都像上面一样可以进行交换

![image-20230925102415942](./Image/Category,Functors,and%20Natural%20Transformations/6.png)

我们称$\tau a,\tau b,\tau c,\cdots$为自然变换$\tau$的分量($\text{components}$).

自然变换通常被称为函子的态射($\text{a morphism of functors}$):在$B$中每个分量$\tau c$可逆的自然变换$\tau$被称为自然等价($\text{natural equivalence}$)或者更好的说法是自然同构($\text{natural isomorphism}$);使用符号$\tau: S \cong T$表示.在这种情况下,$\tau c$的逆$(\tau c)^{-1}$是$B$中自然同构的逆$\tau^{-1} : T \xrightarrow{\bullet} S$的一个分量.

行列式是一个自然变换.为了说明这一点,令$\text{det}_K M$为$n \times n$矩阵$M$的行列式,其元素完全属于交换环$K$.$K^*$表示$K$的单位群(即可逆元素).因此,当$M$非奇异时,$\text{det}_K$是一个$\text{GL}_n K \to K^*$的一个群态射($\bold{Grp}$中的一个箭头).因为对于所有的环$K$,行列式均由同一个公式所定义(即逆序数定义法),所以交换环的每个态射$f : K \to K'$都诱导下图交换

![image-20230925105005292](./Image/Category,Functors,and%20Natural%20Transformations/7.png)

这说明行列式变换$\text{det }: \text{GL}_n\cdot  \to \cdot^*$在两个函子$\bold{CRng} \to \bold{Grp}$上是自然的.

对于每个群到其导出子群的射影$p_G : G \to G/[G,G]$定义了一个从恒等函子到$\bold{Grp} \to \bold{Ab} \to \bold{Grp}$的变换$p$.此外$p$是自然变换,因为每一个群同态$f : G \to H$都定义了一个明显的同态$f'$使得下图交换

![image-20230925111704505](./Image/Category,Functors,and%20Natural%20Transformations/8.png)

二次特征群($\text{double character group}$)在所有$\text{Abel}$群组成的范畴$\bold{Ab}$中给出了一个具有启发性的例子.使用$D(G)$表示$G$的特征标群($\text{character group}$),$DG = \text{Hom}(G, \R/\Z)$是所有群同态$t : G \to \R/\Z$所构成的具有我们所熟知的群结构的群(即$t$可以构成一个群),其中$\R/\Z$是实数模$1$的加性群,

> 特征标为一个$f : G \to \C \setminus\{0\}$的集合,考虑$\C \setminus \{0\}\to S^1=\R/\Z$就不难发现$DG$可以写为$G \to \R/\Z$的同态所构成的群.考虑$f : G \to G'$,$t : G' \to \R/\Z$不难发现$t \circ f : G \to \R/\Z$因此有$t \circ f \in \text{Hom}(G,\R/\Z) = DG$而$t \in \text{Hom}(G',\R/\Z) = DG'$因此我们得到$Df : DG' \to DG$(方向相反).

因此对于每个$\bold{Ab}$上的箭头$f : G' \to G$都确定了一个$\bold{Ab}$上的箭头$Df: DG \to DG'$且$(Df)t = tf : G' \to \R/\Z$对于每个$t$成立.对于可结合的箭头,$D(g \circ f) = Df \circ Dg$.因为这种逆转的存在,$D$并不是一个函子(它是一个"反变"函子,详见$\S \text{II}.2$);然而对于特征标群$DG$再取一次特征标得到的二次特征标群$G \mapsto D(DG)$与恒等函子$I(G) = G$都为$\bold{Ab} \to \bold{Ab}$的函子.对于每个群$G$都有以下同态
$$
\tau_G : G \to D(DG)
$$
它由一种类似的方法得到:对于每个$g \in G$,函数$\tau_Gg : DG \to \R/\Z$通过对于每个$t \in DG$进行操作$t \mapsto tg$来给定;因此有$(\tau_G g)t = t(g)$.我们可以立即验证$\tau$是一个自然变换$\tau : I \xrightarrow{\bullet} DD$.这个陈述只是对于一些基础的观察的精确表达,即若$G$是一个有限群则$\tau$的定义不依赖于人为选择的基,生成子或其他类似的东西.因此如果我们把所有函子限定在有限$\text{Abel}$范畴$\bold{Ab}_f$内,则$\tau$是一个自然同构.

另一方面,对于每个有限$\text{Abel}$群$G$与其特征标群$DG$都存在一个同构$\sigma_G: G \cong DG$,但这种同构依赖于$G$作为循环群直积的表示,因此其不可能是自然的.更确切来说,我们可以把$D$变为协变函子$D': \bold{Ab}_{f,i} \to \bold{Ab}_{f,i}$其中$\bold{Ab}_{f,i}$是对象为所有有限$\bold{Abel}$群,箭头为它们之间的所有同构,令$D'G = DG$且$D' f = Df^{-1}$.那么$\sigma_G : G \to D'G$是一个映射$\sigma : I \to D'$所诱导的函子$\bold{Ab}_{f,i} \to \bold{Ab}_{f,i}$,但是在定义上它不是自然的.

一个类似的例子是有限维向量空间与它的双对偶空间的自然同构.

考虑$\mathbb{k}$上的向量空间范畴$\bold{Vect}(\mathbb{k})$.对任意$\mathbb{k}$-向量空间$V$,定义其对偶空间
$$
V^{\lor}:= \text{Hom}_{\mathbb{k}}(V,\mathbb{k}) = \{\mathbb{k}\text{-}线性映射 V \to \mathbb{k}\}
$$
任一线性映射$f: V_1 \to V_2$诱导对偶空间的反向映射
$$
f^{\lor}: V_2^{\lor} &\to& V_1^{\lor}\\
[\lambda:V_2 \to \mathbb{k}] &\mapsto& \lambda \circ f
$$
易见$D : V \mapsto V^{\lor}$,$f \mapsto f^{\lor}$定义了函子$D : \bold{Vect}(\mathbb{k})^{op} \to \bold{Vect}(\mathbb{k})$.这是一个反变函子

那么我们考虑$DD^{op}: \bold{Vect}_f(\mathbb{k}) \to \bold{Vect}_f(\mathbb{k})$.分别称为对偶和双对偶函子.

当我们把有限序数$n$的范畴$\bold{Finord}$与所有有限集合(在某个宇宙$U$中)所构成的范畴$\bold{Set}_f$进行比较时,出现了另一个自然性的例子.每一个序数$n = \{0,1,\cdots,n-1\}$是一个有限集合,所以包含映射$S$是一个函子$S : \bold{Finord} \to \bold{Set}_f$.另一方面,每个有限集合$X$决定了一个序数$n = \#X$,即$X$中的元素个数(即基数).我们可以对于每个$X$选择一个双射$\theta_X : X \to \#X$.对于两个有限集之间的任意函数$f : X \to Y$我们可以通过$\# f = \theta_Yf\theta_X^{-1}$定义一个序数之间的对应的函数$\#f : \# X \to \# Y$,这确保了图表交换

![image-20230925202819683](./Image/Category,Functors,and%20Natural%20Transformations/9.png)

并且使$\#$为一个函子$\# : \bold{Set}_f \to \bold{Finord}$.若$X$自身为一个序数,我们令$\theta_X$为一个恒等映射.这就确保了合成函子$\# \circ f$是一个$\bold{Finord}$的恒等函子$I'$.另一方面,合成$S \circ \#$不是恒等函子$I : \bold{Set}_f \to \bold{Set}_f$,因为它将每个有限集$X$映射到一个特殊的有限集——与$X$中元素个数相同的序数$n$.然而,上面的方图确实表明$\theta : I \xrightarrow{\bullet}S\#$是一个自然同构.这些都告诉我们有$I\cong 	S \circ \#,I' = \# \circ S$.

更一般地说,范畴$C$和$D$之间的等价($\text{equivalence}$)定义为一对函子$S : C \to D, T:D\to C$以及自然的同构$I_C \cong T \circ S,I_D \cong S \circ T$.这个例子表明这个概念(将在$\S\text{IV}1.4$中进行考察)能够使我们比较"相似"但是"大小"迥异的范畴.

我们将会使用许多其他关于"自然"的例子,正如$\text{Eilenberg-Mac Lane}$首先观察到的那样,定义"范畴"是为了定义"函子",定义"函子"是为了能够定义"自然变换".

### Exercise

1. 令$S$为一个固定集合,$X^S$为所有函数$h : S\to X$的集合.证明$X \mapsto X^S$是函子$\bold{Set} \to \bold{Set}$在对象上的函数,且由$e(h,s) = h(s)$所定义的求值函数$e_X:X^S \times X \xrightarrow{\bullet}X$为一个函数$h$在$s \in S$处的值,它是一个自然变换.

   

   由于$X^S$为一个集合,因此$X \mapsto X^S$确实为一个映射$\bold{Set} \to \bold{Set}$.接下来考虑两个集合之间的映射$f:X \to X'$,不难发现由于$X^S$为所有$S \to X$的集合,考虑$g \in X^S$有$f \circ g : S\to X'\in X'^S$.

   因此$\bold{Set}$上的箭头$f: X\to X'$诱导了一个$\bold{Set}$上的箭头$X^S \to X'^S$因此它是一个函子.

   接下来考虑其求值函子$e_X$与$e_{X'}$.由于$e_X : X^S \times S \to X$,因此其两个函子一个为恒等函子$\text{id}$,另一个是$X \mapsto X^S \times S$.

   我们还需要验证$T : X \mapsto X^S \times S$诱导了一个函子,根据前文的讨论发现其确实是一个函子.

   ![image-20230926214233821](./Image/Category,Functors,and%20Natural%20Transformations/10.png)

   由于上述图表交换,因此$e_X$确实是一个自然变换.

   

2. 若$H$是一个固定的群,证明$G \mapsto H \times G$定义了一个函子$H\times \cdot: \bold{Grp} \to \bold{Grp}$,以及每一个群态射$f : H \to K$定义了一个自然变换$H \times \cdot \xrightarrow{\bullet} K \times \cdot$.

   

   考虑群同态$f : G \to G'$,考虑$H \times f :H \times G \to H \times G'$.

   由于$H \times f(h,g_1g_2) = (h,g_1)(h,g_2)$不难发现其确实是一个同态.

   发现$H \times f$为$H \times G \to H \times G'$的箭头.

   因此$H \times \cdot$确实是一个函子.

   不能发现$K \times \cdot$也是一个函子.

   

   接下来验证$f : H \to K$定义了一个自然变换$e: H \times \cdot \xrightarrow{\bullet} K \times \cdot $.

   考虑

   ![image-20230926215947097](./Image/Category,Functors,and%20Natural%20Transformations/11.png)

   因此$e : H \times \cdot \xrightarrow{\bullet} K \times \cdot$是一个自然变换.

   

3. 若$B$与$C$是群(作为单对象范畴)且$S,T : B \to C$为函子(群同态),证明有一个自然变换$S \xrightarrow{\bullet}T$当且仅当$S$与$T$共轭,即当且仅当有一个元素$h \in C$且$Tg = h(Sg)h^{-1}$对于所有的$g \in B$成立.

     

    若存在自然变换则以下图表交换

    <img src="./Image/Category,Functors,and%20Natural%20Transformations/12.png" alt="image-20230927002147293" style="zoom:33%;" />

    此处$Tg \circ h = h \circ Sg$.

    因此得到$Tg = h (Sg)h^{-1}$.

    

4. 对于函子$S,T : C \to P$其中$C$为一个范畴且$P$为预序,证明当且仅当对于所有的$c \in C$都有$Sc \leq Tc$时存在一个自然变换$S\xrightarrow{\bullet} T$(它是唯一的)

     

    由于存在一个自然变换$S \xrightarrow{\bullet}T$因此对于任意的$c,c' \in C$以及箭头$f : c \to c'$以下图表是自动交换的

    ![image-20230927002645091](./Image/Category,Functors,and%20Natural%20Transformations/13.png)

    对于$p,p' \in P$当且仅当$p \leq p'$时它们之间有一条箭头$p \to p'$.并且根据我们对于自然变换的定义可以轻松得到它是基于$P$中箭头上的一族映射,因此若$\theta_c :Sc \to Tc$则必然有$Sc \leq Tc$.至于唯一性根据箭头的唯一性可以立即得出.

    

5. 证明每一个自然变换$\tau : S \xrightarrow{\bullet} T$定义了一个函数(称为$\tau$)通过将每个可组合箭头对$<g,f>$映射到$Tg \circ \tau f = \tau(gf) = \tau g \circ Sf$来将$C$中的每个箭头$f : c \to c'$映射到$B$中的箭头$\tau f : Sc \to Tc'$上.反过来,证明每一个这样的函数$\tau$来自于唯一一个有着$\tau_c = \tau(1_c)$的自然变换(这给出了自然变换的一个纯箭头描述)

    

    由于$<g,f>$为一个可组合对而$f : c \to c'$因此我们可以定义$g : c' \to c''$.由于$\tau : S \xrightarrow{\bullet} T$为一个自然变换.

    因此下图交换

    ![image-20230927215435747](./Image/Category,Functors,and%20Natural%20Transformations/14.png)

    根据定义不难发现$\tau f := \tau_{c'}\circ Sf$,$\tau g = \tau_{c''} \circ Sg$.

    不难看出$\tau f$和$\tau g$为各自正方形上的对角线.因此题目中所给的等式是成立的,即$\tau f  : Sc \to Tc'$对于每个箭头$f : c\to c'$成立.

    反过来,我们认为每个自然变换都源于这样一个函数$\tau$且$\tau_c = \tau(1_c)$.我们有如下组合$f = 1_{c'} f$且$f = f 1_c$.

    因此$\tau(1_{c'}) \circ Sf = \tau  f$且$Tf  \circ \tau(1_c) = \tau f$.因此我们可以得到$Tf \circ \tau(1_c') = \tau(1_c) \circ Sf$.且$\tau$为一个自然变换

    

6. 令$F$为一个域,证明$F$上所有有限维线性空间所组成的范畴(其态射为全体线性变换)等价于在$\S 2$中所描述的范畴$\bold{Matr}_F$.

    见(李文威.代数学方法第一卷 p40例2.2.15)



## $\S 5\,Monic,Epis\,,and\,\,Zeros$

范畴学处理元素(集合或群的元素)时,通常将它们的性质使用箭头来表示.举个例子,我们不能说集合$X$只有一个元素,而可以说对于任意集合$Y$都确实存在一个函数$Y\to X$.现在我们提出一些"没有元素"方法的实例.

对于一个箭头$e : a\to b$,若存在一个箭头$e' : b \to a$使得$e'e = 1_a$且$ee' = 1_b$则称$e$在$C$中是可逆的.不难发现,如果这样的$e'$存在,它就是唯一的(若不然,则存在$e''$使得$e''e = 1_a$且$ee'' = 1_b$那么$e' = e'1_b = e'(ee'') = e'ee'' = (e'e)e'' = 1_a e''  = e''$因此是唯一的),我们把其记为$e' = e^{-1}$.在通常的证明中,假设复合$e_1e_2$都有定义并且$e_1,e_2$都是可逆的.则$(e_1e_2)^{-1} = e_2^{-1}e_1^{-1}$.若两个对象$a$与$b$在范畴$C$中存在一个可逆箭头(一个同构)$e:a \to b$;我们记为$a \cong b$.对象的同构关系具有明显的自反性,对称性以及传递性.

对于一个箭头$m : a \to b$,若对于任意两个满足等式$m \circ f_1 = m \circ f_2$的平行箭头$f_1,f_2 : d \to a$能推导出$f_1 = f_2$.那么我们就称$m$是$\text{monic}$的(即单的).换句话说,$m$是单箭头当且仅当它总是满足左消去律.在$\bold{Set}$与$\bold{Grp}$中单态射的箭头也就是通常意义下的单射(单态射$\text{monomorphisms}$).

对于一个箭头$h : a\to b$,若对于任意两个满足等式$g_1 \circ h = g_2 \circ h$的箭头$g_1,g_2 : b \to c$可以推出$g_1 = g_2$,我们就称$h$是$\text{epi}$的(即满的).换句话说,$h$是满箭头当且仅当它总是满足右消去律.在$\bold{Set}$中满箭头也就是通常意义下的满射(满态射$\text{epimorphism}$).

对于一个箭头$h : a\to b$,其右逆被定义为一个满足$hr = 1_b$的箭头$r : b \to a$.$h$的右逆(经常不是唯一的)叫做$h$的一个截面($\text{section}$).若$h$有一个右逆,那么$h$是满的.这句话反过来在$\bold{Set}$中成立,但是在$\bold{Grp}$中不成立.类似地,$h$的一个左逆被称作$h$的一个收缩($\text{retraction}$)并且任意一个有左逆的箭头都必然是单箭头.若$gh = 1_a$,则$g$是分裂($\text{split}$)满的,$h$是分裂单的.并且复合$f = hg$是可以被定义它还是幂等的.一般来说,一个箭头$f : b \to b$若$f^2 = f$则称其为幂等的.当存在箭头$g,h$使得$gh = 1$且$f = hg$时,称箭头$f$是幂等的.

对于$C$中的一个对象$t$,若对于$C$中的每个对象$a$都正好存在一个箭头$a \to t$,我们就称$t$是终的($\text{terminal}$).若$t$为一个终对象,则其到自身唯一的箭头$t \to t$是恒等态射,并且$C$中两个终对象在$C$中是同构的.对于$C$中的一个对象$s$,若对于$C$中每个对象$a$都正好存在一个箭头$s \to a$,那么我们称$s$是始的($\text{initial}$).举个例子,在范畴$\bold{Set}$中,空集$\varnothing$就是一个始对象,而任意单点集都是终对象.在群范畴$\bold{Grp}$中,只有一个元素的群既是始对象又是终对象.

对应$C$中的一个对象$z$,若它既是始对象又是终对象,则称$z$为一个零($\text{null}$)对象.若$z$是一个零对象,则该对象在同构的意义下是唯一的,而对于$C$中的任意两个对象$a,b$都存在一个唯一的箭头$a \to z \to b$(经过$z$的复合),称为从$a$到$b$的零箭头($\text{zero arrow}$).任意带有零箭头的组合本身也就是一个零箭头.举个例子,范畴$\bold{Ab}$与范畴$\text{R-} \bold{Mod}$都有零对象(即$0$),$\bold{Set}_*$也是如此(即单点集).

若一个范畴中的所有箭头均可逆,那么这个范畴称为一个广群.一个典型例子是拓扑空间$X$的基本广群($\text{fundamental groupoid}$)$\pi(X)$.$\pi(X)$中的一个对象就是$X$中的一个点$x$,并且$\pi(X)$中的箭头$x \to x'$是路径$f$从$x$到$x'$的同伦类(路径$f$是一个连续函数$I \to X$,$I$为闭区间$I = [0,1]$,且有$f(0) = x,f(1) = x'$,而具有相同的端点$x$和$x'$的两条路径$f,g$,且有两条连续函数$F : I\times I \to X$且$F(t,0) = f(t)$,$F(t,1) = g(t)$,且$F(1,s) = x, F(1,s) = x'$对于所有的$s,t\in I$成立).两条路径$g : x' \to x''$以及$f : x \to x'$的合成($\text{composite}$)是一条路径$h$,即"$f$后面跟着$g$",它的显式方程由
$$
\begin{array}{c}
h(t) &=& f(2t) , & 0 \leq t \leq 1/2\\
     &=& g(2t-1), & 1/2 \leq t \leq 1
\tag{1}
\end{array}
$$
给出

复合也适用于同伦类,并使$\pi(X)$成为一个范畴并且任何一个广群(任何路径的逆都是其反向)

由于广群$G$中的每个箭头都是可逆的,$G$中的每个对象$x$都决定了一个由所有的$g : x \to x$构成的群$\text{Hom}_G(x,x)$.若存在一个箭头$f : x \to x'$,群$\text{Hom}_G(x,x)$和群$\text{Hom}_G(x',x')$在$g \mapsto fgf^{-1}$(即共轭下)是同构的.对于一个广群,如果存在一个箭头可以将一个广群中的任意两个对象连接在一起,就说它是连通的($\text{connected}$).我们可以很容易地证明连通广群是由一个群($\text{Hom}(x,x)$中的一个)和一个集合(所有对象的集合)确定其同构的.使用这种方法,一个道路连通空间$X$的基本广群$\pi(X)$由空间中点的集合以及群$\text{Hom}_{\pi(X)}(x,x)$(即$X$的基本群).

### Exercise

1. 找到一个箭头既是满的又是单的但是不可逆的范畴(例如拓扑空间中的稠密子集)

   

   考虑$\R$的稠密子集$\Q$.

   赋予$\Q$欧式空间拓扑.

   因此我们可以得到一个嵌入映射$\iota : \Q \to \R$.

   对于任意的$X \to \Q$,有$\iota \circ f (x)= f(x)$.从而若$f_1,f_2: X \to \Q$使得$\iota f_1 = \iota f_2$则有$f_1 = f_2$.因此$\iota$是单的.

   接下来考虑$f : \R \to Y$,有$f \circ \iota (x) = g \circ \iota (x)$时,由于$\Q$为$\R$的稠密子集,因此可以在$\Q$中取出一个序列$\{x_n\}$使得$x_n \to x$.

   由于$f\circ \iota(x_n) = f(x_n)$,$g \circ \iota (x_n) = g(x_n)$.

   因此$f(x) = \lim_{n \to \infty} f(x_n) = \lim_{n \to \infty}f\circ \iota(x_n) = \lim_{n \to \infty}g \circ \iota(x_n) = \lim_{n \to \infty}g(x_n) = g(x)$

   这也就说明$f = g$.

   但是显然$\iota$是不可逆的.

   

2. 证明单箭头的合成还是单箭头,满箭头也一样

   

   对于单箭头$m,m'$有$m\circ h_1  = m \circ h'_1 \Rightarrow h_1 = h'_1$.

   考虑$m \circ m'$,以及$ (m\circ m') \circ h_1= (m \circ m') \circ h_2$由于$(m\circ m') \circ h_1= m \circ (m' \circ h_1) = (m \circ m')h_2$因此得到$m' \circ h_1 = m' \circ h_2$即$h_1 = h_2$,因此根据单箭头的定义得到$m \circ m'$是一个单箭头.

   同理证明满箭头的情况.

   

3. 若$g \circ f$是单箭头,则$f$是单箭头,这对$g$成立吗

   

   若$g \circ f$是单箭头,则对于$h_1,h_2$若$(g \circ f) \circ h_1 = (g \circ f )\circ h_2 \Rightarrow h_1 = h_2$.因此得到$g \circ (f \circ h_1) = g \circ (f \circ h_2) \Rightarrow h_1 = h_2$.

   若$f$不为单箭头,则不一定有$h_1 = h_2$,但是对于任意的$h_1,h_2$若满足条件则都有$h_1 = h_2$.因此$f$必然为单箭头.

   若$g$不为单箭头,则不一定有$g \circ f \circ h_1 = g \circ f \circ h_2 \Rightarrow f\circ h_1 = f \circ h_2$对于任意满足条件的$h_1,h_2$成立.即可能存在$k$使得$g \circ f \circ k = g \circ f \circ h_1 \Rightarrow  f\circ k \neq f \circ h_1$.但是由于$f$是一个单箭头.

   因此若$f \circ k \neq f \circ h$则$k \neq h$,所以得到若$(g\circ f) \circ h_1 = (g \circ f) \circ h_2$且$f$为单箭头则必然有$h_1 = h_2$.

   

4. 证明嵌入映射$\Z \to \Q$是一个$\bold{Rng}$上的满箭头.

   

   考虑嵌入映射$\iota : \Z \to \Q$若存在$h_1,h_2: \Q \to R$使得$h_1 \circ \iota = h_2 \circ \iota$则$h_1(\frac{a}{1}) = h_2(\frac{a}{1})$对于所有的$a \in \Z$成立.此时
   $$
   h_1(\frac{1}{a}\frac{a}{1}) = 1 = h_2(\frac{1}{a}\frac{a}{1})
   $$
   因此得到$h_1(\frac{1}{a}) = h_2(\frac{1}{a})$对于所有的$a \in \Z$成立.根据同态的性质可以得到对于任意的$\frac{p}{q} \in \Q$都有$h_1(\frac{p}{q}) = h_2 (\frac{p}{q})$即$h_1 = h_2$.

   因此$\iota$是$\bold{Rng}$上的满箭头

   

5. 在$\bold{Grp}$中证明每个满箭头都是满射(提示:若$\varphi : G \to H$的像为$M$而不是$H$,若$M$的指数为$2$则使用商群$H/M$,若$M$的指数不为$2$则考虑$\text{Sym}(H)$为$H$的所有置换所构成的群,选择$M$的不同陪集$M$,$Mu$以及$Mv$,定义$\sigma \in \text{Sym}(H)$为$\sigma(xu) = x v$,$\sigma(xv) = x u$对于所有的$x \in M$成立,且对于其他元素$\sigma$均为恒等置换.令$\psi : H \to \text{Sym}(H)$将$h$映射为$h$的左乘映射$\psi_h:h' \mapsto hh'$而$\psi'_h =\sigma^{-1}\psi_h \sigma$.则$\psi \varphi = \psi' \varphi$但是$\psi \neq \psi'$)

   

   令$f : G \to H$是满箭头但是不是满同态,则有$M = \text{Im}(f) \subsetneq H$.由于$f$是一个同态,则有$M \leq H$.

   若$[H,M] = 2$则考虑商群$H/M$,且$\pi$为商映射,$\pi \circ f = \tau = \tau \circ f$其中$\tau: H \to 1$.

   

6. 



