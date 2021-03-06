### 7 环境噪声面波层析成像

#### 7.1 引言

地震成像是一类反演问题，它指的是利用通过地球传播的地震波来推断地球内部的力学性质。最为传统的方法是反演P波和S波的到时，其到时和振幅可以用基于程函方程的射线方法进行描述。另外一些方法使用面波、振幅、全波形甚至是由散射波组成的信号，可以基于各自理论近似进行反演。

解决地震成像反演问题的传统方法是基于已知震源性质（如：位置、震源机制和时间）的信号。人工震源主要用于地震勘探，上述性质具有完全可控的特点。而传统的被动源地震学仍主要基于地震记录，其震源的性质可以使用确定性函数来描述，并且可以从观察中很好地确定。

基于震源确定性描述的方法是十分强大的。但是，其也受制于震源的可用性。人工震源通常价格高昂，且能量有限或者（出于许多现实原因）难以部署，而天然地震仅出现在构造活动活跃的地区，且数量相对较少。地球表面的背景震动通常（相当错误的）被称为“背景噪声”，代表了一种不同的地震信号，它是由无法确定地描述的源激发的。

第四章介绍了地震噪声互相关的理论(Fichtner and Tsai, 2018)，其理论基石是”噪声互相关定理“，**该定理指出在具有弱衰减的线性系统中，在两个位置记录的随机波场的互相关的时间导数收敛于系统的格林函数**(e.g., Gouédard et al., 2008)。
$$
\lim _{T \rightarrow \infty} \frac{\partial}{\partial t} C_{A B}(t)=F(t) *\left[G_{A B}(t)+G_{B A}(-t)\right]\tag{7.1}
$$
其中$C_{AB}(t)$为在时间长度为$T$的窗口中计算的位置A和B记录的信号的互相关函数，$G_{AB}(t)$是这两个位置之间的格林函数，$G_{AB}(-t)$为其reciprocal, $F(t)$是与噪声频谱特性相关的时域函数(e.g., Weaver and Lobkis, 2001;Snieder, 2004; Wapenaar, 2004; Roux et al.,2005; Campillo, 2006; Gouédard et al., 2008)。**特别的，$F(t)$为具有纯白噪的Dirac函数**。换而言之，通过计算所有台站长时间记录的噪声互相关函数，每个接收台站可以转换为一个虚拟震源，发射一个以噪声相关函数表示的波场。在过去的十年中，这一原理在地震学中应用产生了一种新的范式，即通过由噪声互相关重构的确定性波场对地球内部进行成像，而不是地震或者人工震源的信号。

Aki(1957)和Claerbout(1968)分别在（天然）地震学和勘探地震学中提出利用随机的地震噪声对地下结构进行成像的想法。然而，直到来到数字地震学时代，当长时间数字记录的地震时间序列能够用于大规模分析时，噪声互相关潜力的应用潜力才能得到充分的开发。Shapiro and Campillo（2004）和Sabra et al. (2005a)首次证明了从被动地震噪声记录的相关性中可以提取确定性波，并立即开展了基于噪声的地震层析成像的首次应用(Shapiro et al., 2005; Sabra et al., 2005b)。

噪声互相关定理在理想的情况（完全随机和波场均分）下是有效的。然而，真实的地震噪声的性质与这一理想的情况想去甚远。地震噪声主要是由固体地球与海洋及大气耦合产生的(e.g., Ardhuin et al., 2011, 2018)。对于高频信号而言，人为噪声源则可能更为重要（参见Chapter 1）。对于上述两种情况，噪声的噪声波场在空间上，时域和频域都不是平稳的。构造成因的强地震源(诸如地震和火山)使得连续的地震时间记录具有强烈的非平稳性。因此。噪声互相关定理并不能直接应用于地震数据。

从台站对的噪声相关中提取确定性波的传播要求在重建的干涉区存在足够多的噪声源(e.g., Snieder, 2004; Roux et al., 2005)。对于面波和体波来说，这些区域的特性存在显著的不同，后者主要位于远离地表的深处。这种差异，加上大部分噪声源位于地表这一事实，使得从噪声互相关函数中提取的主要成分是面波(而且主要为其基阶信号)。从噪声相关中提取体波的条件和应该参见Chapter 8(Nakata and Nishida, 2018)。噪声源在地球表面分布的不均匀性导致了非对称的互相关(即使是重建面波, 参见Chapter 5[Ritzwoller and Feng, 2018]), 并且阻碍了其振幅的正确测量。

正如Chapter 5所述(Ritzwoller and Feng, 2018), 连续的地震记录必须经过预处理用于减弱噪声记录非平稳性和非均匀分布的噪声源的影响。然而，即使经过预处理，真实的噪声互相关函数并不等同于格式函数。因此，现有的大多数基于噪声互相关的成像应用并未完全使用噪声互相关定理。Garnier and Papanicolaou (2009)已经证实即使完整的互相关函数无法完全重建，但当接两个传感器的射线相继进入噪声源区域时，可以有效估计波的传播时间。

#### 7.2 环境噪声走时面波层析成像

正如前一章所解释的，面波的走时是最容易从环境噪声的互相关中所提取的一类信息。因此，基于噪声互相关的主要应用之一是环境噪声表面波层析成像(ANSWT)(e.g., Ritzwoller et al.,2011)。这种方法当应用于地震台网时格外具有优势。通过计算所有台站对足够长的时间的环境噪声的互相关，每一个台站都可以转换为虚拟的源，用以发射表面波，并且可以在其他台站测量旅行时。对于由N个台站所构成的台网，可以提供连接N个源和接收器的$N(N-1)/2$条路径的旅行时测量。从噪声互相关中测量的面波走时的合集可以用类似于有源地震的“标准”方法进行反演。

面波之所以称为面波，是因为其主要沿着表面传播，并且其振幅在一定深度会消失。单频面波沿X方向传播最简单的表达如下：
$$
u_{s w}(x, z, t, \omega) \approx \xi(z, \omega) \exp [i(\omega t-k(\omega) x)]=\xi(z, \omega) \exp [i \omega(t-x / C(\omega))]\tag{7.2}
$$
其中$t$表示时间，$\omega$表示频率，$z$表示深度，$\mu$表示位移向量，$k$表示波数，$\xi$描述波的振幅随深度衰减的本征函数。$C$为相速度：
$$
C(\omega)=\frac{\omega}{k(\omega)}\tag{7.3}
$$
对于这样的波而言，可以定义水平波长$\lambda$:
$$
\lambda(\omega)=\frac{2 \pi C(\omega)}{\omega}\tag{7.4}
$$
地震面波的一个重要的性质称之为频散，即其波数取决于频率。面波的能量集中于$\xi(z, \omega)$最大值的近地表层。通常这个厚度约为半个波长。这表明高频面波(短波长)对于浅层的结构比较敏感，而低频面波(长波长)对于深层的(结构)则更为敏感。平均而言，地球的物质成=成分随着深度会变得更为坚硬，其波速也会增加。因此，面波相速度通常随着波长的增加而增加或者随着频率而减小。(这一特性)的意义在于面波的频散反映了地球弹性性质随深度的变化。因此，测量不同频率面波的相速度和群速度频散便可用于约束地下介质与深度有关的模型。

除了相速度$C(w)$以外，我们还可以定义群速度$U(w)$:
$$
U(\omega)=\left(\frac{\partial k(\omega)}{\partial \omega)}\right)^{-1}\tag{7.5}
$$
根据面波的定义，很自然便可以导出显示相速度。与此同时，面波的能量/信息沿着群速度进行传播(e.g., Biot, 1957)。从这个意义上来说，其物理意义更为明确。因此，如果我们想要估计沿面波一定距离传播所需的时间，我们便需要使用群速度。这两个速度是互相关联的：
$$
U(\omega)=\frac{C(\omega)}{1-\frac{\omega}{C(\omega)} \frac{\partial C(\omega)}{\partial \omega}}\tag{7.6}
$$
**值得注意的是，这个关系包含对频率的偏导数。因此，群速度不能轻易的从离散的相速度测量中计算出来而必须独立地测量。**此外，群速度和相速度深度的敏感核也是不同的(e.g., Ritzwoller et al.,)。因此，从这两种测量中获取的信息是互补的。

传统上，面波的频散被描述为周期($T=1/f=2\pi/\omega$)的函数，而不是频率。因此，在很多本章及其他章节的实例中，群/相速度和其他面波的性质均被描述为周期的函数。

最后，对于单一的源-接收器路径，可进行不止一种的旅行时测量。所测量的在不同周期的面波旅行时(传播的波速)构成了所谓的频散曲线。面波主要有两种类型，Rayleigh波和Love波，且有两种传播速度(群速度和相速度)。因此，对于给定的源-接收器路径和单一模式的面波，共可以测量四种不同的频散曲线。

**测量面波的特定模态的频散曲线需要将与此模态对应的信号从波形中出现的其他波中分离出来。**为了达到此目的，会使用到时频分析的方法(e.g., 1989)。有关该方法的细节已经在Section 3.5予以描述。此外，也可以直接测量群速度相速度(e.g., Lin et al., 2008)，如图5.11所示。

Rayleigh波和Love波具有不同的极化特征，前者以垂向(Z)和径向(R)分量观测地面震动，后者以横波(T)方向进行观测，完整的相关张量包含6个独立的分量。正如Lin et al(2008)年所述，为了分离Rayleigh波和Love波，当考虑驿站台站作为源，另一个台站作为接收台站，互相关矢量应该根据测量的方位角和反方位角旋转到径向和和横波方向。经过旋转后，对于互相关张量的分量信息，可以使用ZZ,RR,RZ,ZR获取Rayleigh波信息，TT分量则与Love波相关联。对于噪声源分布均匀的各向同性介质，混合的RT和TT互相关有望消失。此类分量的强振幅可能表明存在噪声源的强非均匀性，或者介质存在各向异性(e.g., Durand et al., 2011)。

每个独立的互相关均包含正支(因果)和负支(非因果)的信号。在理想的重建下，两侧的信号应该完全对称，正如互相关定理所揭示的。事实上，由于噪声源的分布的非均匀性，振幅的对称性几乎是不可能实现的。当噪声源分布的不均匀性没有那么强时，它会使得正支和负支信号的振幅存在差异，但两侧所测量得到的到时则会非常相似。从正负支测量的旅行时的显著差异意味着噪声源的分布具有强烈的非均匀性，会对旅行时的估计带来偏差。因此，**通过比较正负支旅行时(频散)测量的差异可用于其质量控制。**

ANSWT的标准处理步骤描述如下：

1. 连续地震波形的预处理
2. 计算所有可用的台站和互相关之间的互相关
3. 从不同分量(Rayleigh[ZZ, RR, RZ, ZR], Love[TT])的正支和负支测量频率相关的群/相速度旅行时
4. 质量控制及选取最终的群/相速度旅行时
5. 使用2D面波层析成像方法对测量的频散曲线进行区域化：构建Rayleigh波和Love波的频率相关的相速度和群速度图($C, U^{R, L}(\omega, x, y)$)
6. 在每个地理位置$(x,y)$进行区域频散曲线的1D深度反演，用于构建最终介质的3D模型$(V_{s}(x,y,z))$

对于数据的预处理和面波频散曲线的测量的方法参见Chapter 5(Ritzwoller and Feng, 2018)。在**"稀疏"网络**的情况下，即台间距大于或与所使用的面波的波长相当时，频散曲线的区域化可以表述为2D层析成像问题，即作为测量的相/群旅行时的线性(或迭代线性)反演。在**“密集”网络**的情况下，即台间距小于所使用的面波波长时，局部的相速度可直接从测量的旅行时的空间导数进行估计。

用于获得1D深度剖面的面波频散曲线的深度反演是地震学中最为广泛的反演问题，可以使用多种方法进行求解，其可表述如下。区域化的步骤在特定地理位置产生局部频散曲线作为输入数据：
$$
d=\left[C^{R}(\omega), C^{L}(\omega), U^{R}(\omega), U^{L}(\omega)\right]\tag{7.7}
$$
其中$C$和$U$分别表示相速度和群速度，上标$R$和$L$分别表示Rayleigh波和Love波。这些频散曲线被假定为是局部1D模型的结果：
$$
m=\left[c_{i, j, k, l}(z), \rho(z), Q(z)\right]\tag{7.8}
$$
其中$z$为深度，$c_{i, j, k, l}$为弹性张量，$\rho$为密度，$Q$为品质因子。正演问题可以简写为：
$$
d=F(m)\tag{7.9}
$$
其可有多种方法求解，如Herrmann (2013)的平面层状近似, Woodhouse (1988)的球面几何。

面波频散中所包含的信息不足以约束方程(7.8)中所出现的全部的弹性参数。面波走时对介质的横波速度最为敏感(e.g., Dahlen and Tromp, 1998)。因此，在大多数面波频散反演算法中，模型多是使用$V_{S}(z)$进行参数化，其他参数通常是固定的，或者以某种方式与横波速度成比例。

方程(7.9)的反演可以通过多种方式实现。其中一类是计算与介质弹性参数相关的面波群速度和相速度的线性敏感核(e.g., Herrmann, 2013)。频散曲线的1D深度反演是一个相对低维度的问题，因此可以通过对模型的参数空间进行统计探索，采用Monte-Carlo类型的方法进行求解(e.g., Shapiro and Ritzwoller, 2002; Yang et al., 2008; Moschetti et al., 2010)。这种方法包含了许多随机生成的模型$m$(速度剖面$V_{S}(z)$)，然后根据方程(7.9)计算频散曲线，并与观测数据$d$进行比较，用以选择一组与观测值非常吻合的模型。近年来，随着算力的提高，使得我们可以求解数以万计的正演问题，让这类方法变得十分流行。图7.3c-d给出了一个群速度的Monte-Carlo反演示例。

<img src="https://carlolev.oss-cn-beijing.aliyuncs.com/SeismicAmbientNoise/Figure%207.3..png"/>


##### 7.2.1 “稀疏”台阵下的ANSWT

最为标准的2D走时层析成像是基于面波的射线近似(e.g., Woodhouse, 1974; Wang and Dahlen, 1995)。通过使用该近似，面波层析成像的正演问题包括从一组2D相/群速度图中预测频率相关的旅行时：
$$
t(\omega)=\int_{p} \frac{d s}{v(\omega, x, y)}\tag{7.10}
$$
其中$\omega$为频率，$x$和$y$为表面位置的坐标，$t(\omega)$为Rayleigh波或者Love波的群/相速度旅行时，$v(x,y,z)$对应于各自的速度图，$p$表示射线路径，$s$是沿射线路径的距离.。对于N个站间路径和某一频率特定的速度类型，这便给出了一个N个方程组成的方程组，可以根据测量的走时反演得到$v(x,y,z)$。对于大多数的层析成像问题，这类反演需要额外的正则化项用以保证解的稳定(e.g., [Barmin et al., 2001](https://doi.org/10.1007/PL00001225))。

当存在与波的尺度相当的非均匀性介质时，基于射线理论的近似便会失效。因此，其也被认为是一种**①高频近似**。然而，在ANSWT最为常用，相对较短的周期范围内，2D层析成像的有限频效应是相对较弱的(e.g., [Ritzwoller et al., 2002](https://doi.org/10.1029/2002JB001777))。在ANSWT和面波层析成像中另外一个常用的假设是与②**射线弯曲相关非线性常常被忽略**。在大多数情况下，射线弯曲的影响确实很小。为了考虑这一点，层析成像问题必须通过基于相(而不是群)速度进行2D射线追踪来迭代解决(e.g., Yoshizawa and Kennett, 2002; Rawlinson et al., 2008)。**当只使用相速度时，走时层析成像就是完完全全的2D**。将测量的群速度与考虑射线弯曲相结合，需要在每次迭代时从3D模型中重新计算2D相速度图。当射线弯曲被忽略时，2D的层析成像作为一个正则化的线性反演问题来有效地解决(e.g., Barmin et al., 2001)。

近十年来，这种方法已经被广泛应用全球各个地区，用于研究各个尺度的地壳和上地幔结构。全球尺度(e.g., Nishida et al., 2009; Haned et al., 2016)。其中最为引人瞩目的应用成果莫过于在大尺度台网的应用，诸如北美(e.g., Lin et al., 2008; Yang et al., 2008; Moschetti et al., 2010; Spica et al., 2016; Shen and Ritzwoller, 2016), 欧洲(e.g., Yang et al.,2007; Stehly et al., 2009; Molinari et al., 2015), 中国(e.g., Yao et al., 2006,2008; Liu et al., 2016; Shen et al., 2016)。而且，当使用相对短周期的面波研究浅层结构时，这种方法被证明是十分有效的，已经被用于许多火山系统的研究(e.g., Brenguier et al., 2007; Jaxybulatov et al., 2014; Mordret et al., 2015; Spica et al., 2017), 并开始逐步应用到工业数据(e.g., Mordret et al., 2013a)

##### 7.2.2 "密集"台阵下的ANSWT

现代的地震台网是如此密集使得其能够以亚波长的范围内采集面波。在这种情况下，走时信息可以被用来测量波场的局部信息，使得能够对波的传播和所经过的地下介质开展更为精细的研究。例如，基于亚波长尺度的台网开展聚束分析(e.g., Rost and Thomas, 2002)可以同时测量面波的局部的速度和传播方向。一个大型的台网也可以被划分为许多的子台阵。对所有可用的噪声互相关开展聚束分析会得到一组子台阵之间波的方位角(信息)。而后可以开展走时和方位角的联合反演(Boué et al., 2014)。在不同的子台阵之间进行系统的双波形聚束分析，能够更好地分离面波和体波，提高测量的走时的数量和准确性(Roux et al., 2016; see also Chapter 8)。

通过密集的亚波长采样，从站间互相关中提取的波形集合可以被认为是相干波场，而经过大型网络测量的面波走时可以被用来估计局部走时的梯度。在具有平滑的横向非均质性的介质中，面波走时可以通过射线理论近似来描述(e.g., Woodhouse, 1974; Wang and Dahlen,1995)。在这种情况下，可以基于相位旅行时的局部梯度，使用近似的2D程函方程来估计局部向速度和波的传播方向。
$$
\frac{\bar{k}(r)}{C(\omega, r)}=\nabla \tau(\omega, r)\tag{7.11}
$$
$r$表示位置，$\tau$为相位旅行时，$C$为相速度，$\omega$为频率，$\bar{k}$为描述波传播的局部方向的单位矢量。由此引出了程函层析成像([Lin et al., 2009](https://doi.org/10.1111/j.1365-246X.2009.04105.x)), 其在不同尺度和诸多环境下被用于推测相速度分布及其相关的方位各向异性(e.g., Lin et al., [2011a](https://doi.org/10.1111/j.1365-246X.2011.05070.x), [2013](https://doi.org/10.1190/geo2012-0453.1); [Mordret et al., 2014]()。图5.16展示了使用USArray数据的区域尺度的程函层析成像示例。

密集台阵在时间和空间上采集噪声互相关。这种密集的的采样可以根据谱相关函数(或谱相干函数)来测量局部相速度。这种方法由Keiiti Aki在1957年介绍他著名的SPAC方法时所提出(Aki, 1957; see also Chapter 10)。这种方法的思想是，以面波主导的噪声波场的谱相关函数$CC(\omega)$与相速度$C$和频率$\omega$相关。
$$
C C(\omega)=J_{0}\left(\frac{\omega}{C(\omega)} r\right)\tag{7.12}
$$
其中$r$为台站间距, $J_{0}$为第一类零阶Bessel函数。基于密集台阵，采样的距离小于波长，可以将噪声互相关频谱实部的零交叉点与相应贝塞尔函数的零交叉点联系起来用以得到相速度。这种方法被成功用于USArray的数据([Ekström et al., 2009](https://doi.org/10.1029/2009GL039131))和一些更小的台网([Calkins et al., 2011]( https://doi.org/10.1029/2010JB007657))。

类似的想法可以用略微不同的，即所谓的"focal spot imaging"(焦斑成像, [Hillers et al., 2016](https://doi.org/10.1002/2016JB013014))进行表述,利用了利用噪声互相关和时间反转试验的类比(e.g., Derode et al., 2003)。**在这种方法中，零时刻的振幅被解释为面波的焦点，其大小与局部的相速度有关**。当用于大型密集台阵时，这种方法可以被用于估计相速度图。

##### 7.2.3 基于ANSWT的地震各向异性研究

虽然面波频散曲线对于研究地壳和上地幔的各向同性的横波速度是最为敏感的，但是其也可以用来研究各向异性的信息。使用面波观测地震的各向异性主要有两种方法。**一，测量不同方向传播的面波的速度便可以揭示方位各向异性**(Montagner and Nataf, 1986)。当方位分布采样良好时，走时信息可以通过大型台阵的互相关测量时，这一概念可以得到有效的应用。图7.4d展示了在Valhall油田开展的类似的应用实例。局部相速度以一个具有180°变化周期的偶数阶正弦的形式，明显地随方位角θ的函数变化，正如理论假设对稍微具有各向异性的介质预测的那样(e.g., Smith and Dahlen, 1973)。这种分析方法可以应用于一个大型台阵的所有台站，用以推断快波方向的空间变化和方位各向异性的振幅。

另一个方法是**测量Rayliegh波和Love波频散曲线的"差异"**，当这种差异不能简单的用各向同性模型来解释时。这类观测反映了径向各向异性的存在，即垂直极化和水平极化弹性波之间的速度差异(e.g., Ekström and Dziewonski, 1998)。在这种情况下，模型速度剖面(方程(7.8))参数化为：
$$
m=\left[V_{S V}(z), V_{S H}(z)\right]\tag{7.13}
$$
其中$V_{SV}$和$V_{SH}$分别表示垂直极化和水平极化的S波。图7.3e-f展示了一个Indonesia的Toba火山口区域从Rayliegh波和Love波群速度反演径向各向异性的示例(Jaxybulatov et al., 2014)。

ANSWT已经被广泛应用于研究地震的各向异性。相较于基于地震事件，基于噪声的各向异性研究提取的短周期面波主要对地壳结构较为敏感。因此，ANSWT提供了地壳各向异性的信息，这是以往使用地震事件难以做到的。大尺度的地壳各向异性研究，如美国(e.g., Moschetti et al., 2010; Lin et al., 2011a)和中国(e.g., Huang et al., 2010;Liu et al., 2016; Xie et al., 2017)。在更小的尺度，ANSWT已经被用来解释火山系统(e.g.,Jaxybulatov et al.,2014; Mordret et al., 2015)内和油气储层盖层(e.g., Mordret et al., 2013b; Tomar et al., 2017)的各向异性

#### 7.3 从环境噪声中提取面波振幅和波形信息

当噪声互相关被当做是完全重构的格林函数时，直接噪声互相关定理出发，意味着其振幅也可以被用来推测地壳和地幔的性质。估计波的衰减(品质因子)这样一个重要参数时，需要对振幅进行测量。已经有一些使用噪声互相关(相干)来估计面波衰减分布的尝试(e.g., Prieto et al., 2009; Lawrence and Prieto, 2011)。与此同时，许多研究表明，从噪声互相关中估计衰减会十分容易受到未知的噪声源分布的影响(e.g., Cupillard and Capdeville, 2010; Lin et al., 2011b; Weaver,2011; Stehly and Boué, 2017)。

直接从噪声互相关定理出发的另一个思路是，通过与3D地球模型计算得到的理论格林函数进行对比，直接反演从中提取的面波波形。然而，这种类型的反演是基于噪声互相关波形可以被视作是由位置已知的类力源产生的信号。**当失配函数是基于波形的相位而忽略振幅信息(计算)时，这种近似是可行的**。为了更为精确地反演噪声互相关波形，需要知道噪声源的分布。大体上，可以建立一个关于介质性质和噪声源密度分布的联合反演问题(e.g., Tromp et al., 2010; Fichtner et al., 2017; Sager et al., 2018)。然而，在许多实际情况下，产生噪声互相关的最重要的噪声源位于台阵覆盖区域之外，这类反演问题仍然缺乏约束。

尽管直接应用噪声互相关定理或者反演互相关波形/振幅的方法存在诸多困难，在某些情况下，从噪声互相关中提取的面波振幅信息是可以得到合理的解释的。一种方法是利用Rayleigh波的椭圆度。该椭圆度取决于频率，也与测量的位置下方局部的结构有关(e.g., Tanimoto and Rivera, 2008)。Nakamura (1989)在这一思想的基础上提出了一种简单的技术，当从噪声中可以直接测量HV比时，可用于直接研究地震波的现场放大效应(参见Chapter 10[Hayashi, 2018])。然而，由于噪声中任意混合了Rayliegh波和Love波，对这些测量的解释会变得十分困难(e.g., Bonnefoy-Claudet et al., 2006)。通过使用三分量记录的噪声互相关，使得我们可以分离Rayliegh波和Love波，从而克服这一困难(e.g., Workman et al., 2017)。将这种测量方法系统地应用于密集网络的数据，可以产生互补信息，这些信息可以补充到走时信息中，有助于更好地约束密度、Vp/Vs比(e.g., Lin et al., 2014)和方位各向异性(Lin and Schmandt, 2014)等参数。

尽管在噪声源任意分布的情况下，噪声互相关不能直接解释为介质的格林函数(即对类点力源的响应)，他们仍然可以被视为由未知大小和机制的虚拟源所激发的波场。**一个重要的性质是，当介质平滑变化是，互相关波场的局部是满足波动方程的**。当地球噪声主要由面波的控制的，相应的互相关可以使用2D波动方程进行近似(e.g., Lin et al., 2013)。在密集网络的情况下，这个虚拟波场的相位和振幅可以同时用带有振幅项的完整的2D程函方程进行解释(Lin and Ritzwoller, 2011)。
$$
\frac{1}{|C(\omega, r)|^{2}}=|\nabla \tau(\omega, r)|^{2}-\frac{\nabla^{2} A(\omega, r)}{A(\omega, r) \omega^{2}}\tag{7.14}
$$
其中$r$表示位置，$\tau$表示相位走时，$C$表示相速度，$\omega$表示频率，$A$表示振幅。**一方面，由于考虑了有限频效应，这种方位可以更为精确的解释相位走时信息**。图7.4 c-e给出了基于方程7.14的“Helmholtz”成像得到的Valhall油田区域的相速度图和方位各向异性分布。此外，方程7.14为解释噪声相关的振幅信息提供了一个统一的框架，并为推测其衰减和局部场地放大信息提供了可能(Lin et al., 2012; Bowden et al., 2015)。

#### 7.4 其他结论

在过去的十年里，ANSWT经历了快速的发展，已经成为了不同尺度的地震成像应用最为广泛的方法之一。与此同时，ANSWT距离成为一种"标准"和"常规"的方法仍相距甚远。正如本章所讨论的，ANSWT根据所使用的地震台网和噪声源分布的性质，重新组合了许多可能的方法。总的来说，ANSWT仍然是一个十分活跃的研究领域，仍有许多一阶问题值得我们去研究。

就像所有基于噪声的方法一样，要想改进ANSWT，就需要更好地了解噪声源的性质和分布。为了朝着这个方向前进，我们需要进一步发展描述噪声产生机制的物理模型，以及发展通过分析地震记录确定有效噪声源分布的方法。另外一个问题时数据预处理。我们需要继续改进数据预处理方法，并且要更好的理解数据预处理是如何影响最终的互相关和所测量的面波参数。**到目前为止，大多数预处理方法都是对单个台站和分量的记录进行预处理，而没有研究噪声中不同波的内部相干性**。这类波场的相干性可以使用基于台阵的方法进行研究。

最后，对虚拟波场的处理和从反演由噪声互相关重构的面波的新方案也将持续出现。

