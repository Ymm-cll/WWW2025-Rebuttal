Thank you for your valuable feedback on our manuscript. We greatly appreciate and are encouraged by your acknowledgment of our work. Below is our respectfully composed, point-by-point response to the weaknesses and questions you have highlighted.

>**Weakness1** *The paper primarily focuses on misinformation attacks and does not explore other types of attacks, such as bias and harmful information attacks.*

Sorry for that we may not make it clear. We actually investigated the impact of bias and harmful information attacks on the topology safety of Multi-agent system (MAS), and have summarized the findings in RQ2 (in `Section 4.2`):

- **"Aggregation Safety" Phenomenon 1:** Due to the safety mechanisms of LLMs, the impact of bias and harmful information on attacks within MAS is relatively small and harder to propagate, compared with misinformation. 

- **"Aggregation Safety" Phenomenon 2:** At the same time, we observed that due to interactions between agents, the attacker nodes affected by bias and harmful information attacks have the potential to be corrected, which is discussed in RQ2-Obs1 (in `Section 4.3`). We present the results in the following `Table A`.

*Table A: SAA of attacker node Across Different Topologies on the Bias Dataset*

| Topology/Iteration | Turn1 | Turn2 | Turn3 | Turn4 | Turn5 | Turn6 | Turn7 | Turn8 | Turn9 | Turn10 |
| ------------------ | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ------ |
| Binary Tree        | 4.85  | 11.65 | 9.71  | 11.65 | 11.65 | 11.65 | 10.68 | 12.62 | 12.62 | 12.62  |
| Complete Graph     | 2.91  | 9.71  | 16.5  | 19.42 | 20.39 | 22.33 | 23.30 | 23.30 | 23.30 | 23.33  |

We will update the manuscript to make this clearer.



>**Weakness2** *The paper investigates the safety of a limited number of topologies, and further research is needed to explore the safety of networks with more complex structures.*

We sincerely appreciate your valuable feedback. In response, we would like to offer the following explanations to provide further clarity and information.

- **Experimental Content and Objective:** Our experiment includes common and basic topologies, with the aim of laying the foundation for research on more complex and dynamic topologies in MAS safety.

- **Additional Experiments:** We provide more experiments on complex topologies in `Table B`.

*Table B: MJA Across More Topologies on the Fact Dataset (other settings identical to the experiments in Section 4.2)*

| Topology/Iteration  | Turn1 | Turn2 | Turn3 | Turn4 | Turn5 | Turn6 | Turn7 | Turn8 | Turn9 | Turn10 |
| ------------------- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ------ |
| Layer (N=6)         | 94.90 | 92.55 | 90.33 | 89.28 | 88.24 | 87.84 | 86.80 | 85.88 | 85.75 | 85.23  |
| 2-Center Star (N=6) | 96.47 | 90.59 | 84.71 | 84.71 | 84.71 | 85.88 | 85.88 | 83.53 | 81.18 | 81.18  |
| Grid  (N=9)         | 93.60 | 92.26 | 88.99 | 88.10 | 88.39 | 87.65 | 87.20 | 87.05 | 85.71 | 85.57  |




>**Question1** *How does the NetSafe framework handle the potential for LLM agents to have different levels of trustworthiness or reliability? How is this incorporated into the evaluation of network safety?*

The issue you raised is indeed worthy of attention. However, we kindly wish to note that:

- **Focus of Topic:** Our work primarily focuses on the impact of topologies on the safety of MAS, rather than the impact of individual LLMs.

- **Current Considerations and Additional Experiments:** Based on your suggestions, and considering that different LLMs do vary in safety, we have added experiments for different LLMs *(both open and closed-source LLMs)*. This will be included and discussed in the appendix of the later updated manuscript.

*Table C: MJA Across Different Topologies on the Fact Dataset (**Model: Claude-3-haiku**, other settings identical to the experiments in Section 4.2)*

| Topology/Iteration | Turn1 | Turn2 | Turn3 | Turn4 | Turn5 | Turn6 | Turn7 | Turn8 | Turn9 | Turn10 |
| ------------------ | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ------ |
| Chain              | 77.96 | 74.27 | 72.24 | 61.22 | 50.61 | 41.63 | 33.88 | 32.24 | 28.57 | 28.57  |
| Circle             | 79.25 | 76.23 | 58.11 | 38.87 | 28.3  | 23.77 | 19.62 | 16.98 | 15.85 | 15.09  |
| Binary Tree        | 78.49 | 76.98 | 50.94 | 36.6  | 26.42 | 23.02 | 18.87 | 20.38 | 19.62 | 20.02  |
| Star Graph         | 76.23 | 58.87 | 40.38 | 28.3  | 16.98 | 13.21 | 11.32 | 10.19 | 10.19 | 9.43   |
| Complete Graph     | 76.98 | 63.77 | 35.09 | 28.3  | 24.91 | 24.15 | 23.4  | 23.4  | 20.38 | 18.87  |

*Table D: MJA Across Different Topologies on the Fact/GSMath/Bias Dataset (**Model: Llama-3.1-70B**, other settings identical to the experiments in Section 4.2)*

| Topology/Iteration    | Turn1 | Turn2 | Turn3 | Turn4 | Turn5 | Turn6 | Turn7 | Turn8 | Turn9  | Turn10 |
| --------------------- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ------ | ------ |
| Fact/Binary Tree      | 94.62 | 60.38 | 70.05 | 69.62 | 69.62 | 63.08 | 63.85 | 64.23 | 64. 06 | 63.62  |
| GSMath/Binary Tree    | 72.96 | 57.42 | 75.48 | 67.10 | 68.39 | 70.32 | 70.32 | 65.16 | 66.90  | 67.74  |
| GSMath/Complete Graph | 72.72 | 66.45 | 74.19 | 74.19 | 70.97 | 70.32 | 72.26 | 72.90 | 70.97  | 70.58  |
| Bias/Chain            | 96.22 | 76.22 | 71.89 | 67.57 | 71.35 | 68.11 | 64.86 | 69.73 | 68.65  | 69.27  |
| Bias/Binary Tree      | 95.14 | 77.30 | 78.38 | 74.05 | 78.92 | 72.43 | 76.22 | 72.97 | 73.14  | 72.70  |
| Bias/Complete Graph   | 96.22 | 77.34 | 83.24 | 77.27 | 78.92 | 75.68 | 75.68 | 71.35 | 69.11  | 70.30  |

In `Table C and D`, we present additional experiments results showing that our findings, like `Agent Hallucination` and `Aggregation Safety`, apply to MAS based on different LLMs.



> **Question2** *The paper focuses on misinformation attacks. Are there plans to expand the research to include other types of attacks, such as those targeting the agents’ reasoning abilities or their ability to use external tools?*

Thank you very much for your suggestions! We have indeed taken note of related work on attacking reasoning and tools.

- We will consider attacks on the reasoning capabilities of LLMs in future work, as seen in [1] and [2], as well as attacks on external tools, as discussed in [3] and [4].

- In the appendix of the updated manuscript, we will include a detailed discussion of potential future work, covering but not limited to the two points mentioned above.


**Reference:**

[1] Badchain: Backdoor chain-of-thought prompting for large language models

[2] Watch out for your agents! investigating backdoor threats to llm-based agents

[3] Injecagent: Benchmarking indirect prompt injections in tool-integrated large language model agents

[4] AgentDojo: A Dynamic Environment to Evaluate Attacks and Defenses for LLM Agents
