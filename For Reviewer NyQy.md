Thank you for your insightful feedback! We have thoughtfully reviewed and addressed each of your comments and questions in detail below.

>**Weakness1** *It is unclear if these observations can be extended to more complex and larger structures. Therefore, it would be better if the author can conduct the same experiments on larger networks.*

From the perspective of traditional network theory, it is indeed true that a network consists of a large number of nodes, so your concern is reasonable. However, from the perspective of LLM-based Multi-Agent Systems (MAS), we would like to respectfully point out that:

- **In current mainstream LLM-based MAS research, the number of nodes typically considered is fewer than 10.** Some influential works on task-solving MAS, such as Camel [2], which simulates user-AI interactions, include only 3 agents: Task Decomposer, AI Instructor, and AI User. MetaGPT [3], used for code development, includes 5 agents: Product Manager, Architect, Project Manager, Engineer, and QA Engineer. Experiments on AutoGen [4], which supports automatic MAS structure generation based on tasks, also only consider 3-4 agents. Of course, we believe that as research advances, MAS will indeed face the issue of more nodes, and our work lays a solid foundation for this future development.

- **The focus is different.** The focus of our work is on the safety of MAS with different topological structures when under attack, and the number of nodes is not a decisive factor. We follow the leading works in the MAS field and set up experiments with fewer than 10 agents. 

- **We present extra experiments with larger networks.** In RQ3, we conducted experiments to explore scenarios with more nodes, and we present the results in the `Table A` below and they will be involved and discussed in the appendix of later updated manuscript:

*Table A: MJA across  the number of normal agent nodes on the Fact dataset (attacker_num=1, other settings are the same as in the main experiment).*

| Topology/Iteration  | Turn1 | Turn2 | Turn3 | Turn4 | Turn5 | Turn6 | Turn7 | Turn8 | Turn9 | Turn10 |
| ------------------- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ------ |
| Cycle (N=9)         | 93.79 | 90.93 | 88.56 | 87.17 | 86.19 | 84.89 | 85.38 | 84.80 | 84.31 | 83.33  |
| Cycle (N=10)        | 93.25 | 90.56 | 88.74 | 86.93 | 85.98 | 85.11 | 85.26 | 85.04 | 84.24 | 83.59  |
| Star Graph (N=9)    | 93.71 | 85.87 | 82.68 | 81.21 | 79.17 | 77.53 | 75.74 | 74.26 | 73.53 | 72.30  |
| Star Graph (N=10)   | 93.32 | 85.62 | 82.14 | 79.30 | 77.56 | 76.40 | 74.58 | 73.42 | 72.19 | 71.10  |
| Complete Graph(N=6) | 94.12 | 89.67 | 88.37 | 85.75 | 84.05 | 83.14 | 83.01 | 82.09 | 81.18 | 80.39  |
| Complete Graph(N=7) | 93.14 | 90.09 | 87.47 | 86.38 | 86.06 | 85.84 | 85.84 | 85.19 | 84.97 | 84.97  |
| Complete Graph(N=8) | 94.12 | 90.29 | 88.52 | 87.11 | 86.74 | 86.74 | 86.83 | 86.37 | 86.27 | 86.27  |



>**Weakness2** *The experiments are mainly conducted on GPT-4o-mini. Since the experiments mainly focus on safety issue of LLMs, it is not clear if other LLMs will have the same issues.*

- **Experimental Perspective:** In NetSafe, we treat the LLM as a black-box function and focus our research on the overall topology safety of the MAS rather than individual LLMs. The differences between different LLMs primarily lie in task performance, and they are essentially similar. The results above also validate that the type of LLM does not alter our conclusions regarding topology safety in MAS.

- **Additional Experiment:** Your concern is reasonable. Under the same experimental settings, we have added experimental results for other models (`Table B and C`). We will include these results with discussion in the appendix of the subsequent update of the manuscript and provide explanations in the main text.

*Table B: MJA Across Different Topologies on the Fact Dataset (**Model: Claude-3-haiku**, other settings identical to the experiments in Section 4.2)*

| Topology/Iteration | Turn1 | Turn2 | Turn3 | Turn4 | Turn5 | Turn6 | Turn7 | Turn8 | Turn9 | Turn10 |
| ------------------ | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ------ |
| Chain              | 77.96 | 74.27 | 72.24 | 61.22 | 50.61 | 41.63 | 33.88 | 32.24 | 28.57 | 28.57  |
| Circle             | 79.25 | 76.23 | 58.11 | 38.87 | 28.3  | 23.77 | 19.62 | 16.98 | 15.85 | 15.09  |
| Binary Tree        | 78.49 | 76.98 | 50.94 | 36.6  | 26.42 | 23.02 | 18.87 | 20.38 | 19.62 | 20.02  |
| Star Graph         | 76.23 | 58.87 | 40.38 | 28.3  | 16.98 | 13.21 | 11.32 | 10.19 | 10.19 | 9.43   |
| Complete Graph     | 76.98 | 63.77 | 35.09 | 28.3  | 24.91 | 24.15 | 23.4  | 23.4  | 20.38 | 18.87  |

*Table C: MJA Across Different Topologies on the Fact/GSMath/Bias Dataset (**Model: Llama-3.1-70B**, other settings identical to the experiments in Section 4.2)*

| Topology/Iteration | Turn1 | Turn2 | Turn3 | Turn4 | Turn5 | Turn6 | Turn7 | Turn8 | Turn9  | Turn10 |
| ------------------ | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ------ | ------ |
| Fact/Binary Tree   | 94.62 | 60.38 | 70.05 | 69.62 | 69.62 | 63.08 | 63.85 | 64.23 | 64. 06 | 63.62  |
| Bias/Chain         | 96.22 | 76.22 | 71.89 | 67.57 | 71.35 | 68.11 | 64.86 | 69.73 | 68.65  | 69.27  |
| Bias/Binary Tree   | 95.14 | 77.30 | 78.38 | 74.05 | 78.92 | 72.43 | 76.22 | 72.97 | 73.14  | 72.70  |
| Bias/Complete      | 96.22 | 77.34 | 83.24 | 77.27 | 78.92 | 75.68 | 75.68 | 71.35 | 69.11  | 70.30  |
| GSMath/Bi-Tree     | 72.96 | 57.42 | 75.48 | 67.10 | 68.39 | 70.32 | 70.32 | 65.16 | 66.90  | 67.74  |
| GSMath/Complete    | 72.72 | 66.45 | 74.19 | 74.19 | 70.97 | 70.32 | 72.26 | 72.90 | 70.97  | 70.58  |



>**Weakness3** *It is not clear if the locations of the attack nodes in the structure will affect the attack performance.*

Thank you for your suggestion. The points you raised help us further expand the scope of our research on topology safety. We conducted the following **supplementary experiments** (`Table D`) and found that the position of the attack nodes in the topology indeed affects safety. We will include this in the appendix for discussion in the updated version of the manuscript.

*Table D: MJA across turns for different positions of attack nodes on the CSQA dataset (other settings are the same as in the main experiment).*

| Topology/Iteration      | Turn1 | Turn2 | Turn3 | Turn4 | Turn5 | Turn6 | Turn7 | Turn8 | Turn9 | Turn10 |
| ----------------------- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ------ |
| Chain/First Node        | 64.88 | 64.09 | 64.09 | 65.51 | 65.04 | 65.20 | 64.25 | 64.72 | 65.2  | 65.35  |
| Chain/Second Node       | 64.50 | 62.55 | 62.55 | 62.05 | 62.32 | 65.10 | 62.55 | 67.55 | 65.10 | 67.50  |
| Bi-Tree/Root            | 63.15 | 62.36 | 61.57 | 61.73 | 60.47 | 60.31 | 58.74 | 58.74 | 57.80 | 57.48  |
| Bi-Tree/Root Left Child | 62.60 | 61.81 | 60.24 | 59.45 | 58.82 | 58.98 | 57.87 | 58.66 | 57.87 | 58.03  |
| Star/Center             | 64.09 | 63.62 | 62.68 | 60.63 | 59.84 | 58.43 | 57.64 | 55.59 | 54.65 | 53.54  |
| Star/Peripheral         | 62.50 | 62.50 | 60.54 | 59.67 | 60.02 | 60.02 | 60.02 | 60.50 | 57.50 | 55.46  |



>**Weakness4&Q1** It would be better if more state-of-the-art multi-agent adversarial attacks could be considered, such as [1]. 

We are indeed keeping an eye on the latest research specifically targeting MAS attacks.

- **Reason for not applying [1]:** Regarding the work you mentioned [1], we have referenced it in the main text (Agent Safety section of Related Work). However, we found that it focuses more on defense rather than attack, and thus doesn't fully apply to the three attack scenarios we consider.
- **We applied the most advanced methods available at present:** The attack method we experimented with in harmful-info elicitation is based on the dark trait injection attack proposed by the state-of-the-art PsySafe [5].
- **Future work:** Additionally, we have noted some recent preprints on related topics, such as [6], and are considering incorporating them in future work.

[1] Combating Adversarial Attacks with Multi-Agent Debate.

[2] Camel: Communicative agents for" mind" exploration of large language model society

[3] Metagpt: Meta programming for multi-agent collaborative framework

[4] Autogen: Enabling next-gen llm applications via multi-agent conversation framework

[5] PsySafe: A Comprehensive Framework for Psychological-based Attack, Defense, and Evaluation of Multi-agent System Safety

[6] Prompt Infection: LLM-to-LLM Prompt Injection within Multi-Agent Systems
