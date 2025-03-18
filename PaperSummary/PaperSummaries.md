## [ChatDev - Communicative Agents for Software Development](https://arxiv.org/abs/2307.07924)

- Splitting a large task in smaller quantitative tasks performed by multiple agents to achieve better results
- Asking a LLM to self-reflect till it converges on a single answer
- Swapping roles and asking the opposite on providing feedback, and then swapping back can increase performance in certain situations.
- Providing LLM with tools which it can use to self-reflect


## [Reflexion Language Agents with Verbal Reinforcement Learning](https://arxiv.org/abs/2303.11366)

- Asking model on failure how it could improve itself, then summarizing that and using in memory and prompting again.
- Keeping a short detailed memory of the actions that have just happened, and a summarized long term memory for past experiences.
- Use LLM to generate self-reflection, and then storing them in a vector DB, pulling them with RAG for long-term memory


## [Cognitive Architectures for Language Agents](https://arxiv.org/abs/2309.02427)

- Short term and long term memory. Short term includes the imitate actions state, Long term memory is divided into three distinct types. Procedural memory stores the production system itself: the set of rules that can be applied to working memory to determine the agent’s behavior. Semantic memory stores facts about the world, while episodic memory stores sequences of the agent’s past behaviors.
- Using augmented retrieval to load the most relevant memory
- model can choose between retrieval (read from long-term memory), reasoning (update the short-term working memory with LLM), and learning (write to long-term memory)


## [AutoGen Enabling Next-Gen LLM Applications via Multi-Agent Conversation](https://arxiv.org/abs/2308.08155)

- AutiGen agent capabilities are powered by LLM backed agents, human proxy agents, and tool backed agents.
- AutoGen utilizes conversation programming, a paradigm that considers two concepts: computation: the actions agents take to compute their response in a multi-agent conversation. And the second is control flow: the sequence (or conditions) under which these computations happen.
- Autogen uses various control flow management patterns: 1) Natural language control via LLM, 2) programming language control, 3) Control transition between natural and programming language. 


## [MetaGPT Meta Programming for A Multi-Agent Collaborative Framework](https://arxiv.org/abs/2308.00352)

- The framework follows Standardized Operating Procedures (SOPs) that guide the sequence of operations. 
- Structured Communication Interfaces: Agents communicate through documents and diagrams (structured outputs) rather than dialogue. These documents contain all necessary information, preventing irrelevant or missing content. Subscribe Mechanism: information is stored in a global message pool. Any agent can directly retrieve required information from the shared pool, eliminating the need to inquire about other agents and await their responses. Instead of relying on dialogue, agents utilize role-specific interests to extract relevant information. They can select information to follow based on their role profiles. In practical implementations, an agent activates its action only after receiving all its prerequisite dependencies.


## [AgentBoard An Analytical Evaluation Board of Multi-turn LLM Agents](https://arxiv.org/abs/2401.13178)

- AgentBoard introduces a unified progress rate metric, in addition to success rates, to track detailed advancements of agents. This metric helps in identifying significant progress that might not be evident through success rates alone.
- AgentBoard assess LLMs across several facets: memory that measures incorporating long-range information in context, planning that assesses decomposing complex goals into manageable sub-goals, world modeling which tests knowledge necessary for task completion, retrospection that captures the ability to use environmental feedback, grounding that focuses on competency in generating valid actions, and spatial navigation that represents efficiency in moving to a target location


## [ReAct Synergizing Reasoning and Acting in Language Models](https://arxiv.org/abs/2210.03629)

-


## [Gorilla Large Language Model Connected with Massive APIs](https://arxiv.org/abs/2305.15334)

-


## [Chain-of-Thought Prompting Elicits Reasoning in Large Language Models](https://arxiv.org/abs/2201.11903)

- A chain of thought is a series of intermediate natural language reasoning steps that lead to the final output
- COT allows models to decompose multi-step problems into intermediate steps, which means that additional computation can be allocated to problems that require more reasoning steps.
- COT provides an interpretable window into the behavior of the model, suggesting how it might have arrived at a particular answer and providing opportunities to debug where the reasoning path went wrong.
- COT reasoning can be used for tasks such as math word problems, commonsense reasoning, and symbolic manipulation, and is potentially applicable to any task that humans can solve via language.

## [Understanding the planning of LLM agents A survey](https://arxiv.org/abs/2402.02716)

- They present a novel and systematic taxonomy for LLM-based agent planning that divides existing works into five important categories, covering task decomposition, multi-plan selection, external module-aided planning, reflection and refinement and memory-augmented planning

- Task Decomposition: This kind of method adopts the idea of divide and conquer, decomposing the complicated into several sub-tasks and then sequentially planning for each sub-task.
  - Task decomposition generally involves two crucial steps: firstly, decomposing the complex task, referred to as the “decompose” step, and secondly, planning for the sub-tasks, known as the “sub-plan step”. 
  - Decomposition-first methods decompose the task into sub- goals first and then plan for each sub-goal successively
  - Interleaved decomposition involves interleaved task decomposition and sub-task planning, where each decomposition only reveals one or two sub-tasks at the current state

- Multi-plan Selection. This kind of method focuses on lead- ing the LLM to “think” more, generating various alternative plans for a task. Then a task-related search algorithm is em- ployed to select one plan to execute.
  - Multi-plan generation involves generating a dozen paths of plans to comprise the candidate plan set. Mainstream methods consider employing uncertainty in the decoding process of generative models.
  - Self-consistency applies the naive majority vote strategy, regarding the plan with the most votes as the optimal choice. Tree-of-Thought (ToT) supports tree search algorithms, such as conventional BFS and DFS. When selecting a node for expansion, it uses LLM to evaluate multiple actions and chooses the optimal one. LLMMCTS and RAP also employ the Monte Carlo Tree Search (MCTS) algorithm for search. LLM A* utilizes the classic A* algorithm from artificial intelligence to assist LLM in search. The Chebyshev distance from the current position to the target position serves as the heuristic cost function for selecting the optimal path.

- External Planner-Aided Planning. This methodology is crafted to employ an external planner to elevate the planning procedure, aiming to address the issues of efficiency and in- feasibility of generated plans, while the LLM mainly plays the role in formalizing the tasks. 

- Reflection and Refinement. This methodology emphasizes improving planning ability through reflection and refinement. It encourages LLM to reflect on failures and then refine the plan.
    - Due to existing hallucination issues and insufficient reasoning abilities for complex problems, LLM-Agents may make errors and get stuck in “thought loops” during planning due to limited feedback. Reflecting on and summarizing failures helps agents correct errors and break out of such loops in subsequent attempts. 

- Memory-augmented Planning. This kind of approach enhances planning with an extra memory module, in which valuable information is stored, such as commonsense knowledge, past experiences, domain-specific knowledge, et al. The information is retrieved when planning, serving as auxiliary signals.
  - In contrast to deep reinforcement learning where updates are achieved by modifying model parameters, in the LLM agent, this update occurs through self- reflection by the LLM itself, culminating in textual verbal feedbacks. These textual feedbacks can serve as both long- term and short-term memory, influencing the agent’s subsequent planning outputs through the prompts.
  - Generative Agents store the daily experiences of human-like agents in text form and retrieve memories based on a composite score of recency and relevance to the current situation. MemoryBank, TiM, and RecMind encode each memory using a text encoding model into a vector and establish an indexing structure, such as FAISS library. During retrieval, the description of the current status is used as a query to retrieve memories from the memory pool.
  - Embodied memory involves fine tuning the LLM with the agent’s historical experiential samples, embedding memories into the model parameters.

- Interactive Retrieval Environments: Interactive retrieval environments simulate the process of information retrieval and reasoning that humans undergo in real life. In these environments, agents are often allowed to interact with search engines and other web services, using actions such as searching keywords or executing click, forward, and backward operations to acquire more information, thereby obtaining answers to questions or completing information retrieval tasks.

- Interactive Programming Environments: Interactive programming environments simulate the interaction between programmers and computers, testing the agent’s planning ability in solving computer-related problems. In these environments, agents are required to interact with computers to solve problems by writing code or instructions. They would receive various feedback including compile and runtime error messages, as well as execution results.


## [Mixture-of-Agents Enhances Large Language Model Capabilities](https://arxiv.org/abs/2406.04692)

- The structure of MoA is constructed of LLM layers. LLMs in the first layer independently generate responses to a given prompt. These responses are then presented
to agents in the next layer (which may reuse a model from the first layer) for further refinement. This iterative refinement process continues for several cycles until obtaining a more robust and comprehensive response.
- Selection of LLMs for each MoA layer is guided by two primary criteria: 
    - **Performance Metrics**: The average win rate of models in layer i plays a significant role in
determining their suitability for inclusion in layer i + 1. 
    - **Diversity Considerations**: The diversity of model outputs is also crucial. Responses generated by heterogeneous models contribute
significantly more than those produced by the same model.
-  During the collaboration process, we can categorize LLMs into two distinct roles:
    - **Proposers** excel at generating useful reference responses for use by other models. Goal is to offer more context and diverse perspectives.
    - **Aggregators** are models proficient in synthesizing responses from other models into a single, high quality output. Goal maintain or enhance output quality
- The number of proposers in each layer affect the final output quality by varying n. The scores increases monotonically with n, reflecting the benefits of having more auxiliary information. 
-  Using a diverse set of LLMs as proposers is also very impactful. For each n, comparing the two settings: “single-proposer” where the n responses are generated by the same LLM with a temperature of 0.7; and “multiple-proposer” where each response is generated by a different LLMs; Overall, using multiple different LLMs consistently yielded better results.


## [Apple Intelligence Foundation Language Models](https://arxiv.org/abs/2407.21075)

- Apple foundation model (AFM) base models are dense decoder-only that share input/output embedding matrix to reduce memory usage for parameters, pre-normalization with RMSNorm for training stability, query/key normalization to improve training stability, grouped-query attention (GQA) with 8 key-value heads to reduce the KV-cache memory footprint, the SwiGLU activation for higher efficiency, RoPE positional embeddings with the base frequency set to 500k for long-context support.
- AFM pre-training can be broken into three distinct stages: 1. core which consumes most of the compute budget, 2. continued, where they down-weight the lower quality bulk web-crawl data, favoring a higher code and math weight instead combined with inclusion of the licensed data, 3. context-lengthening which is similar to another continued pre-training stage, but conducted at longer sequence length and with synthetic long-context data included in the mixture.
  - All three stages use decoupled weight decay for regularization, as well as a simplified version of µParam. All stages maintain sharded model and optimizer states in float32, casting to bfloat16 for the forward and backward passes for efficiency.
- AFM post-training efforts include a series of data collection and generation, instruction tuning, and alignment innovations. AFM post-training process contains two stages: supervised fine-tuning (SFT) and reinforcement learning from human feedback (RLHF). 
  - Apple presents two new post-training algorithms: (1) a rejection sampling fine-tuning algorithm with teacher committee (iTeC), and (2) a reinforcement learning from human feedback (RLHF) algorithm with mirror descent policy optimization and a leave-one-out advantage estimator (MDLOO) that are used on their reinforcement learning iterations and lead to significant model quality improvements.
  - Apple uses a hybrid data strategy in our post-training pipeline, which consists of both human annotated and synthetic data. 
  - Apple found that algorithms that leverage negative examples, e.g., online RLHF, DPO, IPO, to be better in improving reasoning skills such as math, while rejection sampling fine-tuning learns instruction following and writing skills more effectively.
  - We can elevate the performance of even small models to best-in-class performance through task-specific fine-tuning and have developed an architecture, based on runtime-swappable adapters, to enable the single foundation model to be specialized for dozens of such tasks.
    - For each task, we adapt all of AFM’s linear projection matrices in the self-attention layers and the fully connected layers in the pointwise feedforward networks. By fine-tuning only the adapters, the original parameters of the base pre-trained model remain unchanged, preserving the general knowledge of the model while tailoring the adapters to support specific tasks.
    - Previous works have found that 4-bit quantized models only have marginal loss of quality (typically measured in pre-training metrics) compared to the original 32/16-bit float-point versions. 
    -  Regarding adapter size, we found that adapter rank of 16 offers the optimal tradeoff between model capacity and inference performance. However, to provide flexibility for various use cases, we provide a suite of accuracy-recovery adapters in different ranks {8, 16, 32} for application teams to select from.
    -  Mixed-precision quantization Residual connections exist in every transformer block and every layer in AFM. So it is unlikely that all layers have the equal importance. Following this intuition, we further reduce the memory usage by pushing some layers to use 2-bit quantization (default is 4-bit). On average, AFM-on-device can be compressed to only about 3.5 bits per weight (bpw) without significant quality loss. We choose to use 3.7 bpw in production as it already meets the memory requirements.
    -  Before feature-specific finetuning, we first train accuracy-recovery adapters on the same pretraining and post-training data, which is critical to preserve the model quality. The feature adapters are initialized from these accuracy-recovery adapters.


## [Automated Design of Agentic Systems](https://arxiv.org/abs/2408.08435)
- Automated Design of Agentic Systems (ADAS), which aims to automatically create powerful agentic system designs, including inventing novel building blocks and/or combining them in new ways. It involves using a search algorithm to discover agentic systems across a search space that optimize an evaluation function.
- The core concept of Meta Agent Search is to instruct a meta agent to iteratively create interestingly new agents, evaluate them, add them to an archive that stores discovered agents, and use this archive to help the meta agent in subsequent iterations create yet more interestingly new agents.
  - Search Space: The search space defines which agentic systems can be represented and thus discovered in ADAS.
  - Search Algorithm: The search algorithm defines how ADAS algorithms explore the search space. Since the search space is often very large or even unbounded, the exploration-exploitation tradeoff should be considered. Ideally, the algorithm can both quickly discover high-performance agentic systems and avoid remaining stuck in a local optimum.
  - Evaluation Function: Depending on the application of the ADAS algorithm, we may consider different objectives to optimize, such as performance, cost, latency, or safety of agents. An evaluation function defines how to evaluate a candidate agent on those objectives.
 

## [A Survey on the Memory Mechanism of Large Language Model based Agents](https://arxiv.org/abs/2404.13501)
- In the agent-environment interaction process, there are three key phases, that is, (1) the agent perceives information from the environment, and stores it into the memory; (2) the agent processes the stored information to make it more usable; and (3) the agent takes the next action based on the processed memory information.
  - Memory Writing. This operation aims to project the raw observations into the actually stored memory contents, which are more informative and concise. It corresponds to the first phase of the agent-environment interaction process.
  - Memory Management. This operation aims to process the stored memory information to make it more effective, for example, summarizing high-level concepts to make the agent more generalizable, merging similar information to reduce redundancy, and forgetting unimportant or irrelevant information to remove its negative influence. This operation corresponds to the second phase of the agent-environment interaction process.
  - Memory Reading. This operation aims to obtain important information from the memory to support the next agent action. It corresponds to the third phase of the agent-environment interaction process.
- Memory Sources:
  - Inside-trial Information: In the agent-environment interaction process, the historical steps within a trial are usually the most relevant and informative signals to support the agent’s future actions.
  - Cross-trial Information: For LLM-based agents, the information accumulated across multiple trials in the environment is also a crucial part of the memory, typically including successful and failed actions and their insights, such as failure reasons, common action patterns to succeed, and so on.
  - External Knowledge: LLM-based agents can easily incorporate external knowledge in textual forms (e.g., Wikipedia 3) to facilitate their decisions. Moreover, most external knowledge can be acquired by accessing the APIs of various tools dynamically in real time according to the task needs, thus mitigating the problem of outdated knowledge. 
- Memory Forms
  - there are two forms to represent the memory contents: textual form and parametric form. In textual form, the information is explicitly retained and recalled by natural languages. In parametric form, the memory information is encoded into parameters and implicitly influences the agent’s actions.
- Evaluation of memory mechanisms involves both direct and indirect methods to assess how well the memory supports the agent. Direct evaluations include subjective human judgment or objective metrics like retrieval accuracy, while indirect evaluations test the agent’s performance on tasks requiring long-term memory, such as conversation continuity, multi-step reasoning, or knowledge-based question answering.



