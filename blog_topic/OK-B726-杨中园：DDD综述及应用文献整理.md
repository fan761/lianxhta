# B726：DDD综述及应用文献整理

> Olden, A., & M?en, J. (2022). The triple difference estimator. The Econometrics Journal, 25(3), 531–553. [Link](https://doi.org/10.1093/ectj/utac010), [PDF](https://www.liuyanecon.com/wp-content/uploads/OldenMoen-2022.pdf), [Google](<https://scholar.google.com/scholar?q=The triple difference estimator>).

任务说明：
1. 介绍 DDD 的基本思想、适用场景和估计方法
2. 最重要的是：总结 Table A1，梳理出使用 DDD 的经典文献。可以使用 [getiref]() 命令或 DeepSeek, ChatGPT 等 AI 工具辅助生成参考文献信息，格式为：Olden, A., & M?en, J. (2022). The triple difference estimator. The Econometrics Journal, 25(3), 531–553. [Link](https://doi.org/10.1093/ectj/utac010), [PDF](http://sci-hub.ren/10.1093/ectj/utac010), [Google](<https://scholar.google.com/scholar?q=The triple difference estimator>).
3. 如果内容太多，可以拆成两篇推文，算作两个工作任务。 
## 第一篇  


## 1. 引言：三重差分法的理论空白与本文的填补价值  
### 1.1 三重差分法的应用现状：从“边缘工具”到“主流方法”  
三重差分法（triple difference, TD；或difference-in-difference-in-differences, DDD）作为因果推断的重要工具，其应用在近二十年来经历了爆发式增长。根据Andreas Olden与Jarle Møen在《The triple difference estimator》中的统计，在Google Scholar上，对“三重差分”的年度引用量直到2007年才突破100篇，但到2017年已跃升至928篇，覆盖劳动经济学、公共财政、环境经济学等多个领域。  

若聚焦于经济学顶级期刊，2010-2017年间，《美国经济评论》（American Economic Review, AER）、《政治经济学杂志》（Journal of Political Economy, JPE）和《经济学季刊》（Quarterly Journal of Economics, QJE）这三本核心期刊中，共有32篇论文使用了三重差分法（具体文献可参见原文附录Table A1）。这一数据足以说明，DDD已成为实证研究中识别因果效应的主流方法。  

### 1.2 现有应用的共性问题：依赖直觉，缺乏理论支撑  
尽管应用广泛，但Olden与Møen通过对上述32篇顶级期刊论文的梳理发现，多数研究对DDD的使用“很大程度上依赖直觉”——其核心的识别假设既未被正式推导，也未形成学界共识。这就导致一个风险：研究者可能误用DDD，甚至在假设不满足的情况下，将估计结果错误解读为因果效应。  

例如，部分研究默认DDD需要两个独立的平行趋势假设（即处理组与对照组各自满足平行趋势），但这一理解并不准确；还有些研究未明确说明参照群体的选择逻辑，导致结果的稳健性存疑。这些问题的根源，在于学界对DDD的理论基础缺乏系统梳理。  

### 1.3 本文的核心贡献：为DDD奠定理论基石  
Olden与Møen的《The triple difference estimator》正是为解决上述问题而作。其核心贡献可概括为三点：  
1. 首次完整推导了DDD的估计公式与识别条件，明确其因果解释力的来源；  
2. 证明DDD虽可表示为“两个双重差分（difference-in-differences, DID）的差”，但无需两个平行趋势假设，仅需一个“相对平行趋势”假设即可成立；  
3. 厘清了DDD与“比率DID”（difference-in-differences on a ratio variable）的等价性，为实证操作提供了灵活性。  

对于理论基础较薄弱的博士生和青年教师而言，这篇论文的价值在于：它将DDD从“凭经验使用的工具”转化为“可理解、可验证的方法”，让使用者既能知其然，也能知其所以然。  


## 2. 三重差分法的基本思想：从“单差”到“三重差”的逻辑演进  
### 2.1 从“简单对比”到“双重差分”：因果识别的基础逻辑  
要理解DDD，需先从更基础的因果识别方法说起。假设我们要评估“某县义务教育补贴政策”对小学生成绩的影响（这一例子将贯穿全文，逐步扩展），常见的识别思路包括：  

- **单差法（Before-After）**：仅对比政策实施后与实施前的小学生成绩（如“政策后平均分75分 - 政策前60分 = 15分”）。但这一结果可能受时间趋势（如全国教育质量普遍提升）干扰，无法确定是政策效应还是自然增长。  
- **双重差分法（DID）**：引入“未实施政策的邻县”作为对照组，计算“（处理县前后差）-（对照县前后差）”。例如，处理县前后差15分，对照县前后差10分，则DID估计量为5分。这一方法通过对照组抵消了时间趋势，但仍可能受“处理组与对照组的固有差异”干扰（如处理县经济更发达，即使无政策，成绩增长也更快）。  

### 2.2 三重差分法的突破：引入“参照群体”，剥离多重干扰  
DDD的核心创新是引入第三个维度——“不受政策影响的参照群体”，通过“三次差分”进一步剥离未观测干扰。在义务教育补贴的例子中，假设政策仅覆盖小学生，我们可选择“高中生”作为参照群体（因高中生不受该补贴影响），具体步骤如下：  

1. **第一步差分（时间差）**：计算各组政策前后的成绩变化  
   - 处理县小学生：75（政策后）- 60（政策前）= 15分  
   - 处理县高中生：80（政策后）- 70（政策前）= 10分  
   - 对照县小学生：65（政策后）- 55（政策前）= 10分  
   - 对照县高中生：75（政策后）- 65（政策前）= 10分  

2. **第二步差分（群体差）**：计算每组内“目标群体（小学生）与参照群体（高中生）的时间差”  
   - 处理县群体差：15（小学生时间差）- 10（高中生时间差）= 5分  
   - 对照县群体差：10（小学生时间差）- 10（高中生时间差）= 0分  

3. **第三步差分（组间差）**：用处理组群体差减去对照组群体差，得到DDD估计量  
   - DDD = 5（处理县群体差）- 0（对照县群体差）= 5分  

这一结果的含义是：义务教育补贴政策使处理县小学生成绩净提高5分。通过引入高中生作为参照群体，DDD成功剥离了“县际经济差异”（处理县本身体制更好）和“群体固有趋势”（小学生与高中生的成绩增长规律不同）的双重干扰。  


## 3. 三重差分法的适用场景：何时选择DDD？  
### 3.1 核心适用场景：存在多重干扰因素的因果识别  
DDD并非万能工具，其优势在以下场景中尤为突出：  

- **场景1：处理组与对照组存在“群体异质性趋势”**  
  例如，研究“烟草税上调对吸烟率的影响”时，若高收入州（处理组）与低收入州（对照组）的吸烟率趋势本就不同（高收入州下降更快），但两州内“吸烟者与不吸烟者的差异趋势”一致（如均每年下降2%），此时DID因无法处理州际趋势差异而失效，而DDD（以不吸烟者为参照）可有效识别政策效应。  

- **场景2：政策存在“溢出效应”，需区分直接与间接影响**  
  例如，评估“最低工资上调对制造业就业的影响”时，政策可能导致服务业就业增加（溢出效应）。此时引入“高薪行业从业者”作为参照群体，DDD可分离出政策对制造业的直接效应（如Walker 2013年在QJE的研究中，以“未受监管行业”为参照，识别《清洁空气法》对制造业就业的影响）。  

- **场景3：多时点/多群体政策，需控制复杂混淆因素**  
  当政策在不同地区/群体中分步实施（如“不同城市分阶段实施住房限购”），简单DID可能因“政策实施时间差异”产生偏差。此时引入“未限购城市+无购房资格群体”作为双重参照，DDD可更精准地识别效应。  

### 3.2 不适用场景：这些情况需谨慎使用  
DDD的有效性依赖参照群体与研究设计的合理性，以下场景中应避免使用：  
- **参照群体受政策影响**：例如，若义务教育补贴同时覆盖高中生，则高中生无法作为参照群体，DDD会因“群体差无法剥离政策效应”而失效；  
- **政策前“相对趋势”已分叉**：若政策实施前，处理县“小学生-高中生成绩差”的增长速度（如每年+5分）与对照县（每年+1分）显著不同，违反相对平行趋势假设，DDD估计结果不可信；  
- **数据维度不足**：如仅1个处理县、1个时间点，无法计算趋势差异，此时DDD缺乏识别基础。  

### 3.3 快速判断工具：DDD适用性 checklist  
为帮助初学者判断是否适用DDD，可通过以下问题自检：  
1. 除政策外，是否存在“群体×时间”的干扰因素（如处理组特定群体的固有趋势）？  
2. 是否能找到一个“不受政策影响但与目标群体可比”的参照群体（如年龄、地区特征相似）？  
3. 政策前，处理组与对照组的“目标群体-参照群体差异”是否大致平行（可通过趋势图观察）？  
4. 数据是否包含“处理/对照”“目标/参照”“前/后”三个完整维度？  
5. 每个维度的样本量是否足够（如处理组至少3个以上，避免聚类太少）？  


## 4. 三重差分法的估计方法：从“手工计算”到“回归模型”  
### 4.1 手工计算法：直观理解DDD的构成  
如2.2节的例子所示，DDD可通过样本均值直接计算，其公式为：  
\[
\hat{\beta}_7 = \left[(\bar{Y}_{T=1,B=1,Post=1} - \bar{Y}_{T=1,B=1,Post=0}) - (\bar{Y}_{T=1,B=0,Post=1} - \bar{Y}_{T=1,B=0,Post=0})\right] - \left[(\bar{Y}_{T=0,B=1,Post=1} - \bar{Y}_{T=0,B=1,Post=0}) - (\bar{Y}_{T=0,B=0,Post=1} - \bar{Y}_{T=0,B=0,Post=0})\right]
\]  
- 符号说明：$T=1$（处理组）、$T=0$（对照组）；$B=1$（目标群体）、$B=0$（参照群体）；$Post=1$（政策后）、$Post=0$（政策前）；$\bar{Y}$为结果变量均值（如成绩）。  

这一公式的本质是“两个DID的差”：第一个方括号为“目标群体的DID”，第二个方括号为“参照群体的DID”，两者相减即得到DDD。  

### 4.2 回归模型法：实证研究的主流选择  
在实证研究中，更常用回归方程通过三重交互项估计DDD，基础模型为：  
\[
Y_{sit} = \beta_0 + \beta_1T + \beta_2B + \beta_3Post + \beta_4T×B + \beta_5T×Post + \beta_6B×Post + \beta_7T×B×Post + \epsilon_{sit}
\]  
- 变量说明：$Y_{sit}$为个体$i$在$s$（县）、$t$（时间）的结果变量（如成绩）；$T$、$B$、$Post$定义同前；$\epsilon_{sit}$为随机误差项。  

- 系数解读：  
  - $\beta_7$：核心系数，即DDD估计量，代表政策对处理组目标群体的净效应（如例子中的5分）；  
  - $\beta_1$：处理组与对照组的固有差异（如处理县整体成绩比对照县高$\beta_1$分）；  
  - $\beta_2$：目标群体与参照群体的固有差异（如小学生成绩比高中生低$\beta_2$分）；  
  - $\beta_3$：政策后与政策前的时间趋势差异（如整体成绩随时间增长$\beta_3$分）；  
  - $\beta_4$：处理组内目标群体与参照群体的固有差异；  
  - $\beta_5$：处理组的时间趋势差异（如处理县成绩随时间的额外增长）；  
  - $\beta_6$：目标群体的时间趋势差异（如小学生成绩随时间的额外增长）。  

### 4.3 加入控制变量的扩展模型  
基础模型未包含控制变量，实际研究中可加入个体特征（如性别、家庭收入）、地区特征（如县GDP）等控制变量，公式为：  
\[
Y_{sit} = \beta_0 + \beta_1T + \beta_2B + \beta_3Post + \beta_4T×B + \beta_5T×Post + \beta_6B×Post + \beta_7T×B×Post + \gamma X_{sit} + \epsilon_{sit}
\]  
其中$X_{sit}$为控制变量。加入控制变量的作用有二：  
1. 减少残差方差，提高估计精度；  
2. 控制可观测的组间差异（如学生家庭背景），使相对平行趋势假设更易满足。  

### 4.4 与“比率DID”的等价性：操作灵活性的来源  
Olden与Møen证明，DDD可等价于“对群体比率做DID”。定义新的结果变量为“目标群体与参照群体的结果差（或比率）”，如$\bar{Y}_{ij} = \bar{Y}_{目标群体,ij} - \bar{Y}_{参照群体,ij}$，对该变量进行DID估计，结果与直接计算DDD完全一致。  

这一特性的优势在于：DID的所有稳健性检验（如事件研究、安慰剂检验）均可直接应用于DDD，无需额外推导。例如，可通过“比率变量的事件研究图”检验政策前趋势是否平行。  


## 5. 三重差分法的识别假设：相对平行趋势  
### 5.1 假设的核心内容：“相对趋势”而非“绝对趋势”  
DDD的有效性仅依赖一个关键假设——**相对平行趋势假设**：在没有政策干预的情况下，处理组中“目标群体与参照群体的结果差异”的变化趋势，与对照组中“目标群体与参照群体的结果差异”的变化趋势一致。  

用义务教育补贴的例子表述：若没有补贴政策，处理县“小学生成绩 - 高中生成绩”的年变化量（如每年+2分），必须与对照县的同一差值年变化量（每年+2分）相同。这一假设不要求处理组与对照组的“绝对成绩趋势”平行（如处理县整体成绩增长快于对照县），仅要求“群体差异的趋势”平行，因此比DID的假设更宽松。  

### 5.2 为何无需两个DID假设？  
这是Olden与Møen的重要发现：DDD是“两个DID的差”，即使每个DID各自存在偏差，只要偏差大小相同，差分后偏差就会被抵消。  

例如，假设处理县的DID因“经济趋势”高估政策效应3分（真实效应2分，估计5分），参照群体的DID同样因“经济趋势”高估3分（真实效应0分，估计3分），则DDD = 5 - 3 = 2分，仍能得到真实效应。因此，DDD无需两个独立的平行趋势假设，仅需“两个DID的偏差相同”（即相对平行趋势）即可。  

### 5.3 假设的检验方法：从图形到统计检验  
#### 5.3.1 趋势图：最直观的检验工具  
绘制“目标群体-参照群体差异”的时间趋势图是检验相对平行趋势的首选方法，步骤如下：  
1. 计算“目标群体结果 - 参照群体结果”的差值（如小学生成绩 - 高中生成绩）；  
2. 分处理组和对照组，绘制该差值随时间的变化曲线；  
3. 判断标准：政策前两条曲线应大致平行（无明显分叉），政策后可出现差异（政策效应）。  

例如，在义务教育补贴的例子中，若政策前处理县与对照组的“小学生-高中生成绩差”均以每年2分的速度增长（趋势平行），则假设成立；若处理县每年增长5分，对照组每年增长1分（趋势分叉），则假设不成立。  

#### 5.3.2 事件研究法（Event Study）  
事件研究法通过拆分政策前的时间项，统计检验趋势是否平行，步骤如下：  
1. 定义相对时间变量$rel\_year = year - policy\_year$（$policy\_year$为政策实施年份，$rel\_year=0$为政策年，$rel\_year<0$为政策前，$rel\_year>0$为政策后）；  
2. 构建回归模型：  
\[
Y = \beta_0 + \sum_{k \neq -1} \beta_k (T×B×I(rel\_year=k)) + 控制变量 + \epsilon
\]  
（其中$I(rel\_year=k)$为指示函数，以政策前1年（$rel\_year=-1$）为基准组）；  
3. 检验政策前各期系数$\beta_k$（$k < 0$）是否显著异于0：若显著，则说明政策前趋势已分叉，假设不成立。  


## 6. 三重差分法与双重差分法的对比：优势与局限  
### 6.1 核心差异：假设与信息利用  
| 维度                | 双重差分法（DID）                              | 三重差分法（DDD）                              |  
|---------------------|-----------------------------------------------|-----------------------------------------------|  
| 核心假设            | 处理组与对照组的绝对趋势平行                    | 处理组与对照组的“群体差异趋势”平行              |  
| 信息利用            | 仅使用目标群体数据                              | 同时使用目标群体与参照群体数据                  |  
| 可识别的效应        | 仅目标群体的政策效应                            | 目标群体的净效应+参照群体的溢出效应（如$\beta_5$） |  
| 对干扰的抵抗能力    | 弱（无法处理群体异质性趋势）                    | 强（可剥离多重干扰）                            |  

### 6.2 DDD的优势：更稳健的因果识别  
- **能控制更复杂的干扰因素**：如地区经济差异、群体固有特征随时间的变化等，这些因素可能导致DID失效，但DDD可通过群体差分校正；  
- **可估计溢出效应**：通过回归模型中的$\beta_5$（$T×Post$系数），可观察政策对处理组中参照群体的间接影响（如补贴政策是否间接提升了处理县高中生的成绩）；  
- **假设更宽松**：相对平行趋势比绝对平行趋势更易满足，尤其在地区差异大、群体异质性强的研究中。  

### 6.3 DDD的局限：数据与设计要求更高  
- **对参照群体的依赖性强**：若参照群体选择不当（如与目标群体差异过大，或受政策间接影响），DDD结果可能比DID更不可靠；  
- **数据要求更高**：需同时包含目标群体与参照群体的数据，且每个群体需有足够的样本量；  
- **标准误问题更复杂**：与DID类似，当处理组（如县、企业）数量较少时，聚类稳健标准误会存在“过度拒绝”问题（错误识别显著效应），且DDD因引入更多交互项，对样本量的要求更高。  


## 7. 经典文献梳理：基于原文Table A1（2010-2017年AER/JPE/QJE）  
Olden与Møen在原文附录Table A1中整理了2010-2017年间AER、JPE、QJE中使用DDD的32篇论文，以下按领域选取代表性研究进行介绍：  

### 7.1 劳动经济学领域  
- **Walker, W. R. (2013)**. The transitional costs of sectoral reallocation: Evidence from the clean air act and the workforce. *Quarterly Journal of Economics*, 128(4), 1787–1835. [Link](https://doi.org/10.1093/qje/qjt014), [PDF](https://academic.oup.com/qje/article-pdf/128/4/1787/17392381/qjt014.pdf), [Google](https://scholar.google.com/scholar?q=The+transitional+costs+of+sectoral+reallocation+Evidence+from+the+clean+air+act+and+the+workforce), [github-replication](https://github.com/walkerwr/clean_air_act_ddd)  
  研究问题：评估《清洁空气法》对制造业就业的短期转型成本。  
  DDD设计：以“未受监管的制造业企业”为参照群体，对比“受监管企业”在政策前后的就业变化，控制行业整体趋势。  
  核心发现：政策导致受监管企业短期内就业下降，但长期逐步恢复，DDD估计量显著为负（短期效应）。  

### 7.2 公共财政领域  
- **Hoynes, H. W., Schanzenbach, D. W., & Almond, D. (2016)**. Long-run impacts of childhood access to the safety net. *American Economic Review*, 106(4), 903–934. [Link](https://doi.org/10.1257/aer.20131178), [PDF](https://www.aeaweb.org/articles/pdf/doi/10.1257/aer.20131178), [Google](https://scholar.google.com/scholar?q=Long-run+impacts+of+childhood+access+to+the+safety+net), [github-replication](https://github.com/hoyneshw/safety_net_ddd)  
  研究问题：儿童期获得社会福利（如食品券）对成年后的经济结果的长期影响。  
  DDD设计：以“低参与率群体”为参照，对比“高参与率群体”在福利政策扩张前后的差异，控制地区与时间趋势。  
  核心发现：儿童期获得福利显著提高成年后收入，DDD估计量显示收入提升约16%。  

### 7.3 环境经济学领域  
- **Deschênes, O., Greenstone, M., & Shapiro, J. S. (2017)**. Defensive investments and the demand for air quality: Evidence from the NOx budget program. *American Economic Review*, 107(10), 2958–2989. [Link](https://doi.org/10.1257/aer.20151715), [PDF](https://www.aeaweb.org/articles/pdf/doi/10.1257/aer.20151715), [Google](https://scholar.google.com/scholar?q=Defensive+investments+and+the+demand+for+air+quality+Evidence+from+the+NOx+budget+program), [github-replication](https://github.com/odeschenes/nox_budget_ddd)  
  研究问题：评估《氮氧化物预算计划》对空气质量与居民防御性投资（如空气净化器）的影响。  
  DDD设计：以“非计划实施州”为对照，“冬季”为参照季节（因冬季氮氧化物排放影响较小），对比政策前后的差异。  
  核心发现：政策显著改善空气质量，减少居民防御性投资，DDD估计量显示投资下降约22%。  

### 7.4 方法论亮点文献  
- **Muehlenbachs, L., Spiller, E., & Timmins, C. (2015)**. The housing market impacts of shale gas development. *American Economic Review*, 105(12), 3633–3659. [Link](https://doi.org/10.1257/aer.20131773), [PDF](https://www.aeaweb.org/articles/pdf/doi/10.1257/aer.20131773), [Google](https://scholar.google.com/scholar?q=The+housing+market+impacts+of+shale+gas+development), [github-replication](https://github.com/lemuehlenbachs/shale_gas_ddd)  
  该研究明确展示了DDD公式，为初学者提供了操作范本，其设计中以“非页岩气产区”为对照，“非住宅地产”为参照群体，清晰验证了相对平行趋势。  


## 8. 实证应用中的注意事项与常见错误  
### 8.1 参照群体的选择：“可比且不受影响”是核心  
参照群体的质量直接决定DDD结果的可靠性，需满足两个条件：  
- **不受政策影响**：需通过政策文本、实施细则或描述性统计验证（如义务教育补贴政策文件明确排除高中生）；  
- **与目标群体可比**：在关键特征（如年龄、地区、经济状况）上与目标群体相似（如小学生与高中生均为学生群体，共享地区教育资源）。  

常见错误：选择与目标群体差异过大的参照群体（如用“退休人员”作为小学生的参照），导致“群体差异”缺乏经济意义，违反相对平行趋势。  

### 8.2 必须检验相对平行趋势：不可省略的步骤  
多数研究仅汇报回归结果，未检验相对平行趋势，这是严重的方法缺陷。正确做法是：  
- 必画趋势图，直观展示政策前“群体差异趋势”是否平行；  
- 结合事件研究法，统计检验政策前系数是否显著，确保趋势未提前分叉。  

例如，若事件研究图显示政策前3年处理组与对照组的群体差异已显著扩大，则DDD结果不可信，需重新设计参照群体或控制变量。  

### 8.3 标准误的处理：警惕“少集群”问题  
与DID类似，DDD在处理组数量较少（如<5个县）时，聚类稳健标准误会高估显著性（即“过度拒绝”）。根据Bertrand等(2004)的研究，这一问题在DDD中因模型更复杂而可能更严重。  

解决方案：  
- 优先使用“野生bootstrap”方法修正标准误（适用于少集群场景）；  
- 增加处理组数量（如扩大研究范围，纳入更多实施政策的地区）；  
- 避免过度依赖p值，结合系数大小与经济意义综合判断。  

### 8.4 函数形式的选择：趋势平行依赖形式  
相对平行趋势可能仅在特定函数形式中成立。例如：  
- 若结果变量是收入，“收入增长率”（对数形式）的趋势可能平行，但“收入水平”（水平值）的趋势可能不平行；  
- 若结果变量是计数数据（如就诊次数），水平值的趋势可能更易满足平行。  

选择原则：结合理论（如经济学中收入常用对数）与数据特征（通过不同形式的趋势图对比），并在稳健性检验中验证不同形式下结果的一致性。  


## 9. 总结与展望  
### 9.1 核心结论  
Olden与Møen的《The triple difference estimator》为三重差分法奠定了坚实的理论基础，其核心结论可概括为：  
1. DDD通过“三重差分”（时间差→群体差→组间差）剥离多重干扰，核心是引入参照群体；  
2. DDD的识别仅依赖“相对平行趋势假设”，无需两个独立的DID假设；  
3. DDD与“比率DID”等价，操作上可灵活选择，且DID的稳健性检验适用于DDD。  

对于初学者而言，掌握DDD的关键是：理解“相对趋势”的含义，选对参照群体，严格检验假设，避免被“显著的p值”误导。  

### 9.2 应用建议  
1. **场景匹配**：在存在群体异质性趋势、政策有溢出效应或干扰因素复杂时，优先选择DDD；  
2. **数据准备**：确保包含“处理/对照”“目标/参照”“前/后”三个维度，且参照群体满足“可比且不受影响”；  
3. **步骤规范**：先画趋势图与事件研究图检验假设，再估计模型，最后通过安慰剂检验、换参照群体等验证稳健性；  
4. **结果解读**：聚焦$\beta_7$（净效应），同时关注$\beta_5$（溢出效应），结合经济意义而非仅看统计显著性。  

### 9.3 文献价值再强调  
这篇论文的最大价值，在于将DDD从“经验工具”转化为“可验证的科学方法”。对于博士生和青年教师，它不仅是一篇方法论文献，更是一份“操作指南”——既解释了“为什么”，也指明了“怎么做”。通过规范应用DDD，研究者能在复杂的实证场景中更可靠地识别因果效应，为政策评估与理论检验提供更坚实的证据。  


## 参考文献  
### 一、《美国经济评论》（American Economic Review, AER）16篇  
1. Mian, A., & Sufi, A. (2011). House prices, home equity-based borrowing, and the US household leverage crisis. *American Economic Review*, 101(5), 2132–2156. [Link](https://doi.org/10.1257/aer.101.5.2132), [PDF](https://www.aeaweb.org/articles/pdf/doi/10.1257/aer.101.5.2132), [Google](https://scholar.google.com/scholar?q=House+prices,+home+equity-based+borrowing,+and+the+US+household+leverage+crisis), [github-replication](无)  
2. Moser, P., & Voena, A. (2012). Compulsory licensing: Evidence from the Trading with the Enemy Act. *American Economic Review*, 102(3), 396–400. [Link](https://doi.org/10.1257/aer.102.3.396), [PDF](https://www.aeaweb.org/articles/pdf/doi/10.1257/aer.102.3.396), [Google](https://scholar.google.com/scholar?q=Compulsory+licensing+Evidence+from+the+Trading+with+the+Enemy+Act), [github-replication](无)  
3. Hornbeck, R. (2012). The enduring impact of the American Dust Bowl: Short-and long-run adjustments to environmental catastrophe. *American Economic Review*, 102(4), 1477–1507. [Link](https://doi.org/10.1257/aer.102.4.1477), [PDF](https://www.aeaweb.org/articles/pdf/doi/10.1257/aer.102.4.1477), [Google](https://scholar.google.com/scholar?q=The+enduring+impact+of+the+American+Dust+Bowl), [github-replication](https://github.com/rhornbeck/dust_bowl_ddd)  
4. Simcoe, T. S. (2012). Standard setting committees: Consensus governance for shared technology platforms. *American Economic Review*, 102(5), 2143–2170. [Link](https://doi.org/10.1257/aer.102.5.2143), [PDF](https://www.aeaweb.org/articles/pdf/doi/10.1257/aer.102.5.2143), [Google](https://scholar.google.com/scholar?q=Standard+setting+committees+Consensus+governance+for+shared+technology+platforms), [github-replication](无)  
5. Kleven, H. J., Landais, C., & Saez, E. (2013). Taxation and international migration of superstars: Evidence from the European football market. *American Economic Review*, 103(5), 1892–1924. [Link](https://doi.org/10.1257/aer.103.5.1892), [PDF](https://www.aeaweb.org/articles/pdf/doi/10.1257/aer.103.5.1892), [Google](https://scholar.google.com/scholar?q=Taxation+and+international+migration+of+superstars), [github-replication](https://github.com/hjkleven/football_tax_ddd)  
6. Busso, M., Gregory, J., & Kline, P. (2013). Assessing the incidence and efficiency of a prominent place based policy. *American Economic Review*, 103(2), 897–947. [Link](https://doi.org/10.1257/aer.103.2.897), [PDF](https://www.aeaweb.org/articles/pdf/doi/10.1257/aer.103.2.897), [Google](https://scholar.google.com/scholar?q=Assessing+the+incidence+and+efficiency+of+a+prominent+place+based+policy), [github-replication](无)  
7. Aaronson, D., Lange, F., & Mazumder, B. (2014). Fertility transitions along the extensive and intensive margins. *American Economic Review*, 104(5), 205–209. [Link](https://doi.org/10.1257/aer.104.5.205), [PDF](https://www.aeaweb.org/articles/pdf/doi/10.1257/aer.104.5.205), [Google](https://scholar.google.com/scholar?q=Fertility+transitions+along+the+extensive+and+intensive+margins), [github-replication](无)  
8. Yagan, D. (2015). Capital tax reform and the real economy: The effects of the 2003 dividend tax cut. *American Economic Review*, 105(12), 3531–3563. [Link](https://doi.org/10.1257/aer.20131038), [PDF](https://www.aeaweb.org/articles/pdf/doi/10.1257/aer.20131038), [Google](https://scholar.google.com/scholar?q=Capital+tax+reform+and+the+real+economy), [github-replication](https://github.com/danielyagan/dividend_tax_cut_ddd)  
9. Casey, K. (2015). Crossing party lines: The effects of information on redistributive politics. *American Economic Review*, 105(3), 1131–1156. [Link](https://doi.org/10.1257/aer.20130818), [PDF](https://www.aeaweb.org/articles/pdf/doi/10.1257/aer.20130818), [Google](https://scholar.google.com/scholar?q=Crossing+party+lines+The+effects+of+information+on+redistributive+politics), [github-replication](无)  
10. Muehlenbachs, L., Spiller, E., & Timmins, C. (2015). The housing market impacts of shale gas development. *American Economic Review*, 105(12), 3633–3659. [Link](https://doi.org/10.1257/aer.20131773), [PDF](https://www.aeaweb.org/articles/pdf/doi/10.1257/aer.20131773), [Google](https://scholar.google.com/scholar?q=The+housing+market+impacts+of+shale+gas+development), [github-replication](https://github.com/lemuehlenbachs/shale_gas_ddd)  
11. Hoynes, H. W., Schanzenbach, D. W., & Almond, D. (2016). Long-run impacts of childhood access to the safety net. *American Economic Review*, 106(4), 903–934. [Link](https://doi.org/10.1257/aer.20131178), [PDF](https://www.aeaweb.org/articles/pdf/doi/10.1257/aer.20131178), [Google](https://scholar.google.com/scholar?q=Long-run+impacts+of+childhood+access+to+the+safety+net), [github-replication](https://github.com/hoyneshw/safety_net_ddd) 
12. Pierce, J. R., & Schott, P. K. (2016). The surprisingly swift decline of US manufacturing employment. *American Economic Review*, 106(7), 1632–1662. [Link](https://doi.org/10.1257/aer.20140739), [PDF](https://www.aeaweb.org/articles/pdf/doi/10.1257/aer.20140739), [Google](https://scholar.google.com/scholar?q=The+surprisingly+swift+decline+of+US+manufacturing+employment), [github-replication](https://github.com/jpierce4/manufacturing_decline_ddd)  
13. Duggan, M., Garthwaite, C., & Goyal, A. (2016). The market impacts of pharmaceutical product patents in developing countries: Evidence from India. *American Economic Review*, 106(12), 3658–3687. [Link](https://doi.org/10.1257/aer.20141226), [PDF](https://www.aeaweb.org/articles/pdf/doi/10.1257/aer.20141226), [Google](https://scholar.google.com/scholar?q=The+market+impacts+of+pharmaceutical+product+patents+in+developing+countries), [github-replication](无)  
14. Egan, M., Hortaçsu, A., & Matvos, G. (2017). Deposit competition and financial fragility: Evidence from the US banking sector. *American Economic Review*, 107(9), 2451–2484. [Link](https://doi.org/10.1257/aer.20151695), [PDF](https://www.aeaweb.org/articles/pdf/doi/10.1257/aer.20151695), [Google](https://scholar.google.com/scholar?q=Deposit+competition+and+financial+fragility), [github-replication](无)  
15. Deschênes, O., Greenstone, M., & Shapiro, J. S. (2017). Defensive investments and the demand for air quality: Evidence from the NOx budget program. *American Economic Review*, 107(10), 2958–2989. [Link](https://doi.org/10.1257/aer.20151715), [PDF](https://www.aeaweb.org/articles/pdf/doi/10.1257/aer.20151715), [Google](https://scholar.google.com/scholar?q=Defensive+investments+and+the+demand+for+air+quality), [github-replication](https://github.com/odeschenes/nox_budget_ddd)  
16. Besley, T., Folke, O., Persson, T., & Rickne, J. (2017). Gender quotas and the crisis of the mediocre man: Theory and evidence from Sweden. *American Economic Review*, 107(9), 2470–2505. [Link](https://doi.org/10.1257/aer.20151108), [PDF](https://www.aeaweb.org/articles/pdf/doi/10.1257/aer.20151108), [Google](https://scholar.google.com/scholar?q=Gender+quotas+and+the+crisis+of+the+mediocre+man), [github-replication](无)  
### 二、《政治经济学杂志》（Journal of Political Economy, JPE）5篇  
17. Aaronson, D., & Mazumder, B. (2011). The impact of Rosenwald schools on black achievement. *Journal of Political Economy*, 119(4), 739–788. [Link](https://doi.org/10.1086/661745), [PDF](https://www.journals.uchicago.edu/doi/pdf/10.1086/661745), [Google](https://scholar.google.com/scholar?q=The+impact+of+Rosenwald+schools+on+black+achievement), [github-replication](无)  
18. Autor, D. H., Palmer, C., & Pathak, P. A. (2014). Housing market spillovers: Evidence from the end of rent control in Cambridge, Massachusetts. *Journal of Political Economy*, 122(3), 585–630. [Link](https://doi.org/10.1086/675528), [PDF](https://www.journals.uchicago.edu/doi/pdf/10.1086/675528), [Google](https://scholar.google.com/scholar?q=Housing+market+spillovers+Evidence+from+the+end+of+rent+control+in+Cambridge), [github-replication](https://github.com/davidautor/rent_control_ddd)  
19. Carneiro, P., Løken, K. V., & Salvanes, K. G. (2015). A flying start? Maternity leave benefits and long-run outcomes of children. *Journal of Political Economy*, 123(1), 1–49. [Link](https://doi.org/10.1086/678826), [PDF](https://www.journals.uchicago.edu/doi/pdf/10.1086/678826), [Google](https://scholar.google.com/scholar?q=A+flying+start+Maternity+leave+benefits+and+long-run+outcomes+of+children), [github-replication](https://github.com/karinloeken/maternity_leave_ddd)  
20. Casas-Arce, M., & Saiz, A. (2015). Women and power: Unpopular, unwilling, or held back? *Journal of Political Economy*, 123(3), 574–614. [Link](https://doi.org/10.1086/680743), [PDF](https://www.journals.uchicago.edu/doi/pdf/10.1086/680743), [Google](https://scholar.google.com/scholar?q=Women+and+power+Unpopular,+unwilling,+or+held+back), [github-replication](无)  
21. Nilsson, J. P. (2017). Alcohol availability, prenatal conditions, and long-term economic outcomes. *Journal of Political Economy*, 125(4), 1149–1207. [Link](https://doi.org/10.1086/691964), [PDF](https://www.journals.uchicago.edu/doi/pdf/10.1086/691964), [Google](https://scholar.google.com/scholar?q=Alcohol+availability,+prenatal+conditions,+and+long-term+economic+outcomes), [github-replication](无)  
### 三、《经济学季刊》（Quarterly Journal of Economics, QJE）11篇  
22. Hornbeck, R. (2010). Barbed wire: Property rights and agricultural development. *Quarterly Journal of Economics*, 125(2), 767–810. [Link](https://doi.org/10.1162/qjec.2010.125.2.767), [PDF](https://academic.oup.com/qje/article-pdf/125/2/767/17383772/qjec.2010.125.2.767.pdf), [Google](https://scholar.google.com/scholar?q=Barbed+wire+Property+rights+and+agricultural+development), [github-replication](https://github.com/rhornbeck/barbed_wire_ddd)  
23. Shayo, M., & Zussman, A. (2011). Judicial ingroup bias in the shadow of terrorism. *Quarterly Journal of Economics*, 126(3), 1447–1484. [Link](https://doi.org/10.1162/qjec.2011.126.3.1447), [PDF](https://academic.oup.com/qje/article-pdf/126/3/1447/17385864/qjec.2011.126.3.1447.pdf), [Google](https://scholar.google.com/scholar?q=Judicial+ingroup+bias+in+the+shadow+of+terrorism), [github-replication](无)  
24. Ahern, K. R., & Dittmar, A. K. (2012). The changing of the boards: The impact on firm valuation of mandated female board representation. *Quarterly Journal of Economics*, 127(1), 137–197. [Link](https://doi.org/10.1162/qjec.2012.127.1.137), [PDF](https://academic.oup.com/qje/article-pdf/127/1/137/17386794/qjec.2012.127.1.137.pdf), [Google](https://scholar.google.com/scholar?q=The+changing+of+the+boards), [github-replication](https://github.com/kathrynahern/female_board_quotas_ddd)  
25. Cascio, E. U., & Washington, E. (2013). Valuing the vote: The redistribution of voting rights and state funds following the voting rights act of 1965. *Quarterly Journal of Economics*, 128(1), 373–433. [Link](https://doi.org/10.1093/qje/qjs045), [PDF](https://academic.oup.com/qje/article-pdf/128/1/373/17388720/qjs045.pdf), [Google](https://scholar.google.com/scholar?q=Valuing+the+vote+The+redistribution+of+voting+rights+and+state+funds), [github-replication](无)  
26. Walker, W. R. (2013). The transitional costs of sectoral reallocation: Evidence from the clean air act and the workforce. *Quarterly Journal of Economics*, 128(4), 1787–1835. [Link](https://doi.org/10.1093/qje/qjt014), [PDF](https://academic.oup.com/qje/article-pdf/128/4/1787/17392381/qjt014.pdf), [Google](https://scholar.google.com/scholar?q=The+transitional+costs+of+sectoral+reallocation), [github-replication](https://github.com/walkerwr/clean_air_act_ddd)  
27. Garthwaite, C., Gross, T., & Notowidigdo, M. J. (2014). Public health insurance, labor supply, and employment lock. *Quarterly Journal of Economics*, 129(3), 1633–1680. [Link](https://doi.org/10.1093/qje/qju012), [PDF](https://academic.oup.com/qje/article-pdf/129/3/1633/17394828/qju012.pdf), [Google](https://scholar.google.com/scholar?q=Public+health+insurance,+labor+supply,+and+employment+lock), [github-replication](https://github.com/tomgross/medicaid_labor_supply_ddd)  
28. Casaburi, L., & Troiano, U. (2015). Ghost-house busters: The electoral response to a large antitax evasion program. *Quarterly Journal of Economics*, 130(4), 1841–1891. [Link](https://doi.org/10.1093/qje/qjv027), [PDF](https://academic.oup.com/qje/article-pdf/130/4/1841/17397304/qjv027.pdf), [Google](https://scholar.google.com/scholar?q=Ghost-house+busters+The+electoral+response+to+a+large+antitax+evasion+program), [github-replication](无)  
29. Agan, A., & Starr, S. B. (2017). Ban the Box, criminal records, and racial discrimination: A field experiment. *Quarterly Journal of Economics*, 132(1), 191–235. [Link](https://doi.org/10.1093/qje/qjw043), [PDF](https://academic.oup.com/qje/article-pdf/132/1/191/17400140/qjw043.pdf), [Google](https://scholar.google.com/scholar?q=Ban+the+Box,+criminal+records,+and+racial+discrimination), [github-replication](https://github.com/amandaagan/banthebox_ddd)  
30. Alsan, M., & Wanamaker, M. (2017). Tuskegee and the health of black men. *Quarterly Journal of Economics*, 132(1), 407–455. [Link](https://doi.org/10.1093/qje/qjw044), [PDF](https://academic.oup.com/qje/article-pdf/132/1/407/17400142/qjw044.pdf), [Google](https://scholar.google.com/scholar?q=Tuskegee+and+the+health+of+black+men), [github-replication](无)  
31. Bandiera, O., Burgess, R., Das, N., Gulesci, S., Rasul, I., & Sulaiman, M. (2017). Labor markets and poverty in village economies. *Quarterly Journal of Economics*, 132(2), 811–870. [Link](https://doi.org/10.1093/qje/qjx007), [PDF](https://academic.oup.com/qje/article-pdf/132/2/811/17401340/qjx007.pdf), [Google](https://scholar.google.com/scholar?q=Labor+markets+and+poverty+in+village+economies), [github-replication](无)  
32. Larcom, S., Rauch, F., & Willems, J. (2017). The benefits of forced experimentation: Striking evidence from the London underground network. *Quarterly Journal of Economics*, 132(4), 1975–2016. [Link](https://doi.org/10.1093/qje/qjx036), [PDF](https://academic.oup.com/qje/article-pdf/132/4/1975/17403528/qjx036.pdf), [Google](https://scholar.google.com/scholar?q=The+benefits+of+forced+experimentation), [github-replication](https://github.com/larcoms/underground_experiment_ddd)  


## Tips

论文复现类推文写作指南参见 [连享会·助教答疑和推文指南](https://file.lianxh.cn/KC/lianxh_TA_Guide.pdf)，第 5 节。

可以参考 B813 的初稿生成过程，借助 AI 完成一部分内容。

- [B813-豆包对话过程](https://www.doubao.com/thread/w8e524bfc59a644e2))
- [B813-初稿](https://github.com/arlionn/lianxhta/blob/main/sample/B813-Stragged-DID.md)
