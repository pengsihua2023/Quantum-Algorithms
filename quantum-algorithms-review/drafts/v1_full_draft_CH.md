# 量子算法及其应用：基础、进展、实践约束与未来方向

---

**摘要**

量子算法（quantum algorithms）构成量子计算研究的核心支柱之一，为经典计算机难以处理的特定问题类别提供了计算优势的可能性。在过去四十年间，该领域已从少数具有重要概念意义的成果，发展为涵盖搜索算法、代数算法、量子模拟、线性代数方法、变分方法及量子优化框架的广泛研究图景。与此同时，"量子优势"的内涵日益精细化，因为强渐近性结果并不会自动转化为在现实硬件上的实际优势。

本综述从理论与实践两个维度，对量子算法领域的主要研究进展进行系统梳理。我们首先概述与算法设计最为相关的基础概念，继而考察重要的历史里程碑，并将现代进展归纳为若干核心算法族。文章着重区分具有严格复杂性理论优势的算法，与主要面向近期启发式应用的算法，尤其是在含噪中等规模量子（noisy intermediate-scale quantum，NISQ）体制下的算法。此外，我们还系统审视四个主要应用领域——密码学与后量子安全、量子化学与材料科学、组合优化与运筹学，以及机器学习与数据分析——对各领域的研究进展、局限性及现实前景作出评估。

本文讨论当前制约该领域发展的实践约束，包括噪声、电路深度、资源估计、输入模型假设，以及与强经典基准进行公平比较的必要性。这些问题对于解读算法进展的相关断言至关重要，尤其是在优化和量子机器学习等领域，理论前景与实践证据之间并不总是吻合。

总体而言，量子算法研究已产生深刻的理论洞见，并形成了若干极具影响力的计算范式。然而，这些进展的长远影响，将取决于未来工作能否将形式上的加速优势与可扩展、资源可知、经验上可信的实现方案相连接。本综述旨在对该领域的发展历程、现状及开放性挑战提供结构化、均衡的论述。

**关键词：** 量子算法，量子计算，量子优势，量子模拟，变分量子算法，NISQ，容错量子计算，后量子密码学，量子机器学习，量子优化

---

## 1. 引言

量子计算已成为物理学、计算机科学、数学与工程学交叉前沿最具智识雄心、技术挑战性最强的研究方向之一。其核心在于利用量子力学原理——叠加（superposition）、纠缠（entanglement）与干涉（interference）——执行经典硬件难以胜任或效率低下的计算任务。尽管量子处理器的物理实现已获得大量关注与投入，但支撑整个研究大厦的理论基础，正是量子算法的研究。正是算法决定了量子计算机能在哪些问题上比经典计算机更高效，这种优势在何种条件下成立，以及实践中其优势幅度有多大。缺乏严格的算法结果，关于量子计算变革潜力的断言便只能停留于推测。因此，本综述将量子算法置于分析的核心，将硬件与实现视为重要但相对次要的问题加以讨论。

量子系统可作为计算资源这一思想，源于Feynman的奠基性观察：在经典计算机上模拟量子力学系统似乎需要指数级的开销，而一台自身按量子力学规律运作的计算机，或许能够自然地完成此类模拟 [Feynman, 1982]。Deutsch通过引入量子图灵机，并展示一个量子算法可以超越任何经典确定性算法的简单问题，将这一直觉形式化 [Deutsch, 1985]。这些早期概念性工作确立了量子计算优势在理论上的可能性，但对于这种优势能否延伸至具有实际意义的问题，仍未给出答案。

Shor对整数分解和离散对数计算的高效量子算法的发现，对这一问题给出了振聋发聩的回答 [Shor, 1994; Shor, 1997]——这表明量子计算机原则上能够破解被广泛部署的密码方案；与此同时，Grover算法针对无结构搜索问题实现了经过严格证明的平方加速 [Grover, 1996]。这些里程碑式的成果极大地推动了该领域的发展，并激励研究者在多样化的问题领域中广泛探索量子算法优势。此后三十年间，量子算法的研究图景大幅拓展，涵盖量子模拟 [Lloyd, 1996; Childs et al., 2018]、量子线性代数 [Harrow et al., 2009]、量子游走（quantum walks）[Ambainis, 2003; Childs et al., 2003]、变分与混合量子-经典方法 [Peruzzo et al., 2014; Farhi et al., 2014]，以及面向优化与机器学习的量子方法 [Biamonte et al., 2017]。若干综述与教材已对这一领域的部分内容进行了系统梳理 [Nielsen and Chuang, 2000; Childs and van Dam, 2010; Montanaro, 2016]。

尽管该领域发展迅速，但理论成果与实际部署之间的差距日益凸显。许多量子算法提供了经过严格论证的渐近加速，然而其实际相关性取决于较大的常数因子、错误纠正所需的大量量子比特开销，或者远超可预期硬件容量的输入规模。Preskill对当前技术阶段作出的影响深远的界定——含噪中等规模量子（NISQ）时代 [Preskill, 2018]——清晰表明：近期量子设备在缺乏完整容错能力的条件下运行，量子比特数量与电路深度均有限，且所受的噪声水平对算法能力构成了显著制约。

本综述围绕四个核心主题展开。其一，**按问题类型与作用机制分类**：理解量子算法最有成效的方式，并非将其视为单一类别，而是视为利用计算问题不同结构特征的不同算法族——周期性、对称性、图结构、特征值间隔或解空间几何。其二，**理论加速断言必须在具体资源需求的背景下加以诠释**：若一个算法所需的逻辑量子比特数量、门操作次数或错误纠正轮数，使得计算远超任何可预期设备的能力，那么指数级的渐近加速在实践中意义有限。其三，**始终如一地区分NISQ时代算法与容错算法**：这两种体制的差别不仅在于规模，更在于本质。其四，**强调与现有最优经典方法进行公平比较的必要性**：量子优势是一个相对性断言，而经典算法与硬件仍在持续改进 [Tang, 2019; Huang et al., 2020]。

本文其余部分的结构安排如下：第2节综述基础概念；第3节梳理历史发展；第4节考察主要算法族；第5节讨论应用领域；第6节分析实践约束；第7节列举开放问题；第8节提出结论性评述。

---

## 2. 与算法相关的量子计算基础

深入理解量子算法，需要熟悉量子力学与理论计算机科学中若干基础概念。本节着重从算法意义的角度介绍这些概念，力求以具有普遍适用性的方式呈现，面向不同科学背景的读者。我们遵循权威参考文献所建立的标准形式体系 [Nielsen and Chuang, 2000; Kaye et al., 2007]。

量子信息的基本单元是量子比特（qubit），即一个二能级量子系统，其状态由二维复希尔伯特空间中的一个向量描述。在计算基底下，量子比特的状态写作 |psi> = alpha|0> + beta|1>，其中 alpha 和 beta 为复振幅，满足 |alpha|^2 + |beta|^2 = 1。叠加并不意味着量子比特同时持有两个值，也不意味着量子计算机"同时尝试所有答案"。量子算法的计算能力，源于通过精心设计的操作序列对振幅进行操控的能力，使系统在测量时正确答案的振幅较大，而错误答案的振幅较小。朴素的"指数级并行"诠释长期以来是困惑的持久根源 [Aaronson, 2013]。

n 个量子比特构成的寄存器，占据维数为 2^n 的希尔伯特空间。这一状态空间的指数增长，是量子计算优势潜力的数学根源，但开发这一潜力需要通过纠缠与干涉对振幅进行协调操控。

**纠缠**（entanglement）是量子子系统之间一种无经典类比的关联形式。纠缠作为计算资源，使量子比特间的关联得以建立和利用。然而，仅有纠缠并不能保证加速；在没有干涉的情况下，纠缠是必要但不充分的条件 [Jozsa and Linden, 2003]。

**量子干涉**（quantum interference）可以说是支撑量子算法加速的最重要机制。由于量子振幅是复数，它们可以相长叠加或相消叠加。设计良好的量子算法通过安排操作，使正确答案的振幅相长干涉，而错误答案的振幅相消干涉。这一原则——通过干涉实现振幅放大——是从Deutsch-Jozsa算法到Grover搜索算法，再到Shor分解算法的运算核心 [Bernstein and Vazirani, 1997]。

标准框架是**量子电路模型**（quantum circuit model），其中一次计算是将一系列量子门——即酉变换——作用于量子比特寄存器，随后进行测量。单量子比特门操控振幅；双量子比特门（最常用的是CNOT门）产生纠缠。任意酉变换均可分解为单量子比特门与CNOT门（普适性）[Nielsen and Chuang, 2000]。电路深度（序列步骤数）、宽度（量子比特数）与门数量是主要的资源度量指标。

**测量**在本质上是概率性的，会不可逆地使叠加态坍缩。大多数量子算法以高概率给出正确答案；振幅放大 [Brassard et al., 2002] 可以系统地提高成功概率。

**计算复杂性理论**提供了严格的分析框架。复杂类 BQP（有界错误量子多项式时间，bounded-error quantum polynomial time）包含量子计算机能以有界错误在多项式时间内求解的问题。BQP 包含 P，但其与 NP 的精确关系至今仍是开放问题 [Watrous, 2009; Aaronson, 2013]。量子计算机并非万能的问题求解器：适合量子加速的问题构成了一个具体的、有结构的子集。量子优势的断言必须依据精确的复杂性理论假设加以评估 [Preskill, 2018]。

---

## 3. 量子算法的兴起：历史里程碑

量子算法的发展并非源于某一瞬间的单一洞见，而是跨越数十年的累积性智识探索。从早期的概念性提案到当代面向硬件的启发式方法，该领域经历了若干不同阶段，每一阶段都拓展了可借助量子加速处理的问题范围。

### 3.1 早期基础（1982—1994年）

量子算法的思想渊源通常可追溯至费曼（Feynman）1982年的论断：在经典计算机上模拟量子力学系统，所需资源似乎随系统规模呈指数增长，而依照量子力学原理运行的计算机则有可能高效地执行此类模拟 [Feynman, 1982]。尽管费曼的提议在严格意义上并非一个算法，但它确立了根本性的研究动机：存在某些计算任务，量子力学对其可能提供内在优势。

迈向将这一直觉形式化的第一个具体步骤，是Deutsch于1985年构造的量子图灵机（quantum Turing machine）及其关联算法——该算法能够以少于任何经典确定性程序所需的求值次数，确定布尔函数的某一全局性质 [Deutsch, 1985]。随后，Deutsch与Jozsa对此思想的深化延伸至一个承诺问题（promise problem）：量子算法仅需一次查询即可确定性地给出结论，而任何确定性经典算法则需要指数量级的查询次数 [Deutsch and Jozsa, 1992]。Bernstein-Vazirani算法（Bernstein-Vazirani algorithm）进一步精化了这一图景，展示了一个可由单次量子查询解决、而经典算法需要线性次查询的问题 [Bernstein and Vazirani, 1997]。

一项关键进展来自Simon算法（Simon's algorithm），该算法处理的是寻找表征二对一函数的隐藏比特串问题 [Simon, 1997]。Simon的构造在有界误差情形下实现了量子与经典查询复杂度之间的指数级分离。尤为重要的是，该算法引入了一种结构性范式，并被证明具有深远影响：将计算问题归约为周期性检测，再通过量子傅里叶采样（quantum Fourier sampling）提取隐藏的代数结构加以求解。这一范式很快成为该领域最具代表性成果的核心引擎。

### 3.2 突破性时代（1994—1996年）

1994年，Shor证明了整数分解（integer factoring）与离散对数计算——这两类问题被普遍认为经典上难以处理，并构成RSA与Diffie-Hellman密码体系安全性的基础——可在量子计算机上以多项式时间求解 [Shor, 1997]。该算法的机制直接建立在Simon范式之上：分解问题被归约为求模幂函数（modular exponentiation function）的周期问题，继而通过循环群上的量子傅里叶变换（quantum Fourier transform）加以解决。这一结论的影响是即时而深远的，不仅涉及密码学，更触及计算复杂性理论的理论基础。

两年后，Grover给出了互补性的结果：一个用于无结构搜索（unstructured search）的量子算法，能够在N个无序候选项中以 $O(\sqrt{N})$ 次搜索谕示（oracle）求值找到目标项，而经典方法则需要 $\Omega(N)$ 次求值 [Grover, 1996]。尽管加速幅度为平方级而非指数级，其普适性仍令人瞩目。此外，Bennett等人证明了Grover算法的渐近最优性：不存在任何量子算法能以少于 $\Omega(\sqrt{N})$ 次查询解决无结构搜索问题 [Bennett et al., 1997]。这一最优性结论为量子计算在无结构问题上的能力设定了严格上界，并阐明了指数级加速需要依赖可利用的问题结构。

Shor算法与Grover算法共同划定了量子算法格局的两极：针对具有丰富代数结构问题的指数级加速，以及针对一般性搜索问题的平方级加速。这一二元结构至今仍持续塑造着该领域的研究议程。

### 3.3 算法范式的扩展（1990年代末—2000年代）

在奠基性突破之后，此后十年见证了算法工具箱的大幅扩展。一项关键进展是量子相位估计（量子相位估计，QPE）的形式化——该方法提供了从幺正算符中提取本征值的通用程序 [Kitaev, 1995; Cleve et al., 1998]。量子相位估计迅速成为量子算法设计中最为通用的子程序之一，在Shor算法、量子模拟协议及大量后续构造中均居于核心地位。

Brassard等人将Grover搜索推广至振幅放大（振幅放大，amplitude amplification）与振幅估计（振幅估计，amplitude estimation）框架，使任意量子算法的成功概率均可得到提升，并能以平方级加速估计特定测量结果的概率 [Brassard et al., 2002]。这些技术将Grover型加速的适用范围大幅拓展至无结构搜索之外。

一个独立而颇具影响力的范式源自对量子游走（量子游走，quantum walks）的研究。离散时间量子游走（discrete-time quantum walks）被形式化 [Aharonov et al., 2001]，其算法潜力随后通过Ambainis的元素相异性算法（element distinctness algorithm） [Ambainis, 2003] 以及连续时间量子游走（continuous-time quantum walks）在某些图结构遍历中实现的指数级加速 [Childs et al., 2003] 得到了充分展示。量子游走提供了一种与基于傅里叶方法本质上不同的算法框架。

哈密顿量模拟（哈密顿量模拟，Hamiltonian simulation）在这一时期也趋于成熟。Lloyd于1996年证明局域哈密顿量可通过乘积公式（product formulas）高效模拟 [Lloyd, 1996]，此后相继出现了精度不断提升的算法，尤以Berry等人针对稀疏哈密顿量模拟实现近最优复杂度的工作为代表 [Berry et al., 2007]。

这一时期最具争议性的贡献或许当属HHL算法（HHL算法），该算法证明量子计算机在特定条件下能够以指数级更快的速度求解线性方程组，超越已知经典方法 [Harrow, Hassidim, and Lloyd, 2009]。该算法为机器学习、优化及科学计算开辟了猜想性的关联路径，但后续分析揭示，其实际适用性对输入准备、输出读取、条件数及稀疏性等方面的假设具有高度敏感性。

### 3.4 NISQ时代的适应（2014年至今）

最近这一阶段受到近期硬件现实的深刻塑造。变分量子本征求解器（VQE，变分量子本征求解器）由Peruzzo等人提出，采用混合量子-经典方法：参数化量子线路制备试探态，经典优化器调整参数以最小化能量期望值 [Peruzzo et al., 2014]。此后不久，Farhi、Goldstone与Gutmann提出了量子近似优化算法（QAOA，量子近似优化算法），将类似的变分思想应用于组合优化问题 [Farhi, Goldstone, and Gutmann, 2014]。

Preskill于2018年将当前技术阶段界定为含噪中等规模量子（NISQ，含噪中等规模量子）时代，为这一转变提供了概念框架与命名 [Preskill, 2018]。NISQ范式将浅层线路深度、噪声鲁棒性以及量子-经典混合反馈回路置于渐近复杂度保证之上。尽管这种务实取向催生了大量研究活动，但同时也引发了若干张力：变分算法通常缺乏严格的性能保证，且对实际相关实例证明明确量子优势仍是一项开放性挑战。

### 3.5 小结

量子算法的历史可理解为经历了四个相互交叠的阶段：奠定非经典算法行为可能性的概念基础阶段；证明指数级与平方级加速均可实现的里程碑突破阶段；涵盖相位估计、振幅放大、量子游走、哈密顿量模拟及量子线性代数的算法范式持续扩展阶段；以及适应近期硬件约束的当代阶段。每一阶段都拓展了量子算法至少在原则上可处理的问题范围。

---

## 4. 核心算法族与机制

量子算法的全貌，最好不要理解为各个独立结果的扁平化目录，而应视为若干算法族的集合——每个算法族均围绕一种利用量子叠加、干涉或纠缠的独特机制而构建。本节对主要算法族进行综述，就每一族分别考察其所针对的问题类别、核心量子机制、代表性算法、理论意义、实际局限性及开放问题。

### 4.1 搜索与振幅放大

Grover算法 [Grover, 1996] 针对无结构搜索问题——从N个无序候选项中识别目标项——通过迭代施用一个将目标态相位翻转的谕示算符以及一个放大目标态振幅的扩散算符，以 $O(\sqrt{N})$ 次量子查询实现目标。每次迭代在二维子空间中将量子态向目标旋转，经过约 $(\pi/4)\sqrt{N}$ 次迭代后，目标项以高概率被找到。

该基本原理由Brassard等人 [2002] 推广，可用于提升任意量子算法的成功概率。振幅估计可估计成功概率本身，并在量子计数、近似积分及蒙特卡罗加速中充当子程序 [Montanaro, 2015]。

Grover算法被证明是最优的：Bennett等人 [1997] 与Zalka [1999] 独立证明，任何用于无结构搜索的量子算法均需至少 $\Omega(\sqrt{N})$ 次查询。这一下界是量子复杂性理论中少数几个无条件分离结果之一。该框架已被推广至回溯算法的量子加速 [Montanaro, 2018] 以及变时振幅放大（variable-time amplitude amplification） [Ambainis, 2012]。

平方级加速虽然是无条件的，但远比指数级分离温和。在实际中，实现谕示算符的代价往往主导资源开销，而对于有结构的搜索问题，经典启发式方法常常优于朴素的无结构搜索模型。

### 4.2 分解、周期查找与隐子群问题

Shor算法 [Shor, 1997] 将分解问题归约为周期查找，并利用量子傅里叶变换（QFT，量子傅里叶变换）求解后者。给定 $f(x) = a^x \bmod N$，该算法制备叠加态，在叠加态上求值 $f$，再对输入寄存器施用QFT。干涉图样使概率集中于与周期 $r$ 相关的值，由此可推导出 $N$ 的非平凡因子。该算法运行时间为 $O(n^3)$，相对于已知最佳经典方法实现了指数级加速。

隐子群问题（HSP，隐子群问题）提供了一个涵盖分解与离散对数的通用代数框架 [Lomonaco and Kauffman, 2002]。对于阿贝尔群，QFT可高效求解HSP。对于非阿贝尔群，情形则远不乐观：图同构问题（graph isomorphism）可被表述为对称群上的HSP，格问题（lattice problems）与二面体群上的HSP相关，但针对这些情形的高效量子算法至今仍难以实现 [Regev, 2004]。

其密码学意义深远，推动了美国国家标准与技术研究院（NIST）后量子密码学（Post-Quantum Cryptography）标准化进程 [NIST, 2022]。然而，针对密码学相关密钥长度实现Shor算法，远超当前硬件能力：Gidney与Ekera [2021] 估计，分解一个2048位RSA整数约需2000万个含噪物理量子比特。

### 4.3 量子模拟

模拟量子多体系统（quantum many-body systems）的动力学与平衡性质，在一般情形下对经典计算机而言是难以处理的：希尔伯特空间（Hilbert space）的维度随粒子数指数增长。这正是Feynman [1982] 提出量子计算设想的根本动机。

针对哈密顿量模拟，已发展出多种算法策略。乘积公式（Trotterization，乘积公式/Trotter分解）将时间演化分解为一系列较简单指数算符的乘积 [Lloyd, 1996]。高阶Suzuki-Trotter分解（higher-order Suzuki-Trotter decompositions）改进了误差复杂度。尽管形式简单，乘积公式已被证明具有相当强的实用性，其实际表现往往优于最坏情形误差界所预测的结果 [Childs et al., 2018]。

更近期的技术实现了近最优复杂度。幺正算符线性组合（LCU，幺正算符线性组合）方法 [Childs and Wiebe, 2012] 将目标运算表示为较简单幺正算符的加权和。量子信号处理（quantum signal processing） [Low and Chuang, 2017] 与量子奇异值变换（QSVT） [Gilyen et al., 2019] 实现了最优查询复杂度，并提供了统一的理论框架。

哈密顿量模拟是BQP完全的（BQP-complete） [Osborne, 2012]，确立了量子模拟作为量子计算最自然应用的地位。其应用涵盖量子化学 [Aspuru-Guzik et al., 2005]、凝聚态物理及高能物理 [Georgescu et al., 2014]。针对有实用价值的量子化学模拟的资源估计，表明此类演示超出了近期可实现范围 [Reiher et al., 2017]。

### 4.4 量子相位估计与本征值问题

量子相位估计（QPE）提供了从幺正算符中系统性提取本征值的程序，是一个基础性子程序 [Kitaev, 1995; Cleve et al., 1998]。给定幺正算符 $U$ 及其本征态 $|\psi\rangle$，满足 $U|\psi\rangle = e^{2\pi i\phi}|\psi\rangle$，QPE利用 $n$ 个辅助量子比特、$U^{2^k}$ 的受控施用以及逆QFT，将 $\phi$ 估计至 $n$ 位精度。

QPE是Shor算法、HHL算法及量子化学模拟的关键组成部分。标准QPE需要较深的线路，要求容错运行。迭代相位估计（iterative phase estimation）将辅助量子比特开销降至单个量子比特 [Svore et al., 2014]。QSVT框架 [Gilyen et al., 2019] 厘清了QPE在更广泛的最优量子算法类中的结构性角色，揭示了此前看似独立的若干技术之间的深层联系。

### 4.5 量子线性代数

HHL算法 [Harrow, Hassidim, and Lloyd, 2009] 在特定条件下提供了求解 $Ax = b$ 的指数级更快方法。该算法将 $b$ 编码为量子态，施用QPE将其在 $A$ 的本征基下分解，执行受控旋转以对本征值求逆，再反计算相位估计。所得结果是与 $A^{-1}|b\rangle$ 成比例的量子态，制备时间为 $O(\log(N) \cdot s^2 \cdot \kappa^2 / \epsilon)$。

HHL算法催生了量子机器学习 [Rebentrost et al., 2014]、量子微分方程求解器 [Berry, 2014]、量子推荐系统 [Kerenidis and Prakash, 2016] 及量子主成分分析 [Lloyd et al., 2014] 等方向的大量提案。

然而，实际适用性需要多个条件同时满足：$|b\rangle$ 的高效量子态制备、稀疏或可高效分解的矩阵、较小的条件数，以及以量子形式输出的充分性。Tang [2019] 证明，对于特定输入模型，存在具有可比性能的经典算法——这一去量子化（dequantization）方案已推广至其他量子启发的经典算法 [Chia et al., 2020]，从而大幅缩小了真正具有超多项式加速的适用范围。

### 4.6 量子游走算法

量子游走（量子游走）为搜索、图论及代数问题提供了一种替代性范式。离散时间量子游走 [Aharonov et al., 2001] 在同时包含位置自由度与硬币自由度的希尔伯特空间上运作。连续时间量子游走 [Farhi and Gutmann, 1998] 以图的邻接矩阵（adjacency matrix）作为哈密顿量进行演化。两种表述均可实现空间搜索的平方级加速 [Childs and Goldstone, 2004]。

Ambainis [2007] 针对元素相异性问题获得了最优的 $O(N^{2/3})$ 算法。Magniez等人 [2011] 发展了量子游走搜索算法的MNRS框架。Childs [2009] 证明了连续时间量子游走的计算普适性（computational universality）。量子游走算法往往具有问题特异性，其在近期硬件上的实际实现在很大程度上仍有待探索。

### 4.7 变分与混合量子-经典算法

变分与混合算法是专门针对NISQ器件约束而发展起来的。变分方法以经典参数对量子线路 $U(\theta)$ 进行参数化，测量目标函数，并通过经典优化迭代调整参数。

VQE [Peruzzo et al., 2014] 以基态能量为目标。QAOA [Farhi, Goldstone, and Gutmann, 2014] 将变分原理应用于组合优化。这些算法可适应浅层线路，并可针对特定硬件拓扑结构进行调整。

核心挑战包括贫瘠高原（barren plateau，贫瘠高原）现象 [McClean et al., 2018]——对于一般参数化线路，代价函数的梯度景观呈指数级平坦化，使经典优化难以为继。这一问题源于过度纠缠、全局代价函数、噪声，以及缺乏问题结构的硬件高效拟设（hardware-efficient ansatze） [Cerezo et al., 2021]。误差缓解技术（error mitigation techniques） [Temme et al., 2017; Endo et al., 2018] 能够降低偏差，但引入了不利的采样开销。变分方法能否在实际规模上实现有意义的量子优势，是当前该领域争议最为激烈的问题之一。

### 4.8 量子优化

组合优化（combinatorial optimization）涵盖了大量具有重要实际意义的问题。量子退火（quantum annealing） [Kadowaki and Nishimori, 1998] 将目标函数编码为Ising哈密顿量的基态，并利用量子隧穿效应（quantum tunneling） [Farhi et al., 2001]。绝热量子计算（adiabatic quantum computation）与线路模型之间的等价性 [Aharonov et al., 2007] 在原则上确立了其计算普适性。

QAOA代表了一种基于门模型（gate-model）的方法。Farhi与Harrow [2016] 证明，在合理的复杂性假设下，低深度QAOA无法被经典方法高效模拟，这表明存在一种计算分离——尽管未必意味着实际优势。

量子优化中量子优势的实证证据十分有限。基准测试研究普遍发现经典方法仍具竞争力甚至更优 [Guerreschi and Matsuura, 2019]。除非BQP包含NP（这并不被预期成立），否则量子计算机无法在一般情形下高效求解NP难问题。因此，量子优化中的量子优势很可能以多项式级加速或针对特定问题结构的优势形式呈现，而非泛化的指数级加速。

---

## 5. 量子算法的应用

前述各节主要从量子算法的计算机制与理论性质角度对其加以审视。本节转换视角，着眼于应用领域，探讨这些算法在哪些方面可能具备实际价值。一个反复出现的主题由此浮现：尽管量子算法在众多领域展现出令人信服的理论优势，但从算法加速到实际部署的路径，远比早期的乐观预期更为漫长、更具不确定性。

### 5.1 密码学与后量子安全

或许量子计算迄今影响最深远的实际应用，恰恰是那个根本无需真正建造量子计算机即可显现的领域。Shor算法 [Shor, 1997] 证明，足够强大的量子计算机将使当前部署最为广泛的公钥密码体系——RSA、椭圆曲线密码学（Elliptic Curve Cryptography, ECC）与Diffie-Hellman密钥交换——从根本上失去安全性。这一理论结果已催生了全球范围内对密码基础设施进行重新设计的努力。

其资源需求极为可观。Gidney与Ekera [2021] 估计，对一个2048位RSA模数进行因式分解，大约需要两千万个含噪物理量子比特。大多数专家评估认为，具备密码学意义的量子计算机至少需要十年乃至更长时间才能实现 [Mosca and Piani, 2023]。

尽管存在时间线上的不确定性，密码学界已在"现在收获、日后解密"（harvest now, decrypt later）威胁的驱动下，以高度紧迫感作出回应。美国国家标准与技术研究院（NIST）于2022年完成后量子密码学标准化进程，选定了基于格问题（CRYSTALS-Kyber、CRYSTALS-Dilithium、FALCON）与基于哈希方案（SPHINCS+）的算法 [NIST, 2022]。向上述后量子标准的迁移工作已在政府、金融及科技行业全面展开。

作为算法方案的补充，量子密钥分发（Quantum Key Distribution, QKD，量子密钥分发）提供了信息论意义上的安全保证。BB84协议 [Bennett and Brassard, 1984] 与E91协议 [Ekert, 1991] 的安全性建立在量子力学定律之上，而非依赖计算困难性假设。基于卫星的QKD已将可达传输距离显著延伸 [Liao et al., 2017]，但受制于基础设施需求，大规模部署仍十分有限。

Grover算法对对称密码学的影响则相对有限：将密钥长度加倍即足以维持等效安全性 [Grassl et al., 2016]。综上所述，量子算法对密码学的影响是真实存在的，并已对实践产生深刻影响，尽管能够利用这些漏洞的量子计算机目前尚不存在。

### 5.2 量子化学与材料科学

量子化学与材料科学被普遍认为是量子计算最自然、最具前景的应用领域。其核心动机直截了当：模拟分子与材料中电子的行为本质上是一个量子力学问题，而经典计算机在表征量子态方面面临根本性困难——随着系统规模增长，量子态的复杂度呈指数级扩张。

密度泛函理论（Density Functional Theory, DFT，密度泛函理论）、耦合簇方法（Coupled Cluster Methods，耦合簇方法，尤其是CCSD(T)）、密度矩阵重正化群（Density Matrix Renormalization Group, DMRG，密度矩阵重正化群）以及张量网络方法（Tensor Network Methods，张量网络方法）等经典方法，通过不同的近似策略在许多体系中表现出色，但在处理强关联电子体系时却力不从心 [Motta and Rice, 2022]。

量子算法提供了一种本质上不同的途径。Aspuru-Guzik等人 [2005] 提出将量子相位估计应用于化学模拟，原则上可以以多项式资源代价提取基态能量。面向近期设备，变分量子本征求解器（Variational Quantum Eigensolver, VQE）[Peruzzo et al., 2014] 提供了一种混合方法。VQE已在小型分子体系上得到验证：Kandala等人 [2017] 在超导量子比特上计算了H₂、LiH和BeH₂的基态能量，而Google AI量子团队 [2020] 则在十二量子比特系统上进行了Hartree-Fock计算。

频繁被援引的重大挑战是对固氮酶（nitrogenase）铁钼辅因子（FeMo cofactor, FeMoCo）的模拟。Reiher等人 [2017] 估计，对FeMoCo进行量子模拟大约需要一百个逻辑量子比特及数十亿个T门。Lee等人 [2021] 提出了基于张量超缩并（tensor hypercontraction）的更高效算法，使门的数量减少了数个量级，但整体资源需求仍远超现有硬件的承受能力。Goings等人 [2022] 进行了全面评估，得出结论认为，要在化学领域实现有实用价值的量子优势，仍需取得重大进一步突破。

一个关键考量是经典方法的竞争强度。对于弱关联体系，经典方法可在可接受的计算成本下达到化学精度。量子优势最有可能在强关联体系中得以实现——如过渡金属配合物、某些催化中间体以及奇异材料相——这些正是经典方法力有不逮之处 [Williams et al., 2020]。核心悬而未决的问题在于：在何种分子规模与关联强度下，实用优势的跨越点将会出现。

### 5.3 优化与运筹学

组合优化问题广泛存在于工业与商业领域。量子加速的潜力已吸引了大量商业投入，使其成为当前最受关注的应用方向之一。然而，这也是一个理想与实证优势之间差距尤为显著的领域。

量子近似优化算法（Quantum Approximate Optimization Algorithm, QAOA）[Farhi et al., 2014] 将优化目标编码为量子哈密顿量，并利用交替的问题酉算子与混合酉算子层叠加以求解。量子退火（Quantum Annealing，量子退火）在D-Wave商业系统中得到实现 [Johnson et al., 2011]，利用量子隧穿效应遍历能量景观。

金融行业在此方向尤为活跃。Orus等人 [2019] 综述了量子计算在金融领域的应用，将投资组合优化、风险分析和期权定价列为主要目标。Stamatopoulos等人 [2020] 展示了基于振幅估计的衍生品定价量子算法。在物流领域，Harwood等人 [2021] 探索了量子方法在车辆路径规划中的应用。

基准测试的记录令人警醒。Guerreschi与Matsuura [2019] 得出结论，QAOA若要实现量子优势，所需电路深度将远超近期设备所能支持的范围。D-Wave量子退火实验结论亦存在争议：Ronnow等人 [2014] 在将优化后的经典算法纳入比较后，并未发现可归因于量子效应的确定性加速 [Albash and Lidar, 2018]。

当前态势的特征是商业预期高涨而近期优势的实证依据匮乏。目前尚无理论结果能为NP难优化问题建立无条件量子加速，实现实用优势可能有赖于识别出特定问题结构，使量子方法能够利用经典算法无法捕捉的特征。

### 5.4 机器学习与数据分析

量子计算与机器学习的交叉地带引发了强烈兴趣，同时也激起了同样强烈的争论。早期提案在很大程度上受HHL算法启发，提出了颠覆性的加速前景：量子支持向量机（Quantum Support Vector Machine，量子支持向量机）[Rebentrost et al., 2014]、量子主成分分析（Quantum Principal Component Analysis，量子主成分分析）[Lloyd et al., 2014] 以及量子神经网络（Quantum Neural Network，量子神经网络）。

后续分析揭示了根本性障碍。Aaronson [2015] 指出了数据加载瓶颈（data loading bottleneck，数据加载瓶颈）：将经典数据编码为量子态通常需要与数据规模成正比的资源，从而抵消了指数级加速。Tang [2019] 证明，受量子技术启发的经典算法在相似数据访问假设下可以达到相当的性能，由此开创了去量子化（dequantization，去量子化）研究方向，大幅削弱了量子机器学习的加速论断。

量子核方法（Quantum Kernel Methods，量子核方法）[Havlicek et al., 2019; Schuld and Killoran, 2019] 探索将量子电路用作特征映射，从而规避部分数据加载问题。然而，对于实际数据集，证明其相对于经典核方法的优势仍是一个开放问题 [Huang et al., 2021]。贫瘠平台（barren plateau）现象 [McClean et al., 2018] 限制了变分量子机器学习架构在大规模条件下的可训练性。

若干研究方向仍具有前景。量子计算机在涉及量子传感器或量子实验所产生的固有量子数据的学习任务中，可能具备优势 [Huang et al., 2022]。当前态势是重新校准：宏观加速论断已被大幅削弱，该领域正转向这样一种认识——优势可能仅在涉及量子原生数据的特定细分场景中涌现。

纵观上述四个应用领域，一个共同模式清晰可辨：量子算法为潜在优势提供了坚实的理论基础，但将其转化为实际收益受到硬件限制、资源需求、经典竞争和基准测试挑战的多重制约。密码学是量子算法已对实践产生变革性影响的领域，尤为突出。量子化学在最终实现实际优势方面具有最为充分的科学依据。优化与机器学习在当前能力与已证明的实用价值之间面临最显著的鸿沟。

---

## 6. 实际约束与理论和现实之间的鸿沟

量子算法的理论图景在众多领域展现出计算优势的诱人愿景。然而，将这些理论承诺转化为已实现的实际收益，面临着重重艰巨障碍。

### 6.1 含噪中等规模量子时代的局限

含噪中等规模量子（Noisy Intermediate-Scale Quantum, NISQ，含噪中等规模量子）这一术语，用以描述由大约50至1000个量子比特构成、在没有完整量子纠错情况下运行的设备 [Preskill, 2018]。这类设备受三个相互关联的约束所定义：量子比特数量不足、门保真度远低于深层电路所需的阈值，以及有限相干时间对电路深度施加的硬性上限。

当前各硬件平台各具不同的权衡特性。超导量子比特处理器（Superconducting Qubit Processor，超导量子比特处理器，IBM、Google）具备快速门操作和最多量子比特数的优势，但连接性有限且相干时间短。囚禁离子系统（Trapped-Ion System，囚禁离子系统，IonQ、Quantinuum）提供更高的门保真度和全互联拓扑，但门操作速度较慢。光子架构（Photonic Architecture，光子架构，Xanadu）可在室温下运行，但在确定性双量子比特门的实现方面面临挑战。

Google进行的里程碑实验中，53量子比特Sycamore处理器在约200秒内完成了对随机量子电路的采样——这一任务据估计需要经典计算机耗费数千年——从而为量子计算优越性（quantum computational supremacy，量子计算优越性）建立了概念验证 [Arute et al., 2019]。然而，随后经典算法的改进大幅缩小了所估计的经典计算成本 [Pan and Zhang, 2022]。IBM利用127量子比特Eagle处理器进行的实验提供了证据，表明含噪量子电路能够产生超越实际经典模拟能力的可靠期望值 [Kim et al., 2023]。尽管上述工作代表了切实的进展，但均尚未达到在具有公认实际价值的问题上展示算法优势的水平。

### 6.2 容错量子计算的资源需求

超越NISQ局限的路径有赖于量子纠错（quantum error correction，量子纠错）。表面码（surface code，表面码）在物理错误率低于约1%的阈值条件下实现容错 [Fowler et al., 2012]。其开销极为可观：编码单个逻辑量子比特可能需要数千个物理量子比特。

对具有计算意义问题的资源需求极为惊人。Gidney与Ekera估计，对2048位RSA进行因式分解约需两千万个物理量子比特 [Gidney and Ekera, 2021]。Reiher等人估计，模拟FeMoCo需要数百个逻辑量子比特和数十亿个T门 [Reiher et al., 2017]。Lee等人提出了更高效的方法，但仍要求远超现有能力的容错硬件 [Lee et al., 2021]。

尽管如此，近期进展仍提供了谨慎乐观的依据。Google量子人工智能团队证明，将表面码规模从距离3扩展至距离5，逻辑错误率随之降低，跨越了盈亏平衡阈值 [Google Quantum AI, 2023]。这证实了量子纠错的基本原理在实践中是可以实现的，即便迈向全面容错的道路依然漫长。

### 6.3 数据访问、预言机假设与隐藏代价

许多备受称誉的量子加速是在查询复杂性模型（query complexity model，查询复杂性模型）中得到证明的——在该模型中，算法通过预言机（oracle）访问输入 [Aaronson, 2015]。当预言机必须以显式电路实现时，这一框架可能遮蔽实际代价。

数据加载问题（data loading problem，数据加载问题）对处理经典数据的算法而言尤为突出。量子随机存取存储器（Quantum Random-Access Memory, QRAM，量子随机存取存储器）由Giovannetti、Lloyd与Maccone提出，可在与数据库规模的对数成正比的时间内实现叠加查询 [Giovannetti et al., 2008]。然而，QRAM的实际实现高度不确定：所提出的架构需要错误率极低的量子路由器，且目前尚无令人信服的物理实现方案。

态制备的代价往往被低估。一个在特定量子态条件下实现指数加速的算法，若制备该量子态本身的代价呈指数级，则可能毫无优势可言。类似地，从量子输出中提取经典信息需要测量，而量子态层析重建的代价随量子比特数目呈指数增长。

### 6.4 公平经典比较的必要性

量子启发式方法有时是与较弱的经典基准进行比较，而非与最先进的方法对比。Guerreschi与Matsuura证明，对于可访问的问题规模，QAOA的表现劣于经过良好调优的经典启发式算法 [Guerreschi and Matsuura, 2019]。

经典算法并非静止不动。去量子化研究方向 [Tang, 2019]，以及张量网络方法、随机数值线性代数和蒙特卡洛算法的进展，已缩小了量子算法曾似乎占据优势的差距。渐近优势并不自动转化为实际优势：渐近符号所隐含的常数与前置因子可能极为庞大，在纳入纠错开销后尤为如此。

上述观察强调了建立标准化基准测试规范的必要性：须与最优经典方法进行比较，须计入完整的资源代价，并在具有实际意义的问题实例上评估性能。

### 6.5 小结

理论承诺与实践现实之间的鸿沟，仍是核心挑战之所在。弥合这一鸿沟需要在多个方面同步取得进展：硬件改进、更高效的纠错方案、面向资源约束的算法设计、对假设条件的如实核算，以及严格的经典对比。

---

## 7. 开放问题与未来展望

量子算法研究的日趋成熟，不仅积累了丰富的技术方法，也使该领域对最迫切开放问题的认识愈发清晰。

### 7.1 面向资源约束的算法设计

一个标志性转变是研究重心从纯粹的渐近分析转向具体的资源估算。对 Shor 因式分解算法与量子化学模拟的资源分析揭示了主要开销所在，并推动了更高效实现方案的发展 [Gidney and Ekera, 2021; Lee et al., 2021]。

一个颇具前景的中间阶段是早期容错量子计算（early fault-tolerant quantum computing），在该阶段可使用数量有限的经纠错逻辑量子比特。Campbell 专门针对这一阶段提出了相应算法 [Campbell, 2021]。识别适用于这一过渡阶段的算法，是近期最具影响力的研究方向之一。

### 7.2 经典-量子混合工作流

近期量子计算机在更大规模的计算工作流中，将主要作为专用加速器发挥作用。误差缓减技术（error mitigation techniques）——如概率误差消除 [Temme et al., 2017] 与准概率分解 [Li and Benjamin, 2017]——以增加采样开销为代价，扩展了含噪设备的实际应用范围。面向特定计算瓶颈而非通用优势的领域专用算法设计，或将更具成效。

### 7.3 迈向有意义的基准测试标准

标准化基准测试规程的缺失，阻碍了严格的性能评估。面向应用的基准测试（application-oriented benchmarks）针对公认具有实际价值的特定任务评估量子计算机，代表了一个富有成效的方向 [Lubinski et al., 2023]。此类基准测试必须纳入与最优经典方法的比较，并报告完整的资源开销。可重复性与开放获取的基准测试问题集将使整个学术界受益匪浅。

### 7.4 基础性开放问题

若干基础性问题至今悬而未决。在充分考虑纠错、数据加载与输出提取开销的现实条件下，量子优势对哪些问题依然成立？在实现完全容错之前，量子优势能否在具有实际意义的问题上得到证明，这一问题至关重要。对量子加速更严格的下界估计将具有极高价值。识别哪些结构特征使问题适合量子加速，仍是理论研究的核心挑战。

### 7.5 新兴算法方向

面向微分方程的量子算法，对某些特定类别的问题承诺指数级加速，在工程与物理科学领域具有广泛应用前景 [Berry et al., 2017]。量子蒙特卡洛估算（quantum Monte Carlo estimation）为广泛的估算问题提供了二次方量级的改进 [Montanaro, 2015]。量子低密度奇偶校验码（quantum LDPC codes）的进展或将开辟新的算法可能性。受量子启发的经典算法（quantum-inspired classical algorithms）作为量子算法研究的重要副产品，产生了若干若非受量子方法启发则难以发现的新型经典算法 [Bharti et al., 2022]。

### 7.6 小结

该领域正经历富有成效的成熟演进，研究焦点已从"量子计算机能否更快？"转向"量子计算在何时、针对何种问题、在多大程度上真正有用？"回答这一问题，需要算法设计、复杂性理论、硬件工程、纠错技术与应用科学之间持续深入的交叉融合。

---

## 8. 结论

量子算法的研究是现代计算科学中智识内涵最为丰富、影响最为深远的研究纲领之一。历经约四十年的发展，该领域经历了数个不同阶段：20 世纪 80 年代至 90 年代初期的概念奠基，90 年代中期的里程碑式突破，随后的范式持续扩展，以及当前适应近期硬件约束的时代。

Deutsch、Jozsa、Simon、Bernstein 与 Vazirani 的奠基性贡献确立了量子计算在严格定义的条件下能够提供可证明的超越经典计算的优势 [Deutsch and Jozsa, 1992; Simon, 1997; Bernstein and Vazirani, 1997]。Shor 的因式分解算法对一个具有深远实际意义的问题展示了指数级量子加速 [Shor, 1997]。Grover 的搜索算法为非结构化问题确立了可证明最优的二次方加速 [Grover, 1996]。在这些里程碑成果之外，量子算法研究还延伸至量子模拟 [Lloyd, 1996; Childs et al., 2018]、量子线性代数 [Harrow et al., 2009]、量子游走 [Childs et al., 2003; Ambainis, 2007] 以及变分方法 [Peruzzo et al., 2014; Cerezo et al., 2021]。

应用前景既令人期待，又参差不齐。在密码学领域，Shor 算法所构成的威胁已催化了向后量子标准的全球性过渡。在量子化学领域，量子模拟提供了最具说服力的长期应用场景，并存在真正超越经典计算可达范围的明确目标 [Reiher et al., 2017]。在优化领域，量子方法优于最优经典方法的严格证据仍然有限。在机器学习领域，初期的热情已因去量子化结果 [Tang, 2019] 与数据加载约束而趋于冷静。

贯穿全局的核心张力，在于理论基础的深厚性与实际约束的严峻性之间的矛盾。含噪中等规模量子（NISQ）时代产生了有价值的阶段性成果 [Arute et al., 2019; Kim et al., 2023]，但影响最为深远的算法需要容错硬件，其资源估算仍然令人望而生畏 [Gidney and Ekera, 2021; Fowler et al., 2012]。预言机与数据访问假设引入了隐性成本 [Aaronson, 2015; Giovannetti et al., 2008]，而经典算法的持续改进确保了量子优势的门槛始终是一个移动的标靶。

前进之路是多维度的：面向资源约束的算法设计、经典-量子混合工作流、误差缓减技术 [Temme et al., 2017; Li and Benjamin, 2017]、与最优经典方法的公正基准比较 [Lubinski et al., 2023]，以及领域专用算法设计。该领域的学术严肃性有赖于保持诚实、均衡的评价——在认可真实进展的同时，避免对近期能力的过度渲染。

量子算法代表着一批具有真正科学深度的研究成果，证明了量子力学原理可以以经典计算无可比拟的方式被用于计算目的。针对结构化代数问题的指数级加速、搜索与估算的二次方量级改进，以及模拟量子系统的天然适配性，均是具有持久意义的成就。然而，将这种理论上的丰富性转化为实际的计算优势——针对真正重要的问题、在现有硬件上、相较于持续改进的经典方法——仍是未来数十年的核心挑战。应对这一挑战，需要在算法设计、复杂性理论、硬件工程、纠错技术与应用科学等多个维度上持续深入努力，并以严格、诚实、注重资源约束的评价原则为根本导向。

---

---

## 参考文献

*以下参考文献按英文原格式列出（学术惯例）：*

[1] Aaronson, S. (2013). *Quantum Computing since Democritus*. Cambridge University Press.

[2] Aaronson, S. (2015). Read the fine print. *Nature Physics*, 11(4), 291-293.

[3] Abbas, A., et al. (2024). Challenges and opportunities in quantum optimization. *Nature Reviews Physics*, 6, 718-735.

[4] Aharonov, D., van Dam, W., Kempe, J., Landau, Z., Lloyd, S., and Regev, O. (2007). Adiabatic quantum computation is equivalent to standard quantum computation. *SIAM Journal on Computing*, 37(1), 166-194.

[5] Aharonov, Y., Davidovich, L., and Zagury, N. (2001). Quantum random walks. *Physical Review A*, 48(2), 1687-1690. [Note: Original 1993; formalized in the quantum walk framework by Aharonov et al., 2001.]

[6] Albash, T., and Lidar, D. A. (2018). Adiabatic quantum computation. *Reviews of Modern Physics*, 90(1), 015002.

[7] Ambainis, A. (2003). Quantum walks and their algorithmic applications. *International Journal of Quantum Information*, 1(4), 507-518.

[8] Ambainis, A. (2007). Quantum walk algorithm for element distinctness. *SIAM Journal on Computing*, 37(1), 210-239.

[9] Ambainis, A. (2012). Variable time amplitude amplification and quantum algorithms for linear algebra problems. *Proceedings of STACS 2012*, 636-647.

[10] Arute, F., Arya, K., Babbush, R., et al. (2019). Quantum supremacy using a programmable superconducting processor. *Nature*, 574(7779), 505-510.

[11] Aspuru-Guzik, A., Dutoi, A. D., Love, P. J., and Head-Gordon, M. (2005). Simulated quantum computation of molecular energies. *Science*, 309(5741), 1704-1707.

[12] Bennett, C. H., Bernstein, E., Brassard, G., and Vazirani, U. (1997). Strengths and weaknesses of quantum computing. *SIAM Journal on Computing*, 26(5), 1510-1523.

[13] Bennett, C. H., and Brassard, G. (1984). Quantum cryptography: Public key distribution and coin tossing. *Proceedings of IEEE International Conference on Computers, Systems, and Signal Processing*, 175-179.

[14] Bernstein, E., and Vazirani, U. (1997). Quantum complexity theory. *SIAM Journal on Computing*, 26(5), 1411-1473.

[15] Berry, D. W. (2014). High-order quantum algorithm for solving linear differential equations. *Journal of Physics A: Mathematical and Theoretical*, 47(10), 105301.

[16] Berry, D. W., Ahokas, G., Cleve, R., and Sanders, B. C. (2007). Efficient quantum algorithms for simulating sparse Hamiltonians. *Communications in Mathematical Physics*, 270(2), 359-371.

[17] Berry, D. W., Childs, A. M., Ostrander, A., and Wang, G. (2017). Quantum algorithm for linear differential equations with exponentially improved dependence on precision. *Communications in Mathematical Physics*, 356(3), 1057-1081.

[18] Bharti, K., Cervera-Lierta, A., Kyaw, T. H., et al. (2022). Noisy intermediate-scale quantum algorithms. *Reviews of Modern Physics*, 94(1), 015004.

[19] Biamonte, J., Wittek, P., Pancotti, N., Rebentrost, P., Wiebe, N., and Lloyd, S. (2017). Quantum machine learning. *Nature*, 549(7671), 195-202.

[20] Brassard, G., Hoyer, P., Mosca, M., and Tapp, A. (2002). Quantum amplitude amplification and estimation. *Contemporary Mathematics*, 305, 53-74.

[21] Campbell, E. T. (2021). Early fault-tolerant simulations of the Hubbard model. *Quantum Science and Technology*, 7(1), 015007.

[22] Cerezo, M., Arrasmith, A., Babbush, R., et al. (2021). Variational quantum algorithms. *Nature Reviews Physics*, 3(9), 625-644.

[23] Chia, N.-H., Gilyen, A., Li, T., Lin, H.-H., Tang, E., and Wang, C. (2020). Sampling-based sublinear low-rank matrix arithmetic framework for dequantizing quantum machine learning. *Proceedings of the 52nd Annual ACM SIGACT Symposium on Theory of Computing*, 387-400.

[24] Childs, A. M. (2009). Universal computation by quantum walk. *Physical Review Letters*, 102(18), 180501.

[25] Childs, A. M., Cleve, R., Deotto, E., Farhi, E., Gutmann, S., and Spielman, D. A. (2003). Exponential algorithmic speedup by a quantum walk. *Proceedings of the 35th Annual ACM Symposium on Theory of Computing*, 59-68.

[26] Childs, A. M., and Goldstone, J. (2004). Spatial search by quantum walk. *Physical Review A*, 70(2), 022314.

[27] Childs, A. M., Maslov, D., Nam, Y., Ross, N. J., and Su, Y. (2018). Toward the first quantum simulation with quantum speedup. *Proceedings of the National Academy of Sciences*, 115(38), 9456-9461.

[28] Childs, A. M., and van Dam, W. (2010). Quantum algorithms for algebraic problems. *Reviews of Modern Physics*, 82(1), 1-52.

[29] Childs, A. M., and Wiebe, N. (2012). Hamiltonian simulation using linear combinations of unitary operations. *Quantum Information and Computation*, 12(11-12), 901-924.

[30] Cleve, R., Ekert, A., Macchiavello, C., and Mosca, M. (1998). Quantum algorithms revisited. *Proceedings of the Royal Society of London A*, 454(1969), 339-354.

[31] Deutsch, D. (1985). Quantum theory, the Church-Turing principle and the universal quantum computer. *Proceedings of the Royal Society of London A*, 400(1818), 97-117.

[32] Deutsch, D., and Jozsa, R. (1992). Rapid solution of problems by quantum computation. *Proceedings of the Royal Society of London A*, 439(1907), 553-558.

[33] Ekert, A. K. (1991). Quantum cryptography based on Bell's theorem. *Physical Review Letters*, 67(6), 661-663.

[34] Endo, S., Benjamin, S. C., and Li, Y. (2018). Practical quantum error mitigation for near-future applications. *Physical Review X*, 8(3), 031027.

[35] Farhi, E., Goldstone, J., and Gutmann, S. (2014). A quantum approximate optimization algorithm. arXiv:1411.4028.

[36] Farhi, E., Goldstone, J., Gutmann, S., and Sipser, M. (2001). Quantum computation by adiabatic evolution. arXiv:quant-ph/0001106.

[37] Farhi, E., and Gutmann, S. (1998). Quantum computation and decision trees. *Physical Review A*, 58(2), 915-928.

[38] Farhi, E., and Harrow, A. W. (2016). Quantum supremacy through the quantum approximate optimization algorithm. arXiv:1602.07674.

[39] Feynman, R. P. (1982). Simulating physics with computers. *International Journal of Theoretical Physics*, 21(6/7), 467-488.

[40] Fowler, A. G., Mariantoni, M., Martinis, J. M., and Cleland, A. N. (2012). Surface codes: Towards practical large-scale quantum computation. *Physical Review A*, 86(3), 032324.

[41] Georgescu, I. M., Ashhab, S., and Nori, F. (2014). Quantum simulation. *Reviews of Modern Physics*, 86(1), 153-185.

[42] Gidney, C., and Ekera, M. (2021). How to factor 2048 bit RSA integers in 8 hours using 20 million noisy qubits. *Quantum*, 5, 433.

[43] Gilyen, A., Su, Y., Low, G. H., and Wiebe, N. (2019). Quantum singular value transformation and beyond: Exponential improvements for quantum matrix arithmetics. *Proceedings of the 51st Annual ACM SIGACT Symposium on Theory of Computing*, 193-204.

[44] Giovannetti, V., Lloyd, S., and Maccone, L. (2008). Quantum random access memory. *Physical Review Letters*, 100(16), 160501.

[45] Goings, J. J., White, A., Lee, J., et al. (2022). Reliably assessing the electronic structure of cytochrome P450 on today's classical computers and tomorrow's quantum computers. *Proceedings of the National Academy of Sciences*, 119(38), e2203533119.

[46] Google AI Quantum and Collaborators. (2020). Hartree-Fock on a superconducting qubit quantum computer. *Science*, 369(6507), 1084-1089.

[47] Google Quantum AI. (2023). Suppressing quantum errors by scaling a surface code logical qubit. *Nature*, 614(7949), 676-681.

[48] Grassl, M., Langenberg, B., Roetteler, M., and Steinwandt, R. (2016). Applying Grover's algorithm to AES: Quantum resource estimates. *Post-Quantum Cryptography (PQCrypto 2016)*, Lecture Notes in Computer Science, 9606, 29-43.

[49] Grover, L. K. (1996). A fast quantum mechanical algorithm for database search. *Proceedings of the 28th Annual ACM Symposium on Theory of Computing*, 212-219.

[50] Guerreschi, G. G., and Matsuura, A. Y. (2019). QAOA for Max-Cut requires hundreds of qubits for quantum speed-up. *Scientific Reports*, 9(1), 6903.

[51] Harrow, A. W., Hassidim, A., and Lloyd, S. (2009). Quantum algorithm for linear systems of equations. *Physical Review Letters*, 103(15), 150502.

[52] Harwood, S., Gambella, C., Trenev, D., Simonetto, A., Bernal Neira, D., and Greber, D. (2021). Formulating and solving routing problems on quantum computers. *IEEE Transactions on Quantum Engineering*, 2, 3100118.

[53] Havlicek, V., Corcoles, A. D., Temme, K., et al. (2019). Supervised learning with quantum-enhanced feature spaces. *Nature*, 567(7747), 209-212.

[54] Huang, H.-Y., Broughton, M., Cotler, J., et al. (2021). Power of data in quantum machine learning. *Nature Communications*, 12(1), 2631.

[55] Huang, H.-Y., Broughton, M., Mohseni, M., et al. (2020). Classical simulation of quantum supremacy circuits. arXiv:2005.06787.

[56] Huang, H.-Y., Kueng, R., and Preskill, J. (2022). Quantum advantage in learning from experiments. *Science*, 376(6598), 1182-1186.

[57] Johnson, M. W., Amin, M. H. S., Gildert, S., et al. (2011). Quantum annealing with manufactured spins. *Nature*, 473(7346), 194-198.

[58] Jozsa, R., and Linden, N. (2003). On the role of entanglement in quantum-computational speed-up. *Proceedings of the Royal Society of London A*, 459(2036), 2011-2032.

[59] Kadowaki, T., and Nishimori, H. (1998). Quantum annealing in the transverse Ising model. *Physical Review E*, 58(5), 5355-5363.

[60] Kandala, A., Mezzacapo, A., Temme, K., et al. (2017). Hardware-efficient variational quantum eigensolver for small molecules and quantum magnets. *Nature*, 549(7671), 242-246.

[61] Kaye, P., Laflamme, R., and Mosca, M. (2007). *An Introduction to Quantum Computing*. Oxford University Press.

[62] Kerenidis, I., and Prakash, A. (2016). Quantum recommendation systems. arXiv:1603.08675.

[63] Kim, Y., Eddins, A., Anand, S., et al. (2023). Evidence for the utility of quantum computing before fault tolerance. *Nature*, 618(7965), 500-505.

[64] Kitaev, A. Y. (1995). Quantum measurements and the Abelian stabilizer problem. arXiv:quant-ph/9511026.

[65] Lee, J., Berry, D. W., Gidney, C., et al. (2021). Even more efficient quantum computations of chemistry through tensor hypercontraction. *PRX Quantum*, 2(3), 030305.

[66] Li, Y., and Benjamin, S. C. (2017). Efficient variational quantum simulator incorporating active error minimization. *Physical Review X*, 7(2), 021050.

[67] Liao, S.-K., Cai, W.-Q., Liu, W.-Y., et al. (2017). Satellite-to-ground quantum key distribution. *Nature*, 549(7670), 43-47.

[68] Litinski, D. (2023). How to compute a 256-bit elliptic curve private key with only 50 million Toffoli gates. *Quantum*, 7, 993.

[69] Lloyd, S. (1996). Universal quantum simulators. *Science*, 273(5278), 1073-1078.

[70] Lloyd, S., Mohseni, M., and Rebentrost, P. (2014). Quantum principal component analysis. *Nature Physics*, 10(9), 631-633.

[71] Lomonaco, S. J., and Kauffman, L. H. (2002). Quantum hidden subgroup problems: A mathematical perspective. *Quantum Computation and Information*, 305, 139-202.

[72] Low, G. H., and Chuang, I. L. (2017). Optimal Hamiltonian simulation by quantum signal processing. *Physical Review Letters*, 118(1), 010501.

[73] Lubinski, T., Johri, S., Varosy, P., et al. (2023). Application-oriented performance benchmarks for quantum computing. *IEEE Transactions on Quantum Engineering*, 4, 3100332.

[74] Magniez, F., Nayak, A., Roland, J., and Santha, M. (2011). Search via quantum walk. *SIAM Journal on Computing*, 40(1), 142-164.

[75] McClean, J. R., Boixo, S., Smelyanskiy, V. N., Babbush, R., and Neven, H. (2018). Barren plateaus in quantum neural network training landscapes. *Nature Communications*, 9(1), 4812.

[76] Montanaro, A. (2015). Quantum speedup of Monte Carlo methods. *Proceedings of the Royal Society A*, 471(2181), 20150301.

[77] Montanaro, A. (2016). Quantum algorithms: An overview. *npj Quantum Information*, 2, 15023.

[78] Montanaro, A. (2018). Quantum-walk speedup of backtracking algorithms. *Theory of Computing*, 14(15), 1-24.

[79] Mosca, M., and Piani, M. (2023). Quantum threat timeline report 2022. Global Risk Institute.

[80] Motta, M., and Rice, J. E. (2022). Emerging quantum computing algorithms for quantum chemistry. *WIREs Computational Molecular Science*, 12(3), e1580.

[81] Nielsen, M. A., and Chuang, I. L. (2000). *Quantum Computation and Quantum Information*. Cambridge University Press.

[82] NIST. (2022). Post-Quantum Cryptography Standardization. National Institute of Standards and Technology. https://csrc.nist.gov/projects/post-quantum-cryptography.

[83] Orus, R., Mugel, S., and Lizaso, E. (2019). Quantum computing for finance: Overview and prospects. *Reviews in Physics*, 4, 100028.

[84] Osborne, T. J. (2012). Hamiltonian complexity. *Reports on Progress in Physics*, 75(2), 022001.

[85] Pan, F., and Zhang, P. (2022). Simulation of quantum circuits using the big-batch tensor network method. *Physical Review Letters*, 128(3), 030501.

[86] Peruzzo, A., McClean, J., Shadbolt, P., et al. (2014). A variational eigenvalue solver on a photonic quantum processor. *Nature Communications*, 5, 4213.

[87] Preskill, J. (2018). Quantum computing in the NISQ era and beyond. *Quantum*, 2, 79.

[88] Rebentrost, P., Mohseni, M., and Lloyd, S. (2014). Quantum support vector machine for big data classification. *Physical Review Letters*, 113(13), 130503.

[89] Regev, O. (2004). Quantum computation and lattice problems. *SIAM Journal on Computing*, 33(3), 738-760.

[90] Reiher, M., Wiebe, N., Svore, K. M., Wecker, D., and Troyer, M. (2017). Elucidating reaction mechanisms on quantum computers. *Proceedings of the National Academy of Sciences*, 114(29), 7555-7560.

[91] Ronnow, T. F., Wang, Z., Job, J., et al. (2014). Defining and detecting quantum speedup. *Science*, 345(6195), 420-424.

[92] Schuld, M., and Killoran, N. (2019). Quantum machine learning in feature Hilbert spaces. *Physical Review Letters*, 122(4), 040504.

[93] Shor, P. W. (1997). Polynomial-time algorithms for prime factorization and discrete logarithms on a quantum computer. *SIAM Journal on Computing*, 26(5), 1484-1509.

[94] Simon, D. R. (1997). On the power of quantum computation. *SIAM Journal on Computing*, 26(5), 1474-1483.

[95] Stamatopoulos, N., Egger, D. J., Sun, Y., et al. (2020). Option pricing using quantum computers. *Quantum*, 4, 291.

[96] Svore, K. M., Hastings, M. B., and Freedman, M. (2014). Faster phase estimation. *Quantum Information and Computation*, 14(3-4), 306-328.

[97] Tang, E. (2019). A quantum-inspired classical algorithm for recommendation systems. *Proceedings of the 51st Annual ACM SIGACT Symposium on Theory of Computing*, 217-228.

[98] Temme, K., Bravyi, S., and Gambetta, J. M. (2017). Error mitigation for short-depth quantum circuits. *Physical Review Letters*, 119(18), 180509.

[99] Watrous, J. (2009). Quantum computational complexity. In *Encyclopedia of Complexity and Systems Science*, Springer, 7174-7201.

[100] Williams, K. T., Yao, Y., Li, J., et al. (2020). Direct comparison of many-body methods for realistic electronic Hamiltonians. *Physical Review X*, 10(1), 011041.

[101] Zalka, C. (1999). Grover's quantum searching algorithm is optimal. *Physical Review A*, 60(4), 2746-2751.
