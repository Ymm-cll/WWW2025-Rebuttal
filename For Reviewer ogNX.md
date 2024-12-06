We would like to express our heartfelt gratitude for your insightful comments and for affirming our research. In response, we have provided point-by-point answers to the weaknesses and your questions. 


>**Weakness1** *This paper uses five pre-defined topological structures. In the real world, the topological structures of multi-agent systems are often a combination of these pre-defined types. To better reflect practical applications, it is recommended to conduct additional experiments under these more realistic and complex settings.*

- **Experiment Content and Objective:** Our experiments include typical and basic topologies, with the aim of laying the foundation for research on more complex and dynamic topologies in Multi-agent System (MAS) safety.
- **Realistic Topologies in MAS:** In fact, the existing Chain and Complete Graph topologies are realistic explorations of the safety of structures used in previous influential MAS works, such as Camel [1] and Multi-agent Debate [2] (the main difference in experiments is the system prompts for the agents).
- **Additional Experiments:** We agree with your suggestion. For more complex topologies, we can simply modify the adjacent matrix in the code of NetSafe for further experiments and study. Then We provide additional experiments below and they will be involved and discussed to the appendix  section in later updated manuscript.

*Table A: MJA Across More Topologies on the Fact Dataset (other settings identical to the experiments in Section 4.2)*

| Topology/Iteration  | Turn1 | Turn2 | Turn3 | Turn4 | Turn5 | Turn6 | Turn7 | Turn8 | Turn9 | Turn10 |
| ------------------- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ------ |
| Layer (N=6)         | 94.90 | 92.55 | 90.33 | 89.28 | 88.24 | 87.84 | 86.80 | 85.88 | 85.75 | 85.23  |
| 2-Center Star (N=6) | 96.47 | 90.59 | 84.71 | 84.71 | 84.71 | 85.88 | 85.88 | 83.53 | 81.18 | 81.18  |
| Grid  (N=9)         | 93.60 | 92.26 | 88.99 | 88.10 | 88.39 | 87.65 | 87.20 | 87.05 | 85.71 | 85.57  |

​      


> **Weakness2** *AgentSmith and PsySafe propose attacks on multi-agent systems. Are these attacks compatible with the proposed framework? It is recommended to include additional results and observations related to these existing attacks.*

Thank you for your valuable suggestions. We have taken them into careful consideration and are pleased to provide the following:

- **AgentSmith explores attacks in multimodal scenarios**, while we focus on the text modality. However, the multi-modal attack methods used in AgentSmith can be adapted by replacing the agents in NetSafe with multi-modal agents, thus enabling the exploration of topological security in multi-modal scenarios.

- **We explored the attacks proposed in PsySafe.** We used the Dark Trait Injection attack proposed by PsySafe to conduct experiments on harmful information attack (in `Section 4.1` Datasets).


[1] Camel: Communicative agents for" mind" exploration of large language model society

[2] Encouraging divergent thinking in large language models through multi-agent debate
