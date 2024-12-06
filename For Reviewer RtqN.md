Thank you for your valuable feedback on our manuscript! We are immensely gratified and encouraged to learn that our proposed framework, the problem tackled, and our experiments have garnered your acknowledgment. Below is our point-by-point reply to the weaknesses and questions you pointed out.

> **Weakness 1** *Some experimental datasets (e.g., generated fact statements, GPT-generated bias statements) may not fully represent the complexities of real applications.*

We appreciate your reasonable concerns but would like to kindly point out that:

- **Our work is rooted in previous research.** The notion of Safety we considered in the Multi-Agent System (MAS) context is derived from LLM Safety and is reflected in our settings of experimental datasets. Many surveys on LLM Safety, such as [1], indicate that the main work on Safety is to prevent models from being used for malicious purposes, primarily including the prevention of model-generated misinformation, bias, and harmful content. In our experimental dataset setup (in `Section 4.1`), we categorize misinformation into three levels—fact, commonsense, and reasoning—using the `Fact`, `CSQA`, and `GSMath` datasets. For bias and harmful information, we turn to the `Bias` and `AdvBench` datasets.
- **NetSafe aims to lay the foundation for future work.** It is true that the safety problems in more complex scenarios may be intricate, but they are typically combinations or variants of misinformation, bias, and harmful content, or other issues such as privacy. NetSafe provides solid foundational experimental contents and findings that can indeed reflect some current scenarios, such as Complete Graph for Multi-agent Debate [2], paving the way for future explorations of topological safety in more complex scenarios.
- **The GPT generation does not impact the experiment.** We have carefully verified the reasonableness of the generated facts and biases and using GPT for dataset generation is commonly used in the LLM-based agent field [3].



> **Weakness 2** *While the proposed framework and experiments are thorough, the paper lacks a clear discussion on the practical application of NetSafe to real-world LLM-based multi-agent systems (is there any real scenarios where this framework could be deployed).*

We greatly appreciate your valuable comments, and we plan to include a discussion on the application of NetSafe in real MAS scenarios in the appendix of the updated manuscript. In the meantime, we would like to share some preliminary thoughts:

- **Provide a topological perspective for designing safer MAS.** One of the purposes of NetSafe is to provide a topological perspective for the design of a safer LLM-based MAS. Currently, there is a surge of research and application in MAS, both in academia and industry, and the findings from NetSafe (in `Section 4.5`) encourage the design of MAS to be appropriately low in connectivity and short in processes to reduce potential safety risks (of course, this may lead to trade-off issues between safety and performance).
- **NetSafe can serve as a potential evaluation framework for the safety of MAS.** For some MAS frameworks that dynamically generate or optimize workflows based on task characteristics to solve these tasks (AutoGen [4], EvoAgent [5], AgentSquare [6], GPTSwarm [7]), the framework of NetSafe can be migrated to provide safety assessments for the topology of the designed workflows, providing guidance to get systems that are more secure against malicious attacks.
- **Offer new insights for LLM Safety research.** We find that the phenomenon of `Agent Hallucination` places higher demands on LLMs serving as agents: weaker hallucinations and higher performance are necessary to avoid the generation of misinformation, which could significantly degrade the performance of the entire network.

[1] Attacks, Defenses and Evaluations for LLM Conversation Safety: A Survey

[2] Encouraging divergent thinking in large language models through multi-agent debate

[3] Camel: Communicative agents for" mind" exploration of large language model society

[4] Autogen: Enabling next-gen LLM applications via multi-agent conversation framework

[5] EvoAgent: Towards Automatic Multi-Agent Generation via Evolutionary Algorithms

[6] AgentSquare: Automatic LLM Agent Search in Modular Design Space

[7] GPTSwarm: Language Agents as Optimizable Graphs
