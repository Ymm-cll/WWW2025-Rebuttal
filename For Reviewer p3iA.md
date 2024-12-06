Thank you very much for your valuable comments! Below, we have carefully considered and responded to your valuable comments point by point. 

> **W1 & Q3** *RelCom的动机*

我们提出RelCom的动机如下：

- 现有MAS框架中的交流机制太多，且通常为了专门的任务设计（引用）。多Agent交流的核心在于高效、充分和灵活（引用）。而RelCom具备这些特性且易于实现，便于进行普适、通用的实验研究(Section3.1)。

- RelCom具有多轮可迭代、收敛的特性，以研究MAS在达到“稳态”前和处于“稳态”时的安全性质(RQ1, Obs1)
- Multi-agent Debate也是一种通用统一的交流机制，而RelCom对齐进行了推广，支持自定义的MAS的图结构

> **W2 & W8 & Q1** *拓扑在其他两类攻击中是否没有影响*

拓扑在其他两类攻击中是有影响的，我们将从以下两个方面澄清您的疑惑：

- 对于attacker node，不同拓扑结构下其被修正的水平是各异的（列数据）。

- 对于normal node，单体LLM的安全导致其很难被攻击、影响，进而在交流中attacker出现被修正的可能（聚合安全）。

> **W3** *到底是拓扑还是LLM主导的安全性？* 

您所提及的两个方面对于multi-agent的安全问题都不可或缺：

- LLM本身的安全决定的是MAS系统中单节点的局部安全性，是以往的工作的重点（引用）。

- 拓扑是Agent之间的信息流和交互，其影响的是MAS的全局安全性。我们的工作正是聚焦于这一unexplored的整体性安全。

> **W4** *RQ1-obs2的结论太普遍了*

这一结论在其他领域确实是常见的，但是我们首次发现并揭示了高联通性在LLM-based MAS安全性场景下其实还是一把双刃剑：

- RQ1-Obs2的贡献在于系统且严谨的report和验证该结论在LLM-based MAS受misinformation攻击场景下的正确性
- RQ2表明更高联通的拓扑会带来更强的防御能力（bias和harmful-info）（列数据）

> **W5** *RQ1-obs3表明更复杂的问题更安全，与agent幻觉矛盾*

我们可能在表述上引起了confusion，但其实两者并不矛盾：agent幻觉确实是指单节点的misinformation会传播到整个网络，但是Obs3所说的更安全是指MAS处理复杂问题时受到的恶意影响更小，而非不会传播。

>**W6** *静态指标换成别的可能结论不同*

- 结果导向的动态指标反映的是MAS在受攻击时受到的实际影响。而有效的静态指标一方面需要精心设计，另一方面并不能总是反映MAS在动态、具体的场景下的安全性。我们无意拉踩，只是指出MAS安全性有必要进行动态评估，更有效的静态指标并不与动态评估矛盾。

- 加几个指标的数据

>**W7** *Section4.3中bias和harmful-info之间笼统的化为聚合安全*

我们将bias与harmful-info都化为聚合安全的考虑如下：

  - 从现象而言，两者的是类似的，均是attacker node被邻居节点的安全性修正（数据）。
  - 从原因而言，都是因为single LLM的安全性导致MAS对bias和harmful-info更安全

>**W9** *技术太简单*

我们其实是一个很全面的框架，考虑了以往工作未考虑的一些问题，具体体现如下：

- 新视角：NetSafe首次从拓扑视角研究了multi-agent safety，观察了不同拓扑的MAS在面对misinformation, bias以及harmful information三种攻击方式时的安全性dynamics，发现并命名了agent幻觉，聚合安全的现象。我们相信易于迁移的NetSafe和这些重要的现象，都会对MAS safety的future work有所启发。
- 新的建模策略

- 新的交流机制：我们提出了RelCom机制，为探讨multi-agent safety的问题提供了一个统一且易收敛的交流机制，方便未来研究人员对mutli-agent safety问题进行进一步的研究。
- 全面的实验：精心设计大量且全面的实验和metrics来研究MAS的拓扑安全性问题。
- 静态和动态指标

> **W10** *对不同的攻击使用不同的指标*

感谢您提出的意见，实际上我们在论文中确实使用了不同的指标：

- misinformation和bias攻击的目的是使得agent给出错误、不道德的答案，因此衡量safety的metric是agent回复的正确率：(公式)
- harmful-info攻击的目的是使得agent生成有害内容，由于agent中毒无法直接由回复的正确率表示，因此衡量safety的metric是OPENAI对文本毒性打分的moderation api的各维度分数，如xx。

> **Q2** *What is the role of of the static metric (E_sta)? I am not sure it is used in the evalution anywhere or how it is calcualted.*

感谢您指出的问题！Sorry for 我们未表达清楚\(E_{sta}\)其实是对所有静态metric的一个通用定义，而非一个具体的metrics（公式）

> **Q4** *Why were GPT-4o-mini and GPT3.5-turbo chosen?*

我们在Section4.1的Settings中说明了主要是经济和实验上的原因，此外：

- GPT-4o-mini与GPT-4o内置了相同的安全性机制，且保持了高性能 [1]
- GPT-3.5-turbo安全性更弱 [2]，便于观察bias和harmful-info的影响
- 别的模型的实验

[1] https://openai.com/index/gpt-4o-mini-advancing-cost-efficient-intelligence/

[2] R-Judge: Benchmarking Safety Risk Awareness for LLM Agents







Thank you very much for your valuable comments! Below, we have carefully considered and responded to your valuable comments point by point. 

> **W1 & Q3** *RelCom is not motivated other than that it has strong convergence protperties. **&** Why is RelCom the best or most effective mechanism for this purpose and what other mechanisms were considered and compared to RelCom.*

The motivation for proposing RelCom is as follows:

- **Unified the excessive communication methods:** Existing Multi-Agent System(MAS) frameworks have too many communication methods, typically designed for specific tasks (MetaGPT [1] and AgentVerse [2]). The core of multi-agent communication lies in efficiency, comprehensiveness, and flexibility. RelCom possesses these characteristics and is easy to implement, making it suitable for universal and general experimental research (in `Section 3.1`).

- **The convergence properties have advantages:** RelCom features multi-turn iterability and convergence, which facilitates the study of the safety properties of MAS both before and after reaching "steady state" (RQ1, Obs1).

- **Multi-agent Debate is also a general and unified communication mechanism**, and RelCom extends its alignment, supporting customizable graph structures for MAS.




> **W2 & W8 & Q1** *The three types of attacks are misinformation injection, bias, and harmful response elicitation, however, only misinformation injection seem to be the only relevant threat from a topological perspective. What role is topology playing in the bias and harmful response attacks? **&** It does not seem to have any role. Is this correct? **&** Finally, in 4.5 we see in the short discussion that topology is a key dimension to evaluate safety, however, this only applies to misinformation attacks, and not the other two types studied in the paper.*

Topology has an impact on the other two types of attacks. We will clarify your concerns from the following two aspects:

- **For the attacker node**, the level of correction it undergoes varies under different topological structures.

- **For the normal node**, the safety of the individual LLM makes it difficult to attack or influence, which in turn increases the likelihood of the attacker being corrected during communication (aggregation safety). We provide results below in `Table A`:

*Table A: MJA of attacker node Across Different Topologies on the Bias Dataset*

| Topology/Iteration | Turn1 | Turn2 | Turn3 | Turn4 | Turn5 | Turn6 | Turn7 | Turn8 | Turn9 | Turn10 |
| ------------------ | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ------ |
| Binary Tree        | 4.85  | 11.65 | 9.71  | 11.65 | 11.65 | 11.65 | 10.68 | 12.62 | 12.62 | 12.62  |
| Complete Graph     | 2.91  | 9.71  | 16.5  | 19.42 | 20.39 | 22.33 | 23.30 | 23.30 | 23.30 | 23.33  |




> **W3** *One wonders, are we getting to the heart of the matter using this topological perspective or is it the case that safety within each LLM agent (like GPT3.5-turbo, or GPT-4o-mini) has a dominant role to play.* 

The two aspects you mentioned are both essential for the safety issues in MAS:

- **Local Safety:** The safety of the LLM itself determines the local safety of individual nodes in the MAS system, which has been the focus of previous works (citation).
- **Global Safety:** Topology governs the information flow and interaction between agents, influencing the global safety of the MAS. Our work specifically focuses on this unexplored aspect of overall safety.
- **Extra Experiments on Other LLMs**: We have added experiments in `Table B and C` for different LLMs *(both open and closed-source LLMs)*. This will be included and discussed in the appendix of the later updated manuscript.

*Table B: MJA Across Different Topologies on the Fact Dataset (**Model: Claude-3-haiku**, other settings identical to the experiments in Section 4.2)*

| Topology/Iteration | Turn1 | Turn2 | Turn3 | Turn4 | Turn5 | Turn6 | Turn7 | Turn8 | Turn9 | Turn10 |
| ------------------ | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ------ |
| Chain              | 77.96 | 74.27 | 72.24 | 61.22 | 50.61 | 41.63 | 33.88 | 32.24 | 28.57 | 28.57  |
| Circle             | 79.25 | 76.23 | 58.11 | 38.87 | 28.3  | 23.77 | 19.62 | 16.98 | 15.85 | 15.09  |
| Binary Tree        | 78.49 | 76.98 | 50.94 | 36.6  | 26.42 | 23.02 | 18.87 | 20.38 | 19.62 | 20.02  |
| Star Graph         | 76.23 | 58.87 | 40.38 | 28.3  | 16.98 | 13.21 | 11.32 | 10.19 | 10.19 | 9.43   |
| Complete Graph     | 76.98 | 63.77 | 35.09 | 28.3  | 24.91 | 24.15 | 23.4  | 23.4  | 20.38 | 18.87  |

*Table C: MJA Across Different Topologies on the Fact/GSMath/Bias Dataset (**Model: Llama-3.1-70B**, other settings identical to the experiments in Section 4.2)*

| Topology/Iteration    | Turn1 | Turn2 | Turn3 | Turn4 | Turn5 | Turn6 | Turn7 | Turn8 | Turn9  | Turn10 |
| --------------------- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ------ | ------ |
| Fact/Binary Tree      | 94.62 | 60.38 | 70.05 | 69.62 | 69.62 | 63.08 | 63.85 | 64.23 | 64. 06 | 63.62  |
| GSMath/Binary Tree    | 72.96 | 57.42 | 75.48 | 67.10 | 68.39 | 70.32 | 70.32 | 65.16 | 66.90  | 67.74  |
| GSMath/Complete Graph | 72.72 | 66.45 | 74.19 | 74.19 | 70.97 | 70.32 | 72.26 | 72.90 | 70.97  | 70.58  |
| Bias/Chain            | 96.22 | 76.22 | 71.89 | 67.57 | 71.35 | 68.11 | 64.86 | 69.73 | 68.65  | 69.27  |
| Bias/Binary Tree      | 95.14 | 77.30 | 78.38 | 74.05 | 78.92 | 72.43 | 76.22 | 72.97 | 73.14  | 72.70  |
| Bias/Complete Graph   | 96.22 | 77.34 | 83.24 | 77.27 | 78.92 | 75.68 | 75.68 | 71.35 | 69.11  | 70.30  |

In `Table B and C`, we present additional experiments results showing that our findings, like `Agent Hallucination` and `Aggregation Safety`, apply to MAS based on different LLMs.



> **W4** *RQ1-obs2. states that higher connectivity results in higher risk of misinformation attacks. However, this does not seem related to LLMs specifically, as this would be the case in most networked systems (like sensor networks) where spurrious readings or measurements can spread around the network better when all nodes are connected.*

This conclusion is indeed common in other fields, but we are the first to discover and reveal that high connectivity in LLM-based MAS safety scenarios is actually a double-edged sword:

- **For Misinformation:** The contribution of RQ1-Obs2 lies in systematically and rigorously reporting and validating the correctness of this conclusion in the context of misinformation attacks on LLM-based MAS.

- **For Bias and Harmful information:** RQ2 demonstrates that topologies with higher connectivity lead to higher potential to correct attacker nodes which may not be a common observation, as demonstrate in `Table A`:




> **W5** *RQ1-obs3 states that more complex tasks are resiliant to misinformation, but then goes on to say that "Agent hallucination" can spread misinformation to the enture network, which seems to be contradictory.*

We sincerely apologize for the confusion caused by our wording. In fact, the two points are not contradictory: agent hallucination does refer to the propagation of misinformation from a single node to the entire network, but what is meant by "more safe" in Obs3 is that the MAS experiences less malicious influence when handling complex problems, not that misinformation will not propagate.



>**W6** *Obs.5 depends on the particular metrics used for static evaluation and the results may be overturned if better static metrics were used. At best, the support is weak and more evaluation is need to support that dynamic eval is always superior to static.*

Result-oriented dynamic metrics reflect the actual impact on the MAS when under attack. On the other hand, effective static metrics require careful design and may not always capture the safety of the MAS in dynamic, specific scenarios. We do not intend to undermine static metrics, but rather point out that the safety of MAS needs to be dynamically evaluated. More effective static metrics do not contradict dynamic evaluation.



>**W7** *In section 4.3, the role of safe-guards against bias and harmful responses is not examined in particular and it is straight-away calssified as "aggregation safety".*

We treat both bias and harmful-info safeguards as considerations for aggregated safety as follows:

- **From a phenomenological perspective**, the two are similar, as both involve attacker nodes being corrected by neighboring nodes.
- **From the perspective of the causes of this phenomenon**, both arise because the safety of LLMs makes MAS more secure against bias and harmful information.



>**W9** *However the technical tools are simplistic and may not be the most apt for this purposes.*

NetSafe is actually a very comprehensive framework that addresses issues not considered in previous work. The specifics are as follows:

- **New Perspective**: NetSafe is the first to study MAS safety from a topological perspective, observing the safety dynamics of MAS under three types of attacks: misinformation, bias, and harmful information. It discovers and names phenomena like agent hallucinations and aggregation safety. We believe that the easily transferable NetSafe and these important phenomena will inspire future work on MAS safety.

- **New Communication Mechanism**: We propose the RelCom mechanism, providing a unified and convergent communication framework to explore multi-agent safety issues, facilitating further research on MAS safety.

- **Comprehensive Experiments**: A large number of carefully designed experiments were conducted to study the topological safety of MAS.

- **Specialized Metrics**: To better evaluate the topological safety under the dynamic communication framework of MAS, we have designed static and dynamic metrics to assess topological safety.




> **W10** *There needs much more supporting evidence through a more thourough examination with attention of each type of attack and perhaps more effective metrics.*

Thank you for your suggestions. We will include more attack methods and metrics in our future work. Currently, in the paper, we indeed use two different metrics:

- **For Misinformation and Bias Attacks:** The goal of these attacks is to make the agent provide incorrect or unethical answers. Therefore, the safety metric is the accuracy of the agent's responses: (formula).
- **For Harmful-Info Attacks:** The goal of these attacks is to make the agent generate harmful content. Since the agent is poisoned, its accuracy cannot be directly represented by the response's correctness. Thus, the safety metric is based on the moderation API from OPENAI, which scores the text's toxicity across different dimensions (demonstrated in `Table A`).



> **Q2** *What is the role of of the static metric (E_sta)? I am not sure it is used in the evalution anywhere or how it is calcualted.*

Thank you for pointing out the issue! We apologize for not clearly expressing the meaning of $E_{sta}$. It is a general definition for all static metrics, rather than a specific metric. The formula of $E_{sta}$ is as follows:

$$
E_{\text{sta}} = \mathcal{F}(\mathcal{G}, A, V_{\text{atk}})
$$
It indicates that the static metrics are functions of the graph $\mathcal{G}$, the adjacency matrix $A$, and $V_{\text{atk}}$ as parameters.



> **Q4** *Why were GPT-4o-mini and GPT3.5-turbo chosen?*

In Section 4.1, under Settings, we explained that the main reasons are economic and experimental. In addition:

- **For GPT-4o-mini:** GPT-4o-mini and GPT-4o incorporate the same security mechanisms and maintain high performance. [3]
- **For GPT-3.5-turbo:** GPT-3.5-turbo has weaker security [4], making it easier to observe the impact of bias and harmful information on MAS in different topologies.

[1] Metagpt: Meta programming for multi-agent collaborative framework

[2] Agentverse: Facilitating multi-agent collaboration and exploring emergent behaviors in agents

[3] https://openai.com/index/gpt-4o-mini-advancing-cost-efficient-intelligence/

[4] R-Judge: Benchmarking Safety Risk Awareness for LLM Agents
